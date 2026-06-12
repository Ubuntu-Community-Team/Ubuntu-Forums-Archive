---
title: "hp 2133- Ubuntu 9.04 jaunty jackalope"
date: 2009-04-27
forum: Hardware
---

### Post by lean-mini on 2009-04-27
Señores. esto funciona y bien!!
Posteo sobre esta hp 2133, porque la misma es muy particular. 
He probado el jaunty y la verdad es que todo se instala rápido y fácil (lo instalé usb, instalación nueva). Antes tenía la v. 8.04.2 Hardy Heron. Pero jaunty mejoró el video (ya no más vesa) y el wifi (ya no más ndiswrapper). Lo demás está muy bien, tiene un inicio muy rápido, consume pocos recursos, la vida de la batería mejoró bastante, incorpora openoffice 3.0 que supera apreciablemente al 2.4, y firefox 3.09 que ya lo tenía hardy heron.
Si alguién tiene ésta hp mini, que originalmente viene con el SUSE Linux 10.0, cambien tranquilos porque mejora incomparablemente. Y si alguién tiene Win$ gate$ se los aseguro que funciona mucho mejor que el mejor intento que es el xp.
Saludos
LEan

---

### Post by faktorqm on 2009-04-28
postea por favor un lspci y un lsusb para tener como referencia que hardware esta soportado. gracias. salu2!

---

### Post by clasificado on 2009-04-28
¿un lshw no es mas completo?

Sino tampoco es que sobra

clasificado

---

### Post by tokarliz86 on 2009-06-10
hola,mi problema es que tengo una hp 2133 y le puse ubuntu netbook remix y no puedo hacer andar compiz me dice no se pueden activar efectos si alguien me podria dar una mano para solucionar esto,yo se que es por problemas de compatibilidad con la placa de video VIA integrada,busque por todos lados y no puedo hacerla funcionar si alguien me ayudara estari muy agradecido!!!

---

### Post by tokarliz86 on 2009-06-10
como hiciste andar compiz y los efectos 3d????????me podes decir??????????

---

### Post by ADICTOALMAXIMO on 2009-06-10
Te hace falta placa

---

### Post by guillermolisi on 2009-06-10
Lo que te estan diciendo es que con placas de video VIA no hay aceleracion grafica posible, aun con los drivers que se suponen son para esas placas.

Si buscas en este foro thread relacionados con video VIA vas a encontrar mucho material, te ahorraras mucho tiempo y trabajo y no te sentiras desdichado pero no solo (hay varios que te acompañan en suerte).

No se sabe si algun dia la gente de VIA abrira sus puertas para desarrollar drivers adecuados con aceleracion 3D.

---

### Post by guillermolisi on 2009-06-10
Uni los dos threads ya que hablan sobre el mismo tema y hasta, aparentemente, del mismo hardware.

---

### Post by guillermolisi on 2009-06-10
> **lean-mini said:**
> Señores. esto funciona y bien!!
Posteo sobre esta hp 2133, porque la misma es muy particular. 
He probado el jaunty y la verdad es que todo se instala rápido y fácil (lo instalé usb, instalación nueva). Antes tenía la v. 8.04.2 Hardy Heron. Pero jaunty mejoró el video (ya no más vesa) y el wifi (ya no más ndiswrapper). Lo demás está muy bien, tiene un inicio muy rápido, consume pocos recursos, la vida de la batería mejoró bastante, incorpora openoffice 3.0 que supera apreciablemente al 2.4, y firefox 3.09 que ya lo tenía hardy heron.
Si alguién tiene ésta hp mini, que originalmente viene con el SUSE Linux 10.0, cambien tranquilos porque mejora incomparablemente. Y si alguién tiene Win$ gate$ se los aseguro que funciona mucho mejor que el mejor intento que es el xp.
Saludos
LEan

Que placa de video tenes en esa maquina ? (por eso el lspci, lshw, lsusb)

