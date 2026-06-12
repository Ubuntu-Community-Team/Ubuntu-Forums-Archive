---
title: "Problema de instalación Ubuntu Karmic"
date: 2009-12-01
forum: Instalación y Actualización
---

### Post by Caranthir on 2009-12-01
Luego de leer algunos libros, en especial "la ética hacker y el espíritu dela era de la información" de Pekka Himanen, me decidi a dar el paso total al software libre, el problema es que el paso definitivo, el so, no pude darlo.

El problema es que baje el iso de la versión 9.10 (desktop) de ubuntu (karmic koala) la queme en el cd a velocidad baja para no tener problemas. Luego, reinicio el pc, booteo, elijo idioma, elijo instalar (quiero que formatee el pc y quedarme solo con el como so)y me da una pantalla roja.

Luego trato de instalar desde windows, reinicio, y en la carga, elijo ubuntu, pero me da una pantalla con lineas horizontales. 

Estuve buscando por internet y lo más probable es que sea un problema con mi tarjeta de video... pero aún sabiendo eso no se que hacer para mejorarlo. En la instalación, había una opción de modo gráfico seguro, pero tampoco funciono. Revise errores en el disco y no hay. Sigo usando windows.

Gracias por cualquier ayuda.

---

### Post by Carlos C on 2009-12-02
Puedes probar con instalar la versión alternate:

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

Sería recomendable que nos dijeras cuál es el modelo de tarjeta gráfica que usas.

Saludos.

---

### Post by moreback on 2009-12-02
Si el LiveCD de Ubuntu te corre sin problemas, puedes hacer la instalación desde ahí mismo. Viene con un icono en el escritorio para iniciar la instalación.

Saludos.

---

### Post by Caranthir on 2009-12-02
> **Carlos C said:**
> Puedes probar con instalar la versión alternate:

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

Sería recomendable que nos dijeras cuál es el modelo de tarjeta gráfica que usas.

Saludos.

La estoy descargando. Cuando termine tratare de correrlo a ver que sucede.

El modelo de la tarjeta es Radeon 9200 (si nesecitas más datos dime y trato de averiguarlos)

	 		
> Si el LiveCD de Ubuntu te corre sin problemas, puedes hacer la instalación desde ahí mismo. Viene con un icono en el escritorio para iniciar la instalación.

Saludos. 	

Corri el cd en windows y lo instalo, pero solo con windows, la opción de instalarlo como uúnico so no funciono. Al reiniciar el pc, me da la opción de ir a ubuntu, pero al aceptarla, me da otra pantalla de colores.

---

### Post by Caranthir on 2009-12-02
Baje la versión alternate del cd y me dio el mismo problema. Instale desde windos y al abrirla (cuando escojo) me da la misma pantalla roja. Luego botie desde el cd y lo mismo, al elegir instalar, la pantalla roja. Y marque "modo gráfico seguro"... mismo resultado...

Que puedo hacer ahora? Que datos nesecitan?

---

### Post by moreback on 2009-12-02
Si leyeras lo que puso Carlos_C verías que estamos pidiéndote información acerca de tu tarjeta. Yo además creo que debes darnos información de tu monitor.

Recuerda ser bien detallado al hacerlo.

---

### Post by Caranthir on 2009-12-02
Pense que como habia dado el nombre con eso bastaba... tratare de dar la información que pueda proveer (cualquier consejo de como obtenerla sería útil)

---------------
Display Devices
---------------
        Card name: RADEON 9200 SERIES   
     Manufacturer: ATI Technologies Inc.
        Chip type: RADEON 9250/9200 Series AGP (0x5964)
         DAC type: Internal DAC(400MHz)
       Device Key: Enum\PCI\VEN_1002&DEV_5964&SUBSYS_C0081043&REV_01
   Display Memory: 128.0 MB
     Current Mode: 1024 x 768 (32 bit) (75Hz)
          Monitor: Monitor Plug and Play
  Monitor Max Res: 1600,1200
      Driver Name: ati2dvag.dll
   Driver Version: 6.14.0010.6614 (English)
      DDI Version: 9 (or higher)
