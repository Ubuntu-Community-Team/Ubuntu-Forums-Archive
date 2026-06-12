---
title: "Graphic Tablet working in 5 steps!!"
date: 2010-05-06
forum: Hardware
---

### Post by al.do on 2010-05-06
[COLOR="blue"]*METHOD FOR **UBUNTU 11.04**:*[/COLOR]

The old methods still working on **Ubuntu 11.04** (Thanks **BCtom**)
For the **Waltop** models (like **Genius Gpen-F509**) you don't need install **Wizardpen** driver, only connect the tablet and enjoy.

You can know if your tablet is Waltop model with this command:

```
cat /proc/bus/input/devices
```

In my case (**Genius Gpen-F509**) the **MachtProduct** is:

```
N: Name="         WALTOP             Tablet    "
```



[COLOR="blue"]*METHOD FOR **UBUNTU 10.10**: (thanks **negora** for the solution and **doctormo** for update the ppa repository)*[/COLOR]

**1.** Install the Wizardpen driver from the deb package **[COLOR="blue"]wizardpen_0.7.3-1_i386.deb[/COLOR]** or the ppa repository, you can add add the repository with this command:

```
sudo add-apt-repository ppa:doctormo/xorg-wizardpen && sudo apt-get update && sudo apt-get install xserver-xorg-input-wizardpen
```

**2.** Restart and enjoy your tablet :)

**IMPORTANT:** If your tablet don't work properly after the restart, try modifying the **70-wizardpen.conf** file putting your configuration manually and report the bug:

For **Gnome** users:
```
sudo gedit /usr/share/X11/xorg.conf.d/70-wizardpen.conf
```

For **KDE** users:
```
sudo kate /usr/share/X11/xorg.conf.d/70-wizardpen.conf
```

If you cannot edit this file, use this command and then try to edit again:

```
sudo cp /usr/lib/X11/xorg.conf.d/70-wizardpen.conf /usr/share/X11/xorg.conf.d
```

...and now put the info that I explain in the method for **Ubuntu 10.04** in the point 2.



*[COLOR="blue"]METHOD FOR **UBUNTU 10.04**[/COLOR]*

I've tried with another configuration for **70-wizardpen.conf** and this works better.

**1.** Install **Wizardpen** driver from sources or deb binaries (I used the deb package **[COLOR="blue"]wizardpen_0.7.3-1_i386.deb[/COLOR]**)

**2.** Type this command in the terminal to know the **MachProduct** info of your Pentablet:

```
cat /proc/bus/input/devices
```

In my case the **MachtProduct** is:

```
N: Name="         WALTOP             Tablet    "
```

**3.** Use the calibration tool in the terminal:

```
wizardpen-calibrate /dev/tablet-event
```

**4.** Edit the file **70-wizardpen.conf** using root privileges: 

For **Gnome** users:
```
sudo gedit /usr/lib/X11/xorg.conf.d/70-wizardpen.conf
```

For **KDE** users:
```
sudo kate /usr/lib/X11/xorg.conf.d/70-wizardpen.conf
```

So, my new **70-wizardpen.conf** file for **[COLOR="Green"]Genius G-pen F509[/COLOR]** is: 

```
Section "InputClass"
   Identifier "wizardpen"
   MatchDevicePath "/dev/input/event*"
   [COLOR="Blue"]MatchProduct "WALTOP|Tablet"[/COLOR]
   Driver "wizardpen"
[COLOR="DimGray"]#[CALIBRATION] This data was taken from wizard-calibrate tool.[/COLOR]
        Option          "TopX"          "260"
        Option          "TopY"          "377"
        Option          "BottomX"       "17782"
        Option          "BottomY"       "10584"
[COLOR="DimGray"]#[END CALIBRATION][/COLOR]
EndSection
```

And this is for **[COLOR="Green"]Genius PenSketch 9x12[/COLOR]**.

```
Section "InputClass"
   Identifier "wizardpen"
   MatchDevicePath "/dev/input/event*"
   [COLOR="Blue"]MatchProduct "Tablet|PF1209"[/COLOR]
   Driver "wizardpen"
[COLOR="DimGray"]#[CALIBRATION] This data was taken from wizard-calibrate tool.[/COLOR]
   Option          "TopX"          "0"
   Option          "TopY"          "1553"
   Option          "BottomX"       "32541"
   Option          "BottomY"       "32762"
[COLOR="DimGray"]#[END CALIBRATION][/COLOR]
EndSection
```

---

### Post by al.do on 2010-05-06
Sorry for the double post, delete this comment.

---

### Post by overdrank on 2010-05-07
Threads merged :)

---

### Post by al.do on 2010-05-07
I'm sorry, yesterday my internet conection was giving problems and the thread was created two times. Please delete one of the merged messages because they are the same.

---

### Post by euripides on 2010-05-08
Thank you so much, al.do!

Your instructions worked for mine Aiptek 1400u (aka Waltop) too :-D

Happy painting,

euripides

---

### Post by al.do on 2010-05-09
You're welcome. I'm happy that this solution has been useful for you.

---

### Post by bombel on 2010-05-09
Thank you. My Genius f610 works now too!
:)

---

### Post by BCtom on 2010-05-09
Thank you very much! 

My Tablet W8060U (UC-Logic) now works like a charm. I was getting worried after I upgraded to Ubuntu 10.04 that I was never going to get this fixed for a few months after everyone else got theirs going. thanks for the how-to instructions.

Tom

---

### Post by negora on 2010-05-10
Hello! I'm just in the same situation with my UG-LOGIC Tablet WP8060U. However I'm not being able to make it work. Just to clarify... Do you all use the i386 edition of Ubuntu or, on the contrary, you use the amd64 one? Thank you.

---

### Post by negora on 2010-05-10
I believe to have found part of the origin of my issue and a solution. I've 2 important conclusions:

1 - My tablet is not "recognized" as being a tablet but a pointer, so the "MatchIsTablet" rule at /usr/lib/X11/xorg.conf.d/70-wizardpen.conf won't work ever. I've tried different possibilities and "MatchIsPointer" works right.

I guess that it has something to do with UDEV and the rule files. On HAL there was a key which allowed to set the device as a tablet (as a stylus really):

```
<merge key="input.product" type="string">stylus</merge>
```

However, I've no idea about if this could be achieved in UDEV in a similar way.


2 - If I only replace "MatchIsTablet" by "MatchIsPointer", this will activate the rule but cause the pointer to move and get stuck to the coordinate 0,0 . It's mandatory to set the dimensions of the tablet to make it work.


So, summarizing, here it's my 70-wizardpen.conf file:

```
Section "InputClass"
   Identifier "wizardpen"
   MatchIsPointer "on"
   MatchDevicePath "/dev/input/event*"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver "wizardpen"
   Option "TopX" "2650"
   Option "TopY" "3563"
   Option "TopZ" "10"
   Option "BottomX" "30733"
   Option "BottomY" "29715"
   Option "BottomZ" "511"
EndSection

Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsPointer "on"
   MatchDevicePath "/dev/input/mouse*"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver ""
EndSection
```

In my case the "MatchVendor" rule works fine by the way.


We've been investigating this issue at:

LaunchPad bug #576610: [https://bugs.launchpad.net/wizardpen/+bug/576610](https://bugs.launchpad.net/wizardpen/+bug/576610) .
LaunchPad bug #573191: [https://bugs.launchpad.net/wizardpen/+bug/573191](https://bugs.launchpad.net/wizardpen/+bug/573191) .

---

### Post by lisboaferreira on 2010-05-10
Hi,

Here is the deal... I've followed all the instructions, but the pen's buttons just don't work.

Can someone help me please ?

mine is the gpen f 509

tks.

---

### Post by BCtom on 2010-05-10
Hi Negora,

I'm only running 32bit myself, and I noticed that you only used the "event*" rather than what the "how-to" suggests. 

I also noticed that you have Z-coordinates in your conf file, is that your pressure sensitivity? I seem to have this with just the configuration I have now.

> **negora said:**
> Hello! I'm just in the same situation with my UG-LOGIC Tablet WP8060U. However I'm not being able to make it work. Just to clarify... Do you all use the i386 edition of Ubuntu or, on the contrary, you use the amd64 one? Thank you.

Here is the input of my 70-wizarpen.conf file:

> Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/event4"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    Option          "TopX"          "826"
        Option          "TopY"          "2626"
        Option          "BottomX"       "32747"
        Option          "BottomY"       "32762"
   Driver "wizardpen"
EndSection

Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/mouse*"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver ""
EndSection

---

### Post by negora on 2010-05-10
**BCtom:** First of all, thanks for spending your time to answer.

Finally I could solve it. In my case it was the MatchIsTablet rule which caused my head aches. I don't know why, but my tablet and also others' seem not to be recognized as a tablet, but just as a simple pointer. Replacing MatchIsTablet by MatchIsPointer and adding the tablet features as Option lines did the miracle :) .

---

### Post by al.do on 2010-05-11
**lisboaferreira**; What architecture are you using? (32bits or 64bits)
I used the deb package with the same tablet in Ubuntu 32 and works great, if you are using amd64 please try to compile the sources.

---

