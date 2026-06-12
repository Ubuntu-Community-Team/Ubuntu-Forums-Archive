---
title: "Instalar huawei mt810"
date: 2010-10-10
forum: Hardware
---

### Post by Nico._G on 2010-10-10
Hola gente del foro son nuevo aqui y estoy bajando la 10.10 de ubuntu para provar.

Use mandriva por un tiempo pero nunca cambie a otra distro porque tube siempre el problema con la configuracion con mi modem HUAWEI MT810 de arnet (NUNCA lo pude configurar con exito) y esta vez me intereso mucho ubuntu y quier usarla 

Por eso queisiera saber si me pueden dar una mano para instalar mi modem

Encontre algunas pero muy viejas del 2007/8 

Gracias

---

### Post by edboy on 2010-10-10
Hola, fijate en este post de T! En una de esas te ayuda.

[http://www.taringa.net/posts/downloads/4829427/Configurar-Modem-Huawei-MT810-en-Ubuntu.html](http://www.taringa.net/posts/downloads/4829427/Configurar-Modem-Huawei-MT810-en-Ubuntu.html)

---

### Post by hectorivand on 2010-10-10
No es una conexión ADSL común y corriente?
 
Saludos
Nacho

---

### Post by juancarlospaco on 2010-10-11
Pero ese tiene ficha RJ-45 o no?, la web de control esta en 10.0.0.2

---

### Post by wanwel on 2010-11-17
hola, hoy he comenzado a utilizar ubuntu con la version 10.10 y me encuentro con el mismo inconveniente
no logre conectar el modem Huawei MT810
he intentado seguir diversas guias de este foro, de taringa y de otras paginas pero sin exito, desde uso de herramientas como ubudsl o la sugerida por edboy

alguien podria ayudarme un poco?
Nico._G lograste que te funcionara?

---

### Post by gmunioz on 2010-11-18
Hola wanwel:

Mira en esta página:

[http://www.modemhuawei.com.ar/](http://www.modemhuawei.com.ar/)

Drivers, ayuda y guia para Ubuntu

---

### Post by wanwel on 2010-11-18
hola, gracias por responder, he leido esa guia y he localizado mi inconveniente.
se debe a que no puedo instalar build-essential no estoy sabiendo el porque aun pero cuando intento instalar la situacion es la siguiente:
estoy sin internet por no poder colocar el modem
coloco el live cd
usando synaptic o por comando en la terminar obtengo los siguientes errores:

```
W: Falló al obtener cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/pool/main/g/gcc-4.4/g++-4.4_4.4.4-14ubuntu5_i386.deb
  Fichero no encontrado
W: Falló al obtener cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/pool/main/g/gcc-defaults/g++_4.4.4-1ubuntu2_i386.deb
  Fichero no encontrado
W: Falló al obtener cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/pool/main/d/dpkg/libdpkg-perl_1.15.8.4ubuntu3_all.deb
  Fichero no encontrado
W: Falló al obtener cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/pool/main/p/patch/patch_2.6-2ubuntu1_i386.deb
  Fichero no encontrado
W: Falló al obtener cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/pool/main/d/dpkg/dpkg-dev_1.15.8.4ubuntu3_all.deb
  Fichero no encontrado
W: Falló al obtener cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/pool/main/b/build-essential/build-essential_11.5_i386.deb
  Fichero no encontrado
W: Falló al obtener cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/pool/main/f/fakeroot/fakeroot_1.14.4-1ubuntu1_i386.deb
  Fichero no encontrado
W: Falló al obtener cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/pool/main/liba/libalgorithm-diff-perl/libalgorithm-diff-perl_1.19.02-1_all.deb
  Fichero no encontrado
W: Falló al obtener cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/pool/main/liba/libalgorithm-merge-perl/libalgorithm-merge-perl_0.08-1_all.deb
  Fichero no encontrado

```

he buscado manualmente los ficheros y si se encuentran en los directorios correspondientes en el cd
aun no tengo mucho manejo de ubuntu asi que no puedo saber que llevar a cabo para solucionar ese problema

---

### Post by juancarlospaco on 2010-11-21
Eso es un Warning del Sources.list, sucede que no todos esos paquetes estan en el CD por defecto,
synaptic: Archivo---Generar script de descarga de archivos.

Igual no entiendo en que esta relacionado con lo anterior...  :(

---

### Post by myqp on 2010-11-21
para q empresa es. claro, personal, movisar? fijate q el asistente de instalción te pone servidores y dns que no son correctos para argentina, quizá debas modificar eso. TAMBIÉN ver los métodos de autenticaxión que algunos no estan soportados, anda probando de a uno a ver con cual se conecta:o:o

---

### Post by wanwel on 2010-11-21
yo consulte el tema de las advertencias, porque tratando de seguir la guia
[http://www.taringa.net/posts/downloads/4829427/Configurar-Modem-Huawei-MT810-en-Ubuntu.html](http://www.taringa.net/posts/downloads/4829427/Configurar-Modem-Huawei-MT810-en-Ubuntu.html)
en la que dice que debemos instalar los paquetes build-essential
tuve ese inconveniente
no puedo avanzar en la guia a causa de ese inconveniente
mi consulta seria si para que se instalen los repositorios desde el cd habia que hacer algo mas que solo activar con "$ sudo apt-cdrom add" en la terminal

sigo sin podes solucionarlo

es un modem de arnet el "alfajorcito" huawei smartax mt810 solo posee conexion mediante USB y segun la mayoria de las guias es lo mismo 
instalar build-essential porque se necesitan realizar algunas compilaciones
agregar driver y firmware
configurar el script de conexion

---

### Post by gmunioz on 2010-11-21
Desde este sitio:

[http://packages.ubuntu.com/maverick/build-essential](http://packages.ubuntu.com/maverick/build-essential)

Puedes bajar el paquete, que requiere a:

dpkg-dev (>= 1.13.5)
g++ (>= 4:4.4.3)
gcc (>= 4:4.4.3)
libc6-dev
make

Se instalan ejecutando en el directorio (carpeta)
donde se alojan la orden:

sudo dpkg -i *.deb

---

### Post by biale on 2010-11-23
> posee conexion mediante USB

Lado WAN ADSL?  También podrías pedir que te lo cambien por un dispositivo con salida Ethernet y de paso tener la posibilidad de armar una red local (?)

---

### Post by wanwel on 2010-11-24
gracias por las respuestas, me puse a instalar manualmente y el problema se centra en g++
he probado bajar ubuntu 10.04 y es el mismo inconveniente, estoy viendo como unica solucion pedir el cambio de modem, yo no soy el titular del servicio por eso no queria recurrir a ese metodo.
nuevamente gracias por los aportes

---

### Post by wanwel on 2010-11-26
he logrado que ande el modem, solucione tambien mi inconveniente con los repositorios y ahora toy usando Ubuntu

lo postie en otro lado donde tambien pregunte:

ATENCION, esto solo lo he testeado en Ubuntu 10.10 no sabria decirles de  otras versiones, al parecer Ubuntu 10.10 trae el firmware y driver  necesario para su funcionamiento asi que no he necesitado realizar  ningun otro procedimiento mas que instalar Ubuntu,  tener conectado el  modem y seguir los pasos 

   1. Necesitamos br2684ctl. Lo descargamos de: [http://ubuntu.mirrors.tds.net/ubuntu/pool/universe/b/br2684ctl/br2684ctl](http://ubuntu.mirrors.tds.net/ubuntu/pool/universe/b/br2684ctl/br2684ctl)... y lo instalamos. 
   2. Levantamos el módulo br2684 (como root o con sudo): 
      modprobe br2684 
   3. Configuramos VPI y VC (como root o sudo): 
      br2684ctl -c 0 -b -a 0.33 
      Para Arnet son 0 y 33. Por eso "0.33" 
      Para Speedy son 8 y 35. Tendríamos que poner "8.35" 
   4. Levantamos la interfaz de red: 
      ifconfig nas0 up 
   5. Abrimos los siguientes archivos: 
      gedit /etc/ppp/pap-secrets 
      gedit /etc/ppp/chap-secrets 
      y colocamos, cambiando con nuestros datos por supuesto, lo siguiente adentro: 
      "usuario@proveedorinternet" * "contraseña" 
      Guardamos y listo.  
Una vez realizados todos estos pasos, ahora queda hacer la conexión con el comando: 
pppoeconf 
Va a aparecer nas0 como interfaz. Se colocan los datos y listo. 

espero que a alguien le sea util. 
saludos! 

Nahuel

---

