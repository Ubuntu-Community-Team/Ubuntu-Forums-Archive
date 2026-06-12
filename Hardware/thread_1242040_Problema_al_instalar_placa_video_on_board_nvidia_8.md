---
title: "Problema al instalar placa video on board nvidia 8200"
date: 2009-08-16
forum: Hardware
---

### Post by rojojuan on 2009-08-16
Paso a contarles el problema. Instalé Jaunty en una máquina nueva (ECS con AMD x3). Este mother tiene una placa integrada Nvidia 8200 y probé instalar los driver privativos desde Jaunty, pero funciona mal. Encontré otra ayuda que decía instalar el driver 180 modaliasis desde un servidor y también instalar desde Synaptics nvidia-glx-180. Probé también correr nvidia-xconfig. La cuestión es que cuando paso el puntero sobre la  barra superior de la pantalla, comienza a titilar muy rápido. Corregí el el xorg.conf la resolución del monitor (de tanto manoseo estaba mal y le coloqué la indicada en el manual. Mejoró un poco, tiene aceleración gráfica (glxgears ok) pero además de ese “parpadeo” los videos se ven muy lentos.
Estuve leyendo también que uno de los problemas puede ser un bug de Jaunty para administrar esa placa on board. 
Si alguien puede darme una mano, desde ya agradecido.

---

### Post by mama21mama on 2009-08-16
Hola, yo diria que instales la versión del driver 185.18.31 

Corrige muchas cosas: instalacon [http://mamalibre.eshost.com.ar/?q=node/213](http://mamalibre.eshost.com.ar/?q=node/213)

Saludos

---

### Post by rojojuan on 2009-08-16
> **mama21mama said:**
> Hola, yo diria que instales la versión del driver 185.18.31 

Corrige muchas cosas: instalacon [http://mamalibre.eshost.com.ar/?q=node/213](http://mamalibre.eshost.com.ar/?q=node/213)

Saludos

Gracias por el aporte. Instalé este driver y sigue todo igual. Alguna otra idea? Se espera que la próxima versione de Nvidia corrija este problema? Me parece que la cuestión son las placas on board, no?

---

### Post by mama21mama on 2009-08-16
Hola, yo tengo ese con el ultimo kernel 2.6.30.4 y funciona, tambien tengo una onboar GeForce 7050/nForce 610i 

Saludos

---

### Post by rojojuan on 2009-08-18
> **mama21mama said:**
> Hola, yo tengo ese con el ultimo kernel 2.6.30.4 y funciona, tambien tengo una onboar GeForce 7050/nForce 610i 

Saludos

Bueno, el propietario de la máqina la necesita para trabajar, así que la llevó así y más adelante vemos. Gracias por tu ayuda.

---

