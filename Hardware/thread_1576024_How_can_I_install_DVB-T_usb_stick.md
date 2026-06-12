---
title: "How can I install DVB-T usb stick?"
date: 2010-09-16
forum: Hardware
---

### Post by KutViZ on 2010-09-16
I have an Avermedia Hybrid HD dvb usb stick, but so far I can't managed to make it work. I downloaded a .fw file in /lib/firmware directory, but the os don't want to recognize the stick.

---

### Post by KutViZ on 2010-09-17
that's all??...

---

### Post by dougalkerr on 2010-09-17
Mmm... I have one of these sitting at work. I wander if I can get it to work? It will have to wait till Monday though.

---

### Post by KutViZ on 2010-09-18
Since then I installed an Avermedia driver (hope the right one) and v4l-dvb modules. When i'm trying modprobe with the driver version it says: 
FATAL: Error inserting h826d (/lib/modules/2.6.32-21-generic/kernel/drivers/media/dvb/dvb-usb/h826d.ko): Unknown symbol in module, or unknown parameter (see dmesg)

In dmesg:
> 
[  600.757206] AVerMedia USB Wrapper for H826D version 0.28 loaded
[  600.828895] h826d: disagrees about version of symbol dvb_dmxdev_release
[  600.828905] h826d: Unknown symbol dvb_dmxdev_release
[  600.829140] h826d: disagrees about version of symbol video_devdata
[  600.829145] h826d: Unknown symbol video_devdata
[  600.831235] h826d: disagrees about version of symbol dvb_dmx_init
[  600.831240] h826d: Unknown symbol dvb_dmx_init
[  600.833219] h826d: disagrees about version of symbol dvb_register_adapter
[  600.833221] h826d: Unknown symbol dvb_register_adapter
[  600.833438] h826d: disagrees about version of symbol dvb_dmx_release
[  600.833440] h826d: Unknown symbol dvb_dmx_release
[  600.834811] h826d: disagrees about version of symbol dvb_dmxdev_init
[  600.834813] h826d: Unknown symbol dvb_dmxdev_init
[  600.834953] h826d: disagrees about version of symbol dvb_unregister_frontend
[  600.834955] h826d: Unknown symbol dvb_unregister_frontend
[  600.835276] h826d: disagrees about version of symbol video_register_device
[  600.835278] h826d: Unknown symbol video_register_device
[  600.835639] h826d: disagrees about version of symbol dvb_dmx_swfilter_packets
[  600.835641] h826d: Unknown symbol dvb_dmx_swfilter_packets
[  600.837284] h826d: disagrees about version of symbol video_device_release
[  600.837286] h826d: Unknown symbol video_device_release
[  600.837799] h826d: disagrees about version of symbol video_device_alloc
[  600.837800] h826d: Unknown symbol video_device_alloc
[  600.838344] h826d: disagrees about version of symbol video_unregister_device
[  600.838346] h826d: Unknown symbol video_unregister_device
[  600.838492] h826d: disagrees about version of symbol dvb_unregister_adapter
[  600.838494] h826d: Unknown symbol dvb_unregister_adapter
[  600.840805] h826d: disagrees about version of symbol dvb_register_frontend
[  600.840807] h826d: Unknown symbol dvb_register_frontend
I've read a different mode of viewing tv, it needs to do this: scan /usr/share/dvb/dvb-t/&#8230; but the result is:
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2273: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory

But still, the worst thing is, there is no dvb directory in /dev.

---

### Post by jimmers on 2010-09-19
Have you tried installing:-

dvb-apps
w-scan

Both in Synaptic.

Luck

---

### Post by KutViZ on 2010-09-21
Both are installed.

