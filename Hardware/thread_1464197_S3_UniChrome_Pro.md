---
title: "S3 UniChrome Pro"
date: 2010-04-27
forum: Hardware
---

### Post by PoNcHo87 on 2010-04-27
Buenas, quisiera saber si alguien tiene instalado el driver de la placa de video OnBoard S3 UniChrome Pro IGP, ya que el Ubuntu 9.10 no me lo detecta automaticamente, y el fabricante solo creo el driver hasta la 9.04.-
Alguien lo tiene instalado?
O sabe como podria adaptar el driver de la 9.04 a la 9.10?
Dejo el link de la 9.04: [http://www.viaarena.com/Driver/via-xserver-86a-50283_src.tgz](http://www.viaarena.com/Driver/via-xserver-86a-50283_src.tgz) 
Muchas gracias.-

```
Integrated VIA UniChrome™ Pro IGP
- Dual pixel pipelines
- 128-bit 2D/3D engine
- 200MHz engine clock speed
- 16-64MB shared memory

Optional external AGP 8X/4X port

MPEG-2 hardware acceleration 

``````
# sudo lshw
*display UNCLAIMED
                description: VGA compatible controller
                product: K8M800/K8N800/K8N800A [S3 UniChrome Pro]
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 bus_master cap_list
                configuration: latency=32 mingnt=2
                resources: memory:f0000000-f3ffffff(prefetchable) memory:f4000000-f4ffffff memory:f5000000-f500ffff(prefetchable)
```

---

### Post by guillermolisi on 2010-04-28
Hay por lo menos un thread sobre los drivers para placas de video VIA en este subforo y varios mas en la seccion general (en Ingles).

VIA no libero su tecnologia para que sus drivers pudieran ser funcionales y que la comunidad los mejore. De hecho tuve dos maquinas con ese chip y durante mas de 12 meses estuve probando muchas cosas y nunca pude siquiera que funcionara mejor que con driver Vesa (con /etc/X11/xorg.conf debidamente configurado, cosa que aun tengo por si a alguien le sirve).

Conclusion, cuando quise mas prestaciones de video me compre placas nVidia (ATI aun no habia liberado su tecnologia) y listo, deje de "sufrir".

---

### Post by PoNcHo87 on 2010-04-28
ok, gracias, entonces elijo dejar de sufrir para no seguir sufriendo.-

que son los drivers Vesa?

---

### Post by guillermolisi on 2010-04-29
> **PoNcHo87 said:**
> ok, gracias, entonces elijo dejar de sufrir para no seguir sufriendo.-

que son los drivers Vesa?
Es el driver de video standard, el que se usa cuando inicias la maquina en modo de video seguro.

---

### Post by z37a on 2010-04-30
Viendo que es AGP, me parece que te va a salir mas barato una placa usada GeForce 4 o una cualquiera AGP que la cantidad de antiácidos que vas a necesitar para evitar la ulcera que viene al tratar de hacer andar bien las placas VIA/SIS.

---

### Post by chronos00 on 2010-05-09
Hola!

Yo tambien estoy teniendo problemas con varias maquinas con sl chipset grafico de VIA.

@PoNcHo87, creo q sin lugar a dudas, la solucion mas simple es comprar una GeForce 4 barata y listo. Busque en Mercado Libre una opcion barata y encontre esta q te puede servir: [http://articulo.mercadolibre.com.ar/MLA-86038888-placa-video-agp-4x-2x-1x-nvidia-geforce-mx400-widescreen-new-_JM]("http://articulo.mercadolibre.com.ar/MLA-86038888-placa-video-agp-4x-2x-1x-nvidia-geforce-mx400-widescreen-new-_JM")

Lamentablemente en mi caso no creo q realmente pueda solucionarlo asi, ya que estoy usando un Ubuntu como servidor LTSP, y muchos de los thin-clients tienen este precioso chipstet...

Es decir, cuando los clientes descargan su imagen para bootear y la ejecutan, no logran entrar a la sesion de escritorio por q se ve q no tienen el soporte correcto para el video.

Encontre esta pagina de documentacion en la wiki:
[https://help.ubuntu.com/community/OpenChrome]("https://help.ubuntu.com/community/OpenChrome")
donde hablan sobre un monton de soluciones posibles. Pero puntualmente habla que en la ultima version de Ubuntu hubo cambios que rompe ciertas compatibilidades.

Alguno de Uds q son dueños de este chipset, ha logrado hacerlo andar de alguna manera?

@guillermolisi
Al menos en modo VESA funciona? Como podria configurarlo en modo VESA?

Gracias!

---

### Post by alfplayer on 2010-05-09
> **chronos00 said:**
> Al menos en modo VESA funciona? Como podria configurarlo en modo VESA?

Eso se puede hacer con la opción de booteo *xforcevesa* o con *Driver "vesa"* en el archivo de configuración del servidor X.

---

### Post by guillermolisi on 2010-05-09
> **alfplayer said:**
> Eso se puede hacer con la opción de booteo *xforcevesa* o con *Driver "vesa"* en el archivo de configuración del servidor X.
La opcion de booting va dentro del Grub.

La configuracion del X server esta en /etc/X11/xorg.conf que generalmente no existe y hay que crearlo para editarlo y agregarle el contenido correspondiente.

---

