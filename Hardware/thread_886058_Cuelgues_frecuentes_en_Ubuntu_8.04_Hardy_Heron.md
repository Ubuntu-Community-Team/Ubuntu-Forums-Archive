---
title: "Cuelgues frecuentes en Ubuntu 8.04 Hardy Heron"
date: 2008-08-10
forum: Hardware
---

### Post by caparral on 2008-08-10
*No sé que esta pasando últimamente pero Ubuntu se queda trabado y no responde a ninguna tecla, dejando como única opción apagarlo manualmente, eso me preocupa porque anteriormente no pasaba, no ejecuto demasiadas aplicaciones para poder pensar que ello lo puede estar ocasionando, aunque para dar datos específicos lo único que ejecuto es Compiz y mayormente Firefox, pero como dije anteriormente no tenía ningún problema tiempo atrás, también de un día para acá se me viene desconfigurando el touchpad,específicamente el scroll de éste, se desconfigura y ya no lo puedo utilizar sino hasta que cierre sesión, reinicie o apague el sistema ¿a alguien más le esta sucediendo? ¿qué pudiera ser? ¿Alguna solución que me recomienden? Mi máquina es una HP Pavilion DV6646us, saludos y muchas gracias de antemano!!!*

---

### Post by sergiom99 on 2008-08-10
esto te pasa despues de un rato de usarlo? despues de recuperar el sistema desde la hibernacion/suspension?
A mi alguna vez me paso lo del scroll del touchpad cuando retome desde el sistema suspendido, pero no le di mucha importancia porque generalmente uso un minimouse wireless en vez del touchpad.

---

### Post by caparral on 2008-08-11
*Bueno de que se me trabe sucede después de estar trabajando un rato, algo que me parece raro, quizás no lo notaba anteriormente porque no duraba más de 30 minutos en Ubuntu. Respecto a lo de la desconfiguración del scroll en el touchpad sucede mientras el sistema estaba en suspensión y reactivo el ingreso a éste, pero de vez en cuando en pleno uso se desconfigura después de un rato, cierro la tapa de la lap y vuelvo a abrirla y ya vuelve a funcionar el scroll del touchpad, eso no es lo que me preocupa, sino porque de 1 día para acá se me está trabando el SO sin dejarme opción de hacer nada, algo de lo cual no tengo idea, quien este pasando por el mismo problema o sepa algo para solucionarlo que lo comente por favor!!!*

---

### Post by Mauro22 on 2008-08-11
Los cuelgues como son?

Totales, o podes mover el mouse?

Duran mucho o poco?

Te comento, a mi se me congelaba el entorno grafico, pero podia mover el mouse. Se soluciono al desinstalar el paquete: powernowd

```
sudo apt-get purge powernowd
```


PD: No tengo la misma PC pero si los cuelgues son asi, proba eso.

---

### Post by caparral on 2008-08-11
> **Mauro22 said:**
> Los cuelgues como son?

Totales, o podes mover el mouse?

Duran mucho o poco?

Te comento, a mi se me congelaba el entorno grafico, pero podia mover el mouse. Se soluciono al desinstalar el paquete: powernowd

PD: No tengo la misma PC pero si los cuelgues son asi, proba eso.

*Como explico en el post principal, son cuelgues totales, de los cuales no puedo realizar ninguna acción, no puedo mover mouse, no puedo hacer absolutamente nada más que apagar el sistema de modo manual!!!*

---

### Post by sergiom99 on 2008-08-11
instalaste algo que te acuerdes ultimamente?
como para tener idea a partir de que buscar.

---

### Post by caparral on 2008-08-11
*Sí he instalado cosas pero no recuerdo cuales, la mayoría directamente de repositorios, hoy no he experimentado cuelgue alguno, pero lo que si he identificado en que momento me comienza a fallar el touchpad, resulta que cuando me pongo a escribir en los foros, como este xD el cursor que se muestra intermitente al escribir en el recuadro, desaparece de la sección donde me había quedado escribiendo la última palabra o letra y si muevo el cursor fuera de ese recuedro la línea intermitente que se muestra al editar el texto desaparece y tengo que volverme a situar con el cursor del touchpad en la zona donde me quedé o si muevo el cursor del touchpad para editar una letra anterior y no la modifico con el cursor en la zona a editar se me regresa a la última sección donde escribí algo, digamos cuando esta funcional, ubico con el cursor del touchpad la zona a editar y puedo mover el mouse a donde yo quiera y seguirá ahí el cursor intermitente de texto escribiendo donde yo lo coloqué y cuando no esta funcional sino mantengo el cursor del mouse en la zona a editar se va a la ultima zona donde puse algo o se va a donde quiere, todo esto provocando que el scroll quede sin uso en el touchpad, eso es lo que sucede!!!*

---

### Post by h9005 on 2008-08-11
Que buen avatar quien es la de la foto mauro 222?

---

### Post by Mauro22 on 2008-08-11
No se, jeje, "la chica firefox" :popcorn:

---

### Post by [P]oli on 2008-08-11
> **Mauro22 said:**
> No se, jeje, "la chica firefox" :popcorn:

[OffTopic] Dejá de sacarle fotos a mi novia ¬¬ [/OffTopic]

---

