---
title: "Lista de Tarjetas de Video que no Funcionaran con Intrepid"
date: 2008-10-28
forum: Hardware
---

### Post by vk-cdg on 2008-10-28
Leyendo uno de los blogs que consulto a diario me encuentro con un post que me deja un tanto preocupado, mas que nada por la cantidad de placas que listan.

Pego el post


Hay varias tarjetas de video que no funcionarán con Intrepid Ibex por problemas con los drivers de nVidia.
```

NVIDIA GPU product 	Device PCI ID
GeForce2 MX/MX 400 	0×0110
GeForce2 MX 100/200 	0×0111
GeForce2 Go 	        0×0112
Quadro2 MXR/EX/Go 	0×0113
GeForce4 MX 460 	0×0170
GeForce4 MX 440 	0×0171
GeForce4 MX 420 	0×0172
GeForce4 MX 440-SE 	0×0173
GeForce4 440 Go 	0×0174
GeForce4 420 Go 	0×0175
GeForce4 420 Go 32M 	0×0176
GeForce4 460 Go 	0×0177
Quadro4 550 XGL 	0×0178
GeForce4 440 Go 64M 	0×0179
Quadro NVS 400 	        0×017A
Quadro4 500 GoGL 	0×017C
GeForce4 410 Go 16M 	0×017D
GeForce4 MX 440 with AGP8X 	0×0181
GeForce4 MX 440SE with AGP8X 	0×0182
GeForce4 MX 420 with AGP8X 	0×0183
GeForce4 MX 4000 	0×0185
Quadro4 580 XGL 	0×0188
Quadro NVS 280 SD 	0×018A
Quadro4 380 XGL 	0×018B
Quadro NVS 50 PCI 	0×018C
GeForce2 Integrated GPU 	0×01A0
GeForce4 MX Integrated GPU 	0×01F0
GeForce3 	0×0200
GeForce3 Ti 200 	0×0201
GeForce3 Ti 500 	0×0202
Quadro DCC 	0×0203
GeForce4 Ti 4600 	0×0250
GeForce4 Ti 4400 	0×0251
GeForce4 Ti 4200 	0×0253
Quadro4 900 XGL 	0×0258
Quadro4 750 XGL 	0×0259
Quadro4 700 XGL 	0×025B
GeForce4 Ti 4800 	0×0280
GeForce4 Ti 4200 with AGP8X 	0×0281
GeForce4 Ti 4800 SE 	0×0282
GeForce4 4200 Go 	0×0286
Quadro4 980 XGL 	0×0288
Quadro4 780 XGL 	0×0289
Quadro4 700 GoGL 	
NVIDIA GPU product 	Device PCI ID
RIVA TNT 	0×0020
RIVA TNT2/TNT2 Pro 	0×0028
RIVA TNT2 Ultra 	0×0029
Vanta/Vanta LT 	0×002C
RIVA TNT2 Model 64/Model 64 Pro 	0×002D
Aladdin TNT2 	0×00A0
GeForce 256 	0×0100
GeForce DDR 	0×0101
Quadro 	0×0103
GeForce2 GTS/GeForce2 Pro 	0×0150
GeForce2 Ti 	0×0151
GeForce2 Ultra 	0×0152
Quadro2 Pro 	0×0153
```

