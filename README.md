# Simulación de las estrellas de una galaxia con método Monte Carlo

descripción



## Como funciona
Definiremos `n` al comienzo del código como el número de estrellas de la galaxia que queremos simular.
#### Funciones

- `stars(n)`: esta función tiene como input `n` y retorna dos arrays llamados en la función `star_mass` y `star_alpha`.
  - `star_mass`: array de n elementos con masas aleatorias para las estrellas entre 0.08 y 100 masas solares.
  - `star_alpha`: array de n elementos con los valores de alpha correspondientes a las masas del array `star_mass` siguiendo la definición de [Kroupa 2001](https://arxiv.org/abs/astro-ph/0009005)

- `SFR(n)`: esta función tiene como input `n` y retorna un array llamado en la función `birth_time`. La función distribuye la fomación de las estrellas simuladas de forma uniforme en un rango de edades entre 0 y 10 [Gyr] para obtener como resultado una tasa de formación estelar constante.
  - `birth_time`: array de n elementos con el tiempo en el que se formó cada estrella de la simulación.

- `MS_lf(n, star_mass)`: esta función tiene como inputs `n` y `star_mass` retornando un array llamado en la función `lifetime`.
  - `lifetime`: array de n elementos que indican el tiempo que cada estrella necesita para salir de la secuencia principal y terminar como una remanente.

- `remnant(star_mass, birth_time, lifetime)`: esta función tiene como inputs `star_mass`, `birth_time` y `lifetime`, por lo que depende de las tres funciones anteriormente definidas. Como output entrega dos arrays llamados en la función `remanente` y `final_mass`.
  - `remanente`: array de n elementos que indican el remanente en el que se convirtieron las estrellas al final de la simulación en caso de que sus `lifetime` sean mayores que su `birth_time` donde `1` indica 'Enana Blanca', `2` indica 'Estrella de Neutrones' y `3` indica 'Agujero Negro'. En el caso contrario, es decir, que sus `lifetime` sean menores que su `birth_time` no habrá remanente donde `0` indica que la estrella sigue en la secuencia principal.
  - `final_mass`: es un array de n elementos que indican la masa final de los remanentes de las estrellas. Si la estrella sigue en la secuencia principal se deja la masa inicial de la estrella. Las masas finales siguen las ecuaciones de [Kalirai 2008](https://arxiv.org/abs/0706.3894) para enanas blancas y [Raithel 2018](https://arxiv.org/abs/1712.00021) para estrellas de neutrones y agujeros negros, todas con ligeras modificaciones para modelar todo nuestro rango de masas.

## Flowchart

![flowchart](Flowchart.png)
