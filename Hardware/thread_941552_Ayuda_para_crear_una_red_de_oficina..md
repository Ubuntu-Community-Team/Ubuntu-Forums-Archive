---
title: "Ayuda para crear una red de oficina."
date: 2008-10-08
forum: Hardware
---

### Post by santiagofrias on 2008-10-08
Amigos: Les comento el caso. Trabajo en una Oficina Técnica del Poder Judicial de Tucumán y tenemos una red interna con 10 pc conectadas entre sí. Esta red es de Windows XP y comparte archivos entre sí mediante un Grupo de Trabajo independiente a los demás Grupos de Trabajo del Poder Judicial.
Ahora bien, tengo intenciones de promocionar en este medio el Software Libre y quería realizar una experiencia piloto en la oficina para luego presentarlo como proyecto. Hasta aquí podrán deducir que la red del Poder Judicial trabaja con Windows, con todo lo que representa ello (pagar actualizaciones constantemente, virus, etc.).
Estuve probando con las maquinas para pasar la red que tenemos y creo que estoy haciendo algo mal o faltan parámetros.
La idea es tener un “Servidor” que trabaje en Linux (Ubuntu) y las otras con Win XP, (esto porque nadie más maneja Linux y porque como Oficina Técnica, se utilizan programas como Autocad, Corel, Adobe,etc)
Les paso la información de la red que tenemos actualmente a ver si me pueden ayudar ya que probé usando toda la información de los Thread aqui y solo me confundí más (no olviden que soy muy novato en Linux,:( :

Red Windows XP
Grupo de Trabajo = arquicom
Direcciones I.P. = 172.31.10.7 (van del 6 al 15) (la 7 sería el servidor)
Mascara de Sub Red = 255.255.0.0
Puerta de enlace predeterminada = 172.31.0.1
DNS Preferido = 200.45.191.35
DNS Alternativo = 200.45.191.40
No se que otra información necesitarían pero desde ya les agradezco profundamente y recuerden que utilizaría las herramientas que trae Ubuntu para crear esto.

---

### Post by faktorqm on 2008-10-08
Ok, tenes interfaz grafica en tu servidor? te pregunto esto antes de tirarte todos los comandos en consola y que me insultes. 

De todas maneras no se que queres hacer, si me explicas mejor te ayudo mejor. Gracias y salu2!

---

### Post by santiagofrias on 2008-10-08
> **faktorqm said:**
> Ok, tenes interfaz grafica en tu servidor? te pregunto esto antes de tirarte todos los comandos en consola y que me insultes. 

De todas maneras no se que queres hacer, si me explicas mejor te ayudo mejor. Gracias y salu2!

Si faktorqm, la interfaz gráfica que utilizo es la de Ubuntu 8.04 y Win XP (no se si te refieres a eso) y la idea es hacer que la máquina que funcionaría como servidor que sea mediante Ubuntu y las otras con Win XP; asi creo que tendría mejor control de la red, ya que actualmente cada usuario del Grupo de Trabajo, está entrando practicamente como Adminstrador
Gracias

---

### Post by faktorqm on 2008-10-08
Ahh vos queres levantar un dominio pero en ubuntu? Mira que es jodido eso eh! Salu2!

---

### Post by santiagofrias on 2008-10-08
No, lo que quiero es pasar toda la red para que en vez de trabajar con Win XP, trabaje en Ubuntu. Es una red interna, de oficina con un grupo de trabajo bajo una red Windows.
Solo quiero compartir archivos entre máquinas como lo venia haciendo con el XP, solo que ahora con Ubuntu, pero las otras maquinas seguirian teniendo XP

---

### Post by faktorqm on 2008-10-08
Si, ok.

Hacelo con el tutorial que te pase en este post de samba [http://ubuntuforums.org/showthread.php?t=940579](http://ubuntuforums.org/showthread.php?t=940579)

y con respecto a la configuracion, tendrias que ir a sistema -> administracion -> red y configurar las direcciones ip y demases.

En el samba, o sea, en una parte del archivo de configuracion que te nombra mi tuto tendrias que poner:

```
[global]
workgroup = arquicom
```

mas las opciones de segurizar las carpetas por usuario y demas que eso lo explica mi tuto. Salu2!!!!

---

### Post by santiagofrias on 2008-10-08
Ok, gracias faktorqm, ya mismo me pongo a trabajar y luego les comento como salió.

---

### Post by ADICTOALMAXIMO on 2009-03-18
Y loko

como termino estoo

---

### Post by guillermolisi on 2009-03-19
> **santiagofrias said:**
> Amigos: Les comento el caso. Trabajo en una Oficina Técnica del Poder Judicial de Tucumán y tenemos una red interna con 10 pc conectadas entre sí. Esta red es de Windows XP y comparte archivos entre sí mediante un Grupo de Trabajo independiente a los demás Grupos de Trabajo del Poder Judicial.
Ahora bien, tengo intenciones de promocionar en este medio el Software Libre y quería realizar una experiencia piloto en la oficina para luego presentarlo como proyecto. Hasta aquí podrán deducir que la red del Poder Judicial trabaja con Windows, con todo lo que representa ello (pagar actualizaciones constantemente, virus, etc.).
Estuve probando con las maquinas para pasar la red que tenemos y creo que estoy haciendo algo mal o faltan parámetros.
La idea es tener un “Servidor” que trabaje en Linux (Ubuntu) y las otras con Win XP, (esto porque nadie más maneja Linux y porque como Oficina Técnica, se utilizan programas como Autocad, Corel, Adobe,etc)
Les paso la información de la red que tenemos actualmente a ver si me pueden ayudar ya que probé usando toda la información de los Thread aqui y solo me confundí más (no olviden que soy muy novato en Linux,:( :

Red Windows XP
Grupo de Trabajo = arquicom
Direcciones I.P. = 172.31.10.7 (van del 6 al 15) (la 7 sería el servidor)
Mascara de Sub Red = 255.255.0.0
Puerta de enlace predeterminada = 172.31.0.1
DNS Preferido = 200.45.191.35
DNS Alternativo = 200.45.191.40
No se que otra información necesitarían pero desde ya les agradezco profundamente y recuerden que utilizaría las herramientas que trae Ubuntu para crear esto.
Santiago

Me parece que no entiendo bien cual seria la funcion de ese "servidor" con Ubuntu.

Actualmente tenes una red por grupo de trabajo que funciona bajo WinXP. Agregas una maquina con Ubuntu que formaria parte de ese grupo de trabajo, la que llamas "servidor", y que necesita Samba para integrar ese grupo de trabajo (hasta aqui creo que entendi bien), pero no termino de ver cual es la funcion de esa maquina. Aparenta no ser un puesto de trabajo porque la llamas "servidor" pero no mencionas que servicios prestaria (como PDC no va porque no tenes un domino para la LAN, asi que para validar usuarios en la red no es. Me queda como posible opcion que sea Fileserver). Es decir, como aporta esta maquina a tu proyecto piloto con SL ?

---