Now I have some more infos. The type of the tuner is Avermedia AverTV Volar HD Nano (A867). I've downloaded the proper driver, but can't make it. 
> 
gepzsir@gepzsir-laptop:~/Letöltések/a867$ make
make -C /lib/modules/2.6.32-24-generic/source O=/lib/modules/2.6.32-24-generic/build SUBDIRS=`pwd` modules
make[1]: Entering directory `/lib/modules/2.6.32-24-generic/source'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.32-24-generic/source'
make: *** [default] Error 2

There's a line in the Readme: "Make sure it links to kernel header or kernel tree before moving to the next step. It often points to /usr/src/xxxx" How can i make it?

---

### Post by KutViZ on 2010-09-25
any help?
here's a link for the driver. just scroll down and you will find it.
[http://www.avermedia.com/avertv/Product/ProductDetail.aspx?Id=516&tab=APDriver](http://www.avermedia.com/avertv/Product/ProductDetail.aspx?Id=516&tab=APDriver)

---

### Post by manok on 2010-09-28
Where you able to install the driver? I'm having the same queries to install the driver. I don't know how to link the driver to the kernel tree. Please help if you can.

---

### Post by IcarusR on 2010-09-28
If /lib/modules/`uname -r`/source does not exist then create symlink to it from /usr/src/xxxx (where xxxx is your kernel version).

Not tried this but I believe it should work.

---

### Post by KutViZ on 2010-09-28
> **IcarusR said:**
> If /lib/modules/`uname -r`/source does not exist then create symlink to it from /usr/src/xxxx (where xxxx is your kernel version).

Not tried this but I believe it should work.
finally i made the symbolic link. I had to copy some files in usr/src/xxxx too:
> Missing files that required to build driver: /lib/modules/2.6.35-22-generic-pae/source/drivers/media/dvb/dvb-usb/dvb-usb-common.h dvb-usb/dvb-usb.h dvb-usb/dvb-usb-ids.h
then the compiler started to working... i was so happy for a moment until this popped up:
> gepzsir@gepzsir-laptop:~/a867$ make
make -C /lib/modules/2.6.35-22-generic-pae/source O=/lib/modules/2.6.35-22-generic-pae/build SUBDIRS=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic-pae'
  CC [M]  /home/gepzsir/a867/af903x-core.o
  CC [M]  /home/gepzsir/a867/af903x-devices.o
  CC [M]  /home/gepzsir/a867/af903x-drv.o
  CC [M]  /home/gepzsir/a867/af903x-fe.o
/home/gepzsir/a867/af903x-fe.c:220: warning: &#8216;af903x_set_bandwidth&#8217; defined but not used
  CC [M]  /home/gepzsir/a867/af903x-tuner.o
  CC [M]  /home/gepzsir/a867/cmd.o
  CC [M]  /home/gepzsir/a867/standard.o
  CC [M]  /home/gepzsir/a867/demodulator.o
  CC [M]  /home/gepzsir/a867/demodulatorextend.o
  CC [M]  /home/gepzsir/a867/usb2impl.o
/home/gepzsir/a867/usb2impl.c:1: fatal error: linux/autoconf.h: No such file or directory.
compilation terminated.
make[3]: *** [/home/gepzsir/a867/usb2impl.o] Error 1
make[2]: *** [_module_/home/gepzsir/a867] Error 2
make[1]: *** [sub-make] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic-pae'
make: *** [default] Error 2


now what can i do?

---

### Post by Richbeanz on 2010-10-03
I'm stuck on this one as well, this is what I get when I try 
$ ls /lib/modules/`uname -r`/source

richb@richb-desktop:/usr/local/src/a867$ ls /lib/modules/`uname -r`/source 
ls: cannot access /lib/modules/2.6.32-25-generic/source: No such file or directory

I dont understand quite what [IcarusR]("http://ubuntuforums.org/member.php?u=179763") means, 

"If /lib/modules/`uname -r`/source does not exist then create symlink to  it from /usr/src/xxxx (where xxxx is your kernel version)."

If /lib/modules/2.6.32-25-generic/source does not exist then  how can I create a symlink to something that does not exist. I am totally 
new to this so I am struggling to understand...

Any help appreciated.
Thanks

---

### Post by IcarusR on 2010-10-03
Richbeanz

> If /lib/modules/`uname -r`/source does not exist then create symlink to it from /usr/src/xxxx (where xxxx is your kernel version).

That was meant in reference to this line from the readme.txt

"Make sure it links to kernel header or kernel tree before moving to the next step. It often points to /usr/src/xxxx"

& this question from the OP

> There's a line in the Readme: "Make sure it links to kernel header or kernel tree before moving to the next step. It often points to /usr/src/xxxx" How can i make it? 

I no longer have the tar ball so I can not explain it any better.

---

### Post by jimmers on 2010-10-03
Try this link:-
                       #toc, .toc, .mw-warning { border: 1px solid rgb(170, 170, 170); background-color: rgb(249, 249, 249); padding: 5px; font-size: 95%; }#toc h2, .toc h2 { display: inline; border: medium none; padding: 0pt; font-size: 100%; font-weight: bold; }#toc #toctitle, .toc #toctitle, #toc .toctitle, .toc .toctitle { text-align: center; }#toc ul, .toc ul { list-style-type: none; list-style-image: none; margin-left: 0pt; padding-left: 0pt; text-align: left; }#toc ul ul, .toc ul ul { margin: 0pt 0pt 0pt 2em; }#toc .toctoggle, .toc .toctoggle { font-size: 94%; }body { font-size: 12pt; font-family: 'Times New Roman'; }table {  }td { border-collapse: collapse; text-align: left; vertical-align: top; }         [www.betavine.net/bvportal/resources/datacards](www.betavine.net/bvportal/resources/datacards)




Luck

---

### Post by IcarusR on 2010-10-03
jimmers

Your link to betavine is for 3G datacards, ie modems not DVB-T tuners.

---

### Post by Richbeanz on 2010-10-04
My lack of knowledge about this subject is vast. I would like to install the driver and if someone could describe to me how I could accomplish it by making the symlink. 

"If /lib/modules/`uname -r`/source does not exist then create symlink to it from /usr/src/xxxx (where xxxx is your kernel version)."

So How do I go about this?  
I think I need go to file "/usr/src/xxxx" and create a link there called "/lib/modules/`uname -r`/source" which links to "/lib/modules/`uname -r`/" and make a new file in there called source? Is that correct?

Okay so I tried this...
richb@richb-desktop:/usr/local/src/a867$ sudo ln -s /lib/modules/`uname -r`/source /usr/src/linux-headers-2.6.32-25-generic
Then I get...
richb@richb-desktop:/usr/local/src/a867$ ls /lib/modules/`uname -r`/source
ls: cannot access /lib/modules/2.6.32-25-generic/source: No such file or directory

Same output  as earlier!

I'm confused! Can anyone help me out to install this driver please? Or if anyone could point me in the direction of a decent simple tutorial on how to install a DVB-T USB driver such as the Avermedia A867.

---

### Post by Richbeanz on 2010-10-08
Okay, so no replies. I decided to have a try after days of reading. This is what I tried... 
I made a copy of source into lib/modules/2.6.32-25-generic/source then I tried; 

$ ls /lib/modules/`uname -r`/source
 and what do you know it came up with the file so I tried
$ make
$ sudo make install

and it installed BUT still no joy when I try
$ lsmod | grep a867  I get nothing so I try a shutdown, unplug the device, startup, and 
replug it in, but no go...
$ lsusb gives me this

richb@richb-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 003 Device 002: ID 03f0:0024 Hewlett-Packard KU-0316 Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 07ca:1867 AVerMedia Technologies, Inc. 
Bus 001 Device 004: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

 This is what I now get when I 
$ dmesg
[ 1558.751387] usb 1-6: USB disconnect, address 6
[ 1561.244027] usb 1-6: new high speed USB device using ehci_hcd and address 7
[ 1561.381890] usb 1-6: configuration #1 chosen from 1 choice
[ 1561.389925] a867: disagrees about version of symbol dvb_usb_device_init
[ 1561.389930] a867: Unknown symbol dvb_usb_device_init

Can anyone help with what is happening now? Whats up with the disagreement and the unknown symbol??
Should I give up and stick with Windows?? I so like Ubuntu and MythTV though...

---

### Post by Richbeanz on 2010-10-20
Okay so did I fart in the room or something? lol 
Sorry if I offended or whatever it was to kill this thread... 
Anyway I'm getting in over my depth, so I guess I have to wait untill the new driver A867 is updated into Ubuntu next version.

---

### Post by Richbeanz on 2010-10-20
OMG I just updated my software and the usb stick is now detected and working MythTV can see the tuner and its all go!
Thanks team Ubuntu You Rock!

---

### Post by KutViZ on 2010-10-30
So, i'm still trying to make the official driver. After some file copying here's a another problem:
> gepzsir@gepzsir-laptop:~/a867$ make
make -C /lib/modules/2.6.35-22-generic-pae/source O=/lib/modules/2.6.35-22-generic-pae/build SUBDIRS=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic-pae'
  CC [M]  /home/gepzsir/a867/af903x-core.o
  CC [M]  /home/gepzsir/a867/af903x-devices.o
  CC [M]  /home/gepzsir/a867/af903x-drv.o
  CC [M]  /home/gepzsir/a867/af903x-fe.o
/home/gepzsir/a867/af903x-fe.c:220: warning: &#8216;af903x_set_bandwidth&#8217; defined but not used
  CC [M]  /home/gepzsir/a867/af903x-tuner.o
  CC [M]  /home/gepzsir/a867/cmd.o
  CC [M]  /home/gepzsir/a867/standard.o
  CC [M]  /home/gepzsir/a867/demodulator.o
  CC [M]  /home/gepzsir/a867/demodulatorextend.o
  CC [M]  /home/gepzsir/a867/usb2impl.o
  CC [M]  /home/gepzsir/a867/user.o
  CC [M]  /home/gepzsir/a867/mxl5007t.o
/home/gepzsir/a867/mxl5007t.c: In function &#8216;a867_mxl5007t_release&#8217;:
/home/gepzsir/a867/mxl5007t.c:596: error: implicit declaration of function &#8216;kfree&#8217;
/home/gepzsir/a867/mxl5007t.c: In function &#8216;a867_mxl5007t_attach&#8217;:
/home/gepzsir/a867/mxl5007t.c:654: error: implicit declaration of function &#8216;kzalloc&#8217;
/home/gepzsir/a867/mxl5007t.c:654: warning: assignment makes pointer from integer without a cast
/home/gepzsir/a867/mxl5007t.c:661: warning: assignment makes pointer from integer without a cast
/home/gepzsir/a867/mxl5007t.c:664: warning: assignment makes pointer from integer without a cast
/home/gepzsir/a867/mxl5007t.c:667: warning: assignment makes pointer from integer without a cast
make[3]: *** [/home/gepzsir/a867/mxl5007t.o] Error 1
make[2]: *** [_module_/home/gepzsir/a867] Error 2
make[1]: *** [sub-make] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic-pae'
make: *** [default] Error 2
Can I manage somehow that the compiler skip making the mxl5007t.c? (or any ideas what's the problem?) I mean after configure, because I only have the makefile...

---

### Post by majo33 on 2010-11-11
To compile a867 driver, follow these steps (change the 2.6.35-23-generic-pae to the appropriate kernel version):
1) copy missing *.h files into [FONT="Courier New"]/usr/src/linux-headers-2.6.35-23-generic-pae/drivers/media/dvb/...[/FONT]
I copied them from the ubuntu kernel source package:
[FONT="Courier New"]apt-get install linux-source package
cd /usr/src/linux-source-2.6.35/
tar -jxf linux-source-2.6.35.tar.bz2[/FONT]
The required *.h files can be found in [FONT="Courier New"]/usr/src/linux-source-2.6.35/linux-source-2.6.35/drivers/media/dvb/...[/FONT]

2) create the symlink [FONT="Courier New"]/lib/modules/lib/modules/2.6.35-23-generic-pae/source[/FONT]
[FONT="Courier New"]ln -s /usr/src/linux-headers-2.6.35-23-generic-pae/ /lib/modules/2.6.35-23-generic-pae/source[/FONT]

3) edit the first line of [FONT="Courier New"]usb2impl.c[/FONT]:
[FONT="Courier New"]#include <linux/autoconf.h>[/FONT]
to
[FONT="Courier New"]#include <generated/autoconf.h>[/FONT]

4) add this line into [FONT="Courier New"]mxl5007t.c[/FONT] (line 26)
[FONT="Courier New"]#include <linux/slab.h>[/FONT]

5) run [FONT="Courier New"]make[/FONT]


I found that this driver is working on Ubuntu 10.04 (32bit), but (unfortunately) not on Ubuntu 10.10 (64bit). I'll test it on Ubuntu 10.10 (32bit).

---

### Post by KutViZ on 2010-11-11
Driver compiled and installed :) Big thx!

---

### Post by majo33 on 2010-11-11
I want to update my last post. I found that the tuner is also working on Ubuntu 10.10 64bit, but it collide with my usb wifi adapter (TP-LINK TL-WN422G). If I want to watch TV in Linux I have to unplug the wifi adapter:(

---

### Post by manok on 2010-11-19
You guys are geniuses! I finally got this driver to work in the new 2.6.35 kernel. I even raised a ticket with Avermedia Support. They said the'll look into it, but here you go, now it works. Please keep posted as there might be new problems compiling it for the next kernel upgrade. Thanks to you all!

---

### Post by majo33 on 2012-03-07
This is a patch for Ubuntu 11.10 kernel 3.X. Apply it in the driver directory.
```