### Post by lisboaferreira on 2010-05-11
> **al.do said:**
> **lisboaferreira**; What architecture are you using? (32bits or 64bits)
I used the deb package with the same tablet in Ubuntu 32 and works great, if you are using amd64 please try to compile the sources.


Thanks al.do, 

I use the 32bits, but now I noticed that you had updated to UBUNTU 10.04, I'm still on the 09.10... I guess that might be the problem... what you think ?

I'm trying to update it (again), yesterday my conection was too lazy and I was forced to give up before it was finished...

Well, I'll keep in touch, hoping the problem is with UBUNTU version...

---

### Post by al.do on 2010-05-11
I never tried the method of this thread in Ubuntu 9.10.

---

### Post by migueleonm on 2010-05-15
My gpen works perfectly but i have a problem with GIMP, regular mouse buttons and wheel do not work inside gimp. Same with my laptop and the touchpad.

---

### Post by arcr14 on 2010-05-16
Hola,se que no debo escribir en español pero no se escribir en inglés, lo que pasa es que tengo un problema con mi tableta.
Desde el principio: Conecto mi tableta y puedo me puedo mover con el lapicero en el escritorio pero una vez que pico con el lapicero a la tableta, esta se queda como congelada durante un rato y tengo q esperar hasta q vuelva a parpadear( estaba estática). Supuse entonces que era porque no había instalado los drivers o que se yo, entonces me puse a buscar en google y encontré este tema, hice todo lo indicado el archivo 70-wizardpen.conf me quedó así:

```
Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/event*"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver		"wizardpen"
	Option		"Device"	"/dev/input/event*"
	Option		"TopX"		"1786"
	Option		"TopY"		"39"
	Option		"BottomX"	"14665"
	Option		"BottomY"	"15278"
EndSection
Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/mouse*"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver ""
EndSection

```
Lo guardé y reinicié, pero la tableta seguía con el mismo problema, es decir se congela cuando le pico con el lapicero.

Entonces probé cambiando los asteriscos("Device"	"/dev/input/event*"; "/dev/input/mouse*") por los números correspondientes. También probé cambiando ahi donde dice MatchIsTablet por MatchIsPointer y aún así no funcionaba.

Ahora no sé que más hacer, supongo q el problema está la configuración del lapicero pero no se que debo cambiar o en donde, es que soy nuevo en Ubuntu.

Por favor ayudenme.

---

### Post by negora on 2010-05-16
**arcr14:** ¿Te has asegurado de que los números de "mouse" y "event" sean los correctos en tu caso?

---

### Post by arcr14 on 2010-05-16
He gracias por responder rápido.

Si mira he escrito esto cat /proc/bus/input/devices, luego:

I: Bus=0003 Vendor=172f Product=0500 Version=0110
N: Name="WALTOP International Corp. Media Tablet"
P: Phys=usb-0000:00:1d.0-1.3/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/input/input10
U: Uniq=
H: Handlers=kbd mouse2 event7 
B: EV=10001f
B: KEY=c03 1f0001 0 0 e08effdf01cfffff fffffffffffffffe
B: REL=143
B: ABS=1fffff0001000003
B: MSC=10

entonces cambié los asteriscos por 7 y 2 respectivamente, pero eso después de haber probado de como viene por defecto.

---

### Post by negora on 2010-05-16
**arcr14:** El mejor truco para averiguar dónde está el problema es comentar ciertas líneas, comprobar si funciona y, en caso de que no sea así, ir eliminando comentarios progresivamente y repetir el proceso. Yo te recomiendo comentar MatchIsVendor y MatchIsPointer , ya que son los que tengo comprobados que causan más problemas. En tu caso es posible que MatchIsVendor no coincida...

Si deseas conocer el nombre de fabricante y producto que debería tener el archivo de configuración, ejecuta el siguiente comando, desenchufa y enchufa tu tableta, y busca las claves ID_VENDOR_ENC e ID_MODEL_ENC en la salida ofrecida:

```
sudo udevadm monitor --property
```

Si no quieres reiniciar el ordenador en cada prueba, abre una consola y reinicia X mediante este comando (reinicia GDM, pero implica reiniciar X):

```
sudo service gdm restart
```

---

### Post by arcr14 on 2010-05-16
Creo que el vendor si es el correcto, igual he probado cambiándolo por lo que resultó del comando que es esto: WALTOP\x20International\x20Corp.
No funciona.

-Mi tableta es una Genius M712 pero en el reverso de la caja dice algo de KYE systems o algo así.
- Estoy usando una versión 64bits de Ubuntu, tiene esto algo que ver

---

### Post by negora on 2010-05-16
Ten en cuenta que \x20 significa un espacio en Unicode. Así que no escribas \x20 literalmente, sino dicho espacio. En otras palabras: "WALTOP International Corp". O eso, o comenta la línea MatchVendor.

Que uses la versión de 64 bits en principio no tiene nada que ver, siempre y cuando hayas descargado e instalado la versión adecuada del controlador. Yo también pensé que en mi caso podía ser eso, pero en absoluto. Asegúrate de tener la última versión, que es la 0.7.3.

---

### Post by arcr14 on 2010-05-16
Oye, gracias, ahora si funciona, comenté las líneas de Matchvendor y problema resuelto. Gracias nuevamente.
Ahora el único problema es que el mouse se ha desactivado pero eso ya no es de importancia.

---

### Post by negora on 2010-05-16
**arcr14:** En ese caso toca no comentar la línea y probar lo que te digo de los espacios. También puedes probar a usar el texto ".*WALTOP.*" . Esto teóricamente debería hacer que esta regla coja cualquier periférico de ese fabricante y evite el ratón (salvo que sea de la misma marca, que lo dudo).

Si no quieres darle más vueltas y deseas que tanto ratón como tableta funcione, entonces comenta MatchVendor y quita el asterisco de las claves Device para poner los números que correspondan.

Yo te recomiendo no hacer esto último y gastar unos minutos intentando lo primero, ya que si un día desconectas la tableta, es posible que su número cambie.

En fin, enhorabuena y que logres solucionar este último escollo.

PS. Apologizes to everybody for speaking in Spanish, but this user doesn't speak English and got a simple question. The problem has been solved ;) .

---

### Post by arcr14 on 2010-05-16
yes, both tablet and mouse are of the same brand. Then I tried what you mentioned first, but does not work, then I tried the latter and it works. I do not think the numbers will change because I've done the command cat / proc / bus / input / device several times and always gives the same numbers.

PS: These lines have been translated with google translator

---

### Post by negora on 2010-05-16
**arcr14:** Hi again. Another way to solve it is adding a rule of type MatchProduct. You must use the value from the ID_MODEL_ENC key. Remember to replace \x20 by soaces.

It's identical to the MatchVendor rule, but limited to the product model.

---

### Post by bombel on 2010-05-17
Hello again!
I found that my event number change and i have to edit 70-wizardpen.conf every time to make my tablet working.
So, I put event* in 
```
Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"

# Here I hardcoded the event*, please check wich event is yours.
   MatchDevicePath "/dev/input/[COLOR="Red"]event*[/COLOR]"

# This line is the original one. Removed because my tablet was not matched.
#   MatchVendor "*WALTOP*|*Tablet*"

#[CALIBRATION] This data was taken from wizard-calibrate tool.
        Option          "TopX"          "260"
        Option          "TopY"          "377"
        Option          "BottomX"       "17782"                                                                                                                                              
        Option          "BottomY"       "10584"   
#[END CALIBRATION]

   Driver "wizardpen"

EndSection
```

---

### Post by migueleonm on 2010-05-18
A algunos de ustedes les sirve el mouse perfectamente en GIMP mientras la tableta está activa? a mi no, el mouse funciona pero no dentro del area de trabajo de gimp, es decir, el boton izquierdo y la rueda del mouse no hacen nada pero si lo muevo por fuera del area de trabajo entonces si funcionan.

---

### Post by negora on 2010-05-18
**migueleonm:** In my case, while using GIMP, I've to choose between either the mouse or the stylus, never both at the same time (in the canvas, I mean).

---

### Post by migueleonm on 2010-05-18
Thank you for the reply. I googled this several days ago and apparently is a common problem, is a BIG problem. No solution in the web.

---

### Post by al.do on 2010-05-18
> **migueleonm said:**
> A algunos de ustedes les sirve el mouse perfectamente en GIMP mientras la tableta está activa? a mi no, el mouse funciona pero no dentro del area de trabajo de gimp, es decir, el boton izquierdo y la rueda del mouse no hacen nada pero si lo muevo por fuera del area de trabajo entonces si funcionan.

A mi me funcionan perfecto tanto el mouse como la tableta en Gimp. Lo que hice fue seleccionar en **preferencias > dispositivos** la opción **mode:screen** para la tableta y el mouse.

---

### Post by andrew87 on 2010-05-26
Hello

I'm Italian, I'm sorry for my bad English, I hope that you can understand me...

I've got the Trust TB-6300 tablet + mouse, I minutely followed this guide:

[https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)

My problem is the sequent: the pen work correctly, but the mouse, when I try to move, put the cursor in the top left corner of the screen, and don't move at all... the button seems to work correctly too.

