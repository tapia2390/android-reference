# Buenas prácticas de desarrollo Android

A continuación encontrarán una serie de buenas prácticas a tomar en cuenta para a la hora de programar aplicaciones móviles
para las plataformas Android.
Como bien sabemos a la hora de desarrollar aplicaciones nativas para Android, usamos el lenguaje de programación Java y en esta
ocación el IDE oficial Android Studio.
Si bien Android Studio nos ofrece de por defecto la estructura general del proyecto, a medida que vayamos profundizando en el desarrollo
de una aplicación o vayamos creando aplicaciones más complejas necesitaremos crear un código entendible por cualquier miembro del equipo,
un código modular que pueda ser escalable fácilmente y por sobre todo un código limpio basándonos en estándares de programación que
solo los buenos desarrolladores siguen.


https://github.com/futurice/android-best-practices
https://github.com/futurice/android-best-practices/tree/master/templates/rx-architecture


## Estructura del proyecto

### Estructura base
```
├─ app
│  ├─ libs
│  ├─ src
│  │  ├─ androidTest
│  │  │  └─ java
│  │  │     └─ com/domain/project
│  │  └─ main
│  │     ├─ java
│  │     │  └─ com/domain/project
│  │     ├─ res
│  │     └─ AndroidManifest.xml
│  ├─ build.gradle
│  └─ proguard-rules.pro
├─ build.gradle
└─ settings.gradle
```

### Estructura JAVA

#### Nomenclatura de paquetes
Los paquetes se nombran en singular y con letras minúsculas.
```
activity
fragment
adapter
model
util
```

#### Nomenclatura de clases
Las clases java se nombran utilizando el estándar “UpperCamelCase”, es decir utilizando
una combinación de palabras que empiezan con mayúscula como “ClasePrincipal”.
```
MainActivity
LoginActivity
RegisterFragment
DetailFragment
```

### Comentar una clases
```java
/**
  * Initializing GUI
  **/
private void init() {
    Toolbar toolbar = (Toolbar) findViewById(R.id.toolbar);
    TextView text = (TextView) findViewById(R.id.text);
}
```

### Estructura RES

#### Nomenclatura de paquetes
Al igual que en la sección Java, también se nombran los paquetes en minúsculas pero
no siempre en singular, habrá casos en los que usemos plurales como la carpeta “values”
y otros casos donde se usan guiones como en el caso de crear carpetas para para soporte de
de versiones android como “values-v21”.
```
drawable
layout
manu
values
values-v21
```

### Definir formato de Colors.xml

```xml
<resources>
    <color name="colorPrimary">@color/black</color>
    <color name="colorPrimaryDark">@color/green</color>
    <color name="colorAccent">@color/white</color>

    <!-- basic colors -->
    <color name="white">#FFFFFF</color>
    <color name="black">#000000</color>
    <color name="green">#27D34D</color>
    <color name="blue">#2A91BD</color>
    <color name="orange">#FF9D2F</color>
    <color name="red">#FF432F</color>

    <!-- opacity white -->
    <color name="white_100">#00FFFFFF</color>
    <color name="white_75">#BFFFFFFF</color>
    <color name="white_50">#80FFFFFF</color>
</resources>
```

### Definir cadenas estáticas por pantalla en strings.xml

```xml
<resources>
    <string name="app_name">Abaco</string>
    <!-- activity_menu -->
    <string name="menu_home">Inicio</string>
    <string name="menu_contact">Contactos</string>
    <string name="menu_profile">Perfil</string>
    <!-- fragment_profile -->
    <string name="label_lastname">Apellido</string>
    <string name="label_name">Nombre</string>
</resources>
```

#### Uso de las carpetas “mipmap“ y “drawable”
Android Studio nos provee por defecto de ambas carpetas para almacenar los recursos gráficos del proyecto.

La carpeta `mipmap`, sirve exclusivamente para almacenar el icon launcher de la aplicación, es decir que solo
almacenará los archivos `ic_launcher.png` y su distribución será así:
```
├─ mipmap-hdpi
│  ├─ ic_launcher.png
│  |
├─ mipmap-mdpi
│  ├─ ic_launcher.png
│  |
├─ mipmap-xhdpi
│  ├─ ic_launcher.png
│  |
├─ mipmap-xxhdpi
│  ├─ ic_launcher.png
│  |
├─ mipmap-xxxhdpi
│  ├─ ic_launcher.png
│  |
```

La carpeta `drawable`, sirve para almacenar recursos .xml tales como los selector, shape y derivados.
La carpeta `drawable-hdpi`, `drawable-xhdpi`y demás sirven para almcenar los recursos gráficos de la aplicación, como íconos, logos, imágenes de fondo, etc.

#### Utilizar fuentes de texto
Si bien Androi Studio no nos provee de una carpeta por defecto para almacenar archivos .ttf .otf o derivados, podemos optar por crear nuestra propia
paquetería para almacenar otros archivos que no sea recursos gráficos.

Crearemos una carpeta llamanda `assets` y dentro crearemos la carpeta `font`, aquí podremos guardar nuestros archivos .ttf o derivados.

```
─ main
   ├─ assets
   │  └─ font
   ├─ java
   │  └─ com/domain/project
   ├─ res
   └─ AndroidManifest.xml
```

### Crear tus componentes customizados (widgets)

## TextView customizados


### Crea tus utilitarios
A medida que ganamos experiencia como desarrolladores, generamos código que puede ser reutilizable los más comunes
son los utilitarios, pequeñas clases con funciones específicas como por ejemplo un utilitario cuyo único objetivo es
retornar la cantidad de días que han transcurrido desde el origen del mundo hasta la fecha de hoy.

```
─ main
   ├─ assets
   │  └─ font
   ├─ java
   │  └─ com/domain/project
   │     └─ activity
   │     └─ fragment
   │     └─ util
   ├─ res
   └─ AndroidManifest.xml
```
