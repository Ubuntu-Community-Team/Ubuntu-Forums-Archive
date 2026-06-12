---
title: "Nuevo en Ubuntu e Incomunicado"
date: 2009-11-03
forum: Hardware
---

### Post by Gerli on 2009-11-03
Hola, acabo de entrar al mundo de Ubuntu, los cargue con el WUBI una maravilla, pero no puedo hacer funcionar el modem de banda ancha movil ni tampoco crear un acceso telfonico.  El modem de banda ancha es un ZTE y el sistema da un error larguisimo cuando lo intento instalar. Agradeceria soporte.):P

---

### Post by Fak89 on 2009-11-04
> **Gerli said:**
> Hola, acabo de entrar al mundo de Ubuntu, los cargue con el WUBI una maravilla, pero no puedo hacer funcionar el modem de banda ancha movil ni tampoco crear un acceso telfonico.  El modem de banda ancha es un ZTE y el sistema da un error larguisimo cuando lo intento instalar. Agradeceria soporte.):P

Podes postearnos el error?
Bienvenido a GNU/Linux y al software libre! :biggrin:

---

### Post by Gerli on 2009-11-04
Tratare pero tengo primero que pasar la PC a Ubuntu, copiarlo y volver a w. Salvo que primero resuelva como instalar un acceso telefonico, me podras guiar.

---

### Post by Snyflex on 2009-11-04
Hola a Todos!

Soy nuevo en Ubuntu, Instale la ultima version, 9.10 Karmic.
Hasta ahora todo Fine!, excepto el Internet, tengo un Modem USB 3G Alcatel xO3O. En la version 9.04 por lo menos me lo reconocia como USB, pero ahora ni siquiera eso.
Eh indagado en infinidad de de sites en busca de Informacion para esto y no termino pegandole bien al tema.
Ayuda con esto, como dije soy Nuevesito en Linux.
Gracias!;)
Un Saludo;

---

### Post by josecuervo86 on 2009-11-04
> **Snyflex said:**
> Hola a Todos!

Soy nuevo en Ubuntu, Instale la ultima version, 9.10 Karmic.
Hasta ahora todo Fine!, excepto el Internet, tengo un Modem USB 3G Alcatel xO3O. En la version 9.04 por lo menos me lo reconocia como USB, pero ahora ni siquiera eso.
Eh indagado en infinidad de de sites en busca de Informacion para esto y no termino pegandole bien al tema.
Ayuda con esto, como dije soy Nuevesito en Linux.
Gracias!;)
Un Saludo;

Hola Snyflex. Para empezar, podrias poner en una terminal (**Aplicaciones** > **Accesorios** > **Terminal**) lo siguiente:

```
lsusb
```

y pegar aca el resultado?

---

### Post by Snyflex on 2009-11-04
Bus 007 Device 005: ID 1c9e:6061
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 064e:a101 Suyin Corp.Acer CrystalEye Webcam
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Lo mas probable ustedes ya lo sepan..:D Pero con el Modem Enchufado la primera linea aparece, pero si lo quito no aparece.
Saludos;

---

### Post by Fak89 on 2009-11-04
> **Gerli said:**
> Tratare pero tengo primero que pasar la PC a Ubuntu, copiarlo y volver a w. Salvo que primero resuelva como instalar un acceso telefonico, me podras guiar.

Si, es verdad que tenes que andar reiniciando a cada momento y se que es totalmente molesto, pero bueno. Va 1 sola ves. Desde Ubuntu podes entrar a los discos o particiones de Windows desde "Lugares", fijate que vas a encontrar algunos accesos llamados "Sistema de archivos de X Gb", crea un archivo de texto y pega el error que te da ahí.

