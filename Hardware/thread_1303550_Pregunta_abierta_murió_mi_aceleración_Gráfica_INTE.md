---
title: "Pregunta abierta: murió mi aceleración Gráfica INTEL en Jaunty"
date: 2009-10-28
forum: Hardware
---

### Post by HayatoJin on 2009-10-28
Pregunta...
Tengo un Notebook Easy Note E4715 PackardBell con tarjeta INTEL 
(Intel Extreme Graphics 2 Video Controller)...El modelo específico no lo tengo a mano en este momento...

EL tema es que estaba instalando una actualización, en la que incorporaba el Kernel que trae el "kernelmodesetting" incorporado...

Despues de reiniciar, me apareció: el siguiente error:

```
"Ubuntu is running in low graphics mode
 The folowing error was encountered. You may need to update your configuration to solve this.
 EE Intel (0): No kernel modestting driver detected
EE Screen(1): Found but none have a usable configuration."


```Revisando en internet encontré esta página:

[http://www.ubuntu-es.org/?q=node/119072](http://www.ubuntu-es.org/?q=node/119072)

En la que me recomendaban algunas "soluciones". No se si fue debido a mi ignorancia o que no tenia el mismo problema que yo, pero la solución solo me funciona a medias:

-Volví a un driver "anterior" (con lo que obtuve mi resolución anterior de 1024x768 )
-Active al "compositing" "a mano"

El tema es que desde ese día JAMÁS volví a poder activar los efectos de escritorio...he probado "glxgears" y me dice que está activada la aceleración, he manoseado harto el xorg.config...y nada.

(Aparte he actualizado el sistema 2 veces y cada vez que actualizo vuelvo a tener el 
error de "Ubuntu is running in low graphics mode")

¿Alguien me puede decir que pasa?

(Estoy esperando a mañana para empezar a bajar 9.10 y ver si con eso se soluciona)

---

### Post by moreback on 2009-10-30
Haz que tu Ubuntu parta con un kernel oficial, yo tengo una tarjeta Intel y con los kernels oficiales no he tenido problemas.

---