Driver Attributes: Final Retail
 Driver Date/Size: 5/3/2006 13:51:00, 258048 bytes
      WHQL Logo'd: Yes
  WHQL Date Stamp: n/a
              VDD: no disponible
         Mini VDD: ati2mtag.sys
    Mini VDD Date: 5/3/2006 13:50:42, 1540608 bytes
Device Identifier: {D7B71EE2-1A24-11CF-256A-02E0A0C2CB35}
        Vendor ID: 0x1002
        Device ID: 0x5964
        SubSys ID: 0xC0081043
      Revision ID: 0x0001
      Revision ID: 0x0001
      Video Accel: 
 Deinterlace Caps: n/a
         Registry: OK
     DDraw Status: Enabled
       D3D Status: Enabled
       AGP Status: Not Available
DDraw Test Result: Not run
 D3D7 Test Result: Not run
 D3D8 Test Result: Not run
 D3D9 Test Result: Not run

---

### Post by moreback on 2009-12-03
¿Y el monitor?

¿Cuales son los rangos de frecuencias en que trabaja?

Puede ser que el servidor gráfico no le esté achuntando al rango que acepta el monitor.

También veo que es una ATI... hartos problemas hay con ellas.

---

### Post by Caranthir on 2009-12-03
> **moreback said:**
> ¿Y el monitor?

¿Cuales son los rangos de frecuencias en que trabaja?

Puede ser que el servidor gráfico no le esté achuntando al rango que acepta el monitor.

También veo que es una ATI... hartos problemas hay con ellas.

Lo que dice el monitor en la parte de atras es:

Model no: mr1708n
Power Rating 100-240v ~ 50/60 hz 2.5A

Si no es eso lo que me estan pidiendo, diganme de donde sacar la información por favor.

---

### Post by Carlos C on 2009-12-04
Según parece tu tarjeta es soportada por Ubuntu:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Es extraño que no funcione. Te sugiero que leas con atención esto, puede que tenga que ver con lo que te ocurre:

