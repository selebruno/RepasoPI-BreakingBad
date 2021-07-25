<p align='left'>
    <img src='https://static.wixstatic.com/media/85087f_0d84cbeaeb824fca8f7ff18d7c9eaafd~mv2.png/v1/fill/w_160,h_30,al_c,q_85,usm_0.66_1.00_0.01/Logo_completo_Color_1PNG.webp' </img>
</p>

# Repaso Proyecto Individual - Breaking Bad

<p align="left">
  <img height="200" src="./bb.png" />
</p>

## Objetivos del Proyecto

- Construir una App utlizando React, Redux, Node y Sequelize.
- Afirmar y conectar los conceptos aprendidos en la carrera.
- Aprender mejores prácticas.
- Aprender y practicar el workflow de GIT.
- Usar y practicar testing.


## BoilerPlate

El boilerplate cuenta con dos carpetas: `api` y `client`. En estas carpetas estará el código del back-end y el front-end respectivamente.

En `api` crear un archivo llamado: `.env` que tenga la siguiente forma:

```
DB_USER=usuariodepostgres
DB_PASSWORD=passwordDePostgres
DB_HOST=localhost
```

Reemplazar `usuariodepostgres` y `passwordDePostgres` con tus propias credenciales para conectarte a postgres. Este archivo va ser ignorado en la subida a github, ya que contiene información sensible (las credenciales).

Adicionalmente será necesario que creen desde psql una base de datos llamada `breakingbad`

El contenido de `client` fue creado usando: Create React App.

## Enunciado

La idea general es crear una aplicación en la cual se puedan ver distintos personajes de Breaking Bad junto con información relevante de los mismos utilizando la api externa [The Breaking Bad API](https://breakingbadapi.com/) y a partir de ella poder, entre otras cosas:

  - Buscar personajes
  - Filtrarlos / Ordenarlos
  - Agregar nuevos personajes

__IMPORTANTE__: Para poder utilizar esta API externa no es necesario crearse una cuenta.

__IMPORTANTE__: Para las funcionalidades de filtrado y ordenamiento NO pueden utilizar los endpoints de la API externa que ya devuelven los resultados filtrados u ordenados sino que deben realizarlo ustedes mismos. En particular alguno de los ordenamientos o filtrados debe si o si realizarse desde el frontend.

### Únicos Endpoints/Flags que pueden utilizar

  - GET https://breakingbadapi.com/api/characters
  - GET https://www.breakingbadapi.com/api/characters/?name={name}

### Requerimientos mínimos:


__IMPORTANTE__: No se permitirá utilizar librerías externas para aplicar estilos a la aplicación. Tendrán que utilizar CSS con algunas de las opciones que vimos en dicha clase (CSS puro, CSS Modules o Styled Components)

#### Tecnologías necesarias:
- [ ] React
- [ ] Redux
- [ ] Express
- [ ] Sequelize - Postgres

#### Frontend

Se debe desarrollar una aplicación de React/Redux que contenga las siguientes pantallas/rutas.

__Pagina inicial__: deben armar una landing page con
- [ ] Alguna imagen de fondo representativa al proyecto
- [ ] Botón para ingresar al home (`Ruta principal`)

__Ruta principal__: debe contener
- [ ] Input de búsqueda para encontrar personajes por nombre
- [ ] Área donde se verá el listado de personajes. Deberá mostrar su:
  - Imagen
  - Nombre
  - Nickname
- [ ] Botones/Opciones para filtrar por status y por personaje existente o agregado por nosotros
- [ ] Boton/Opcion para ordenar tanto ascendentemente como descendentemente los personajes por orden alfabético
- [ ] Paginado para ir buscando y mostrando los siguientes personajes

__IMPORTANTE__: Dentro de la Ruta Principal se deben mostrar tanto los personajes traidos desde la API como así también los de la base de datos.

__Ruta de detalle de personaje__: debe contener
- [ ] Los campos mostrados en la ruta principal para cada personaje (imagen, nombre y nickname)
- [ ] Ocupación
- [ ] Status
- [ ] Cumpleaños
- [ ] Temporadas en las que aparece

__Ruta de creación de personaje: debe contener
- [ ] Un formulario __controlado__ con los siguientes campos
  - Nombre
  - Nickname 
  - Cumpleaños 
  - Status
  - Imagen
- [ ] Posibilidad de seleccionar/agregar una o más ocupaciones
- [ ] Botón/Opción para crear un nuevo personaje
 

#### Base de datos

El modelo de la base de datos deberá tener las siguientes entidades (Aquellas propiedades marcadas con asterísco deben ser obligatorias):

- [ ] Personaje con las siguientes propiedades:
  - ID *
  - Nombre *
  - Nickname *
  - Cumpleaños *
  - Status
  - Imagen
- [ ] Ocupación con las siguientes propiedades:
  - ID
  - Nombre

La relación entre ambas entidades debe ser de muchos a muchos ya que un personaje puede tener varias "ocupaciones" en simultaneo y, a su vez, una "ocupación" puede corresponder a múltiples personajes. Por ejemplo, Kimberly Wexler es 'lawyer', pero a su vez existen otros personajes con esa ocupación.

__IMPORTANTE__: Pensar como modelar los IDs de los personajes en la base de datos. Existen distintas formas correctas de hacerlo pero tener en cuenta que cuando hagamos click en alguno, este puede provenir de la API o de la Base de Datos por lo que cuando muestre su detalle no debería haber ambigüedad en cual se debería mostrar. Por ejemplo si en la API el personaje Walter White ` tiene id = 1 y en nuestra base de datos creamos un nuevo personaje `Walter Black` con id = 1, ver la forma de diferenciarlas cuando querramos acceder al detalle de los mismos.

#### Backend

Se debe desarrollar un servidor en Node/Express con las siguientes rutas:

__IMPORTANTE__: No está permitido utilizar los filtrados, ordenamientos y paginados brindados por la API externa, todas estas funcionalidades tienen que implementarlas ustedes.

- [ ] __GET /characters__:
  - Obtener un listado de los primeros 6 personajes
  - Debe devolver solo los datos necesarios para la ruta principal
- [ ] __GET /characters?name="..."__:
  - Obtener un listado de los primeros 6 personajes que contengan la palabra ingresada como query parameter
  - Si no existe ningun personaje mostrar un mensaje adecuado
- [ ] __GET /character/{idPersonaje}__:
  - Obtener el detalle de un personaje en particular
  - Debe traer solo los datos pedidos en la ruta de detalle de personaje
  - Incluir las ocupaciones asociadas
- [ ] __GET /ocupaciones__:
  - Obtener todas las ocupaciones posibles
  - En una primera instancia deberán obtenerlas desde la API externa y guardarlas en su propia base de datos y luego ya utilizarlas desde allí
- [ ] __POST /character__:
  - Recibe los datos recolectados desde el formulario controlado de la ruta de creación de personaje por body
  - Crea un personaje en la base de datos

#### Testing
- [ ] Al menos tener un componente del frontend con sus tests respectivos
- [ ] Al menos tener una ruta del backend con sus tests respectivos
- [ ] Al menos tener un modelo de la base de datos con sus tests respectivos