Sin reiniciar.. vamos a ver el tema de internet, hay varios que en esta ultima entrega de Ubuntu tenemos problemas con internet y lo solucionamos con un comando. Por ahí a vos te funcione igual.
Anda a "Aplicaciones", "Accesorios", "Terminal" y pone
[PHP]sudo pppoeconf[/PHP]
Pone tu contraseña de administrador (root) - no la vas a ver - y seguí los pasos. Por ahí cuando termines ya tengas internet.

Si no tenés internet, reinicia tranqui y busca ese archivo de texto para ponernos el error :P

Saludos!

---

### Post by Snyflex on 2009-11-04
Dios pero que es lo que pasa!!!

Aparte de que no me reconoce el Modem ni siquiera como Dispositivo USB no hace nada cuando le conecto el cable de red que tengo de mi Desktop con con Windows e Internet.

Osea no me reconoce la red tampoco.
Que hago en este caso? Ayuda!!

Me esta decepcionando Ubuntu

---

### Post by Fak89 on 2009-11-04
> **Snyflex said:**
> Dios pero que es lo que pasa!!!

Aparte de que no me reconoce el Modem ni siquiera como Dispositivo USB no hace nada cuando le conecto el cable de red que tengo de mi Desktop con con Windows e Internet.

Osea no me reconoce la red tampoco.
Que hago en este caso? Ayuda!!

Me esta decepcionando Ubuntu

Mmmm.. Conectar GNU/Linux en red con Win es algo un poco avanzado.. Yo todavia no me puse a hacerlo.. Lo podes hacer con SAMBA, seguramente en google encontras la Wiki con el tutorial..
Y para el modem por ahi necesites drivers.. yo no conosco mucho de eso porq no uso.. por ahi alguen te pueda ayudar en eso

---

### Post by mama21mama on 2009-11-05
@Snyflex

1º en el foro hay ciertas pautas para que sea lo mas amigable posible.
2º no te cuelgues por favor de otro hilo, crea t propio hilo con tus poblemas
3º esto no es soporte tecnico, es un foro de personas que nos ayudamos entre todos.
4º busca en google antes de comentar


:) saludos

---

### Post by mama21mama on 2009-11-05
> **Gerli said:**
> Tratare pero tengo primero que pasar la PC a Ubuntu, copiarlo y volver a w. Salvo que primero resuelva como instalar un acceso telefonico, me podras guiar.

ok esperamos mas datos del modelo del modem.
Saludos

---

### Post by Snyflex on 2009-11-05
Cuando dije que "Ubuntu" me estaba decepcionando me referia al SO, no al Foro.
De todas formas Gracias por intentar ayudarme, resolveré por mi lado.:p

---

### Post by guillermolisi on 2009-11-05
Por favor, mantenerse en tema y no derivar en OT. Gracias.

---

### Post by Gerli on 2009-11-05
> **Fak89 said:**
> Si, es verdad que tenes que andar reiniciando a cada momento y se que es totalmente molesto, pero bueno. Va 1 sola ves. Desde Ubuntu podes entrar a los discos o particiones de Windows desde "Lugares", fijate que vas a encontrar algunos accesos llamados "Sistema de archivos de X Gb", crea un archivo de texto y pega el error que te da ahí.
 
Sin reiniciar.. vamos a ver el tema de internet, hay varios que en esta ultima entrega de Ubuntu tenemos problemas con internet y lo solucionamos con un comando. Por ahí a vos te funcione igual.
Anda a "Aplicaciones", "Accesorios", "Terminal" y pone
[php]sudo pppoeconf[/php]
Pone tu contraseña de administrador (root) - no la vas a ver - y seguí los pasos. Por ahí cuando termines ya tengas internet.
 
Si no tenés internet, reinicia tranqui y busca ese archivo de texto para ponernos el error :P
 
Saludos!
 