[https://wiki.ubuntu.com/X/Quirks#ATI%20Radeon%20Driver%20Quirks](https://wiki.ubuntu.com/X/Quirks#ATI%20Radeon%20Driver%20Quirks)

Saludos.

---

### Post by Caranthir on 2009-12-09
> **Carlos C said:**
> Según parece tu tarjeta es soportada por Ubuntu:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Es extraño que no funcione. Te sugiero que leas con atención esto, puede que tenga que ver con lo que te ocurre:

[https://wiki.ubuntu.com/X/Quirks#ATI%20Radeon%20Driver%20Quirks](https://wiki.ubuntu.com/X/Quirks#ATI%20Radeon%20Driver%20Quirks)

Saludos.

Gracias por el link... aunque debo decir que lei lo que decía y a pesar de eso no me quedo claro. Como dije en un principio mis conocimientos informáticos son mas que escasos.

¿que es un quirk? entiendo que debo mandar un reporte del error, pero no tengo acceso al tipo de error ¿ de donde lo obtengo?...

> The issues go away when: 
[LIST]
[*]Specifying Option "AGPMode" "#" in xorg.conf 
[*]Using vesa or fglrx driver 
[*]Using some older version of the -ati driver that used a different default AGPMode setting
[/LIST]


entiendo que asi se soluciona pero...

¿que es lo de xorg.conf ? como llego a modificar eso?

¿como se cual es el agpmode por default?...

sigo agradeciendo ayuda

---

### Post by nechus on 2009-12-12
Las tarjetas ATI son complicadas para Ubuntu por el tema de los drivers. Existe una versión modificada de Ubuntu que se llama Ultimate Edition, que trae muchos drivers y códecs que el Ubuntu original no puede incluir por problemas de licencias. Es muy probable que Ultimate Edition contenga los drivers necesarios para tu tarjeta. Descárgala de [http://downloads.sourceforge.net/ue-distro/ultimate-edition-2.5-x86.iso](http://downloads.sourceforge.net/ue-distro/ultimate-edition-2.5-x86.iso)
Ten paciencia porque pesa más de tres gigas. La tienes que grabar en un DVD. Buena suerte! ;)

---

### Post by Carlos C on 2009-12-12
> **Caranthir said:**
> ¿que es lo de xorg.conf ? como llego a modificar eso?

Ese archivo se encuentra en /etc/X11/xorg.conf. Antes de hacer algún cambio te recomiendo respaldarlo:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
Si después quieres volver atrás:
```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

Para editarlo, desde el terminal escribes:
```
sudo gedit /etc/X11/xorg.conf
```

Saludos

---

### Post by Caranthir on 2009-12-12
Veré lo que puedo hacer con l del ultimate edition, ya que no tengo grabador de dvd... en cuanto a lo sgte... entiendo que el "terminal" es como el ejecutar en win?, si es asi, no puedo llegar a el por que aun no instalo nada... ¿o me equivoco nuevamente?

---

### Post by nechus on 2009-12-12
¿Tienes _lector_ de DVD al menos?

---

### Post by Carlos C on 2009-12-12
Estoy un poco confundido. Te sugerí que probaras instalando la versión alternate, pero parece que intentaste instalarla desde windows, ¿es así? Dime una cosa, ¿has probado ver si te corre el Live CD, pero no desde windows, sino booteando directamente desde el cd?

---

### Post by Caranthir on 2009-12-12
Lector tengo.

Carlos... ¿ es la misma versión que me recomendaste bajar antes entonces? por que la descargue y la trate de instalar por las 2 vías, por windows y boteando desde el cd, pero con el mismo resultado, la pantalla roja.

---

### Post by Carlos C on 2009-12-12
En el caso del Live CD ¿tienes al menos acceso al menú del principio? Porque podrías tratar de correr el modo a prueba de errores.

Saludos.

---

### Post by nechus on 2009-12-12
Te puedo enviar el DVD de Ultimate Edition por correo si me dices a dónde. Mi mail: alvareznelson arroba gmail punto com.

---

### Post by Caranthir on 2009-12-25
> **Carlos C said:**
> En el caso del Live CD ¿tienes al menos acceso al menú del principio? Porque podrías tratar de correr el modo a prueba de errores.

Saludos.

Como llego a ese modo?...

Nachus, te mando mi dirección por un mail, muchas gracias¡¡¡

edit: Me llego el live cd de Nachus... junto con unos chocolates entrelagos¡¡¡
gracias... mañana me hare tiempo para trastear y ver que saco en limpio.

Que tengan unas grandes fiestas¡¡¡

---

### Post by wrixis on 2010-04-01
Tengo la misma tarjeta y el mismo error.

Cuando arranco con el cd, si elijo instalar, salta una pantalla roja, si espero un rato sale líneas en la pantalla y de ahí no pasa.

Si elijo livecd, pasa lo mismo.

He usado la 8.04 y no tuve problemas, y si no recuerdo mal, con la 8.10 tampoco tuve problemas.

---

### Post by Carlos C on 2010-04-02
Entiendo que cuando tienes ese modelo de tarjeta debes editar el xorg.conf para que funcione. Supongo que instalando la versión alternate tienes la posibilidad de editar el archivo como dicen aquí:

[http://www.ubuntu-es.org/?q=node/122549#comment-348555](http://www.ubuntu-es.org/?q=node/122549#comment-348555)

---

### Post by CdK1 on 2010-04-03
Otra ideas es, instalar con el CD/versión que te funcionó y de ahí actualizar, fácil, rápido y simple ;)

---

