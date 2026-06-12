---
title: "Aceleracion 3D"
date: 2010-07-29
forum: Hardware
---

### Post by Tosh78 on 2010-07-29
Hola! Ayer tuve que reinstalar mi ubuntu 10.40 64bits y ahora resulta que no me reconoce la aceleracion 3D de mi placa.
Tengo una placa de video ATI Radeon HD y estoy usando el driver sugerido por Ubuntu (no los de la pagina de ATI). La cuestion es que cuando corro PlayOnLinux me aparece un cartel diciendo que no tengo aceleracion 3D. Antes no tenia ningun problema con esto. 
Alguien puede decirme como puedo hacer para activarla? Estuve googleando pero no pude encontrar una solucion a mi caso particular.
Aclaro que los efectos de escritorio funcionan perfectamente. Alguien puede darme una mano?

---

### Post by euzkoarima on 2010-07-30
La verdad no se, pero para ir "acotando" el problema: en juegos nativos de linux tenés el mismo problema ?

Si la respuesta es no, habría que ver que está pasando en wine.

Saludos,
Eduardo

---

### Post by Tosh78 on 2010-08-02
No tengo ningun juego nativo de linux y se me complica bajarlos. Hay algun comando que me pueda decir si esta habilitada o no?

---

### Post by euzkoarima on 2010-08-02
Si está instalado el driver de ati, debería figurarte como instalado el paquete fglrx.
De paso: que placa gráfica tenés, digo porque en las últimas versiones del driver dejaron de soportar placas viejas.

Saludos,
Eduardo

---

### Post by Tosh78 on 2010-08-03
Hola Eduardo! Gracias por contestar. Ese paquete esta instalado, con lo cual deberia entender que si tengo la aceleracion, no?

---

### Post by spydeyrch on 2010-08-03
Hola,

Lo que necesitas hacer es instalar los drivers propietarios de ATI. Tienes que ir al menú sistema -> administración - > "hardware".    Digo "hardware" porque no me acuerdo como se llama en español. Lo siento. :(.  Pero bueno, si haces eso, tu sistema debería encontrar los drivers propietarios de ATI que son adecuados para tu placa, o como decimos acá, tu tarjeta de gráficos. 

Ahora, lo que estaba diciendo euzkoarima es que si tu placa es una ya viejita, los nuevos drivers de ATI dejaron de soportarla. Pero por tu primer comentario, creo que tienes una placa HD de ATI. Yo tengo un ATI HD 3870. Y los nuevos drivers me funcionan muy bien.

Ojala te ayude mi comentario y si por acaso necesitas mas ayuda, no demores en buscarla aquí en el foro.

-Spydey :KS

---

### Post by Tosh78 on 2010-08-03
Gracias a ambos! Si, ya tengo instalados los drivers propietarios. Y mi placa es una HD Radeon 4570, con lo cual deberia funcionar bien, no?

---

### Post by spydeyrch on 2010-08-03
> **Tosh78 said:**
> Gracias a ambos! Si, ya tengo instalados los drivers propietarios. Y mi placa es una HD Radeon 4570, con lo cual deberia funcionar bien, no?


Si, debería funcionar bien con los driver propietarios. Pero  dices que aun con esos drivers, no funciona el PlayOnLinux?

Instalaste el PlayOnLinux antes de instalar los drivers de ATI? Eso puede ser el problema.

Creo que cuando instalas, y corrígeme si es que estoy equivocado, el PlayOnLinux (WINE), ese mismo programa busca los drivers gráficos que se están usando en ese mismo momento y los usa de ahí en adelante ..... aun y si instalas unos drivers nuevos o propietarios. 

Pero, puedo estar completamente equivocado en ese aspecto. Es que no he usado WINE/PlayOnLinux/CrossOver por un buen rato, como 1 año. Así que lo siento si estoy equivocado.

-Spydey :KS

---

### Post by euzkoarima on 2010-08-04
> **Tosh78 said:**
> Hola Eduardo! Gracias por contestar. Ese paquete esta instalado, con lo cual deberia entender que si tengo la aceleracion, no?

Si, debería andar la aceleración, y en otro post decís que tenés una 4570 o sea una placa nueva, soportada por el driver.

Para mi el problema está en la configuración que hay el PlayOnLinux del wine, pero la verdad que de wine se muy poco.

Saludos,
Eduardo

---

