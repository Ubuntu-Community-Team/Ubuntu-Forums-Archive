---
title: "Problema con efectos Kubuntu (KK)"
date: 2009-11-10
forum: Hardware
---

### Post by Mustaine666 on 2009-11-10
Bueno.. otra vez me veo obligado a pedir su ayuda..

resulta que empece a probar Kubuntu Karmic Koala.. 

y quise activarle los efectos graficos.. y resulta que no habia instalado los drivers de video de la placa...

Intel extreme grapichs 64mb .. y ahora resulta que despues de poner usuario y contraseña..

empieza a cargar y despues de q aparece el disco.. se traba y no carga mas..

este problema empezo cuando active los graficos. .

existe alguna solucion?.. desde ya muchas gracias.. espero sus respuestas..

---

### Post by guillermolisi on 2009-11-10
Probaste de iniciar en modo seguro ?

Si asi inicia razonablemente bien podrias instalar los drivers de la placa de video que correspondan.

Te habilita alguna consola con Alt+Ctrl+F1 ?

---

### Post by Mustaine666 on 2009-11-10
> **guillermolisi said:**
> 
Te habilita alguna consola con Alt+Ctrl+F1 ?

si habilita una consola.. me pide usuario y password... y despues de ponerlo queda como una consola normal..

---

### Post by guillermolisi on 2009-11-10
En esa consola ingresa ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Y volve a reinicar. Conta como te fue.

---

### Post by Mustaine666 on 2009-11-11
> **guillermolisi said:**
> En esa consola ingresa ```
sudo dpkg-reconfigure -phigh xserver-xorg
```Y volve a reinicar. Conta como te fue.

lo ingrese tal cual me explicaste.. y despues reinicie... y se traba en el mismo lado! :S

---

### Post by guillermolisi on 2009-11-11
> **Mustaine666 said:**
> lo ingrese tal cual me explicaste.. y despues reinicie... y se traba en el mismo lado! :S
Se traba cuando quiere mostrar el escritorio grafico porque hay algo que no le gusta al Xserver o al monitor.

La maquina inicia bien porque te habilita las consolas, el problema esta con la parte grafica.

Tenes alguna forma de mostrar el contenido de /etc/X11/xorg.conf y la salida de "lspci" ?

---

### Post by jpmorelli on 2009-11-11
Ahora estoy en Gnome, en casa uso el Kubuntu, pero si mal no recuerdo en el kdm ( Gestor de usuarios de inicio ) existe la opcion Kde (a prueba de fallos ), que pasa si usas ese modo ?

Suerte !

---

### Post by Mustaine666 on 2009-11-11
> **jpmorelli said:**
> Ahora estoy en Gnome, en casa uso el Kubuntu, pero si mal no recuerdo en el kdm ( Gestor de usuarios de inicio ) existe la opcion Kde (a prueba de fallos ), que pasa si usas ese modo ?

Suerte !

en modo prueba de fallos.. inicia y vuelve al kdm ..

---

### Post by Mustaine666 on 2009-11-11
> **guillermolisi said:**
> Se traba cuando quiere mostrar el escritorio grafico porque hay algo que no le gusta al Xserver o al monitor.

La maquina inicia bien porque te habilita las consolas, el problema esta con la parte grafica.

Tenes alguna forma de mostrar el contenido de /etc/X11/xorg.conf y la salida de "lspci" ?

la salida del lspci.. la unica forma es verla en la pantalla.. 

y copie.. 
> 
VGA Video Compatible Controller: Intel Corporation 82845G/GL [Brook dale-G]/GE Chipset Integrated Graphics Device (rev03)

---

### Post by josecuervo86 on 2009-11-11
Che, o yo estoy muy equivocado o los drivers ya estan instalados? O sea, no es como con las placas nVidia o ATI donde podes bajar controladores privativos para obtener mejor rendimiento, si no que con los "de fabrica" se maneja. Habría que ver por que otro lado puede venir el problema

---

### Post by Mustaine666 on 2009-11-11
> **josecuervo86 said:**
> Che, o yo estoy muy equivocado o los drivers ya estan instalados? O sea, no es como con las placas nVidia o ATI donde podes bajar controladores privativos para obtener mejor rendimiento, si no que con los "de fabrica" se maneja. Habría que ver por que otro lado puede venir el problema

si.. estuve viendo en la caja de la pc..y es el modelo de la placa.. asi q por lo menos la placa la reconoce!

---

### Post by josecuervo86 on 2009-11-11
Claro, y no solo la reconoce, si no que tiene los drivers instalados. Lo que puede suceder es que no se banque los efectos, pero te lo tendria que haber informado cuando los quisiste activar.

No entiendo como sera en KDE, pero debe haber alguna forma de desactivar los efectos extra

---