cd a867_drv_v1.0.28
patch < a867patch.txt
make

```

---

### Post by ondar on 2012-03-10
Thank you very much. Your patch solved all my problems. My DVB-T usb stick now works fine (Kubuntu 11.10, 64 bit).

---

### Post by majo33 on 2012-05-06
Patch for Ubuntu 12.04, kernel version 3.2 (the previous patch is not required)
```

tar -jxf a867_drv_v1.0.28.tar.bz2
cd a867_drv_v1.0.28
patch < a867_ubuntu_12_04.patch.txt
make

```

---

### Post by SrP3L4 on 2012-05-11
Hi, I'm trying to install a867 drivers. I applied the patch but it doesn't work. This is the output:
```
luis@luis-HP-UBU:~/Descargas/a867_drv_v1.0.28$ make
make -C /lib/modules/3.2.0-24-generic/source O=/lib/modules/3.2.0-24-generic/build SUBDIRS=`pwd` modules
make[1]: se ingresa al directorio «/usr/src/linux-headers-3.2.0-24-generic»
  CC [M]  /home/luis/Descargas/a867_drv_v1.0.28/af903x-core.o
  CC [M]  /home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.o
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c: En la función &#8216;af903x_frontend_attach&#8217;:
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:59:6: error: &#8216;struct dvb_usb_adapter&#8217; no tiene un miembro llamado &#8216;fe_adap&#8217;
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:61:13: error: &#8216;struct dvb_usb_adapter&#8217; no tiene un miembro llamado &#8216;fe_adap&#8217;
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c: En la función &#8216;af903x_tuner_attach&#8217;:
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:67:19: error: &#8216;struct dvb_usb_adapter&#8217; no tiene un miembro llamado &#8216;fe_adap&#8217;
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c: En el nivel principal:
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:201:27: error: se especificó el campo desconocido &#8216;num_frontends&#8217; en el inicializador
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:202:27: error: se especificó el campo desconocido &#8216;fe&#8217; en el inicializador
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:202:27: aviso: llaves alrededor del inicializador escalar [activado por defecto]
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:202:27: aviso: (cerca de la inicialización de &#8216;af903x_properties[0].adapter[0].pid_filter_count&#8217;) [activado por defecto]
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:203:29: aviso: llaves alrededor del inicializador escalar [activado por defecto]
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:203:29: aviso: (cerca de la inicialización de &#8216;af903x_properties[0].adapter[0].pid_filter_count&#8217;) [activado por defecto]
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:207:6: error: el nombre del campo no está en el inicializador de record o union
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:207:6: error: (cerca de la inicialización de &#8216;af903x_properties[0].adapter[0].pid_filter_count&#8217;)
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:209:6: error: el nombre del campo no está en el inicializador de record o union
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:209:6: error: (cerca de la inicialización de &#8216;af903x_properties[0].adapter[0].pid_filter_count&#8217;)
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:209:6: aviso: exceso de elementos en el inicializador de escalar [activado por defecto]
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:209:6: aviso: (cerca de la inicialización de &#8216;af903x_properties[0].adapter[0].pid_filter_count&#8217;) [activado por defecto]
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:210:5: error: el nombre del campo no está en el inicializador de record o union
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:210:5: error: (cerca de la inicialización de &#8216;af903x_properties[0].adapter[0].pid_filter_count&#8217;)
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:210:5: aviso: exceso de elementos en el inicializador de escalar [activado por defecto]
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:210:5: aviso: (cerca de la inicialización de &#8216;af903x_properties[0].adapter[0].pid_filter_count&#8217;) [activado por defecto]
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:211:5: error: el nombre del campo no está en el inicializador de record o union
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:211:5: error: (cerca de la inicialización de &#8216;af903x_properties[0].adapter[0].pid_filter_count&#8217;)
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:211:5: aviso: exceso de elementos en el inicializador de escalar [activado por defecto]
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:211:5: aviso: (cerca de la inicialización de &#8216;af903x_properties[0].adapter[0].pid_filter_count&#8217;) [activado por defecto]
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:212:5: error: el nombre del campo no está en el inicializador de record o union
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:212:5: error: (cerca de la inicialización de &#8216;af903x_properties[0].adapter[0].pid_filter_count&#8217;)
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:212:5: aviso: exceso de elementos en el inicializador de escalar [activado por defecto]
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:212:5: aviso: (cerca de la inicialización de &#8216;af903x_properties[0].adapter[0].pid_filter_count&#8217;) [activado por defecto]
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:213:5: error: el nombre del campo no está en el inicializador de record o union
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:213:5: error: (cerca de la inicialización de &#8216;af903x_properties[0].adapter[0].pid_filter_count&#8217;)
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:213:5: aviso: exceso de elementos en el inicializador de escalar [activado por defecto]
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:213:5: aviso: (cerca de la inicialización de &#8216;af903x_properties[0].adapter[0].pid_filter_count&#8217;) [activado por defecto]
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:214:5: error: el nombre del campo no está en el inicializador de record o union
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:214:5: error: (cerca de la inicialización de &#8216;af903x_properties[0].adapter[0].pid_filter_count&#8217;)
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:214:5: aviso: exceso de elementos en el inicializador de escalar [activado por defecto]
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:214:5: aviso: (cerca de la inicialización de &#8216;af903x_properties[0].adapter[0].pid_filter_count&#8217;) [activado por defecto]
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:216:5: error: el nombre del campo no está en el inicializador de record o union
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:216:5: error: (cerca de la inicialización de &#8216;af903x_properties[0].adapter[0].pid_filter_count&#8217;)
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:216:5: aviso: llaves alrededor del inicializador escalar [activado por defecto]
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:216:5: aviso: (cerca de la inicialización de &#8216;af903x_properties[0].adapter[0].pid_filter_count&#8217;) [activado por defecto]
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:217:5: error: el nombre del campo no está en el inicializador de record o union
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:217:5: error: (cerca de la inicialización de &#8216;af903x_properties[0].adapter[0].pid_filter_count&#8217;)
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:218:5: error: el nombre del campo no está en el inicializador de record o union
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:218:5: error: (cerca de la inicialización de &#8216;af903x_properties[0].adapter[0].pid_filter_count&#8217;)
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:218:5: aviso: exceso de elementos en el inicializador de escalar [activado por defecto]
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:218:5: aviso: (cerca de la inicialización de &#8216;af903x_properties[0].adapter[0].pid_filter_count&#8217;) [activado por defecto]
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:219:5: error: el nombre del campo no está en el inicializador de record o union
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:219:5: error: (cerca de la inicialización de &#8216;af903x_properties[0].adapter[0].pid_filter_count&#8217;)
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:219:5: aviso: exceso de elementos en el inicializador de escalar [activado por defecto]
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:219:5: aviso: (cerca de la inicialización de &#8216;af903x_properties[0].adapter[0].pid_filter_count&#8217;) [activado por defecto]
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:220:5: error: el nombre del campo no está en el inicializador de record o union
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:220:5: error: (cerca de la inicialización de &#8216;af903x_properties[0].adapter[0].pid_filter_count&#8217;)
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:220:5: aviso: llaves alrededor del inicializador escalar [activado por defecto]
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:220:5: aviso: (cerca de la inicialización de &#8216;af903x_properties[0].adapter[0].pid_filter_count&#8217;) [activado por defecto]
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:221:6: error: el nombre del campo no está en el inicializador de record o union
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:221:6: error: (cerca de la inicialización de &#8216;af903x_properties[0].adapter[0].pid_filter_count&#8217;)
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:221:6: aviso: llaves alrededor del inicializador escalar [activado por defecto]
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:221:6: aviso: (cerca de la inicialización de &#8216;af903x_properties[0].adapter[0].pid_filter_count&#8217;) [activado por defecto]
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:222:7: error: el nombre del campo no está en el inicializador de record o union
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:222:7: error: (cerca de la inicialización de &#8216;af903x_properties[0].adapter[0].pid_filter_count&#8217;)
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:224:6: aviso: exceso de elementos en el inicializador de escalar [activado por defecto]
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:224:6: aviso: (cerca de la inicialización de &#8216;af903x_properties[0].adapter[0].pid_filter_count&#8217;) [activado por defecto]
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:225:5: aviso: exceso de elementos en el inicializador de escalar [activado por defecto]
/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.c:225:5: aviso: (cerca de la inicialización de &#8216;af903x_properties[0].adapter[0].pid_filter_count&#8217;) [activado por defecto]
make[3]: *** [/home/luis/Descargas/a867_drv_v1.0.28/af903x-devices.o] Error 1
make[2]: *** [_module_/home/luis/Descargas/a867_drv_v1.0.28] Error 2
make[1]: *** [sub-make] Error 2
make[1]: se sale del directorio «/usr/src/linux-headers-3.2.0-24-generic»
make: *** [default] Error 2
```

---

### Post by majo33 on 2012-05-12
What version of kernel do you use?

---

### Post by SrP3L4 on 2012-05-14
Thanks for your time, my kernel version is 3.2.0-24-generic. I use Ubuntu 12.04 LTS Precise Pangoling.

---

### Post by majo33 on 2012-05-17
I'm using the same kernel. It seems that you have old kernel header/source files installed (not version 3.2). Remove old kernel sources (probably linux-source-3.0 package) then install the linux-source-3.2 package. In directory /usr/src you would find the linux-source-3.2.0.tar.bz2. Extract it and copy from the linux-source-3.2.0 directory missing *.h files into /usr/src/linux-headers-3.2.0-24/drivers/media/dvb/... Then create the symlink (assuming that your kernel is 3.2.0-24-generic)
```
ln -s /usr/src/linux-headers-3.2.0-24-generic/ /lib/modules/3.2.0-24-generic/source
```
Then apply the patch and compile the driver:
```
tar -jxf a867_drv_v1.0.28.tar.bz2
cd a867_drv_v1.0.28
patch < a867_ubuntu_12_04.patch.txt
make
```

---

### Post by TomasF on 2012-05-18
Hi guys,
it might help someone - the installer for AVERMEDIA AVerTV Hybrid Volar HX fixed for kernel 3.2.0 (Ubuntu 12.04). It contains fixes described here - [http://linuxtv.org/wiki/index.php/AVerMedia_AverTV_Hybrid_Volar_HX_%28A827%29]("http://linuxtv.org/wiki/index.php/AVerMedia_AverTV_Hybrid_Volar_HX_%28A827%29")

[http://dl.dropbox.com/u/2381236/AVERMEDIA-Linux-x86-H826D-0.10-beta-kernel3.2.0.sh](http://dl.dropbox.com/u/2381236/AVERMEDIA-Linux-x86-H826D-0.10-beta-kernel3.2.0.sh)

Just copy the file to any folder, check whether it's executable and run following command:
```
sudo ./AVERMEDIA-Linux-x86-H826D-0.10-beta-kernel3.2.0.sh 
```

(Original dirver - [http://www.avermedia.com/Product/ProductDetail.aspx?Id=293&tab=APDriver](http://www.avermedia.com/Product/ProductDetail.aspx?Id=293&tab=APDriver))

---

### Post by SrP3L4 on 2012-05-22
> **majo33 said:**
> I'm using the same kernel. It seems that you have old kernel header/source files installed (not version 3.2). Remove old kernel sources (probably linux-source-3.0 package) then install the linux-source-3.2 package. In directory /usr/src you would find the linux-source-3.2.0.tar.bz2. Extract it and copy from the linux-source-3.2.0 directory missing *.h files into /usr/src/linux-headers-3.2.0-24/drivers/media/dvb/... Then create the symlink (assuming that your kernel is 3.2.0-24-generic)
```
ln -s /usr/src/linux-headers-3.2.0-24-generic/ /lib/modules/3.2.0-24-generic/source
```Then apply the patch and compile the driver:
```
tar -jxf a867_drv_v1.0.28.tar.bz2
cd a867_drv_v1.0.28
patch < a867_ubuntu_12_04.patch.txt
make
```

Hi thanks again, but now i get this:
```
 luis@luis-HP-UBU:~/Descargas/a867_drv_v1.0.28$ make
make -C /lib/modules/3.2.0-24-generic/source O=/lib/modules/3.2.0-24-generic/build SUBDIRS=`pwd` modules
make[1]: se ingresa al directorio «/usr/src/linux-headers-3.2.0-24-generic»
  CC [M]  /home/luis/Descargas/a867_drv_v1.0.28/af903x-core.o
In file included from /home/luis/Descargas/a867_drv_v1.0.28/af903x.h:13:0,
                 from /home/luis/Descargas/a867_drv_v1.0.28/af903x-core.c:1:
include/linux/usb.h: En la función ‘usb_maxpacket’:
include/linux/usb.h:1597:2: error: declaración implícita de la función ‘usb_endpoint_maxp’ [-Werror=implicit-function-declaration]
In file included from /home/luis/Descargas/a867_drv_v1.0.28/af903x.h:15:0,
                 from /home/luis/Descargas/a867_drv_v1.0.28/af903x-core.c:1:
/lib/modules/3.2.0-24-generic/source/drivers/media/dvb/dvb-usb/dvb-usb.h: En el nivel principal:
/lib/modules/3.2.0-24-generic/source/drivers/media/dvb/dvb-usb/dvb-usb.h:17:27: error fatal: media/rc-core.h: No existe el archivo o el directorio
cc1: some warnings being treated as errors
compilación terminada.
make[3]: *** [/home/luis/Descargas/a867_drv_v1.0.28/af903x-core.o] Error 1
make[2]: *** [_module_/home/luis/Descargas/a867_drv_v1.0.28] Error 2
make[1]: *** [sub-make] Error 2
make[1]: se sale del directorio «/usr/src/linux-headers-3.2.0-24-generic»
make: *** [default] Error 2

```

---

### Post by majo33 on 2012-05-23
> **SrP3L4 said:**
> Hi thanks again, but now i get this:
```
 luis@luis-HP-UBU:~/Descargas/a867_drv_v1.0.28$ make
make -C /lib/modules/3.2.0-24-generic/source O=/lib/modules/3.2.0-24-generic/build SUBDIRS=`pwd` modules
make[1]: se ingresa al directorio «/usr/src/linux-headers-3.2.0-24-generic»
  CC [M]  /home/luis/Descargas/a867_drv_v1.0.28/af903x-core.o
In file included from /home/luis/Descargas/a867_drv_v1.0.28/af903x.h:13:0,
                 from /home/luis/Descargas/a867_drv_v1.0.28/af903x-core.c:1:
include/linux/usb.h: En la función ‘usb_maxpacket’:
include/linux/usb.h:1597:2: error: declaración implícita de la función ‘usb_endpoint_maxp’ [-Werror=implicit-function-declaration]
In file included from /home/luis/Descargas/a867_drv_v1.0.28/af903x.h:15:0,
                 from /home/luis/Descargas/a867_drv_v1.0.28/af903x-core.c:1:
/lib/modules/3.2.0-24-generic/source/drivers/media/dvb/dvb-usb/dvb-usb.h: En el nivel principal:
/lib/modules/3.2.0-24-generic/source/drivers/media/dvb/dvb-usb/dvb-usb.h:17:27: error fatal: media/rc-core.h: No existe el archivo o el directorio
cc1: some warnings being treated as errors
compilación terminada.
make[3]: *** [/home/luis/Descargas/a867_drv_v1.0.28/af903x-core.o] Error 1
make[2]: *** [_module_/home/luis/Descargas/a867_drv_v1.0.28] Error 2
make[1]: *** [sub-make] Error 2
make[1]: se sale del directorio «/usr/src/linux-headers-3.2.0-24-generic»
make: *** [default] Error 2

```

That's odd. Edit the symlink [FONT="Courier New"]/lib/modules/3.2.0-24-generic/source[/FONT] (probably now pointing to the [FONT="Courier New"]/usr/src/linux-headers-3.2.0-24-generic[/FONT]) it should point to the /usr/src/linux-source-3.2.0 (directory where you extracted [FONT="Courier New"]linux-source-3.2.0.tar.bz2[/FONT]).
If this doesn't help I can send you a compiled (binary) version of the driver.

---

### Post by JohnAadams on 2012-05-23
ask some it expert they will help you.

---

### Post by SrP3L4 on 2012-05-25
> **majo33 said:**
> That's odd. Edit the symlink [FONT=Courier New]/lib/modules/3.2.0-24-generic/source[/FONT] (probably now pointing to the [FONT=Courier New]/usr/src/linux-headers-3.2.0-24-generic[/FONT]) it should point to the /usr/src/linux-source-3.2.0 (directory where you extracted [FONT=Courier New]linux-source-3.2.0.tar.bz2[/FONT]).
If this doesn't help I can send you a compiled (binary) version of the driver.

Thank you so much majo33 finally works. :)=D>

I delete all source files and reinstall them, then all work fine.

---

### Post by ughi on 2012-07-21
hi all,
I followed the steps explained in the thread, but at last the make command gave me an error on af903x-drv.c. I'm running Ubuntu 11.04

here is the output

```

elisabetta@elisabetta-F3JC:~/Scrivania/a867_drv_v1.0.28$ sudo make
make -C /lib/modules/2.6.38-15-generic/source O=/lib/modules/2.6.38-15-generic/build SUBDIRS=`pwd` modules
make[1]: ingresso nella directory "/usr/src/linux-headers-2.6.38-15-generic"
  CC [M]  /home/elisabetta/Scrivania/a867_drv_v1.0.28/af903x-drv.o
/home/elisabetta/Scrivania/a867_drv_v1.0.28/af903x-drv.c: In function ‘A333TunerPowerControl’:
/home/elisabetta/Scrivania/a867_drv_v1.0.28/af903x-drv.c:458:32: warning: comparison between ‘Bool’ and ‘enum <anonymous>’
/home/elisabetta/Scrivania/a867_drv_v1.0.28/af903x-drv.c:471:41: warning: comparison between ‘Bool’ and ‘enum <anonymous>’
/home/elisabetta/Scrivania/a867_drv_v1.0.28/af903x-drv.c:471:87: warning: comparison between ‘Bool’ and ‘enum <anonymous>’
/home/elisabetta/Scrivania/a867_drv_v1.0.28/af903x-drv.c:473:40: warning: comparison between ‘Bool’ and ‘enum <anonymous>’
/home/elisabetta/Scrivania/a867_drv_v1.0.28/af903x-drv.c:485:27: warning: comparison between ‘Bool’ and ‘enum <anonymous>’
/home/elisabetta/Scrivania/a867_drv_v1.0.28/af903x-drv.c: In function ‘A337TunerPowerControl’:
/home/elisabetta/Scrivania/a867_drv_v1.0.28/af903x-drv.c:516:26: warning: comparison between ‘Bool’ and ‘enum <anonymous>’
/home/elisabetta/Scrivania/a867_drv_v1.0.28/af903x-drv.c:551:26: warning: comparison between ‘Bool’ and ‘enum <anonymous>’
/home/elisabetta/Scrivania/a867_drv_v1.0.28/af903x-drv.c: In function ‘Device_init’:
/home/elisabetta/Scrivania/a867_drv_v1.0.28/af903x-drv.c:1106:3: error: implicit declaration of function ‘init_MUTEX’
make[3]: *** [/home/elisabetta/Scrivania/a867_drv_v1.0.28/af903x-drv.o] Errore 1
make[2]: *** [_module_/home/elisabetta/Scrivania/a867_drv_v1.0.28] Errore 2
make[1]: *** [sub-make] Errore 2
make[1]: uscita dalla directory "/usr/src/linux-headers-2.6.38-15-generic"
make: *** [default] Errore 2

```

anybody knows how to help me, please?
do I need to plug the device in while compiling?

thanks

---

### Post by majo33 on 2012-09-10
You don't need to plug in your device while compiling driver. Try the driver from the AVER official site, there is a new version 1.0.29 (which support multiple kernel versions). Or follow my last post on this page (you need an older patch because you running an older kernel) [http://ubuntuforums.org/showthread.php?t=1576024&page=2]("http://ubuntuforums.org/showthread.php?t=1576024&page=2")

---

### Post by Richbeanz on 2012-09-16
Hello again, I have had this stick running then I updated to 12.04 and have had trouble again to reinstall. I am nearly there but I have this problem now if anyone can advise please?

richb@htpc-lounge:~$ dmesg | grep AVer
[  208.566182] AVerMedia A867 driver module V1.0.29 loaded.
[  208.964791] dvb-usb: found a 'AVerMedia A867 DVB-T Recevier' in warm state.
[  209.503680] DVB: registering new adapter (AVerMedia A867 DVB-T Recevier)
[  209.513905] dvb-usb: AVerMedia A867 DVB-T Recevier successfully initialized and connected.
[  209.514183] dvb-usb: AVerMedia A867 DVB-T Recevier successfully deinitialized and disconnected.
richb@htpc-lounge:~$

Why does it deinitialize? Any clues please?

Thanks in advance.

---

### Post by majo33 on 2012-09-21
> **Richbeanz said:**
> Hello again, I have had this stick running then I updated to 12.04 and have had trouble again to reinstall. I am nearly there but I have this problem now if anyone can advise please?

richb@htpc-lounge:~$ dmesg | grep AVer
[  208.566182] AVerMedia A867 driver module V1.0.29 loaded.
[  208.964791] dvb-usb: found a 'AVerMedia A867 DVB-T Recevier' in warm state.
[  209.503680] DVB: registering new adapter (AVerMedia A867 DVB-T Recevier)
[  209.513905] dvb-usb: AVerMedia A867 DVB-T Recevier successfully initialized and connected.
[  209.514183] dvb-usb: AVerMedia A867 DVB-T Recevier successfully deinitialized and disconnected.
richb@htpc-lounge:~$

Why does it deinitialize? Any clues please?

Thanks in advance.

You can try other usb ports.
On my Ubuntu 12.04 kernel 3.2.0-31-generic it works well (there is no disconnect message in the log).

---

