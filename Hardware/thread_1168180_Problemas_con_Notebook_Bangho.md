---
title: "Problemas con Notebook Bangho"
date: 2009-05-23
forum: Hardware
---

### Post by al2009 on 2009-05-23
Hola, soy nuevo en el foro, soy un feliz usuario de UBUNTU 8.10. La semana pasada me compre una Notebook Bangho (dejo en attach las características técnicas), el equipo viene con Windows Vista Home. Mi problema comenzo cuando quise instalar UBUNTU 8.10 o 9.04, luego de la primera pantalla, al querer instalar, se enloquece la pantalla, parece ser un problema de la placa de video, pero no puedo acceder a ninguna terminal, intente instalar pasando los parametros "acpi=off" "nolapic" "noapic" y todo lo que encontre, estoy utilizando el Alternate CD (porque la instalación es en modo texto), pero el resultado es el mismo al parecer por lo que pude ver googleando es la placa "Tarjeta gráfica SiS Mirage 3 Graphics". El tema es que llame a Bangho y me pasaron los datos de la empresa "PIXART" ellos me comentaron que tienen una distribución basada en DEBIAN que se llama "RXART 3.2" el costo de la instalación y de la licencia es $90, ahora no es por la plata, pero me gustaría poder instalar UBUNTU que es la distribución que me siento comodo. Alguno de Uds. le paso algo similar, tienen idea de como puedo instalar el UBUNTU?

Desde ya muchas gracias por la ayuda que puedan darme.
Saludos
Alberto

---

### Post by Hei Ku on 2009-05-23
Proba instalando con el alternate e iniciando en modo grafico seguro.
Desde ya te aviso que con esa placa de video vas a transpirar para hacerla andar.

---

### Post by guillermolisi on 2009-05-23
> **al2009 said:**
> Hola, soy nuevo en el foro, soy un feliz usuario de UBUNTU 8.10. La semana pasada me compre una Notebook Bangho (dejo en attach las características técnicas), el equipo viene con Windows Vista Home. Mi problema comenzo cuando quise instalar UBUNTU 8.10 o 9.04, luego de la primera pantalla, al querer instalar, se enloquece la pantalla, parece ser un problema de la placa de video, pero no puedo acceder a ninguna terminal, intente instalar pasando los parametros "acpi=off" "nolapic" "noapic" y todo lo que encontre, estoy utilizando el Alternate CD (porque la instalación es en modo texto), pero el resultado es el mismo al parecer por lo que pude ver googleando es la placa "Tarjeta gráfica SiS Mirage 3 Graphics". El tema es que llame a Bangho y me pasaron los datos de la empresa "PIXART" ellos me comentaron que tienen una distribución basada en DEBIAN que se llama "RXART 3.2" el costo de la instalación y de la licencia es $90, ahora no es por la plata, pero me gustaría poder instalar UBUNTU que es la distribución que me siento comodo. Alguno de Uds. le paso algo similar, tienen idea de como puedo instalar el UBUNTU?

Desde ya muchas gracias por la ayuda que puedan darme.
Saludos
Alberto
La placa de video de esa notebook nunca va a funcionar con otro driver que el vesa.

Las placas SIS le hacen una fortisima competencia a las VIA en su caracteristica "disfuncional". SIS se retiro del mercado de tecnologia y no hay soporte ni siquiera comunitario (que sepa) para desarrollo de drivers.

Lamento decir esto, pero es asi nomas.

---

### Post by gmunioz on 2009-05-23
Hola al2...:

Navega hasta esta página:

[http://www.winischhofer.eu/linuxsispart4.shtml#download](http://www.winischhofer.eu/linuxsispart4.shtml#download)

Sigue las instrucciones.

De aquí son los sources que utiliza Gabriel Ortiz en rXart.

Saludos.

---

### Post by guillermolisi on 2009-05-23
> **gmunioz said:**
> Hola al2...:

Navega hasta esta página:

[http://www.winischhofer.eu/linuxsispart4.shtml#download](http://www.winischhofer.eu/linuxsispart4.shtml#download)

Sigue las instrucciones.

De aquí son los sources que utiliza Gabriel Ortiz en rXart.

Saludos.
Interesantisimo.

Muchas gracias por el aporte.

Estuve leyendo rapidamente la informacion que ahi se publica y hay para entretenerse un buen rato.

Algo que me quedo picando es: Que pasa cuando hay un cambio de version en el X.org empaquetado en los repositorios de Ubuntu y tengo funcionando el X.org y demas componentes, compilados o binarios instalados, que se ofrecen para que funcione una placa SIS ?

Todo un tema ...

---

### Post by pablo.s on 2009-05-23
> **guillermolisi said:**
> Algo que me quedo picando es: Que pasa cuando hay un cambio de version en el X.org empaquetado en los repositorios de Ubuntu y tengo funcionando el X.org y demas componentes, compilados o binarios instalados, que se ofrecen para que funcione una placa SIS ?

Todo un tema ...

Y supongo que el usuario tendrá
que hacer la misma movida de
compilar todo el driver (o usar
los binarios) para adaptarlos a
la nueva versión de XOrg.
Es notable leer en la documentación
que linkea Gabriel que el
desarrollador ha descontinuado
el trabajo argumentando que no
quiere seguir ayudando a SiS a que
vendan más placas sin soporte, lo
que me lleva a la reflexión de
Alvaro acerca de los drivers de
NVidia. Ahora le da una nueva
refundamentación a lo de apoyar
a una empresa comprando el
hardware. Antes me parecía un
poco caprichosa la proposición de
no comprar placas NVidia hasta que
liberen los drivers, pero por cierto
que te hace reflexionar bastante.
Por mi parte le huyo al hardware
de AMD como la peste, prefiero el
de Intel. Aunque lo mio es una antigua
costumbre que viene de los dias de
las incompatibilidades de ciertos
procesadores de AMD muy antiguos
(K6, 586).

---

### Post by guillermolisi on 2009-05-23
> **pablo.s said:**
> Y supongo que el usuario tendrá
que hacer la misma movida de
compilar todo el driver (o usar
los binarios) para adaptarlos a
la nueva versión de XOrg.
Es notable leer en la documentación
que linkea Gabriel que el
desarrollador ha descontinuado
el trabajo argumentando que no
quiere seguir ayudando a SiS a que
vendan más placas sin soporte, lo
que me lleva a la reflexión de
Alvaro acerca de los drivers de
NVidia. Ahora le da una nueva
refundamentación a lo de apoyar
a una empresa comprando el
hardware. Antes me parecía un
poco caprichosa la proposición de
no comprar placas NVidia hasta que
liberen los drivers, pero por cierto
que te hace reflexionar bastante.
Por mi parte le huyo al hardware
de AMD como la peste, prefiero el
de Intel. Aunque lo mio es una antigua
costumbre que viene de los dias de
las incompatibilidades de ciertos
procesadores de AMD muy antiguos
(K6, 586).
Si, pense lo mismo respecto de volver a compilar pero en algun momento ni siquiera servira porque los cambios en X.org podrian dejar afuera lo que se logre compilando, es decir con errores o mal funcionamiento.

Dentro del codumento hay varios prerequisitos a observar respecto del versionado de X.org y otros componentes.

Tambien dice de cuando es el binaro de la version Premium, varios años atras, y hoy X.org ha cambiado bastante.

Ni hablar de que representa todo eso de compilar, revisar dependencias, versionado, etc. para alguien que se dedica a actividades no informaticas. Impracticable y solo ayuda a espantar gente.

Sobre ATI y nVidia ... sep, tendre que comprarme una ATI para aportar mi granito de arena y vender rapidamente mis nVidia antes de que no tenga valor en el mercado del usado :D

---

### Post by al2009 on 2009-05-25
Hola quiero agradecer a todos por la ayuda, especialmente a Hei Ku[[COLOR=#339900]****[/COLOR]]("http://ubuntuforums.org/member.php?u=346209"), que con el modo gráfico seguro pude ver ubuntu en la notebook (800*600) pero por el momento suficiente y a GMUNIOZ por el link, no lo instale por falta de tiempo pero voy a hacerlo en la semana. Les dejo una pregunta más, existe el modo gráfico seguro en el alternate cd? porque no lo encontre.

Una vez mas, muchas gracias
Alberto

---

### Post by luks911 on 2009-05-25
> **al2009 said:**
> Hola quiero agradecer a todos por la ayuda, especialmente a Hei Ku[[COLOR=#339900]****[/COLOR]]("http://ubuntuforums.org/member.php?u=346209"), que con el modo gráfico seguro pude ver ubuntu en la notebook (800*600) pero por el momento suficiente y a GMUNIOZ por el link, no lo instale por falta de tiempo pero voy a hacerlo en la semana. Les dejo una pregunta más, existe el modo gráfico seguro en el alternate cd? porque no lo encontre.

Una vez mas, muchas gracias
Alberto

No existe porque no hace falta. Me explico: el Alternate no se pude usar como LiveCD, sirve para instalar, para actualizar desde una versión anterior o para recuperar un sistema. Además, el instalador no es gráfico al estilo del CD "normal" sino que es semigráfico, digamos, porque tampoco es puro texto. Sin embargo, la instalación es tan sencilla como con el LiveCD.

Fijate acá[0] cómo se ve y cómo es el proceso de instalación.

[0] [http://www.guia-ubuntu.org/index.php?title=Instalaci%C3%B3n_con_Alternate_CD](http://www.guia-ubuntu.org/index.php?title=Instalaci%C3%B3n_con_Alternate_CD)

---