I edited my xorg.conf file (even if this edit don't seems to serve)
I edited my 70-wizardpen.conf file whit the correct addres of device.
I try to change MathIsTablet whit MatchIsPointer too

Nothing... the cursor remains stuck in that damn  corner (only with mouse).
But I tried to do a particular edit to xorg.conf file:

> Section "ServerFlags"
        Option "AutoAddDevices" "False"And when I rebooted the system, magically the mouse work perfectly!!!!  but the pen and the keyboard didn't work no more...

I'm going crazy... really.. what can I do?

---

### Post by negora on 2010-05-26
**andrew87:** In your case the MatchVendor rule at 70-wizardpen.conf may be the cause. Try commenting or setting the right value.

---

### Post by andrew87 on 2010-05-26
Thanks negora for your quick reply
So, I tried to comment the MatchVendor rule.... but don't work
I think the that my value is correct yet:

> Section "InputClass"
   Identifier "wizardpen"
   MatchIsPointer "on"
   MatchDevicePath "/dev/input/event4"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver "wizardpen"
   Option "TopX" "2199"
   Option "TopY" "3598"
   Option "BottomX" "30325"
   Option "BottomY" "29278"
   Option "TopZ" "10"
   Option "BottomZ" "1023"
EndSection

Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsPointer "on"
   MatchDevicePath "/dev/input/mouse1"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver ""
EndSectionOr not?

---

### Post by andrew87 on 2010-05-26
Please help me!!

---

### Post by negora on 2010-05-26
**andrew87:** Hello again. Try not to post consecutive messages which don't include extra information, because it's useless. You'll get as many answers as if you hadn't done it.

About your issue, try this:

> Section "InputClass"
   Identifier "wizardpen"
#   MatchIsPointer "on"
   MatchDevicePath "/dev/input/event4"
#   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver "wizardpen"
   Option "TopX" "2199"
   Option "TopY" "3598"
   Option "BottomX" "30325"
   Option "BottomY" "29278"
   Option "TopZ" "10"
   Option "BottomZ" "1023"
EndSection

Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
#   MatchIsPointer "on"
   MatchDevicePath "/dev/input/mouse1"
#   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver ""
EndSection


Make sure to have deleted any mention to the stylus in /etc/X11/xorg.conf and also that the event and mouse numbers on /dev/ are the right ones and have not changed since the last time.

By the way, instead of restarting the PC (if it's the case), open a console (pushing CTRL + ALT + F1 for example) and restart the X server manually instead:

> sudo service gdm restart

---

### Post by andrew87 on 2010-05-26
sorry for the  useless post, but for me it is very important to resolve this problem  ...

So, I edited the file as you suggested, and I clear xorg.conf, but nothing has changed...

---

### Post by negora on 2010-05-26
Are "event4" and "mouse1" really pointing to your devices? Where is the 70-wizardpen.conf file located?

If you perform:

> lssusb

What is the output?

---

### Post by andrew87 on 2010-05-27
Yesterday I tried to change the usb port where it was  connected the tablet, this fact has changed the order of the devices, but I changed the rules too...

ls -al /dev/input/by-id:

> totale 0
drwxr-xr-x 2 root root 120 2010-05-27 11:37 .
drwxr-xr-x 4 root root 280 2010-05-27 11:37 ..
lrwxrwxrwx 1 root root   9 2010-05-27 00:47 usb-1241_1177-event-mouse -> ../event4
lrwxrwxrwx 1 root root   9 2010-05-27 00:47 usb-1241_1177-mouse -> ../mouse1
lrwxrwxrwx 1 root root   9 2010-05-27 11:37 usb-UC-LOGIC_Tablet_WP8060U-event-mouse -> ../event5
lrwxrwxrwx 1 root root   9 2010-05-27 11:37 usb-UC-LOGIC_Tablet_WP8060U-mouse -> ../mouse2
([COLOR=#000000]devices have become event5 and mouse2) and so 70-wizardpen.conf (located in /usr/lib/X11/xorg.conf.d/):

[/COLOR]> Section "InputClass"
   Identifier "wizardpen"
   #MatchIsPointer "on"
   MatchDevicePath "/dev/input/event5"
   #MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver "wizardpen"
   Option "TopX" "2199"
   Option "TopY" "3598"
   Option "BottomX" "30325"
   Option "BottomY" "29278"
   Option "TopZ" "10"
   Option "BottomZ" "1023"
EndSection
Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   #MatchIsPointer "on"
   MatchDevicePath "/dev/input/mouse2"
   #MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver ""
EndSectionInfact tablet works as before, so, you requested my lsusb output:

> Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 5543:0005 UC-Logic Technology Corp. Genius MousePen 8x6 Tablet
Bus 003 Device 002: ID 1241:1177 Belkin F8E842-DL Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubFurthermore,  if it can be useful if, after I move the cursor with the other mouse, and then I  try to move the tablet mouse, do not always take the cursor in the  top left corner of the screen, but, for expample, if I put the mouse in the top right of the tablet, the cursor goes too in the top right corner, and so on...like another pen, but it can't move the position from there...

---

### Post by negora on 2010-05-27
The chip of your tablet is exactly the same as mine... It's really surprising that it's isn't working for you. Do you have Ubuntu 10.04 and have installed the last drivers from the DoctorMo repository?:

```
deb http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu lucid main #WizardPen by DoctorMo
```

It'd be also interesting to check the output of the /var/log/Xorg.0.log file.

By the way, let's put our attention on the behaviour of the stylus only, since I don't use the mouse which was included with the tablet and am not sure about its right behaviour (sorry).

---

### Post by andrew87 on 2010-05-27
Infact the problem for me it's the use of the mouse.... the pen works perfectly...
However I found the problem...
I edited the "70-wizardpen.conf":

> Section "InputClass"
Identifier "wizardpen"
MatchIsTablet "on"
MatchDevicePath "/dev/input/event4"
MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
Driver ""
Option "TopX" "0"
Option "TopY" "0"
Option "BottomX" "32747"
Option "BottomY" "32762"
Option "TopZ" "10"
Option "BottomZ" "1023"
EndSection
Section "InputClass"
Identifier "wizardpen ignore mouse dev"
MatchIsPointer "on"
MatchDevicePath "/dev/input/mouse1"
MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
Driver "mouse"
EndSection As you can see I typed   "mouse" in the rule "driver" in  /dev/input/mouse1 before [COLOR=#000000]there was nothing  written, only the quotes...
But I had to delete the driver rule in [/COLOR]/dev/input/event4[COLOR=#000000], because if both are written, tablet works without problem, but mouse move[/COLOR][COLOR=#000000] the cursor  "orbiting" the last point point where the tablet left it.
With these changes now mouse work, but of course no tablet....

It's a [/COLOR]strange  behavior, I think there is some conflict about recognition between mouse and pen sensor in the tablet... maybe they can't work together?
Not long ago I successful used  both together with previous version of Ubuntu... but now?

---

### Post by oberonking on 2010-05-28
@al.do.. I have the same tablet, Thank you so so so much...

The only thing that I can't make work is that system take my tablet like "stylus"... 
With .fdi stuff I put:

```
<merge key=”info.product” type=”string”>stylus</merge>
```

that's all... 

Now, with xorg.conf.d I try

```
Option "type" "stylus"
```

Nothing happens....

Any idea???

---

### Post by DoctorMO on 2010-06-09
Please do report these problems to the launchpad project, otherwise we won't be able to try and fix them. (I was looking at the default configs that come with the package)

[https://bugs.launchpad.net/wizardpen](https://bugs.launchpad.net/wizardpen)

Also don't forget to email the programmer who's maintaining it for Ubuntu and thank them, it's always great to hear positive reinforcement, beer and monies also welcome when ever you get the chance :-D

---

### Post by Jotavirtual on 2010-06-19
Negora yo tengo el mismo problema que tenias tu con tu tabla usando ubuntu 10.04 que mi calibracion funciona mal y si pulso el lapiz sobre la tabla el cursor se detiene y solo puedo moverlo pulsando el lapiz, pero con el mouse si trabaja bien!

---

### Post by NarfZilla on 2010-07-01
Hey folks...

I was having the same issues with the mouse-or-tablet situation...
I even lost control of the keyboard (I'm glad for having onBoard installed by default on Ubuntu!)

So... by trial and error I get everything working here! (lucid 10.04)

this is my final rules file:

```
Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/event*"
   #MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
	Option		"TopX"		"91"
	Option		"TopY"		"54"
	Option		"BottomX"	"9986"
	Option		"BottomY"	"6190"
   Driver "wizardpen"
EndSection
Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsPointer "on"
   MatchDevicePath "/dev/input/mouse*"
   #MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver "vmmouse"
EndSection
```

I hope this can help someone with troubles...

**THANK** you all very much for sharing this solutions!

I will try to translate this to Portuguese and put it on my blog...

[SIZE="4"]GENERIC TABLETS ON UBUNTULAND: IT IS POSSIBLE![/SIZE]

:guitar:

---

### Post by Riffer on 2010-07-10
I hope people are still watching this thread.  I have a Genius F610, its working but way to sensitive.  Any ideas?

---

### Post by NlTESHADE on 2010-07-12
hi guys,

i have the same tablet and pen as posted, the f509 from genius
i am trying the solution first suggested and i get PERMISSION DENIED
at this point 

wizardpen-calibrate /dev/input/[COLOR=Red]event6[/COLOR]
michael@Niteshade:~$ wizardpen-calibrate /dev/input/event6
event device open: Permission denied

Thats the exact message, can anyone advise please?

---

### Post by Favux on 2010-07-12
Hi NlTESHADE,

It sounds like it is telling you you have to be root/superuser.  That will give you the right permissions.  So try:
```
sudo wizardpen-calibrate /dev/input/event6
```
assuming event6 is the correct event.

Then to edit the 70-wizardpen.conf with a graphical program like gedit use the graphical version of sudo, gksudo:
```
gksudo gedit /usr/lib/X11/xorg.conf.d/70-wizardpen.conf
```

---

### Post by AlexDS on 2010-07-31
> **Favux said:**
> Hi NlTESHADE,

It sounds like it is telling you you have to be root/superuser.  That will give you the right permissions.  So try:
```
sudo wizardpen-calibrate /dev/input/event6
```assuming event6 is the correct event.

Then to edit the 70-wizardpen.conf with a graphical program like gedit use the graphical version of sudo, gksudo:
```
gksudo gedit /usr/lib/X11/xorg.conf.d/70-wizardpen.conf
```

Does anybody tried to get their tablet work in 10.10(alpha2) ?
I had to install a deb package witch i found on the internet called [COLOR=Blue]wizardpen_0.7.3-1_i386.deb[/COLOR] on my 64bit machine by typing ```
dpkg -i --force-architecture wizardpen_0.7.3-1_i386.deb
``` , but when i type ```
sudo wizardpen-calibrate /dev/input/event6
``` it says that there is no such directory (directory not found) something like that. And i went here in Nautilus and the directory and the files exists.
What's wrong ???

---

### Post by NlTESHADE on 2010-08-05
> **AlexDS said:**
> Does anybody tried to get their tablet work in 10.10(alpha2) ?
I had to install a deb package witch i found on the internet called [COLOR=Blue]wizardpen_0.7.3-1_i386.deb[/COLOR] on my 64bit machine by typing ```
dpkg -i --force-architecture wizardpen_0.7.3-1_i386.deb
``` , but when i type ```
sudo wizardpen-calibrate /dev/input/event6
``` it says that there is no such directory (directory not found) something like that. And i went here in Nautilus and the directory and the files exists.
What's wrong ???
Hi, we seem to have the issue, but wen i tried to force like u did i get an error instead, 
when i saw ur message i thought id figured it, i have a 64bit system also

---

### Post by Tango91 on 2010-09-13
Heya,

I have just bought a Trust Flex Design Tablet (shows up in the inputdevices file as:

I: Bus=0003 Vendor=172f Product=0037 Version=0110
N: Name="         WALTOP             Tablet    "
P: Phys=usb-0000:00:1d.2-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input11
U: Uniq=
H: Handlers=mouse2 event6 
B: EV=1f
B: KEY=c03 0 1f0001 0 0 0 0 0 0 0 0
B: REL=143
B: ABS=1fffff00 1000003
B: MSC=10

So Ubuntu can definitely see it. But when i try to calibrate it it gives me the prompt to touch the stylus at any corner, and when i try, nothing happens. I've tried a couple batteries in the stylus but it seems to have no response.

I don't have my windows pc to try it with at the moment, and it's literally fresh from the shop.  Is there a way i might confirm the damn pen actually works? Has anyone else experienced this?

Thanks,

TJ


EDIT: I just rebooted again and i knocked the pen across the tablet at the login screen, and the cursor moved. Not coherently, but it moved.
I'm going to try to calibrate it again.

EDIT 2: The problem is not with this method, it's the pen. i can batter it on the desk and it will work for a second or two.
Against my better judgement i will try to take it to bits and see what's loose in there.

EDIT 3: The battery negative terminal has the world's most crappy solder joint ever at the pcb in the pen - it seems to be the problem. I'm going to go back to Maplin's and ask if i can borrow a soldering iron...

---

### Post by .::welemski::. on 2010-09-15
Yesterday my niece bought a Genius pen tablet and I helped her made it to work in ubuntu. This is how I made the tablet working under Ubuntu Lucid Lynx :

Device:
```
UC-Logic Technology Corp. Genius MousePen 8x6 Tablet
```

Device Image:
[IMG]http://pcworld.com.ph/wp-content/uploads/2009/09/genius-mousepen-i608.jpg[/IMG]

[LIST]
[*]**Step 1:**
Add the driver package repository.
```
http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu lucid main
```
[*]**Step 2:**
Install the driver package using synaptic package manager. The driver name is **xserver-xorg-input-wizardpen** or you can copy and paste the code below in the terminal:

```
sudo apt-get install xserver-xorg-input-wizardpen
```

[*]**Step 3:**
Copy and paste the code below and run in your favorite terminal:
```
ls -l /dev/input
```

Should display similar like this:
```

lrwxrwxrwx 1 root root 9 2010-09-16 07:50 usb-1b1a_USB_Mouse-event-mouse -> ../event4
lrwxrwxrwx 1 root root 9 2010-09-16 07:50 usb-1b1a_USB_Mouse-mouse -> ../mouse1
lrwxrwxrwx 1 root root 9 2010-09-16 07:55 usb-UC-LOGIC_Tablet_WP8060U-event-mouse -> ../event6
lrwxrwxrwx 1 root root 9 2010-09-16 07:55 usb-UC-LOGIC_Tablet_WP8060U-mouse -> ../mouse2


```

Take note that we're only interested on this two:

```
usb-UC-LOGIC_Tablet_WP8060U-event-mouse -> ../event6
usb-UC-LOGIC_Tablet_WP8060U-mouse -> ../mouse2
```

Also take note that my **usb-UC-LOGIC_Tablet_WP8060U-event-mouse** points to "/event6". Yours may point to something like "/event4". So be sure to take note about it.

[*]**Step 4:**

Open the wizard pen config file. Make sure you have write permission:

```
sudo gedit /usr/lib/X11/xorg.conf.d/70-wizardpen.conf
```

Copy and paste the text below in the wizardpen.conf:

```

Section "InputClass"
   Identifier "wizardpen"
   MatchIsPointer "on"
   MatchDevicePath "/dev/input/__REPLACE_ME_MOUSE_EVENT__"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Option	"SendCoreEvents" "true"
   Option	"Device"	"/dev/input/by-id/usb-UC-LOGIC_Tablet_WP8060U-event-mouse"
   Option	"TopX"		"1610"
   Option	"TopY"		"2015"
   Option	"BottomX"	"31220"
   Option	"BottomY"	"32342"
   Option 	"Type" "stylus"
   Driver 	"wizardpen"
EndSection
Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsPointer "on"
   MatchDevicePath "/dev/input/__REPLACE_ME_MOUSE__"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver ""
EndSection


```

Replace the text "__REPLACE_ME_MOUSE_EVENT__" with either of the two:

```
by-id/usb-UC-LOGIC_Tablet_WP8060U-event-mouse
```

or

```
/event6
```

NOTE: Yours may point to **/event4** so verify it using **STEP 3**

Replace the text "__REPLACE_ME_MOUSE__" with either of the two:

CODE]by-id/usb-UC-LOGIC_Tablet_WP8060U-mouse[/CODE]

or

```
/mouse2
```

NOTE: Yours may point to **/mouse1** so verify it using **STEP 3**


[*]**Step 5:**
That's it. Restart GDM or restart your PC. Should work.

[/LIST]

---

### Post by al.do on 2010-09-20
Hi everyone;
I've installed a new tablet on **Ubuntu 10.04**, the model is **[COLOR="green"]Genius Pensketch 9x12[/COLOR]**.
This is my configuration file (**70-wizardpen.conf**).

```
Section "InputClass"
   Identifier "wizardpen"
   MatchDevicePath "/dev/input/event*"
   MatchProduct "Tablet|PF1209"
   Driver "wizardpen"
   Option          "TopX"          "0"
   Option          "TopY"          "1553"
   Option          "BottomX"       "32541"
   Option          "BottomY"       "32762"
EndSection
```

Best Regards!

---

### Post by estefano on 2010-10-06
> **Tango91 said:**
> Heya,

I have just bought a Trust Flex Design Tablet (shows up in the inputdevices file as:

I: Bus=0003 Vendor=172f Product=0037 Version=0110
N: Name="         WALTOP             Tablet    "
P: Phys=usb-0000:00:1d.2-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input11
U: Uniq=
H: Handlers=mouse2 event6 
B: EV=1f
B: KEY=c03 0 1f0001 0 0 0 0 0 0 0 0
B: REL=143
B: ABS=1fffff00 1000003
B: MSC=10

So Ubuntu can definitely see it. But when i try to calibrate it it gives me the prompt to touch the stylus at any corner, and when i try, nothing happens. I've tried a couple batteries in the stylus but it seems to have no response.

I don't have my windows pc to try it with at the moment, and it's literally fresh from the shop.  Is there a way i might confirm the damn pen actually works? Has anyone else experienced this?

Thanks,

TJ


EDIT: I just rebooted again and i knocked the pen across the tablet at the login screen, and the cursor moved. Not coherently, but it moved.
I'm going to try to calibrate it again.

EDIT 2: The problem is not with this method, it's the pen. i can batter it on the desk and it will work for a second or two.
Against my better judgement i will try to take it to bits and see what's loose in there.

EDIT 3: The battery negative terminal has the world's most crappy solder joint ever at the pcb in the pen - it seems to be the problem. I'm going to go back to Maplin's and ask if i can borrow a soldering iron...
I have the very same problem. I dont think is something related to the pen. Have you succeded to configure that damned tablet?

---

### Post by al.do on 2010-10-06
> **estefano said:**
> I have the very same problem. I dont think is something related to the pen. Have you succeded to configure that damned tablet?

Whats the model of your tablet? Put more details please.

---

### Post by estefano on 2010-10-07
> **al.do said:**
> Whats the model of your tablet? Put more details please.
is a Trust "Flex design tablet"

lsusb gives
Bus 003 Device 003: ID 172f:0037 Waltop International Corp. 

...

EDIT1: also, I have to say that the problem is not that it does not work at all: it works randomly!!! 
for example I have seen that "double-clicking" sometimes (but not always) put the cursor on the point I have clicked. Then, say 80% of times, if I press and drag it works. But it is impossible to do things like writing or drowing. just because the behavior is basically random!

---

### Post by al.do on 2010-10-07
> **estefano said:**
> is a Trust "Flex design tablet"

lsusb gives
Bus 003 Device 003: ID 172f:0037 Waltop International Corp. 

...

EDIT1: also, I have to say that the problem is not that it does not work at all: it works randomly!!! 
for example I have seen that "double-clicking" sometimes (but not always) put the cursor on the point I have clicked. Then, say 80% of times, if I press and drag it works. But it is impossible to do things like writing or drowing. just because the behavior is basically random!

Try with ***[COLOR="Blue"]cat /proc/bus/input/devices[/COLOR]*** and put here the info.

---

### Post by DoctorMO on 2010-10-07
*facepalm* We need to fix this ^Y^

Wizardpen should be as simple as installing the driver and restarting, if it's not then please try the mitigation strategies above to get yourself out of a hole, but please:

REPORT IT AS A BUG

You're NOT SUPPOSED to be editing configuration files to make your hardware work. Just like your not supposed to be compiling drivers from source. It's all bad shut that shouldn't be done except when backed into a corner.

As the launchpad project and ppa maintainer I've heard nothing about the configuration problems so I assumed everything was working fine. *sigh*

---

### Post by estefano on 2010-10-10
I give up. I'll give the tablet to some windows user friend :(

---

### Post by al.do on 2010-10-10
> **estefano said:**
> I give up. I'll give the tablet to some windows user friend :(

You can try if the tablet works properly on windows with the original driver.

---

### Post by negora on 2010-10-12
Hello. I've been really busy for some time and have not been able to follow this thread (family matters).

I've found what seems to be a bug on Ubuntu 10.10, after installing the package xserver-xorg-input-wizardpen 0.7.4-2maverick0. The file /usr/lib/X11/xorg.conf.d/70-wizardpen.conf seems to be completely ignored by the X11 server. I've tried to copy it to /usr/share/X11/xorg.conf.d, together with the rest of the default X11 configuration files, and it works perfectly.

---

### Post by oberonking on 2010-10-12
> **negora said:**
> Hello. I've been really busy for some time and have not been able to follow this thread (family matters).

I've found what seems to be a bug on Ubuntu 10.10, after installing the package xserver-xorg-input-wizardpen 0.7.4-2maverick0. The file /usr/lib/X11/xorg.conf.d/70-wizardpen.conf seems to be completely ignored by the X11 server. I've tried to copy it to /usr/share/X11/xorg.conf.d, together with the rest of the default X11 configuration files, and it works perfectly.

You're my personal Heroe..... Thank you so SO much!!!! It works like a charm. :):):)

---

### Post by negora on 2010-10-12
**DoctorMo:** I'm sorry for this kind of question, but LaunchPad is a little mess for certain matters and I'm a little confused. What's the right place to report wizardpen bugs? Should we send them to your space (doctormo's), to wizardpen (owned by ethana2), to wizardpen-testers, or to the mailing list of the last one?

**oberonking:** I'm glad that it has been of help ;) . Fortunately this time I've not had to do hundreds of desperated tests and have found the origin after a few unsuccessful attempts XD .

---

### Post by maxmaster1990 on 2010-10-13
Thanks!! works perfect! i'm spreading the voice to the hispanic users posting this:

> **maxmaster1990 said:**
> [QUOTE=negora;9960437]Hello. I've been really busy for some time and have not been able to follow this thread (family matters).

I've found what seems to be a bug on Ubuntu 10.10, after installing the package xserver-xorg-input-wizardpen 0.7.4-2maverick0. The file /usr/lib/X11/xorg.conf.d/70-wizardpen.conf seems to be completely ignored by the X11 server. I've tried to copy it to /usr/share/X11/xorg.conf.d, together with the rest of the default X11 configuration files, and it works perfectly.

¡Encontré esto hace unas horas!
Hay que copiar este archivo >> **/usr/lib/X11/xorg.conf.d/70-wizardpen.conf**
en este directorio >> **/usr/share/X11/xorg.conf.d**
al lado de los otros archivos de configuración, reinicias y lista la sopa.
Lo que pasa es que hay un bug en 10.10 donde el xorg ignora el archivo, si lo metes allá te va a funcionar perfecto sin tener que haber cambiado nada, con la instalación del paquete xserver-**xorg-input-wizardpen** de DoctorMO normalito basta.
Para instalarlo, agrega este repositorio >> ppa:doctormo/xorg-wizardpen

Escribe en la terminal 
>> **sudo add-apt-repository ppa:doctormo/xorg-wizardpen **
luego
>> **sudo apt-get update**
por ultimo
>> **sudo apt-get install xserver-xorg-input-wizardpen** 

La solución de mover el archivo viene del usuario [**negora**]("http://ubuntuforums.org/member.php?u=561051") como cité arriba desde este **[post]("http://ubuntuforums.org/showthread.php?p=9960656")**
Corran la voz :P[/QUOTE]
Thanks again!

---

### Post by al.do on 2010-10-13
> **negora said:**
> Hello. I've been really busy for some time and have not been able to follow this thread (family matters).

I've found what seems to be a bug on Ubuntu 10.10, after installing the package xserver-xorg-input-wizardpen 0.7.4-2maverick0. The file /usr/lib/X11/xorg.conf.d/70-wizardpen.conf seems to be completely ignored by the X11 server. I've tried to copy it to /usr/share/X11/xorg.conf.d, together with the rest of the default X11 configuration files, and it works perfectly.

Great!! I added the info in the first thread. Thanks.

---

### Post by DoctorMO on 2010-10-14
I've uploaded a new ppa build which puts this configuration file in the right place. I need someone who has not tried this fix, who has a FRESH ubuntu maverick (10.10) install to install this ppa and then driver and see if the device works after a restart.

---

### Post by rouwad on 2010-10-15
Hi, yesterday I did what negora suggested and my G-Pen F610 worked pretty well on ubuntu 10.10,  today I updated the driver through the ppa and it no longer works.

This is the content of my 70-wizardpen.conf
```

Section "InputClass"
        Identifier      "Wizardpen"
        MatchIsTablet   "on"
        MatchDevicePath "/dev/input/event2"
        MatchVendor "WALTOP International Corp. Slim Tablet"
        MatchTag        "wizardpen"
        Driver          "wizardpen"
        Option          "TopX"          "295"
        Option          "TopY"          "210"
        Option          "BottomX"       "20000"
        Option          "BottomY"       "12500"
EndSection

Section "InputClass"
   Identifier      "wizardpen ignore mouse dev"
   MatchDevicePath "/dev/input/mouse*"
   MatchTag        "wizardpen"
   Driver          "mouse"
   Option          "MouseSpeed" "16"
   Option          "ignore"     "true"
EndSection

```I also noticed that the directory /usr/lib/X11**/xorg.conf.d/ **no longer exists, so I created one and pasted its content from **/usr/share/X11/****xorg.conf.d/** but that did't work either[B].

[/B]Any help will be appreciated

---

### Post by Favux on 2010-10-15
Hi rouwad,

Welcome to Ubuntu forums!

The match line is wrong.  MatchProduct not MatchVendor:
```
Section "InputClass"
    Identifier "WizardPen class"
    MatchIsTablet "on"
    MatchProduct "WALTOP"
    MatchDevicePath "/dev/input/event*"
    Driver "wizardpen"
EndSection

Section "InputClass"
    Identifier "WizardPen ignore mouse dev class"
    MatchIsTablet "on"
    MatchProduct "WALTOP"
    MatchDevicePath "/dev/input/mouse*"
    Option "Ignore" "yes"
EndSection
```
In Maverick use:
```
gksudo gedit /usr/share/X11/xorg.conf.d/70-wizardpen.conf

```
From:  [http://ubuntuforums.org/showthread.php?t=1595648](http://ubuntuforums.org/showthread.php?t=1595648)

---

### Post by rouwad on 2010-10-15
Thanks Favux for your prompt reply but I'm afraid that didn't work.

This is how my  70-wizardpen.conf looks like now

```
Section "InputClass"
        Identifier      "Wizardpen"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event2"
        MatchProduct "WALTOP International Corp. Slim Tablet"
        MatchTag        "wizardpen"
        Driver          "wizardpen"
        Option          "TopX"          "295"
        Option          "TopY"          "210"
        Option          "BottomX"       "20000"
        Option          "BottomY"       "12500"
EndSection

Section "InputClass"
   Identifier      "wizardpen ignore mouse dev"
   MatchDevicePath "/dev/input/mouse*"
   MatchTag        "wizardpen"
   Driver          "mouse"
   Option          "MouseSpeed" "16"
   Option          "ignore"     "true"
EndSection
```

Any other ideas :P

---

### Post by Favux on 2010-10-15
Yes, use exactly the one I posted.  Completely replace yours with it.  Your event may be wrong and you don't need the matchtag's either.

---

### Post by rouwad on 2010-10-15
Favux, thank you so much, it is working now like a charm.
You're a :KS

---

### Post by Favux on 2010-10-24
Hi everyone,

It looks like the Waltop tablet now works on the wacom driver in the latest updated Maverick.  See the [Waltop HOW TO]("http://ubuntuforums.org/showpost.php?p=9966110&postcount=1").  That will let you use the more sophisticated wacom bezier pressure curve and other xsetwacom commands for your stylus.

---

### Post by EsbenAndersen on 2010-11-02
Hi everybody.

Nice to see so many helps in order to get these tablets to work.

I have tried all the proposed solutions but I still can't make mine work.

It's an Aiptek 1400u, and I've seen that another guy with the same tablet claims that his is now working perfectly, so I must admit I just don't understand it.

I'm running Ubuntu 10.10. My tablet must be seen by Ubuntu because it partially works. The cursor works ok although with a few glitches every 5 seconds until I press the pen down on the tablet. That makes it freeze. Either for 2-3 seconds or until I press the pen down again.

I've also read this thread: 
[https://help.ubuntu.com/community/AiptekTablet#Ubuntu%2010.10%20%28Maverick%20Meerkat%29](https://help.ubuntu.com/community/AiptekTablet#Ubuntu%2010.10%20%28Maverick%20Meerkat%29)

I can't find out whether it works or not though since I don't know how to add udev rules.

I should say that I am just getting started with Ubuntu, so please spell everything out for me! :) Oh, and I don't know if this is necessary information or not, but I want to use the tablet with GIMP.

If I can't make it work I have to go back to Windows again, and there's nothing in the world I would dislike more than to do that! Ubuntu is so amazing (except for this one thing of course)!

Thank you and keep up the good work,

Esben.

---

### Post by Favux on 2010-11-02
Hi EsbenAndersen,

Welcome to Ubuntu forums!

Could you post the output of:
```
xinput --list
```
in a terminal (Applications > Accessories > Terminal).

---

### Post by EsbenAndersen on 2010-11-02
Hi Favux.

This is the info I get from it:

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                    id=10    [slave  pointer  (2)]
&#9116;   &#8627; WALTOP International Corp. Media Tablet     id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=9    [slave  keyboard (3)]

---

### Post by Favux on 2010-11-02
Hi Esben,

OK since you are in Maverick we should be able to set you up on the Wacom driver.  See the Waltop HOW TO:  [http://ubuntuforums.org/showthread.php?t=1595648](http://ubuntuforums.org/showthread.php?t=1595648)  Ask if you have any questions.

---

### Post by EsbenAndersen on 2010-11-02
Hi again.

This is the file that opens when I enter:

gksudo gedit /usr/share/X11/xorg.conf.d/50-wacom.conf

Section "InputClass"
        Identifier "Wacom class"
        MatchProduct "Wacom|WACOM"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
        #Option "Button2" "2"
        #Option "Button3" "3"
        Option "KeepShape" "on"
EndSection

Section "InputClass"
        Identifier "Wacom serial class"
        MatchProduct "Serial Wacom Tablet"
        Driver "wacom"
        Option "ForceDevice" "ISDV4"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
        Identifier "Wacom N-Trig class"
        MatchProduct "HID 1b96:0001"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
EndSection

I'm not quite sure what to replace and I don't want to do something stupid... :)

Esben.

---

### Post by Favux on 2010-11-02
Hi Esben,

Why does no one post on the HOW TO, he asks rhetorically?

Try changing the first snippet to:
```
Section "InputClass"
Identifier "Wacom class"
MatchProduct "Wacom|WACOM|WALTOP"
MatchDevicePath "/dev/input/event*"
Driver "wacom"
#Option "Button2" "2"
#Option "Button3" "3"
#Option "KeepShape" "on"
EndSection
```
You may want to use the KeepShape Option, but let's keep it simple until it's working.

Where did that 50-wacom.conf come from?  It doesn't look like the default.  Did you make changes to it before now?

---

### Post by EsbenAndersen on 2010-11-02
Yeah! I'm on my way!

I pasted your code and deleted what i had in the 50-wacom.conf file and it works. I have pressure sensitivity and the x/y-thing works as well.

Still one problem though. It seems the tablet uses EXTREME amounts of CPU. The processor goes nuts everytime I use the tablet. That means that when I use GIMP it can't follow my movements and my actions are delayed pretty badly. My laptop is not super strong but I would think it could run GIMP and a tablet at the same time. It is 1.6 ghz Intel Dual Core and 2 GB Ram. I think the graphics card is only 128 mb though. Could the computer power be the reason it doesn't work or is it a configuration?

Thank you SO much for your help so far Favux!

Esben.

---

### Post by Favux on 2010-11-02
Sounds good.

There's a known gtk bug that can mess things up with Gimp.  Install the .xsetwacom.sh and see what happens.  You may need to adjust the RawSample parameter.  Are you seeing a lag between your stylus tip and Gimp displaying the line?

---

### Post by EsbenAndersen on 2010-11-02
I installed it. Doesn't seem to make much of a difference. This is what happens:

I reboot and open GIMP. Then I draw for 10 seconds and everything is fine. Then the events on the screen starts to slow down and become more and more delayed compared to my movements.

How do I change the 'raw data' thing?

Well, it seems to me it may be a graphics card thing. Only 128 mb. Do you think it could be that?

Esben.

---

### Post by Favux on 2010-11-02
Try changing the line:
```
xsetwacom set "WALTOP International Corp. Media Tablet stylus" RawSample "4"  # default is 4, 1-100?
```
From "4" to say "20".  With the bug the sampling rate can be so frequent, in other words so many events are sent, that it can bog down the CPU.  See if this helps.  After the change rerun the script (double click on it).  Remember it's a hidden file so to see it in Places > View click on Show hidden files.

Notice your "Device name" will be different from the one used in the script.  So you need to use the one you now see in the output of 'xinput --list'.  I guessed at it.

---

### Post by EsbenAndersen on 2010-11-11
Hey Favux.
 
I just realized I forgot to thank you properly. I got everything working which I couldn't have done without your help. Hope other people with the same tablet sees your postings.
 
Have a good one!

Esben.

---

### Post by BCtom on 2010-11-11
Thanks Everyone on this thread. When I upgraded to 10.10 I was heart broken when my tablet failed, but now I am one happy camper once again. 

All I needed were steps 1 & 2 and my WP 8060U 8 x 6 graphics tablet worked right after restart.

This is getting scary now that I don't have to have a degree in computer science to hook something up in Ubuntu. LOL!

---

### Post by artifus on 2010-11-26
> **estefano said:**
> I have the very same problem. I dont think is something related to the pen. Have you succeded to configure that damned tablet?

hello. i'm using the latest puppy linux, luci-239, so i'm not sure if this is the right place to post but i also have a trust flex and am struggling. it works randomly with or without drivers, it seems. tested with mpaint, inkscape, gimp and xjournal.

cat /proc/bus/input/devices

says:

WALTOP Tablet
handlers=mouse1 event6

it pops up as event3 sometimes too

current wizardpen reads:


Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/event*"
   MatchVendor "WALTOP|Tablet"
   Driver "wizardpen"
EndSection
Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/mouse*"
   MatchVendor "WALTOP|Tablet"
   Driver "wizardpen"
   Option "Device" "/dev/input/event3"
   Option "TopX" "93"
   Option "TopY" "174"
   Option "BottomX" "12099"
   Option "BottomY" "9073"
EndSection

any suggestions?

---

### Post by Favux on 2010-11-26
Hi artifus,

Welcome to Ubuntu forums!

Try:
```
Section "InputClass"
    Identifier "WizardPen class"
    MatchIsTablet "on"
    MatchProduct "WALTOP"
    MatchDevicePath "/dev/input/event*"
    Driver "wizardpen"
EndSection

Section "InputClass"
    Identifier "WizardPen ignore mouse dev class"
    MatchIsTablet "on"
    MatchProduct "WALTOP"
    MatchDevicePath "/dev/input/mouse*"
    Option "Ignore" "yes"
EndSection
```
From the [Waltop HOW TO]("http://ubuntuforums.org/showpost.php?p=9966110&postcount=1").

---

### Post by artifus on 2010-11-27
thanks favux.

no joy, i'm afraid. seemed to have lost intermitent pick up now, even after reverting back to my original wizardpen file. am back again on your suggested code but still no action after several restartx's and reboots. have noticed on reboot that the num lock led on usb keyboard blinks all thru boot and grub until an os is picked up if the tablet is connected with sluggish keyboard response in grub. don't know if that hints at anything. tablet works on xp.

will start again on page one and maybe a fresh install and see how i get on.

thanks for your help!

---

### Post by Favux on 2010-11-27
Too bad.  Before you do that could you post the output of:
```
xinput --list
```
and the Waltop sections output from:
```
more /proc/bus/input/devices
```

In the .conf file you should try changing the:
```
MatchProduct "WALTOP"
```
lines to
```
MatchVendor "WALTOP"
```

---

### Post by artifus on 2010-11-27
wizardpen:

Section "InputClass"
    Identifier "WizardPen class"
    MatchIsTablet "on"
    MatchVendor "WALTOP"
    MatchDevicePath "/dev/input/event*"
    Driver "wizardpen"
EndSection

Section "InputClass"
    Identifier "WizardPen ignore mouse dev class"
    MatchIsTablet "on"
    MatchVendor "WALTOP"
    MatchDevicePath "/dev/input/mouse*"
    Option "Ignore" "yes"
EndSection


# xinput --list
bash: xinput: command not found
# more /proc/bus/input/devices
I: Bus=0003 Vendor=1241 Product=1503 Version=0110
N: Name="  USB Keyboard"
P: Phys=usb-0000:00:1f.2-2.1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1f.2/usb1/1-2/1-2.1/1-2.1:1.0/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: EV=120013
B: KEY=10000 7 ff800000 7ff febeffdf f3cfffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=1241 Product=1503 Version=0110
N: Name="  USB Keyboard"
P: Phys=usb-0000:00:1f.2-2.1/input1
S: Sysfs=/devices/pci0000:00/0000:00:1f.2/usb1/1-2/1-2.1/1-2.1:1.1/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=13
B: KEY=2000000 39fa d941d001 1e0000 0 0 0
B: MSC=10

I: Bus=0003 Vendor=04d9 Product=0461 Version=0110
N: Name="HID 04d9:0461"
P: Phys=usb-0000:00:1f.2-2.2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1f.2/usb1/1-2/1-2.2/1-2.2:1.0/input/input2
U: Uniq=
H: Handlers=mouse0 event2 
B: EV=17
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10

I: Bus=0003 Vendor=172f Product=0037 Version=0110
N: Name="         WALTOP             Tablet    "
P: Phys=usb-0000:00:1f.2-2.4/input0
S: Sysfs=/devices/pci0000:00/0000:00:1f.2/usb1/1-2/1-2.4/1-2.4:1.0/input/input3
U: Uniq=
H: Handlers=mouse1 event3 
B: EV=1f
B: KEY=c03 0 1f0001 0 0 0 0 0 0 0 0
B: REL=143
B: ABS=1fffff00 1000003
B: MSC=10

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=40001
B: SND=6

# 

thanks again for your help. fresh install is no hassle as this is just a play box with a few frugal installs on to try and get my head round this linux stuff.

edit:

think the trust flex is a rebranded: [http://www.waltop.com.tw/prodDetail.asp?id=33](http://www.waltop.com.tw/prodDetail.asp?id=33)

---

### Post by Favux on 2010-11-27
Alright, I take it the new match line didn't work for you?
```
# xinput --list
bash: xinput: command not found
```
Go to Synaptic Package Manager or Software Center and search 'xinput' and install it.
```
I: Bus=0003 Vendor=172f Product=0037 Version=0110
N: Name=" WALTOP Tablet "
P: Phys=usb-0000:00:1f.2-2.4/input0
S: Sysfs=/devices/pci0000:00/0000:00:1f.2/usb1/1-2/1-2.4/1-2.4:1.0/input/input3
U: Uniq=
H: Handlers=mouse1 event3
B: EV=1f
B: KEY=c03 0 1f0001 0 0 0 0 0 0 0 0
B: REL=143
B: ABS=1fffff00 1000003
B: MSC=10
```
It's definitely a Waltop with a Vendor ID of 172f.  Your product is a little different from most posting because their tablet's name includes Slimline.

You could try both match lines with:
```
MatchVendor "WALTOP Tablet"
```
or
```
MatchProduct "WALTOP Tablet"
```
So are you in Virtual Box?

---

### Post by artifus on 2010-11-27
thanks again, will try now. virtual box? no, lucid puppy - boots into ram, very quick and easy to set up and runs well on older hardware.

---

### Post by artifus on 2010-11-27
# xinput --list
â¡ Virtual core pointer                    	id=2	[master pointer  (3)]
â   â³ Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
â   â³ Mouse0                                  	id=6	[slave  pointer  (2)]
â£ Virtual core keyboard                   	id=3	[master keyboard (2)]
    â³ Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    â³ Keyboard0                               	id=7	[slave  keyboard (3)]
#

---

### Post by Favux on 2010-11-27
OK, the tablet isn't being seen.  So provided you have the WizardPen driver correctly installed that means something is wrong with the .conf, most likely a match line.  Otherwise the .conf file should be correct.

---

### Post by artifus on 2010-11-27
have got random intermittent response again after running:

# wizardpen-calibrate /dev/input/event3

Please, press the stilus at ANY
corner of your desired working area: ok, got 11370,129

Please, press the stilus at OPPOSITE
corner of your desired working area: ok, got 152,9140

According to your input you may put the following
lines into your XF86Config/X.Org configuration file:

	Driver		"wizardpen"
	Option		"Device"	"/dev/input/event3"
	Option		"TopX"		"152"
	Option		"TopY"		"129"
	Option		"BottomX"	"11370"
	Option		"BottomY"	"9140"
# 

it took a few jabs to pick up. have not added extra text yet. got some response in gimp after a few sweeps. frequently cuts out, particularly if pen is lifted from tablet.
installed xserver-xorg-input-wizardpen_0.7.3-1ubuntu1_i386.deb - is this the most up to date? thanks again.

---

### Post by Favux on 2010-11-27
So back to an intermittent response.  Doe the stylus have a battery?  Is it old?

That looks like Martin Owens Lucid WizardPen driver.  Did you get it from his ppa?

---

### Post by artifus on 2010-11-27
> **Favux said:**
> So back to an intermittent response.  Doe the stylus have a battery?  Is it old?

That looks like Martin Owens Lucid WizardPen driver.  Did you get it from his ppa?

yes stylus has a battery, is new and works fine in xp. i think it was downloaded from launchpad - just googled wizardpen deb.

noticed in usr/lib/xorg/mods/input there is a wizardpen_drv.la aswell as the _drv.so. there are no other .la's, just .so's. don't think the .la is recognised or required so can it be safely deleted?

---

### Post by Favux on 2010-11-27
Was it this site?:  [https://launchpad.net/~doctormo/+archive/xorg-wizardpen/+packages?field.name_filter=&field.status_filter=published&field.series_filter=lucid](https://launchpad.net/~doctormo/+archive/xorg-wizardpen/+packages?field.name_filter=&field.status_filter=published&field.series_filter=lucid)

If so then I'm wondering if puppy is lacking a udev rule(s) we need.

Regarding the .la I don't know.  You'd have to either try it (with a back up) or ask Doctor MO.

---

### Post by artifus on 2010-11-27
yes, that was the site. could well be a puppy issue. i shall look into the udev rule, thanks for the tip. think the .la is some sort of libary file, read somewhere that they're often not required. it's the only one i've come across so far and judging by the icon the system isn't sure what it is or what to do with it. see how it goes. thanks for all the help.

---

### Post by artifus on 2010-11-29
getting there! appears to work under wacom but needs tweaking options wise, pressure is way off and response sluggish. may try wizardpen if no joy.

---

### Post by Favux on 2010-11-29
Progress!

I wouldn't have thought you could get the Waltop working on Wacom in Puppy.  It has the 2.6.32 kernel, correct?  Or despite it being Lucid Puppy does it have the 2.6.35 kernel?  Did you try the script for the stylus at the bottom of the Waltop HOW TO?

---

### Post by artifus on 2010-11-29
> **Favux said:**
> Progress!

I wouldn't have thought you could get the Waltop working on Wacom in Puppy.  It has the 2.6.32 kernel, correct?  Or despite it being Lucid Puppy does it have the 2.6.35 kernel?  Did you try the script for the stylus at the bottom of the Waltop HOW TO?

2.6.33.2 in luci_240 - it's not a stable release yet. had to install xf86-input-wacom-0.10.8 which included udev and the xsetwacom utility which i've yet to try.  not had a lot of time and still fiddling. thanks again.

---

### Post by mazursv on 2010-12-24
[IMG]http://lh5.ggpht.com/_dQn12L6dAeE/TRT8BEgYeNI/AAAAAAAAAqI/DX-4hxEv2tI/s800/screenshot_007.png[/IMG]

---

### Post by al.do on 2011-01-30
> **mazursv said:**
> [IMG]http://lh5.ggpht.com/_dQn12L6dAeE/TRT8BEgYeNI/AAAAAAAAAqI/DX-4hxEv2tI/s800/screenshot_007.png[/IMG]

You're welcome. I'm glad to help ;)

---

### Post by lisboaferreira on 2011-04-07
Hi folks !

Sorry for bothering... but I still need help ! !
I have a GPen F509 and I upgraded to the Ubuntu 10.10 (tablet never worked right - it was a gift for the children, my 3 kids) they're disapointed for more than 6 month...

I've followed all the instructions on the threads about the tablet's configuration... here's what happens: on gimp, when the pen touch the tablet (using a pencil for exemple) it draws rightaway, it's as if the button were pressed all the time.

Help me please ! 
Do you have a clue on what the problem might be ?

Thanks for your time !

---

### Post by al.do on 2011-04-07
> **lisboaferreira said:**
> Hi folks !

Sorry for bothering... but I still need help ! !
I have a GPen F509 and I upgraded to the Ubuntu 10.10 (tablet never worked right - it was a gift for the children, my 3 kids) they're disapointed for more than 6 month...

I've followed all the instructions on the threads about the tablet's configuration... here's what happens: on gimp, when the pen touch the tablet (using a pencil for exemple) it draws rightaway, it's as if the button were pressed all the time.

Help me please ! 
Do you have a clue on what the problem might be ?

Thanks for your time !
Hi lisboaferreira,

First; 
Move the pen one centimeter over the surface and tell me if you can move the cursor.  You don't need to touch the surface for move the cursor. So, if you can move the cursor without touch the surface maybe the problem is the pressure in Gimp, but if you can move the cursor only if you are doing pressure over the surface the problem is not Gimp.

Well, if the problem isn't Gimp you have two possibilities: 
1. The driver was installed wrong. 
2. The tablet is broken.

If you followed the steps correctly your G-pen F509 should be working, so you need to check the status of your tablet. 

The method more easily that I know to confirm if your tablet is fine or broken is installing the official driver for Windows or Mac. Why I tell you this? Because two year ago my girlfriend bought the same tablet and she followed my steps but the tablet works bad like yours. She put her tablet in my computer with the same configuration of my tablet and she obtained the same result. At the end she went to the technical service and they confirm the tablet was broken with the official driver. 

Let me know what happens.

Cheers.

Sorry for my bad English.

---

### Post by AlexDS on 2011-04-07
[lisboaferreira]("http://ubuntuforums.org/member.php?u=1063488"): be sure you enabled your Tablet, in Gimp, from Preferences- Imput divices
and secondly try your tablet in Mypaint to see if it least works on that. 
Gimp isn't really a software where you should draw all the time, because has limited touch sensibility when painting, but in Mypaint, you feel like you're really painting/drawing wit a brush/pen . So go for Mypaint, if you wanna just draw/paint.

---

### Post by BCtom on 2011-04-29
Hi everyone. I just upgraded to 11.04 today, just as it became available, and the installation procedure still works OK for my tablet: WP8060U. 

Because mine was an upgrade, I lost my configuration file, so I just reinstalled the Wizard pen deb, told the installer to install anyway (as it now gives you warnings about it not being part of the proper repositories etc...). Followed the instructions here, and it worked just as it did before. 5 mins to install and get working!

Note: using the wizard pen in synaptic did not work for me: kept freaking out about not being able to sort out the dependencies, so I had to download the  **Wizardpen_0.7.3-1_i386.deb** from the website and then installed from my Desktop.

---

### Post by al.do on 2011-05-02
> **BCtom said:**
> Hi everyone. I just upgraded to 11.04 today, just as it became available, and the installation procedure still works OK for my tablet: WP8060U. 

Because mine was an upgrade, I lost my configuration file, so I just reinstalled the Wizard pen deb, told the installer to install anyway (as it now gives you warnings about it not being part of the proper repositories etc...). Followed the instructions here, and it worked just as it did before. 5 mins to install and get working!

Note: using the wizard pen in synaptic did not work for me: kept freaking out about not being able to sort out the dependencies, so I had to download the  **Wizardpen_0.7.3-1_i386.deb** from the website and then installed from my Desktop.

Thanks, I updated the first post.

---

### Post by JugglinPhil on 2011-05-05
> **Tango91 said:**
> Heya,

I have just bought a Trust Flex Design Tablet (shows up in the inputdevices file as:

I: Bus=0003 Vendor=172f Product=0037 Version=0110
N: Name="         WALTOP             Tablet    "
P: Phys=usb-0000:00:1d.2-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input11
U: Uniq=
H: Handlers=mouse2 event6 
B: EV=1f
B: KEY=c03 0 1f0001 0 0 0 0 0 0 0 0
B: REL=143
B: ABS=1fffff00 1000003
B: MSC=10

So Ubuntu can definitely see it. But when i try to calibrate it it gives me the prompt to touch the stylus at any corner, and when i try, nothing happens. I've tried a couple batteries in the stylus but it seems to have no response.

I don't have my windows pc to try it with at the moment, and it's literally fresh from the shop.  Is there a way i might confirm the damn pen actually works? Has anyone else experienced this?

Thanks,

TJ


EDIT: I just rebooted again and i knocked the pen across the tablet at the login screen, and the cursor moved. Not coherently, but it moved.
I'm going to try to calibrate it again.

EDIT 2: The problem is not with this method, it's the pen. i can batter it on the desk and it will work for a second or two.
Against my better judgement i will try to take it to bits and see what's loose in there.

EDIT 3: The battery negative terminal has the world's most crappy solder joint ever at the pcb in the pen - it seems to be the problem. I'm going to go back to Maplin's and ask if i can borrow a soldering iron...

I am having the same problem with the same tablet, however I do not think that it is a pen-problem, since it works fine under Windows 7. Probably more a driver issue, can anybody help with this?

---

### Post by anipet on 2011-05-20
Hi all the way from Mexico, I hadn't written to these forums in a long time since I most usually would and will 'read' my way out of any problem with ubuntu. I'm not really much of what you could call an 'advanced' ubuntu user, but I know my way around the system.

about a month ago I went ahead and tried installing Ubuntu Natty 64 bit, my WP8060U worked without problems just as I plugged it in, now, here's the quirk; the only annoyance I really found was that when trying to work in GIMP (which is a personal favorite of mine), every cursor point made with the stylus kind of required a second click to actually draw something; pressure sensitivity, correct screen recognition and all was there, except for that tiny little quirk on which, I trace once and the cursor just sticks on the screen, doesn't move or do anything, trace and 'click' a second time and a beautiful trace appears on screen as expected from these marvelous devices :)

at first I thought, well, I mustn't have the right driver.. went ahead and tried installing wizardpen from doctor mo's PPA, everything seems to have gone well, pressure sensitivity is still there on mypaint.. but now gimp won't provide me much choices regarding pressure (and I still need to see if it's due to recently switching to an unstable release..) in any case please do ignore the plea for pressure, as it works in other parts of ubuntu. My real problem here is that I still have that annoyance of having to click twice to obtain any line on this app (exactly the same as before and after unstable release)

my best guess here and I'm just guessing since I don't really know a lot about deciphering configuration files is that, I think ubuntu is recognizing the tablet as both a 'USB Input device' AND a mouse at the same time, I am almost certain of this as after installing a notification library that provides information whenever a usb device is connected and identified provides information twice for each time I plug in my tablet. For anything else in terms of info to find out more about this, I might need a little guidance, in any case I hope I've come to the right place for help. And thanks for your attention to my message if you've been strong enough to read my ramble this far. XD

On the other hand and just to provide mention, I think I have the same problem than Andrew87 regarding the mouse and as far as I can read, it doesn't seem we'll get both tablet mouse and pen working together real soon, so that's not really a concern but I provide this as feedback in the testing custom of saying 'doesn't work on a WP8060U', hope it helps any developer reading this out there. I'm willing and able to do any required testing if anyone will guide me through what needs to be done. :)

anyway, thanks again and I just wait for further insight.

EDIT: Got the pressure back working as it used to in GIMP by downgrading, but I still have that problem with the second click to trace... and I've noticed something else.. the tablet is listed on extended devices twice which I think points out more in the direction of my 2x1 theory. :P

-Fer-

---

### Post by ptomulto on 2012-06-09
what about easy pen i405x graphic tablet in ubuntu 12.04, how do i install this?

---

### Post by ptomulto on 2012-06-09
what about gpen i40x in ubuntu 12.04

---

### Post by Favux on 2012-06-09
Hi ptomulto,

Support for that new model wasn't added until the 3.4 kernel, then it will work on the evdev driver.  In the meantime you will need to use either a pre-patched pre-compiled Precise 3.2 kernel or patch it yourself:  [http://ubuntuforums.org/showthread.php?t=1946486](http://ubuntuforums.org/showthread.php?t=1946486)

The Genius Easy Pen i405x, if plugged in, should show:
```
0458:5010
```
in the tablet line of the output of ***lsusb*** in a terminal.  Which translates to:
Vendor ID = 0458 = KYE Systems (Genius is their brand name)
Product ID = 5010

---