---

### Post by spmthis@sourcedevil.com on 2009-07-06
Hey yo tengo el mismo problema, tengo hpmininote 2133, primero probe con 9.04 y tiene los siguiente clavos:

1. el wirless deja de funcionar cada cierto tiempo o cuando se suspende (no he probado con ndiswrapper)

2. el video es VESA y no hice funcionar los drivers de via, tambien se congela en ocaciones.

Pero digamos que si voy por un cafe me funciona sin problemas casi siempre.

NO PRUEBEN el netbook remix, simplemente es megalento, tan lento que con solamente actualizarlo decidi no usarlo, creo que es por que el netbook es para intel atom y no para el via c7 que trae el 2133.

si alguien sabe como hacer funcionar el video gracias, probe con los drivers que estan en via pero ninguno me funciono

---

### Post by netbird on 2009-07-09
> **spmthis@sourcedevil.com said:**
> Hey yo tengo el mismo problema, tengo hpmininote 2133, primero probe con 9.04 y tiene los siguiente clavos:

1. el wirless deja de funcionar cada cierto tiempo o cuando se suspende (no he probado con ndiswrapper)

2. el video es VESA y no hice funcionar los drivers de via, tambien se congela en ocaciones.

Pero digamos que si voy por un cafe me funciona sin problemas casi siempre.

NO PRUEBEN el netbook remix, simplemente es megalento, tan lento que con solamente actualizarlo decidi no usarlo, creo que es por que el netbook es para intel atom y no para el via c7 que trae el 2133.

si alguien sabe como hacer funcionar el video gracias, probe con los drivers que estan en via pero ninguno me funciono

La placa de video no funciona bien bajo Ubuntu 9.04 y no hay driver de VIA disponible todavia, para esta versión. 
Si instalas la versión 8.04, podes utilizar el driver de VIA para la placa de video integrada (CN896/VN896/P4M900 [Chrome 9 HC]). Te paso el link donde bajarlos:

