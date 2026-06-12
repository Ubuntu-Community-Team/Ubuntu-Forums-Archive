---
title: "Problema con cdrom"
date: 2009-05-15
forum: Hardware
---

### Post by thesolitary on 2009-05-15
Posteo porque soy nuevo en Ubuntu... vengo de Windows.
El tema es que salgo de Guatemala y entro en Guatepeor... en Ubuntu reniego mas que en Windows 3.11, seguramente el problema sea yo, porque a Windows le conosco tan de memoria los errores que me parece mas facil.

El tema es asi, tengo el modem MT882 por USB por lo tanto por ahora no tengo internet desde Ubuntu, estoy siguiendo una guia para instalarlo manualmente pero ni a eso le pego (probe UbuDSL y queda en "enchufe el modem" lo enchufo y sigue asi hasta la eternidad).

La guia es esta: [http://ubuntuforums.org/showthread.php?t=426944](http://ubuntuforums.org/showthread.php?t=426944)

El tema es que me trabo en el punto 1 (si, llegué re lejos xD) que es instalar el paquete essential. Probe de las dos formas, por codigo:

```
$ sudo apt-get install build-essential
```

Y por el administrador de Paquetes Synaptic. El error: "E: Failed to mount the cdrom"

Probe con 

```
$ sudo apt-cdrom add
```

Y lo mismo, lo curioso es que el CD esta metido y funciona bien y lo puedo abrir (el cd con el que instale Ubuntu)

Porque sera, Linux no me quiere? :(

---

### Post by emiliano_raso on 2009-05-15
Primero una pregunta:

Que maquina tenes? Y que version de Ubuntu tenes?

Porque leyendo [http://www.ubudsl.com/es/inicio.php](http://www.ubudsl.com/es/inicio.php) encontré que solo es soportado Ubuntu 8.04 Hardy Heron

> UbuDSL es una herramienta que le ayuda a configurar su conexión ADSL usando un modem USB en el Sistema Operativo Linux. Actualmente las distrubuciones soportadas son openSUSE 11.0 y Ubuntu 8.04.

---

### Post by thesolitary on 2009-05-15
> **emiliano_raso said:**
> Primero una pregunta:

Que maquina tenes? Y que version de Ubuntu tenes?

Porque leyendo [http://www.ubudsl.com/es/inicio.php](http://www.ubudsl.com/es/inicio.php) encontré que solo es soportado Ubuntu 8.04 Hardy Heron

Creo que me equivoque iba en Software esto mepa.

La maquina es
Mother Board Asus M2N-MX con GeForce 6150
Microprocesador AMD 64x2 Athlon 4000
Disco rígido SATAII 160GB Western Digital
2GB de RAM (1x2) Corsair 667MHZ

(No esta en 64)

Ubuntu tengo 9.04, capaz que es eso, pero aca mismo un usuario le anduvo bien UbuDSL en Ubuntu 9.04.

Que decis que puede ser?

---

### Post by Mauro22 on 2009-05-16
Si no me equivoco 

$ sudo apt-get install build-essential


el paquete build-essential se baja de internet, y como no tenes todavia, el unico repositorio que tiene es el cd, ahora porque da error el cd no se.


Si lo pones tiene que decir que encontre "Origines de Software" o algo asi, y te da la opcion de agregarlo, 

por ahi tenes que hace un:

sudo apt-get update

para actualizar la lista de paquetes, pero no se si funciona con un cd.

---

### Post by Hei Ku on 2009-05-16
Si pones el cd, podes acceder al contenido? Te lo monta bien automaticamente?
Digo, fuera de synaptics, abriendolo con Nautilius u otro explorador de archivos.

---

### Post by thesolitary on 2009-05-16
> **Hei Ku said:**
> Si pones el cd, podes acceder al contenido? Te lo monta bien automaticamente?
Digo, fuera de synaptics, abriendolo con Nautilius u otro explorador de archivos.

Si me anda perfecto... me lo monta al toque porque me aparece en el escritorio y puedo entrar.
La verdad que si no saben ustedes imaginense yo...

Lo de UbuDSL es cierto, funciona con 8.04 solamente.. me equivoque. Capaz que me bajo esa y fue

---

### Post by Hei Ku on 2009-05-16
Para sortear el problema, podes ir a Synaptic, en la parte de administrar repositorios, y buscar donde figura el CD-ROM y deshabilitarlo. Con eso va a bajar los paquetes directo de internet.

---

### Post by Mauro22 on 2009-05-16
> **Hei Ku said:**
> Con eso va a bajar los paquetes directo de internet.


No tiene internet.

> El tema es asi, tengo el modem MT882 por USB por lo tanto por ahora no tengo internet desde Ubuntu

---

### Post by Hei Ku on 2009-05-16
Cierto.

Probaste desde consola con sudo apt-get install build-essential

Quizas eso nos da un poco mas de información sobre por qué esta fallando.

Por otro lado, no te podes conectar por Ethernet y poner el modem en modo routable? No tiene una salida ethernet ademas de la USB?

---

