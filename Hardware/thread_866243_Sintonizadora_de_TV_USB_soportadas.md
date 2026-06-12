---
title: "Sintonizadora de TV USB soportadas?"
date: 2008-07-21
forum: Hardware
---

### Post by marcosba on 2008-07-21
Gente, ando buscando informacion de alguna sintonizadora de TV que ande sin problemas en Ubuntu. El Requisito, ademas de la compatibilidad, es que sea USB debido a que es para mi Notebook.

Yo vivo en Buenos Aires, Capital Federal. Alguno tiene idea de las que estan en el mercado cual puede andar?

Saludos y gracias.

---

### Post by faktorqm on 2008-07-22
Markitos! sos vo? jajajajaj

[http://www.neoteo.com/ces-2007-hauppauge-presenta-su-sintonizador-de-tv.neo](http://www.neoteo.com/ces-2007-hauppauge-presenta-su-sintonizador-de-tv.neo)
[http://100carretas.es/2007/11/01/redbell-tdt-2go-usb-en-ubuntu-gutsy-gibbon-710/](http://100carretas.es/2007/11/01/redbell-tdt-2go-usb-en-ubuntu-gutsy-gibbon-710/)
[http://crysol.inf-cr.uclm.es/node/289](http://crysol.inf-cr.uclm.es/node/289)

Hauppauge WinTV USB y Hauppauge WinTV USB 2 estan soportadas, dice aca: [http://www.linuxtv.org/wiki/index.php/Analog_TV](http://www.linuxtv.org/wiki/index.php/Analog_TV)

Esta jodida la cosa parece..... Salu2!

---

### Post by marcosba on 2008-07-22
El Mismo!

Responde mi pregunta Pippon!!!! jajaja

Toy buscando pero es complicado por USB. los fabricantes no dan en las especificaciones los chip que llevan las sintonizadoras

---

### Post by eldragon on 2008-07-22
si tenes una cpu medio vieja abandonada, compra una pci y ponesela a esa cajota. instalas mythbuntu (o solo el backend) y tenes television inalambrica en tu notebook o cualquier otra pc con ubuntu.

eso hice yo y anda de pelos, incluso baja la programacion de la pagina de multicanal.

vas a necesitar un buen disco rigidio para mythtv (y con buen disco, digo grande, no rapido).

yo uso una basada en el chip saa3174 de phillips y anda de pelos.

no es la respuesta que buscabas, pero por lo menos es una idea.

ya que lo conoces al pibe este de estudiantes, lo invitas a tomar una birra y te ayuda a configurar todo.

---

### Post by marcosba on 2008-07-22
Ya habia pensado esa posibilidad,pero ya tengo un servidor con ubuntu ke es para filesharing, alojo mi weg, ftp, descarga de torrents, server de mp3, etc. en una buena maquina. queria testear justo eso que decis, pero no quiero gastar plata para andar testeando.

Hay una placa en el mercado que sepas que anda de 10?

---

### Post by eldragon on 2008-07-22
yo tengo una pinnacle PCTV 10. no es muy clara la definicion....

tenia un PCB bastante mas profesional que las demas. pero no esta bien protegido contra interferencias el circuito modulador RF y la señal no es muy clara. (quiza yo soy medio cabron...)

pero andar, anda 10 puntos, no tenes que hacer nada para instalarla. solo enchufarla.

cualquier placa que tenga el chipset saa3174 deberia de andar bien.

cuando vayas a comprar, fijate que tenga protejido el circuito RF con una chapa de metal. cuando lo veas, vas a ver a lo que me refiero. el modelo del chipset aparece escrito en chiquitito sobre la cucaracha mas grande en el impreso :D

y si tenes tiempo, anota todos los modelos, corre a internet, y fijate cuales realmente andan bien.

instalar mythtv puede ser algo complicado, pero una vez que anda, no para.

---

### Post by vk-cdg on 2008-07-22
La ENCORE ENLTV-FM anda bien.

---

### Post by FlyerDie on 2008-07-22
> **vk-cdg said:**
> La ENCORE ENLTV-FM anda bien.

Esta es la que va como piña en UBUNTU? (ya me canse de lidiar con la LTT200 de LG)

[http://articulo.mercadolibre.com.ar/MLA-38187242-sintonizadora-y-capturadora-de-tv-controlremoto-encore-pci-_JM](http://articulo.mercadolibre.com.ar/MLA-38187242-sintonizadora-y-capturadora-de-tv-controlremoto-encore-pci-_JM)

Saludos!

---

### Post by marcosba on 2008-07-22
> **FlyerDie said:**
> Esta es la que va como piña en UBUNTU? (ya me canse de lidiar con la LTT200 de LG)

[http://articulo.mercadolibre.com.ar/MLA-38187242-sintonizadora-y-capturadora-de-tv-controlremoto-encore-pci-_JM](http://articulo.mercadolibre.com.ar/MLA-38187242-sintonizadora-y-capturadora-de-tv-controlremoto-encore-pci-_JM)

Saludos!

Posta anda de 10 en ubuntu esa??

que soft usaste para mirar tele con esa?

anda el composite?

=============
Agrego: no tubiste quilombo con esa placa, porque con Encore muchas buenas experiencias, por no decir ninguna, no tuve y no solo yo.

Tambien venden la kozumi que tiene un chip **Bt878a ** que onda esta?

---

### Post by eldragon on 2008-07-22
esa encore tiene toda la pinta de ser un clon de una flyvideo 2000 que tuve en algun momento., y si, le andaba el composite a esa..

---

### Post by tzulberti on 2008-07-22
> **marcosba said:**
> Posta anda de 10 en ubuntu esa??

que soft usaste para mirar tele con esa?


Yo la tenia y la verdad es que es bastante simple de configurar (editar el archivo de modprob.d y el del tvtime)

Probe otros programas: xtview (o algo similar) pero nunca los pude hacer andar. Tambien probe el mythtv pero fracase rotundamente.

En lo personal, tenia un problema en mi maquina que sino ponia en mute el microfono mientras no la usaba de todas formas se escuchaba el sonido de la tele (nunca supe si era algo de configuracion).

Lo que si, necesitas aceleracion openGl.

> **marcosba said:**
> 
anda el composite?


Pero si deberia de andar... No hace nada con la placa de video asique no deberias tener problemas

Como nota personal, intente de grabar lo que se veia pero nunca puede (usaba un script con mencode) pero tampoco soy una persona que sabe mucho del tema... 

Ademas, nunca le pude hacer andar el control remoto, pero no me calente mucho por eso porque tenia un teclado inalambrico.

---

### Post by vk-cdg on 2008-07-23
> **FlyerDie said:**
> Esta es la que va como piña en UBUNTU? (ya me canse de lidiar con la LTT200 de LG)

[http://articulo.mercadolibre.com.ar/MLA-38187242-sintonizadora-y-capturadora-de-tv-controlremoto-encore-pci-_JM](http://articulo.mercadolibre.com.ar/MLA-38187242-sintonizadora-y-capturadora-de-tv-controlremoto-encore-pci-_JM)

Saludos!

A ver, te cuento mi experiencia (el post va a ser largooooo).

Yo tengo una placa Genius TV11a go (o algo parecido). La tengo desde antes de usar linux.
Cuando me migré a Ubuntu, nunca la pude hacer andar, no encontraba los parámetros de tuner y card por ningún lado. Leyendo por internet, vi un post en un foro de un flaco que la había hecho andar igual que la enconre ENLTV-FM. 

Le pedí a un amigo la encore de el, arranqué mi PC con windows y cambié mi placa por la de el. Para mi sorpresa, windows no detectó ningún hard nuevo. No había dispositivos en conflicto y al abrir el programa de visualizacion de TV todo andaba de 10.
Conclusion, la Genius que yo tengo es un CLON IDENTICO de la encore ENLTV-FM.
Volví a poner mi placa (la Genius) y levanté linux nuevamente. Procedí a configurarla con los parámetros de la ENCORE. Salió andando casi bien. Digo casi bien porque no tengo sonido :(
Probando varias cosas, descubrí que enchufando los parlantes a la salida de la placa directamente, se escucha a un volumen normal (bajo). Mis parlantes son medio "baratitos". Tengo que subir el volumen físico de los parlantes al mango para escuchar algo.

Con la configuración normal (salida de audio de la encore a la entrada auxiliar de la placa de audio) no escucho NADA. Ubuntu algo tiene que ver con esto ya que levantando el LiveCD de mandriva y configurando la placa escucho normalmente, así que es una suma de cosas, mis parlantes son medio KK y ubuntu mete la cola en el medio también. Por el momento la única solución que le encontré es conectar parlantes directo a la salida de la placa. Veremos si con Ubuntu 8.10 se soluciona.
El resto de los chicos del foro que tienen la misma placa no tienen este problema ya que tienen la PC conectada a un amplificador o equipo de música.

Una última aclaración. Yo hoy tengo la Genius (clon de la encore), pero todas las pruebas que hice las hice con ambas placas, para descartar que mi problema fuera por alguna diferencia de hard. La conclusión es que ambas placas son CLONES exactos, es mas... es la misma placa con distinta calcomanía!

---

### Post by faktorqm on 2008-07-23
Yo no sé que placa tengo (es una larga historia...) pero la cosa es que lo unico que dice es "pinnacle". Ubuntu me la reconoce perfecto, y me agrega como si fuera una placa de sonido de mas, o sea, yo tengo la mia digamos, otra mas que me aparece ahí, y la placa capturadora. Tonces para que se escuche lo unico que tuve que hacer es ir a la placa y subirle el volumen y listo, tambien se escucha bajo, pero para mi es la placa, digamos, la capturadora no tiene amplificador (creo, si alguien sabe que si por favor que me corrija) entonces da el volumen que puede por decirlo de alguna manera. Vieron que esto tambien pasa cuando cambian de un canal a otro, que el volumen es distinto, asi que calculo que estas cosas no deben ser la excepción. El caso acá del vikingo es que no le aparece como dispositivo la placa, sino que tiene que puentear la salida de la placa al line-in de la placa de sonido. (si es que no entendi mal...)
A mi me la reconoce como saa3174. Sólo que no tuve que ponerle parámetros digamos, me la toma de una con v4l2 y funciona perfecto. Hasta el VLC me deja ver la capturadora de video digamos con sonido. (punto para VLC... ;)) y tambien me deja ver la webcam, aunque no se que tiene que ver... ¿? :o
Asi que bueno nada, sino pasate por casa Markitos! y te la presto, yo ahora no la uso hasta que venda la compu (es pci). Abrazo grande!!!

---

### Post by FlyerDie on 2008-07-23
Yo por suerte con la Encore (recien compradita) no tuve problemas de sonido..suena fuerte, tenes que conectar la salida de la capturadora al LINE-IN de la de sonido.

Y SI..la capturadora tiene que tener amplificacion ya que la entrada LINE-IN de una placa de sonido, es para entradas amplificadas. si fuera que no es amplificada deberia entrar por MIC que ahi la amplificacion corre por cuenta de la placa de sonido ;)

No se que placa de sonido tienen uds, yo tengo una integrada de chipset nvidia nforce2 (viejo), con un XP+1600.

---

### Post by vk-cdg on 2008-07-24
> **faktorqm said:**
> ...El caso acá del vikingo es que no le aparece como dispositivo la placa, sino que tiene que puentear la salida de la placa al line-in de la placa de sonido. (si es que no entendi mal...)...

Mi placa si aparece como dispositivo en la parte de sonidos, los volúmenes están todos al mango. Esta noche posteo unas capturas de como está. Es algo raro, no se.

---

### Post by eldragon on 2008-07-24
ahora que recuerdo, yo no capture con el composite, use la salida rf de la vcr....refiriendome al post anterior. y sintonze el canal 3.

despues use un script con mencoder para capturar.

---

### Post by ojvulluz on 2010-03-13
Hola a todos

no se si este hilo este demasiado desactualizado, pero, tal como el que lo inició, estoy atras de una PLACA SINTONIZADORA DE TV USB para ver el mundial por cable.

escenario: Notebook con Ubuntu 8.04 funcionando perfecto (placa de video sin aceleracion 3D), vecino que ofrece cable GRATIS... condiciones ideales para comprar una sintonizadora.

Alguien tiene alguna que se consiga en Argentina configurada y funcionando? descarto por el momento control remoto, grabar programas, pausar en tiempo real, solamente mirar la TV con la notebook, sin depender de Justin.tv y otros streamings.

en los sitios habituales de venta por internet hay Avermedia, Genius, KWorld, Encore... pero ningun vendedor sabe que chip tienen sus placas, y mucho menos si son Linux Compatibles...

Entonces, lo dicho: ¿Alguien tiene andando alguna placa TV Tuner USB en Ubuntu?

Gracias!!!!

---

