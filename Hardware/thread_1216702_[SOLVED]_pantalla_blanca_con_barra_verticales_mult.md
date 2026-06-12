---
title: "[SOLVED] pantalla blanca con barra verticales multicolores"
date: 2009-07-18
forum: Hardware
---

### Post by obedlink on 2009-07-18
hola

quiero que me ayuden con este problema que me sucede usando varias distribuciones, este problema me pasa con ubuntu 8.04, ubunut 8.10, OpenSUSE 11.1 y ahora con la build del 16 de julio de ubuntu 9.10.

el problema es cuando meto el liveCD y le doy a "probar ubuntu si alterar mi equipo" o "instalar" casi de inmediato la pantalla se pone de color blanco y poco a poco empiezan a aparecer barras verticales multicolores y con el tiempo realtan mas y la laptop se queda bloqueada, no puedo entrar en la consola "ctrl+alt+f2". hoy realice una prueba instalando con el Disco Alternativo "instalación modo texto" pero luego de reiniciar, al cargar el GDM otra vez la pantalla blanca :(. solo que en este caso si puedo entrar a consola.

pero mi preocupación es que descargue la build del 16 de julio de ubuntu 9.10 y me dá el mismo problema, cosa que la alpha 2 no lo hace y me preocupa que este problema se mantenga hasta la versión final.

que puedo hacer en este caso?, como puedo dar aviso a canonical de este bug para que se solucione y pueda disfrutar de ubuntu 9.10 cuando se lanzado?

mis especificaciones son:
Laptop Dell Studio 1535
Core 2 Duo T5800 2.0 Ghz
4GB Ram DDR2 667Mhz
Intel Graphics GMA965
chipset Intel 965 Express

esos datos son los mas importantes, el resto no creo que sea necesario, ya que el problema es de indole grafico.

dejo una foto, no es de laptop, la encontre en google pero lo que si se es que es una dell Studio con el mismo problema.

[IMG]http://s3.amazonaws.com/satisfaction-production/s3_images/14588/p_inline.jpg[/IMG]

---

### Post by guillermolisi on 2009-07-18
Hay todo un tema con las placas de video Intel 965 como la que tiene tu notebook.

Si te fijas bien, hay cantidad de threads que hablan sobre el tema (Search this forum - Intel 965, y te aparecen todos).

---

### Post by obedlink on 2009-07-25
Problema solucionado!!!

bueno explico, entre ubuntu 8.04, 8.10 y la reciente beta 3 de ubuntu 9.10, la unica que me arranca el Xserver en modo "grafico Seguro" es el ubuntu 8.10, la terminar de instalar el ubuntu 8.10 entre sin ningun problema al sistema lo unico malo es que con una resolucion muy pequeña 800x600, edite el xorg y vi qe en "section device" aparecia driver "vesa" por lo que lo cambie a "intel", reinicie y de nuevo la pantalla blanca, en ese momento se me vino a la mente la pregunta "¿estarán instalados los drivers de intel?", entre en modo consolo y escribi "sudo apt-get install xserver-xorg-video-intel" despues de instalar y de reiniciar gualá!!. resolucion nativa de mi monitor y los efectos de escritorios activados!!!

supongo que con ubuntu 8.04 y la reciente beta de ubuntu 9.10 se puede hacer lo mismo con la diferencia de que se tienen que instalar con el alternate CD, ya que en estos el "modo grafico seguro" no me funciona.

mas tarde instalare el beta 3 ubuntu 9.10 con el alternate CD y os contaré si tambien funciona.

---