[http://www.viaarena.com/displaydrivers.aspx?PageID=1&OSID=45&CatID=3220&SubCatID=189](http://www.viaarena.com/displaydrivers.aspx?PageID=1&OSID=45&CatID=3220&SubCatID=189)

Además te paso un link de la wiki de Ubuntu, con los tests de compatibilidad de los dispositivos.

[https://wiki.ubuntu.com/LaptopTestingTeam/HP2133](https://wiki.ubuntu.com/LaptopTestingTeam/HP2133)

Espero que te sirva y puedas instalar Ubuntu en tu netbook.

Suerte!

---

### Post by alanbadillo on 2009-07-28
Hola, creo que ya recorri todos los foros y paginas hacerca de mi compu (hp 2133) y no pude encontrar los drivers, ni instalar el 8.04.

Sin embargo instale correctamente el 9.04 y luego el remix.

Para los que quieran probar el remix, les advierto (como ya lo dijieron) que esta megalento, pero en preferencias pueden ir a cambier modo de escritorio, esperan algunos tantos segundos, y cambian a escritorio clasico. Sera como tener el ubuntu normal el 9.04 desktop, con la ventaja de poder regresar a la forma netbook. Les digo este tip para que lo dejen asi mientras sale el driver y no se desesperen formateando.

Por cierto, no actualicen a karmic koala (9.10) deja de funcinar el wirless.

Aprovechando, comento que intente instalar una banda ancha movil telcel de mexico, todo hiba bien, pero creo que los puertos o la contraseña esta mal, porque al final me desconecta. Si alguien logro usar una banda ancha por favor paseme el tip.

En cuanto a los que quieran saber como arreglar el problema grafico sin desactivar la red. Les paso los siguientes pasos:

NOTA: NO HAY ACELERACION GRAFICA DE TODOS MODOS CON ESTOS PASOS, Y LAS VARIANTES A MODIFICAR DEL XORG YA LAS INTENTE SIN LOGRAR NADA.

Primero les paso el contenido del xorg.conf, este archivo es el que se encarga de los graficos, es como un archivo de texto, y si de pronto pruebas y estropeas la configuracion, entra en modo a prueba de fallos, luego ingresa con tu nombre y usuario y escribe:

```
sudo nano /etc/X11/xorg.conf
```

NOTA: PARA LOS QUE NO SABEN USAR LINUX CHEQUEN MIS TIPS DEL FINAL

Entonces se abrira el achivo. borren todo y escriban las sguientes cosas:

```
Section "Device"
    Identifier    "Configured Video Device"
    Option "PanelSize" "1024x600"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```

Eso bastara para que funcione la pantalla.

Cuando salgan los drivers sere el primero en postear muchos blogs de como instalarlos en la version mas estable de linux, espero siga siendo esta, no quiero penar que tardaran mucho en salir.

A excepcion de la aceleracion grafica todo bien, un poco lento los videos flash, pero mejor los descargo y luego los veo.

Aqui las notas para los principiantes en linux:

Para no estar usando sudo seguido escriban:

```
sudo su
```

Con eso entraran como root y nada les impedira ejecutar comandos validos.

Lo siguiente es abrir consolas si nuestra pantalla se desconfiguro:

ctrl + shift + f1 .. f2 .. f12

Cada consola es diferente de la otra, cuando el xorg falla no nos dejara usar esa consola, no las malgasten.

Si ya se encuentran el la consola 10 les recomiendo reiniciar para no usar el cortacorriente. escriban como root:

```
reboot
```

Comandos basicos:

```
cp /directorio1/archivo1.ext /directorio2/archivo2.ext
```

Este comando copia el archivo1 del directorio1 al directorio2 con el nombre archivo2

```
mv /directorio1/archivo1.ext /directorio2/archivo2.ext
```

En vez de copiar es cortar, si estan como root no les pedira confirmacion y podrian reemplazar por equivocacion un archivo importante, hay que tener cuidado.

```
mkdir /directorio/nueva_carpeta
```

Crea una carpeta, otra forma es:

```
cd nueva_carpeta*
```

cd por si solo cambia a un directorio, si el directorio no existe marca error, en el caso anterior si el directorio no existe lo crea.

```
cd /home
```

Usos basicos

```
cd ..
```

Regresa un nivel en el arbol

```
dir
```

Muestra los archivos

--help o help muestra ayuda mas avanzada

```
comando --help
```

Donde comando es cualquira de los que existen.

Por ultimo:

```
apt-get update
```

Actualiza el sistema

```
gedit /directorio/archivo_contiene_texto
```

Lo abre en el editor de textos, si es un archivo de sistema no deja modificarlo a menos que lo abramos con sudo o en modo root. Si ponen sudo antes de cualquier comando lo abrira con todo los privilegios.

Para dar privilegios root a un archivo es:

```
chmod x+a /directorio/archivo
```

Claro en modo root o anteponiendo la palabra sudo

Para instalar un archivo con codigo script de instalacion

```
sh ./archivo
```

o tambien

```
./archivo
```

Para movernos a otros directorios

```
cd /directorio/mi\ directorio\ con\ espacios/Que_largo
```

cada que escribamos un directorio pulsemos la tecla tab para que nos complete el texto, si el directorio o archivo no es unico puede que no haga nada o que lo complete hasta la parte en comun. No olviden que es importante escribir las mayusculas o minusculas de cualquier archivo o directorio.

Gracias por leer. :P BYE

---

### Post by kirichof on 2009-11-20
> **alanbadillo said:**
> Por cierto, no actualicen a karmic koala (9.10) deja de funcinar el wirless.
Para quien llegue aquí buscando como solucionar lo del wireless, la solución es instalar el paquete "b43-fwcutter"
```
sudo apt-get install b43-fwcutter
```

---

