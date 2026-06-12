---
title: "huuf : Genera reportes de tu equipo para solicitar ayuda"
date: 2010-02-19
forum: Hardware
---

### Post by Carlos C on 2010-02-19
[IMG]http://img694.imageshack.us/img694/4442/huuf.png[/IMG]

En caso de que necesites solicitar ayuda en el foro y desconozcas las características de tu equipo, te recomendamos instalar huuf. Es un pequeño front end en python que desplegará la información que necesitamos para ayudarte.

Puedes encontrar la última versión en [https://launchpad.net/huuf](https://launchpad.net/huuf). Existe un PPA que puedes agregar a tu lista de repositorios y así mantener huuf actualizado.

[FONT=Arial Black][SIZE=2]1. Cómo agregar el PPA:[/SIZE][/FONT]

1.1. Los usuarios de Karmic pueden agregar el repo mediante el comando:

```
sudo add-apt-repository ppa:kamus/huuf
```1.2. Usuarios de Jaunty y versiones anteriores deben editar su archivo /etc/apt/sources.list y añadir las siguientes líneas:

```
deb http://ppa.launchpad.net/kamus/huuf/ubuntu karmic main 
deb-src http://ppa.launchpad.net/kamus/huuf/ubuntu karmic main
```En el terminal escribes el siguiente comando para añadir la llave correspondiente:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EAB1CAD4

```Ahora actualizas el listado de software disponible:
```
sudo apt-get update
```[FONT=Arial Black][SIZE=2]2. Cómo instalar huuf:[/SIZE][/FONT]
En el terminal escribes:
```
sudo aptitude install huuf
```Este proyecto está en desarrollo y se originó a partir de [FUCH]("http://ubuntuforums.org/showthread.php?t=1211568&page=3"), una iniciativa llevada a cabo por miembros de Ubuntu Chile.
No dudes en reportar cualquier tipo de bug en launchpad.

[IMG]http://img717.imageshack.us/img717/2908/huuf2.png[/IMG]

---

### Post by Maciett on 2010-06-23
Hola,

me acordé de este programa para ver las características del pc, y lo traté de instalar, pero dice:

 ```
sudo apt-get install huuf
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
No se pudieron instalar algunos paquetes. Esto puede significar que
usted pidió una situación imposible o, si está usando la distribución
inestable, que algunos paquetes necesarios no han sido creados o han
sido movidos fuera de Incoming.
La siguiente información puede ayudar a resolver la situación:

Los siguientes paquetes tienen dependencias incumplidas:
  huuf: Depende: python-gtksourceview pero no es instalable
        Depende: python-desktopcouch-records pero no es instalable
E: Paquetes rotos
```

Espero poder instalarlo.

Saludos

---

### Post by Patriciologico on 2010-07-31
No anda el repositorio de Kamus

---