### Post by josecuervo86 on 2009-11-11
Mira, encontre esto: [http://www.kubuntu-es.org/foro/200811/pantalla-negra-kde-41](http://www.kubuntu-es.org/foro/200811/pantalla-negra-kde-41)

Al flaco le paso lo mismo que a vos y lo soluciono asi:

> Edita el archivo ~/.kde4/share/config/kwinrc y remplaza las cadenas siguiente

[Compositing]
Enabled=true

por esto

[Compositing]
Enabled=false

Calculo que con **nano** se debe poder editar (esta en KDE?). Entonces seria 

```
sudo nano /.kde4/share/config/kwinrc
```

---

### Post by Mustaine666 on 2009-11-12
> **josecuervo86 said:**
> Mira, encontre esto: [http://www.kubuntu-es.org/foro/200811/pantalla-negra-kde-41](http://www.kubuntu-es.org/foro/200811/pantalla-negra-kde-41)

Al flaco le paso lo mismo que a vos y lo soluciono asi:



Calculo que con **nano** se debe poder editar (esta en KDE?). Entonces seria 

```
sudo nano /.kde4/share/config/kwinrc
```


despues de probar con sudo nano /.kde4/share/config/kwinrc .. abre nano..

pero no tiene nada  :S .. me resulta muy raro!

---

### Post by guillermolisi on 2009-11-12
> **Mustaine666 said:**
> despues de probar con sudo nano /.kde4/share/config/kwinrc .. abre nano..

pero no tiene nada  :S .. me resulta muy raro!
Tampoco tengo ese archivo en mi KDE4 en la PC del laburo.

Fijate en /usr/share/kubuntu-default-settings/kde4-profile/default/share/config/kwinrc.

Es el unico archivo con ese nombre que encontre en toda la maquina (KDE4.3.3)
Hay un tag Compositing pero no esta la entrada que indicaron.

Lo que tengo en la maquina mencionada, en ese archivo, con efectos activados y funcionando muy bien, es:```

[Compositing]
UnredirectFullscreen=false

[Desktops]
Number=2

[Style]
PluginLib=kwin3_oxygen

[Effect-Cube]
CapColor=0,0,0

[Windows]
TitlebarDoubleClickCommand=Maximize

[Plugins]
kwin4_effect_boxswitchEnabled=false
kwin4_effect_coverswitchEnabled=true
```

---

### Post by josecuervo86 on 2009-11-12
> **Mustaine666 said:**
> despues de probar con sudo nano /.kde4/share/config/kwinrc .. abre nano..

pero no tiene nada  :S .. me resulta muy raro!

Claro, no tiene nada por que no existe. Es muy extraño, habra sido solo para KDE 4.1?

---

### Post by Mustaine666 on 2009-11-12
> **josecuervo86 said:**
> Pero al archivo te lo abre? Fijate que nano es un editor de texto en consola. Te resultaron raras las opciones?


osea nano se abre.. con las opciones abajo.. y con la direccion del archivo arriba,,pero no aparece nada adentro .. esta como si el archivo estuviese vacio

---

### Post by josecuervo86 on 2009-11-12
> **Mustaine666 said:**
> osea nano se abre.. con las opciones abajo.. y con la direccion del archivo arriba,,pero no aparece nada adentro .. esta como si el archivo estuviese vacio

El texto que quoteaste es el que mande justo antes de entender lo que quisiste decir :)

Pasa que al no existir el archivo, nano lo crea en blanco. Lo que podrias hacer es moverte hasta el directorio donde supuestamente esta y hacer un **ls** para ver que archivos hay. De cualquier manera, si no esta es lo mismo que nada. Habrá que buscar por otro lado. Voy a Googlear un ratito ;)

---

### Post by jpmorelli on 2009-11-12
> **Mustaine666 said:**
> en modo prueba de fallos.. inicia y vuelve al kdm ..

A mi una vez me pasó eso y no era el video sino el directorio /tmp que lo habia borrado sin querer, creí que hacía rm en el tmp del home pero al hacer sudo borré el del raíz, y cada vez que iniciaba volvía al gestor de entradas.
En caso que sea eso creé un /tmp con permisos 777, o sea en el raiz

sudo mkdir tmp
sudo chmod 777 /tmp

y funcionó otra vez !

Suerte !

---

### Post by Mustaine666 on 2009-11-14
les cuento.. probe las dos ultimas posibilidades y ninguna funciono.. creo q lo mejor o la solucion posible seria la reinstalacion del kubuntu.. no se que opinan¿

---

### Post by Mustaine666 on 2009-11-15
bueno les comento.. me resigne a no poder solucionar el problema  y reinstale kubuntu.. pero no anduvo.. asi que ahora estoy en ubuntu.. 

gracias por preocuparse a todos.. cuando me compre una placa de video.. 

instalo kubuntu

---

