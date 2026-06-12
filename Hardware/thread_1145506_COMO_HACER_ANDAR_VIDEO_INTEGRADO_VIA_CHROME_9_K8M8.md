---
title: "COMO HACER ANDAR VIDEO INTEGRADO VIA CHROME 9 K8M890CE/K8N890CE EN 1440x900"
date: 2009-05-01
forum: Hardware
---

### Post by fgl82 on 2009-05-01
Posteo esto por si alguien tiene más una computadora con esta maldita placa integrada.

Me pasé toda una tarde hasta que la logré hacer andar en la resolución correcta, así que dejo esto para que no tengan que sufrir el mismo calvario que yo.

Estaba usando el driver "openchrome" y, básicamente, el problema que yo tenía según el Xorg.0.log era que no detectaba correctamente el refresco horizontal de mi monitor.

Por tanto el primer paso es averigurar el refresco horizontal del monitor.

Luego, hay que incorporar esa información en el xorg.conf, dado que el xrandr falla al intentar agregar el modo desde la cli.

Por tanto, deben agregar en el xorg.conf, en la sección Monitor:

        HorizSync 24-70
        Option "PreferredMode" "1440x900"
        VertRefresh 50-75

Con los valores propios de sus monitores.

Luego, en la sección Screen agregar:

        Subsection "Display"
                Depth 24
                Modes "1440x900" 
                Virtual 1440 900
        EndSubSection

Reiniciar el entorno gráfico y... ¡eso es todo amigos!

Quizá este post debería ir en "Hardware" pero mi intención es que lo vea la mayor cantidad de gente posible al entrar al foro, dado que hay varias máquinas económicas con este chipset dando vueltas por ahi.

Por supuesto, dejo a criterio de los moderadores el moverlo o no.

Saludos.

---

### Post by guillermolisi on 2009-05-01
> **fgl82 said:**
> Posteo esto por si alguien tiene más una computadora con esta maldita placa integrada.

Me pasé toda una tarde hasta que la logré hacer andar en la resolución correcta, así que dejo esto para que no tengan que sufrir el mismo calvario que yo.

Estaba usando el driver "openchrome" y, básicamente, el problema que yo tenía según el Xorg.0.log era que no detectaba correctamente el refresco horizontal de mi monitor.

Por tanto el primer paso es averigurar el refresco horizontal del monitor.

Luego, hay que incorporar esa información en el xorg.conf, dado que el xrandr falla al intentar agregar el modo desde la cli.

Por tanto, deben agregar en el xorg.conf, en la sección Monitor:

        HorizSync 24-70
        Option "PreferredMode" "1440x900"
        VertRefresh 50-75

Con los valores propios de sus monitores.

Luego, en la sección Screen agregar:

        Subsection "Display"
                Depth 24
                Modes "1440x900" 
                Virtual 1440 900
        EndSubSection

Reiniciar el entorno gráfico y... ¡eso es todo amigos!

Quizá este post debería ir en "Hardware" pero mi intención es que lo vea la mayor cantidad de gente posible al entrar al foro, dado que hay varias máquinas económicas con este chipset dando vueltas por ahi.

Por supuesto, dejo a criterio de los moderadores el moverlo o no.

Saludos.
Version de Ubuntu ? (De ahi se infiere la del Xserver)(Si, decis que usas JJ pero eso no significa necesariamente que las pruebas las hayas hecho en esa version)
Marca y modelo del monitor en uso ?
Cantidad de RAM asignada a la placa de video ?

---

### Post by fgl82 on 2009-05-01
> **guillermolisi said:**
> Version de Ubuntu ? (De ahi se infiere la del Xserver)(Si, decis que usas JJ pero eso no significa necesariamente que las pruebas las hayas hecho en esa version)
Marca y modelo del monitor en uso ?
Cantidad de RAM asignada a la placa de video ?

Es Jaunty nomás, pero UBUNTU y no KUBUNTU, KUBUNTU lo tengo en mi pc, ésta es la de mi mujer.

Es buena tu pregunta, porque a KUBUNTU no lo pude hacer arrancar con openchrome, algun quilombo con qt tiene que se freeza pero MAL cuando inicia el entorno.

Marca del monitor:Viewsonic
Modelo: VA1703wb

RAM asignada a la placa: 64 MB

Con esto queda andando en la resolución correcta, pero de aceleración 3D ni hablar.

Este chipset de via es famoso por ser muy molesto a la hora de funcionar con linux.

Ah, en el post anterior no dije que , mientras probaba soluciones, cree un nuevo modo de video con un comando que ahora no logro recordar el nombre (gts, gst o algosimilar) y lo introduje en eel xrandr, no sé si ese cambio es permanente o no, ni si tuvo algo que ver o no con la solución. yocreo que no, pero por las dudas lo menciono.

Los comandos para agregar el modo al xrandr son:

xrandr --newmode "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync

xrandr --addmode default "1440x900_60.00"

---

### Post by guillermolisi on 2009-05-01
> **fgl82 said:**
> Es Jaunty nomás, pero UBUNTU y no KUBUNTU, KUBUNTU lo tengo en mi pc, ésta es la de mi mujer.

Es buena tu pregunta, porque a KUBUNTU no lo pude hacer arrancar con openchrome, algun quilombo con qt tiene que se freeza pero MAL cuando inicia el entorno.


Ahhh .... ahora me quedo mas tranquilo :)

Es que me pele los ojos en dos maquinas con Mother Asus y esas benditas placas de video VIA y desisti despues de varios intentos a traves del tiempo. En ambas tengo Kubuntu. Me pasa lo mismo que cometas.

---

### Post by h9005 on 2009-05-01
Si me paso lo mismo quise hacer andar ubuntu con compiz o juegos con aceleracion 3d en estas máquinas y es imposible.

---

### Post by faktorqm on 2009-05-04
3d nada no? yo intente hace mucho tiempo tirar 3d y lo unico que logre fue muchos cuelgues de interfaz grafica :P salu2!

---

### Post by fgl82 on 2009-05-04
> **faktorqm said:**
> 3d nada no? yo intente hace mucho tiempo tirar 3d y lo unico que logre fue muchos cuelgues de interfaz grafica :P salu2!

No, como dije arriba, nada de 3D.

Sí, tal como mencionás, al intentar habilitarlo sólo se consiguen cuelgues varios.

---