Extraido de [http://tuxbelito.wordpress.com/2008/10/27/lista-de-tarjetas-de-video-que-no-funcionaran-con-intrepid/](http://tuxbelito.wordpress.com/2008/10/27/lista-de-tarjetas-de-video-que-no-funcionaran-con-intrepid/)

---

### Post by sergiom99 on 2008-10-28
gracias por la data.
segun entendí yo en los docs de kubuntu, si son soportadas, solo que sin aceleración 3d porque pasan a usar el driver gratuito nv.
[https://wiki.kubuntu.org/IntrepidReleaseNotes](https://wiki.kubuntu.org/IntrepidReleaseNotes)

---

### Post by santiagoward2000 on 2008-10-28
> **sergiom99 said:**
> gracias por la data.
segun entendí yo en los docs de kubuntu, si son soportadas, solo que sin aceleración 3d porque pasan a usar el driver gratuito nv.
[https://wiki.kubuntu.org/IntrepidReleaseNotes](https://wiki.kubuntu.org/IntrepidReleaseNotes)

Driver libre en realidad, los restringidos también son gratuitos. ;) 
Veamos si esto alienta a que los de nvidia liberen los drivers, aunque sea los viejos. Hasta ahora la única excusa que tenían era que "andaban bien"...

---

### Post by sergiom99 on 2008-10-28
> **santiagoward2000 said:**
> Driver libre en realidad, los restringidos también son gratuitos. ;) 
Veamos si esto alienta a que los de nvidia liberen los drivers, aunque sea los viejos. Hasta ahora la única excusa que tenían era que "andaban bien"...

eso eso, se me chispoteo la traduccion. gracias por la aclaracion.

---

### Post by Kubunteando on 2008-10-28
The list is longer than that!

How about the VIA Chrome cards?
Does any of those work?

---

### Post by hictio on 2008-10-28
Muchas gracias por la lista, mi desktop (GeForce2 MX/MX 400) tendra que quedarse en Hardy :(
Igual, es una catramina, instalarle hardy me costo un monton de tiempo.

---

### Post by Hei Ku on 2008-10-28
Las VIA probablemente funcionen con los drivers libres que esta liberando VIA. Contrataron un kernel developer de los grossos para eso, y ya estan liberando drivers.

Y en cuanto a ATI, mi HD4850 ya tiene el patch en Intrepid para usar el driver libre, con 3d y todos los chiches. Y el RadeonHD esta mejorando a pasos agigantados, asi que proximamente tambien va a estar soportada por ese.

Intel, ni hablar.

O sea, muchachos, piensen antes de comprar una NVidia.

---

### Post by faktorqm on 2008-10-28
Che que zarpado... sacan todo el soporte al driver 71.XX, que es exactamente el unico que soporta mi placa de video...
yo venia viendo que le ponian "legacy" al nombre... jajaja pero lo sacan todo mal.
Bueno, parece que me voy a quedar con 8.04 un rato mas de lo que pensaba... y si upgradeo y dejo el kernel de 8.04? salu2!

---

### Post by katon on 2008-10-29
uy,,,,que quilombo ...yo me encargue una nvidia 9600GT , espero que funcione
ya que estamos les pregunto si alguien sabe , cuando la conecte , instalo los drivers restringidos o instalo el ultimo driver de la pagina de nvidia manualmente ?

---

### Post by victor_nesta on 2008-10-29
Mi 7300GT (que no esta en la lista) Esta funcionando 100% en intrepid, con los Drivers privativos de Nvidia.

---

### Post by katon on 2008-10-29
> **victor_nesta said:**
> Mi 7300GT (que no esta en la lista) Esta funcionando 100% en intrepid, con los Drivers privativos de Nvidia.

y como sabes si funcionan los 3d ?

---

### Post by santiagoward2000 on 2008-10-29
El problema no es con todas las nvidia, sino de la serie 4 para abajo (que usan los drivers viejos). La 7300 y la 9600 tendrían que andar sin problemas con los drivers privativos.

---

### Post by vk-cdg on 2008-10-29
> **victor_nesta said:**
> Mi 7300GT (que no esta en la lista) Esta funcionando 100% en intrepid, con los Drivers privativos de Nvidia.

Yo tengo esa placa y por ahora anda de 10!

---

### Post by victor_nesta on 2008-10-29
> **katon said:**
> y como sabes si funcionan los 3d ?

Los juegos que tengo funcionan y cuando escribo en la consola

**victor@nesta-desktop:~$ [SIZE="4"]glxinfo | grep direct[/SIZE]** Obtengo
**[SIZE="4"]direct rendering: Yes[/SIZE]**

Indicando que tengo aceleración

---

### Post by sebastianabate on 2008-10-29
Para los usuarios de ATI (como yo, una onboard x1250) hay una buena noticia, parece que la gente de AMD considera a Ubuntu como un nicho muy importante de mercado, porque para la salida de Intrepid liberaron un driver Beta que tiene soporte para el nuevo Xorg 7.4 (que no está soportado por los últimos drivers que te podés bajar de la página, los 8-10).
Esto quiere decir que para las placas que no tienen aceleración con el driver OpenSource vamos a tener la opción de usar esta versión Beta, que seguramente va a tener sus problemas, pero por lo menos vamos a poder usar el Google Earth, y el Sauerbraten :).

Info sacada de acá: [http://www.phoronix.com/scan.php?page=article&item=canonical_catalyst_811&num=1](http://www.phoronix.com/scan.php?page=article&item=canonical_catalyst_811&num=1)

---

### Post by clasificado on 2008-10-30
¿no son los que corresponden a los drivers legacy?

---

### Post by benjamin_linux on 2008-10-31
No funciona por ahora Envy con Intrepid? Tengo una nvidia 7000m y en Hardy me funciona sólo con Envy, tendría problemas con Intrepid?

---

### Post by rojojuan on 2008-11-01
> **victor_nesta said:**
> Mi 7300GT (que no esta en la lista) Esta funcionando 100% en intrepid, con los Drivers privativos de Nvidia.

En mi caso una xfx 7300GS no funciona en Intrepid, tuve que volver a Hardy.

---

### Post by victor_nesta on 2008-11-01
> **rojojuan said:**
> En mi caso una xfx 7300GS no funciona en Intrepid, tuve que volver a Hardy.

Mira que raro! Esta bien que la 7300GS y la GT son dos cosas diferentes, yo updateé el intrepid desde ultima beta, no creo que tenga que ver ya que el producto final es el mismo. Yo estoy usando Nvidia 177.80, capaz que estoy diciendo pavadas

Ya veremos mas casos y sabremos que pasa, pero ¿son muy malos los controladores/GNU? o ¿ni siquiera reconoce la placa?

---

### Post by rojojuan on 2008-11-11
Una buena noticia:
En la página de Alberto Milone éste anuncia que Nvidia está trabajando en dos betas para que funcionen las Nvidia en Intrepid Ibex
También sostiene que esperen hasta que los nuevos drivers sean liberados. Esperemos que sea así.
Les dejo el enlace:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/251107/comments/40](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/251107/comments/40)

---

### Post by z37a on 2008-11-15
Gente viendo esto recordé que el otro día tuve problemas con una VIA Chrome, no me tomaba el 3D, funcionar funciona pero sin el 3D, hay algún problema con las VIA?

---

### Post by Hei Ku on 2008-11-15
Las VIA tenian drivers muy malos en Linux, extremadamente dificiles de hacerlos andar.
Hace poco los liberaron y contrataron un desarrollador grosso de kernel para trabajar con los drivers, asi que se espera que mejoren rapidamente.

---

### Post by z37a on 2008-11-16
> **Hei Ku said:**
> Las VIA tenian drivers muy malos en Linux, extremadamente dificiles de hacerlos andar.
Hace poco los liberaron y contrataron un desarrollador grosso de kernel para trabajar con los drivers, asi que se espera que mejoren rapidamente.

Habria que listar las placas que mejor funcionan, y bueno tener una buena lista de eso, de esta manera sabriamos que placas comprar para tener una compatibilidad 100%, creo que si a esa lista acceden muchos seguro lso fabricantes van a poner mas empeño.

---

### Post by Hei Ku on 2008-11-17
Las listas existen, y los fabricantes lo saben, pero no les importa excepto que les pegues donde les duele, en el bolsillo.
Votá con tu plata. ;)

---

### Post by annayra on 2008-12-05
Gente, mucho gusto, soy nueva en esto y tengo una Olibook 520, que lamentablemente tiene una placa de video Sis 631 ...   no la vi en la lista de no soportadas. Tuve problema con Ubuntu 8.04, pero se solucionaba, ahora siguiendo los mismos pasos no lo puedo solucionar con este distro.  Me queda la resolucion en 800x600 porque no puede acceder a los ... drivers -ehm modulos. xD 

Quiza tengo que volver a intentar asegurandome paso por paso, o hay algo que tenga que ver con los repositorios que no estoy viendo? 

Muchas gracias por estar ahi.

---

### Post by Hei Ku on 2008-12-05
Podes postear en un thread aparte, junto el resultado que tire el lspci? 
Asi podemos saber el modelo exacto de tu placa.

---