Hola.  Entre en la Terminal y puse los comandos, funciono pero el sistema No encontro al modem de banda ancga, no lo ve.
El mensaje completo del error cunado trato de ejecutar la instalacion del mismo es el siguiente:
Archive:  /media/cdrom1/Install.exe
[/media/cdrom1/Install.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/cdrom1/Install.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/cdrom1/Install.exe or
          /media/cdrom1/Install.exe.zip, and cannot find /media/cdrom1/Install.exe.ZIP, period.
 
Tambien estube leyendo en un ayuda que es probable que el modem no es detectado como tal sino como dispositivo de almacenamiento y que instañamdp el paquete **udev-extras** se podria solucionar.
 
Ahora bien de donde saco y como se instala este paquete, o de que forma se puede continuar para solucionar el aislamiento...
Saludos y Gracias

---

### Post by josecuervo86 on 2009-11-05
Hola Gerli, fijate que estas tratando de ejecutar un archivo .exe y este tipo de archivo ejecutable solo se utiliza en window$. Por lo que vi tu modem no esta reconocido por el sistema. Yo probaria instalando ndiswrapper. Como no tenes internet no lo vas a poder instalar desde ubuntu pero te lo podes bajar de aca: [http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.54-2ubuntu1_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.54-2ubuntu1_all.deb)

---

### Post by Gerli on 2009-11-05
Ya lo baje y lo instale, todo sigue igual
Favor Ayuda...

---

### Post by josecuervo86 on 2009-11-05
Ok, desconecta el modem, conectalo de nuevo y apenas lo conectes corre esto en consola:

```
dmesg
```

Luego pega el resultado aca

---

### Post by mama21mama on 2009-11-05
A veces sucede que debes cambiar de puerto usb, a pasado que en algunos el sistema lo reconoce y en otros puertos para el sistema es como si no estaria enchufado.

Reconocer, me refiero a que el sistema sabe que tiene enchufado algo. Pero esto no quiere decir que este bien configurado ;)

trata de ir cambiando de puertos usb y tira en la terminal

```
lsusb
```

---

### Post by Gerli on 2009-11-05
Ya lo corri, me da un resultado larguisimo, pero no puedo copiarlo en un Pendrive para cambiarlo a otra maquina con W. y comunicacion para poder enviarlo. Estare haciendo algo muy mal...

---

### Post by Gerli on 2009-11-05
> **josecuervo86 said:**
> Ok, desconecta el modem, conectalo de nuevo y apenas lo conectes corre esto en consola:
 
```
dmesg
```
 
Luego pega el resultado aca
 
No me dejo pegarlo porque es muy extenso, intente mandarlo atachado...
 
Quedo a la espera gracias

---

### Post by Gerli on 2009-11-05
Hola, me dice que el comando no lo encuentra
 
Gracias

---

### Post by Gerli on 2009-11-05
Hola, me dice que el comando es desconocido
 
Gracias

---

### Post by Gerli on 2009-11-05
Segun documentacion deberia conseguir e instalar lo siguiente:
 
gnome-network-admin package  para conectar un modem y por el tema del modem de banda ancha el:udev-extras pachage.
 
Siendo que no tengo comunicacion con el sistema Ubunto, como lo consigo desde el Windows.
 
Agradecere ayuda

---

### Post by Gerli on 2009-11-05
> **mama21mama said:**
> ok esperamos mas datos del modelo del modem.
Saludos
 
Estos son los datos del reporte:
Archive:  /media/cdrom1/Install.exe
[/media/cdrom1/Install.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/cdrom1/Install.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/cdrom1/Install.exe or
          /media/cdrom1/Install.exe.zip, and cannot find /media/cdrom1/Install.exe.ZIP, period.
 
Agradecere comentarios

---

### Post by mama21mama on 2009-11-05
Los datos que mandaste no es lo que pretendiamos ver.

Mirate esto, [Configurar internet en Ubuntu modem ZTE mf626]("http://www.taringa.net/posts/linux/2318037/Configurar-internet-en-Ubuntu-modem-ZTE-mf626.html")

Ni idea si es tu modelo, ya que no dijiste que modelo tenias, ZTE creo que debe de haber muchos.

---

