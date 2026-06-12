---
title: "remastersys backup -video drivers"
date: 2008-12-02
forum: Hardware
---

### Post by tsueseres on 2008-12-02
hola, ya probe el comando de remastersys y instale todas mis cosas en un disco duro interno pero cuando inicia ubuntu no detecta la targeta de video 
y ya intente reconfigurando el xorg y nada 

como puedo hacer que me detecte la targeta de video?

---

### Post by EnriqueK on 2008-12-03
Podrías detallar un poco mas, si pudiste correr en modo Live DVD y luego instalarlo, significa que ha podido reconocer el entorno gráfico básico (vesa) que es que que se consigue con Remastersys, programa que expresamente no copia los drivers de la gráfica de donde se genera, para poder correrlo en cualquier otro equipo que pueda tener una gráfica diferente.
Una vez instalado el Live DVD en otro equipo, recién se busca e instala el driver especifico para la tarjeta gráfica que tenga, mientras no se haga esto, el sistema usará el sistema gráfico básico o vesa.
También podría pasar que sencillamente la versión de Ubuntu que estás instalando no sea compatible con el equipo a instalar, yo por ejemplo no pude instalar Intrepid en mi equipo que cuenta con gráfica vga Intel integrada.
En genral, para instalar drivers para Nvidia o ATI, vas a Sistema-> Administración-> Controladores de Harware, allí te reconocerá la presencia de un dispositivo que requiere de software privativo y te permite descargarlo directamente.

---

### Post by tsueseres on 2008-12-03
> **EnriqueK said:**
> Podrías detallar un poco mas, si pudiste correr en modo Live DVD y luego instalarlo, significa que ha podido reconocer el entorno gráfico básico (vesa) que es que que se consigue con Remastersys, programa que expresamente no copia los drivers de la gráfica de donde se genera, para poder correrlo en cualquier otro equipo que pueda tener una gráfica diferente.
Una vez instalado el Live DVD en otro equipo, recién se busca e instala el driver especifico para la tarjeta gráfica que tenga, mientras no se haga esto, el sistema usará el sistema gráfico básico o vesa.
También podría pasar que sencillamente la versión de Ubuntu que estás instalando no sea compatible con el equipo a instalar, yo por ejemplo no pude instalar Intrepid en mi equipo que cuenta con gráfica vga Intel integrada.
En genral, para instalar drivers para Nvidia o ATI, vas a Sistema-> Administración-> Controladores de Harware, allí te reconocerá la presencia de un dispositivo que requiere de software privativo y te permite descargarlo directamente.

Ok kreo k ya te entendi bueno lo que hice fue instalarlo desde fuera con el comando install, pero tmb he podido cargar ubuntu desde el live cd mas no lo he instalado de esta manera solo desde antes de cargar el livecd con el comando install

si ha lo que te refieres es que deberia de ir a sistema administracion Controladores de Harware, bueno ya fui y no vi nada, lo que me interesa es poner los efectos 

no hay alguna manera de que detecte la targeta de video del modo en que lo he instalado?

---

### Post by EnriqueK on 2008-12-05
Si no andan los efectos tal vez sea por que simplemente el equipo no tiene tarjeta aceleradora gráfica, en caso de que si la tuviera, busca en el foro la forma de usar ENVY.
Pasando a otro tema, por fin me decidí a cambiar de equipo por otro mas acorde a los tiempos, antes creé un LiveDVD con Remastersys sin datos personales, al equipo nuevo le instalé el mismo DD, al principio parecía que andaba bien, pero al rato comenzaba a fallar y hasta no me conectaba a internet, así que reinstalé Ubuntu con el Live DVD y todo salió perfecto, hasta el último detalle.

---

### Post by tsueseres on 2008-12-05
> **EnriqueK said:**
> Si no andan los efectos tal vez sea por que simplemente el equipo no tiene tarjeta aceleradora gráfica, en caso de que si la tuviera, busca en el foro la forma de usar ENVY.
Pasando a otro tema, por fin me decidí a cambiar de equipo por otro mas acorde a los tiempos, antes creé un LiveDVD con Remastersys sin datos personales, al equipo nuevo le instalé el mismo DD, al principio parecía que andaba bien, pero al rato comenzaba a fallar y hasta no me conectaba a internet, así que reinstalé Ubuntu con el Live DVD y todo salió perfecto, hasta el último detalle.

no tiene targetas asi como nvidea ni ati, tiene una interna pero si funciona con los efectos ya que instale ubuntu y el compiz pero cuando instalo con el iso de remastersys no puedo sikiera cambiar a efectos normal ni extra alguien sabe por k??

---

