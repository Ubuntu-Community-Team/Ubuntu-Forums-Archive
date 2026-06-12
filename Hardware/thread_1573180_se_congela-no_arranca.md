---
title: "se congela-no arranca"
date: 2010-09-12
forum: Hardware
---

### Post by joseluis on 2010-09-12
hola amigos, 
en uno de mis discos tengo ubuntu 10.04 y en otro disco tengo ubuntu studio 10.10 beta. Ayer apareció, parece, una actualización importante para studio, y me bajó varios paquetes.
La cuestión es que luego de haber bajado todo, me pidió reiniciar, reinicio, y después no arrancó nunca más. 
Se puede ver la pantalla de inicio, pero no sale de ahi.
Si se inicia desde modo gráfico seguro, eso si,sin problemas. Y tambien inicia el otro ubuntu desde el otro disco.
Pero el ubuntu studio 10.10 solo entra en modo gráfico seguro.
Hoy volvió a bajar nuevas actualizaciones, con lo que pensé que se podría resolver el problema, y nada.
¿alguna sugerencia?
gracias por la ayuda que puedan brindarme

---

### Post by Applelnx on 2010-09-12
Puede ser un problema de los controladores de la placa de video. Cuales tenias instalados? Los privativos?

A mi me habia pasado algo similar despues de una actualizacion de kernel, Ubuntu solo me arrancaba en modo graficos seguro y tuve que reinstalar los controladores privativos de ATI.

Saludos

---

### Post by joseluis on 2010-09-12
si..tengo una tarjeta nvidia, con controladores privativos. Voy a probar eso que me contás a ver qué pasa. Luego aviso. gracias


EDITO: Si..es tal cual así como decís. Desinstalé el controlador de la tarjeta nvidia y arrancó muy bien. Lo volví a instalar luego, y volvió a congelarse. Por lo tanto lo que hice es desinstalarlo definitivamente. 
¿se podrá solucionar?

---

### Post by Applelnx on 2010-09-12
Sinceramente no se mucho del tema, cuando me habia pasado a mi, yo los reinstale y volvieron a funcionar bien. Aparentemente se habian desconfigurado con la actualizacion. Estaria bueno que indiques que placa tenes asi alguien que sepa mas del tema te puede dar una mano.

Saludos

---

### Post by josecuervo86 on 2010-09-12
Probaste bajando el controlador directamente desde la pagina de nVidia? **[0]** proba bajando los controladores para tu placa desde ahi e instalandolos manualmente. 
```
sudo sh ./nombredelcontrolador.run
```

**[0]** [http://www.nvidia.com/Download/index.aspx?lang=es](http://www.nvidia.com/Download/index.aspx?lang=es)

---

### Post by joseluis on 2010-09-12
bajé el driver del sitio de nvidia, lo instalé tal como dicen, y nada. No resolvió. Sin dudas es un tema de drivers, porque como dije antes, lo saco y arranca.

---

### Post by josecuervo86 on 2010-09-12
Si no entiendo mal Ubuntu 10.04 anda bien con el controlador, pero Ubuntu Studio se freeza no es asi? Estan usando el mismo controlador? Si estan usando el mismo controlador no creo que sea problemas de drivers. Por otro lado si no lei mal estas usando una Beta de Ubuntu Studio, y como bien dice el nombre, es una **Beta**. Si fuera vos probaria usar el último driver que sabes que anduvo bien, que asumo debe ser el mismo que estas usando en Ubuntu Desktop 10.04

---

### Post by josecuervo86 on 2010-09-12
Fijate aca, hay una **posible** solución a tu problemita: [http://ubuntuforums.org/showthread.php?t=1572254](http://ubuntuforums.org/showthread.php?t=1572254)

---

### Post by joseluis on 2010-09-13
Lo que dice aquí es relatar lo que al parecer me pasa a mi. Gracias. y todo de acuerdo.
La solución que sugieren es lo que yo ya hice, asi que deberé esperar la RC y la Final. Me parece.


Según veo en mi otra partición, en la que tengo ubuntu 10.04, el controlador que está usando es la versión 173.
Ahora, pasando a ubuntu 10.10, cuando pido ver el driver que pueda bajar, no me da opciones de versiones, solo uno que no dice cual es.
No encuentro, no está, en el menú la opción de ingresar a "Controladores de Hardware".
Según SysInfo, me reconoce perfectamente la nvidia 7100
Baje también la versión 173 desde el centro de software,pero no aparece la opción de elegirla entre los controladores a usar por la tarjeta.

bueno..esos son los detalles.

---

### Post by guillermolisi on 2010-09-13
> **joseluis said:**
> Lo que dice aquí es relatar lo que al parecer me pasa a mi. Gracias. y todo de acuerdo.
La solución que sugieren es lo que yo ya hice, asi que deberé esperar la RC y la Final. Me parece.

Podes esperar o informar el problema para aportar a los casos fallidos y que trabajen en una solucion.

Si no recuerdo mal, en la seccion principal de este subforo hay un sticky thread, hecho en Español por Sajnox, que explica como informar bugs.

Recuerden que las versiones no finales, aun en desarrollo, son para experimentar y no se las recomienda para entornos en produccion.

---

### Post by joseluis on 2010-09-13
si...gracias!
voy a ver cómo es esto. Primero parece que tengo que ver si es en verdad un bug, y luego ver cómo lo reporto. Parece que es todo un trabajo.
Voy a ver còmo lo hago

---

