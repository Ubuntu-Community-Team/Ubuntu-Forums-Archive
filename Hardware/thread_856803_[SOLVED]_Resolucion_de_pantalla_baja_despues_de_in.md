---
title: "[SOLVED] Resolucion de pantalla baja despues de instalar driver privativos"
date: 2008-07-11
forum: Hardware
---

### Post by Elrengo on 2008-07-11
hola gente, como les va, acudo a ustedes nuevamente por un conflicto con la resolucion de pantalla.

Recien instale Hardy y con los drivers por defecto la resolucion maxima era 1600x1200, lo normal, despues de instalar los driver privativos para empezar a toquetear compiz, la resolucion maxima es 1024x768,
lo q me complica para ciertas aplicaciones, q queda chico el monitor, aclaro q en Festy no tenia problemas con la resolucion.

por si necesitan mi monitor es un Samsung Syncmaster 796 mb plus, mi placa de video una GF 6600 gt, y mi mother un MSI k9agm3 con chipset ATI 690V

bueno, espero q puedan responder y ayudarme, muchas gracias

matias

---

### Post by faktorqm on 2008-07-12
Hola, el 796 que yo sepa no soporta resolucion de 1600x1200, por eso tuve que comprarme el 997mb :P
De todas maneras tenes que instalar el nvidia-settings. Tambien te recomiendo que uses envy, no se por que siguen insistiendo con el instalador "normal". el paquete que necesitas se llama envy-ng. Si el nvidia-settings no te deja por algo en especial podes probar tambien con "sudo displayconfig-gtk". salu2!!

---

### Post by InsektO on 2008-07-12
@faktorqm: Yo creo que el 796 sí soporta 1600x1200, porque mi monitor es el 795 MB y puede ir a esa resolución (pero a mí particularmente no me gusta).

@Elrengo: Fijate de regenerar el xorg.conf una vez que estén instalados los drivers.

```
sudo nvidia-xconfig
```

Seguramente en el xorg.conf faltan las resoluciones disponibles para el monitor.

---

### Post by Elrengo on 2008-07-13
Hola a todos.

muchas gracias **faktorqm** y **InsektO**. buscando un poco mas detalladamente en el foro encontre la solucion a mi problema, 
[COLOR="Red"]

[SIZE="3"][http://ubuntuforums.org/showthread.php?t=843544]("http://ubuntuforums.org/showthread.php?t=843544")[/COLOR][/SIZE]


El problema radicaba en que al instalar los drivers privativos de Nvidia, me dejo de reconocer el monitor, asi que solo tuve que elejirlo de la lista en 

```
sudo nvidia-xconfig
```

 y problema solucionado.



No encontre antes al post q me salvo, porque debido a mi poca experienicia (por no decir casi ignorancia) no sabia q era la **xorg.conf**, ya q el titulo del post no lo mencionaba, jaja

Otro problema q me surgio es q despues de configurar el monitor la pantalla de inicio se me ponia a una reslucion muy alta y casi ni podia iniciar sesion, pero en este post tambien hablan sobre este tema y explican como solucionarlo.


Y como para colaborar un poco con el foro (ya q mucho mas no puedo ayudar), pongo el CODE para editar la **xorg.conf**, q en este post no esta y tarde un rato googleando para encontrarlo, 


```
sudo gedit /etc/X11/xorg.conf
```


Se q muchos lo sabran, pero espero q ayude a los q no saben, como yo

:guitar::guitar:

---

### Post by faktorqm on 2008-07-13
Claro, soporta la resolución... pero a que frecuencia? a 60hz somos todos vivos... y nos quedamos sin ojitos despues de laburar 12hs (o mas) todos los dias. a 75hz soporta la anterior (sacado de [http://www.samsung.com/ar/consumer/detail/spec.do?group=computersperipherals&type=monitors&subtype=cdt&model_cd=KS17CNJWHQ/XBG&fullspec=F](http://www.samsung.com/ar/consumer/detail/spec.do?group=computersperipherals&type=monitors&subtype=cdt&model_cd=KS17CNJWHQ/XBG&fullspec=F)) Salu2!!

---

### Post by InsektO on 2008-07-13
> **faktorqm said:**
> Claro, soporta la resolución... pero a que frecuencia? a 60hz somos todos vivos... y nos quedamos sin ojitos despues de laburar 12hs (o mas) todos los dias. a 75hz soporta la anterior (sacado de [http://www.samsung.com/ar/consumer/detail/spec.do?group=computersperipherals&type=monitors&subtype=cdt&model_cd=KS17CNJWHQ/XBG&fullspec=F](http://www.samsung.com/ar/consumer/detail/spec.do?group=computersperipherals&type=monitors&subtype=cdt&model_cd=KS17CNJWHQ/XBG&fullspec=F)) Salu2!!

Ah, sí,  obvio, a 60Hz, y es un asco, pero la capacidad técnica en teoría está... Yo de todas formas uso 1400x1050 a 75Hz :)

Saludos.

---

