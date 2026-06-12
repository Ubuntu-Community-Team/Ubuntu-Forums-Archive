---
title: "JMicron xD Card Reader driver Ubuntu 10.10 Kernel 2.6.35-28-generic"
date: 2011-04-01
forum: Hardware
---

### Post by Ramon444 on 2011-04-01
My laptop Acer Aspire 5930G use JMicron card reader. I use Ubuntu 10.10 Kernel 2.6.35-28-generic SD cards worked fine, but xD cards didn't. I have found [driver for xD]("http://ubuntuforums.org/showthread.php?t=1519307&page=2") card support, but it was outdated(for old kernel).
I have send E-mail to JMicron support. At the next day i received new driver which i attached to this post(PWD: 123).

Release Date:
2011/01/19

Support Kernels:
2.6.22~2.6.37

Support Chips:
JMB38x MS/xD Host Controller [DID: 2383/2384, 2388/2389, 2393/2394]

Support Memory Cards:
MemoryStick Standard/Pro/Pro-HG Card
xD-Picture Card

Install Requirement:
1. Kernel srource HEAD
2. Compiler

Install Process:
1. Decompress jmb38x_xxxxxxxx.tbz2
   # tar xjvf jmb38x_xxxxxxxx.tbz2
2. Change directory to jmb38x
   # cd jmb38x
3. Compile drivers with root permission
   # make
   # make install


Now cards(SD, XD) work fine and have automount. MS i don't have to test.

---

### Post by Renshu on 2011-04-10
Hi Ramon444,

Thank you for posting this. I tried this but I need the password to extract the file. Could you post it here so I and others can access the driver.

Thanks :p

Renshu

---

### Post by Ramon444 on 2011-04-10
> **Renshu said:**
> Thank you for posting this. I tried this but I need the password to extract the file. Could you post it here so I and others can access the driver.


Password: 123

> **Ramon444 said:**
> I have send E-mail to JMicron support. At the next day i received new driver which i attached to this post(PWD: 123).


I have posted password in my first post in this topic.
PWD=PassWorD - 123 :)

P.S. I received archive from JMicron already with password.

---

### Post by Renshu on 2011-04-12
Thank you Ramon444, I should have read your posts a little more carefully. 

):P
Renshu

---

### Post by Renshu on 2011-04-12
It works!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Tiede on 2011-04-28
For some reason, it's not working here...
This is what I get:
```

user@Uubuntu:~/Downloads/MS+XD driver/jmb38x$ make
echo /home/user/Downloads/MS+XD driver/jmb38x
/home/user/Downloads/MS+XD driver/jmb38x
make -C /lib/modules/2.6.35-28-generic/build M=/home/user/Downloads/MS+XD driver/jmb38x
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
make[1]: *** No rule to make target `driver/jmb38x'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
make: *** [all] Error 2

```
A quick google offered no solutions.
Anybody has a quick fix?


EDIT: I was attempting this using maverick. Currently, the computer i am using is being upgraded to natty.
I strongly doubt it is a difference in the linux-headers packages, but I am just pulling at straws here.

Of course, the computer was up-to-date with linux-headers-2.6.35.28-generic installed.
I have since also installed linux-headers-2.6.35.28-generic-pae as well, just in case,
if for some weird reason the x86/86_64 package was missing something... of course, that'd be HIGHLY unlikely.


I am probably going to try again with natty when the install is done and post any new findings (if any).

---

### Post by Tiede on 2011-04-29
Well, it was at least worth a try.
It didn't change squat though. Same error. Same problem.

Did you guys have to do anything besides ensuring headers are installed?
Am I missing something here?

---

### Post by Ramon444 on 2011-04-29
I have upgraded to natty too. And after it my card reader don't see SD and xD cards. So the problem has remained in Natty. Natty have Kernel 2.6.38-8-generic. So this driver is to old for new kernel. I have send letter to support, and as soon as i will receive the new driver i will post it here on forum.

---

### Post by Ramon444 on 2011-04-29
> **Tiede said:**
> For some reason, it's not working here...
This is what I get:
```

user@Uubuntu:~/Downloads/MS+XD driver/jmb38x$ make
echo /home/user/Downloads/MS+XD driver/jmb38x
/home/user/Downloads/MS+XD driver/jmb38x
make -C /lib/modules/2.6.35-28-generic/build M=/home/user/Downloads/MS+XD driver/jmb38x
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
make[1]: *** No rule to make target `driver/jmb38x'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
make: *** [all] Error 2

```
A quick google offered no solutions.
Anybody has a quick fix?
Just remove space in /home/user/Downloads/[COLOR="Red"]MS+XDdriver[/COLOR]/jmb38x And it will normally compile.

---

### Post by Ramon444 on 2011-04-29
Please refer to the attached file of the latest MS+xD card driver that is updated to support kernel version 2.6.38.

Support Kernels:
2.6.22~2.6.38

Support Chips:
JMB38x MS/xD Host Controller [DID: 2383/2384, 2388/2389, 2393/2394]

Support Memory Cards:
MemoryStick Standard/Pro/Pro-HG Card
xD-Picture Card

Install Requirement:
1. Kernel srource HEAD
2. Compiler

Install Process:
1. Decompress jmb38x_xxxxxxxx.tbz2
   # tar xjvf jmb38x_xxxxxxxx.tbz2
2. Change directory to jmb38x
   # cd jmb38x
3. Compile drivers with root permission
   # make
   # make install

Known Issues:

Also i added - "modprobe acpiphp"  to /etc/rc.local

So now cards(SD, XD) work fine and have automount in Natty too. MS i don't have to test.

---

### Post by Tiede on 2011-04-29
Cool, extra dark, grind filled coffee beans awesomeness!

I'll try this at once and let you know!
I thought of so many things to do, but hadn't even noticed the space being there.
I will edit this post accordingly once I test it on the said computer later this morning.

---

### Post by Tiede on 2011-04-29
Crazy delicious latte craze!
Everything went smoothly. Thanks a lot Ramon!

---

### Post by Ramon444 on 2011-04-29
> **Tiede said:**
> Crazy delicious latte craze!
Everything went smoothly. Thanks a lot Ramon!

You are welcome :) Nice to hear that.

---

### Post by xtaylord on 2011-04-29
Humm... something's not quite right


make -C /lib/modules/2.6.38-1-generic/build M=/home/d/Downloads/jmb38x
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-1-generic'
  CC [M]  /home/d/Downloads/jmb38x/memstick.o
/home/d/Downloads/jmb38x/memstick.c: In function ‘memstick_init’:
/home/d/Downloads/jmb38x/memstick.c:727: error: implicit declaration of function ‘create_freezable_workqueue’
/home/d/Downloads/jmb38x/memstick.c:727: warning: assignment makes pointer from integer without a cast
make[2]: *** [/home/d/Downloads/jmb38x/memstick.o] Error 1
make[1]: *** [_module_/home/d/Downloads/jmb38x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-1-generic'
make: *** [all] Error 2

---

### Post by Ramon444 on 2011-04-30
Thats normal output:

roman@acer:~/Downloads/jmb38x$ sudo make
[sudo] password for roman: 
echo /home/roman/Downloads/jmb38x
/home/roman/Downloads/jmb38x
make -C /lib/modules/2.6.38-8-generic/build M=/home/roman/Downloads/jmb38x
make[1]: &#1042;&#1093;&#1086;&#1078;&#1091; &#1091; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075; "/usr/src/linux-headers-2.6.38-8-generic"
  LD      /home/roman/Downloads/jmb38x/built-in.o
  CC [M]  /home/roman/Downloads/jmb38x/memstick.o
  CC [M]  /home/roman/Downloads/jmb38x/mspro_block.o
/home/roman/Downloads/jmb38x/mspro_block.c: In function ‘ms_complete_log_phy_tbl’:
/home/roman/Downloads/jmb38x/mspro_block.c:2832:1: warning: the frame size of 1040 bytes is larger than 1024 bytes
  CC [M]  /home/roman/Downloads/jmb38x/xd_card_blk.o
  CC [M]  /home/roman/Downloads/jmb38x/xd_card_ecc.o
  LD [M]  /home/roman/Downloads/jmb38x/xd_card.o
  CC [M]  /home/roman/Downloads&#1103;/jmb38x/flash_bd.o
  CC [M]  /home/roman/Downloads/jmb38x/jmb38x_ms.o
  CC [M]  /home/roman/Downloads/jmb38x/jmb38x_xd.o
  Building modules, stage 2.
  MODPOST 6 modules
  CC      /home/roman/Downloads/jmb38x/flash_bd.mod.o
  LD [M]  /home/roman/Downloads/jmb38x/flash_bd.ko
  CC      /home/roman/Downloads/jmb38x/jmb38x_ms.mod.o
  LD [M]  /home/roman/Downloads/jmb38x/jmb38x_ms.ko
  CC      /home/roman/Downloads/jmb38x/jmb38x_xd.mod.o
  LD [M]  /home/roman/Downloads/jmb38x/jmb38x_xd.ko
  CC      /home/roman/Downloads/jmb38x/memstick.mod.o
  LD [M]  /home/roman/Downloads/jmb38x/memstick.ko
  CC      /home/roman/Downloads/jmb38x/mspro_block.mod.o
  LD [M]  /home/roman/Downloads/jmb38x/mspro_block.ko
  CC      /home/roman/Downloads/jmb38x/xd_card.mod.o
  LD [M]  /home/roman/Downloads/jmb38x/xd_card.ko
make[1]: &#1047;&#1072;&#1083;&#1080;&#1096;&#1072;&#1102; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075; "/usr/src/linux-headers-2.6.38-8-generic"

Thats after fresh install of natty and same after upgrade, but you need kernel headers (by default they are installed) and try to download driver again and make in another folder.

---

### Post by nishant.singh28 on 2011-05-01
Slightly off topic, but any ideas about a similar driver for a Ricoh 592 series MS Pro reader?

---

### Post by Ramon444 on 2011-05-02
> **nishant.singh28 said:**
> Slightly off topic, but any ideas about a similar driver for a Ricoh 592 series MS Pro reader?

Maybe this topic will help you: [http://ubuntuforums.org/showthread.php?t=731892]("http://ubuntuforums.org/showthread.php?t=731892")

or try to mail to Ricoh support, maybe they will help you.

---

### Post by ispmarin on 2011-05-03
Did all the steps above, but it didn't work. It works in Windows 7 after installing the drivers from the JMicron page, but the kernel module is being loaded but the card is not being detected.

---

### Post by Ramon444 on 2011-05-03
> **ispmarin said:**
> Did all the steps above, but it didn't work. It works in Windows 7 after installing the drivers from the JMicron page, but the kernel module is being loaded but the card is not being detected.
Well Windows 7 is another type of OS. :)

I think you have 10.10 problem with not detecting card when it's not inserted before boot.

Try do this:
create a new file called "cardreader-fix.conf" in "/etc/modprobe.d/"
with just the line "options sdhci debug_quirks=1" and reboot

---

### Post by ispmarin on 2011-05-03
Hi there,

Thanks for your answer. I tried the file on modprobe.d directory, but no love. Also there is no acpiphp module on my kernel - the ubuntu stock kernel. 

I only mentioned the Windows 7 part because the device does not show until a card is inserted - only then the sd card reader appears on the Device Manager. 

Searching the web I found several suggestions, but none helped - there is no power saving in my BIOS or in the device properties on Windows.

Any other ideas?

Thanks again.

---

### Post by Ramon444 on 2011-05-03
Try to boot with SD or xD card inserted in card reader. And after boot check in nautilus. If it will see the card then problem will be just with detection.

---

### Post by ispmarin on 2011-05-05
The card is detected if inserted before boot, and if the card is removed and reinserted, it is unmounted and mounted again. How can this be solved? I can't keep the card in the reader or reboot my laptop every time I want to use the card reader... :-)

---

### Post by Ramon444 on 2011-05-05
> **ispmarin said:**
> The card is detected if inserted before boot, and if the card is removed and reinserted, it is unmounted and mounted again. How can this be solved? I can't keep the card in the reader or reboot my laptop every time I want to use the card reader... :-)

Try to add “modprobe pciehp” to /etc/rc.local and then reboot.

If this will not help you can leave any card or card adapter in card reader.

---

### Post by ispmarin on 2011-05-05
Thanks, I'll try that as soon I can reboot my laptop. 

If this doesn't work I'll be in trouble, as I said - this is a laptop that I carry around, so a card sticking out is not convenient or safe. Should I report a bug against the kernel?

---

### Post by Ramon444 on 2011-05-05
> **ispmarin said:**
> If this doesn't work I'll be in trouble, as I said - this is a laptop that I carry around, so a card sticking out is not convenient or safe. Should I report a bug against the kernel?

I think it's not a kernel bug, cause driver is loaded and work, it's just a recognition problem. Also SD card support is built-in kernel. So this driver just add xD and MMC support.

---

### Post by MangeAnanas on 2011-05-18
Hello. I am a Linux noobe. I followed the directions of the first post and it appears that all of the modules are installed. lsmod gives:

Module                                Size           Used by
....
jmb38x_xd         7942  0 
xd_card                                            29442  1    jmb38x_xd
flash_bd             8827  1      xd_card
mspro_block      28113  0 
jmb38x_ms        11553  0 
memstick            9393  2      mspro_block,jmb38x_ms
....

I am using ubuntu 10.10 uname -r gives:
2.6.35-28-generic

Now what do I do? I was hoping to see something in /dev or /media. I have an SD card adapter that has a 4GB SDHC micro SD card in it. I also tried using a 1GB SD micro SD card. How do I access the micro SD card? lspci doesn't give anything to do with the JMB38x. Ubuntu is running as virtual box VM. The main OS (Windows 7) see the JMicron card reader fine.

---

### Post by Ramon444 on 2011-05-18
> **MangeAnanas said:**
> 
Now what do I do? I was hoping to see something in /dev or /media. I have an SD card adapter that has a 4GB SDHC micro SD card in it. I also tried using a 1GB SD micro SD card. How do I access the micro SD card? lspci doesn't give anything to do with the JMB38x. Ubuntu is running as virtual box VM. The main OS (Windows 7) see the JMicron card reader fine.
Try to load Ubuntu with inserted SD card, and then check in File browser. If it will not be avaliable, then it can be some VM issue.

---

### Post by MangeAnanas on 2011-05-20
> **Ramon444 said:**
> Try to load Ubuntu with inserted SD card, and then check in File browser. If it will not be avaliable, then it can be some VM issue.

Thanks. It was the VM. I started Ubuntu live CD and put in an SD card an the file browser popped up.

---

### Post by hydrox24 on 2011-08-18
Incase anyone else gets a similar error when they run make install to this:
```
requires -E or -F flag...
```
and the install hangs until you hit a keypress, all you need to do is edit the Makefile with your favourite editor by finding the
```

        /sbin/depmod -ae

```
and remove the "e" flag as so:
```

        /sbin/depmod -a

```

and the install should work nicely.
Install was conducted on 10.04 with the 2.6.32-33-generic kernel

after all that I simply rebooted with the card in the slot and after that it would auto-mount when I plugged it in at any time.
Thanks for the life-saving post :)
Hope that helps.

---

### Post by okmat on 2011-11-28
Big thanks Ramon444! everything worked for me by following post number 10. I have ubuntu 11.10 on a dell XPS 15z

cheers :)

---

### Post by Flynsarmy on 2012-01-04
There a patch for Oneric? Kernel 3.0.0-14. Attempted to install and all seemed to go well but got a warning:

> /sbin/depmod -ae
WARNING: -e needs -E or -F

EDIT: Replaced with /sbin/depmod -a and no more warnings, but still no working card reader.

---

### Post by kaaloo on 2012-01-07
Not working for me either on 3.0.0-14

---

### Post by Ramon444 on 2012-04-10
I have made update(not clean install) to Ubuntu 11.11 and it's still working. Try to start Ubuntu with inserted card. Maybe this driver is alredy included in new vesion of Ubuntu. Else contact the Vendor of SD card and they will send you new driver.(I did so before)

---

### Post by burulo11 on 2012-05-07
EROOR i need help




root@carlos-pc:/home/carlos/Descargas/MS+XDdriver/jmb38x# make
echo /home/carlos/Descargas/MS+XDdriver/jmb38x
/home/carlos/Descargas/MS+XDdriver/jmb38x
make -C /lib/modules/3.2.0-24-generic-pae/build M=/home/carlos/Descargas/MS+XDdriver/jmb38x
make[1]: se ingresa al directorio «/usr/src/linux-headers-3.2.0-24-generic-pae»
  CC [M]  /home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.o
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:28:27: error: expected ‘)’ before ‘uint’
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:240:1: aviso: la definición de datos no tiene tipo o clase de almacenamiento [activado por defecto]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:240:1: aviso: el tipo de dato por defecto es ‘int’ en la declaración de ‘EXPORT_SYMBOL’ [-Wimplicit-int]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:240:1: aviso: nombres de parámetros (sin tipos) en la declaración de la función [activado por defecto]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:272:1: aviso: la definición de datos no tiene tipo o clase de almacenamiento [activado por defecto]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:272:1: aviso: el tipo de dato por defecto es ‘int’ en la declaración de ‘EXPORT_SYMBOL’ [-Wimplicit-int]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:272:1: aviso: nombres de parámetros (sin tipos) en la declaración de la función [activado por defecto]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:286:1: aviso: la definición de datos no tiene tipo o clase de almacenamiento [activado por defecto]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:286:1: aviso: el tipo de dato por defecto es ‘int’ en la declaración de ‘EXPORT_SYMBOL’ [-Wimplicit-int]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:286:1: aviso: nombres de parámetros (sin tipos) en la declaración de la función [activado por defecto]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:311:1: aviso: la definición de datos no tiene tipo o clase de almacenamiento [activado por defecto]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:311:1: aviso: el tipo de dato por defecto es ‘int’ en la declaración de ‘EXPORT_SYMBOL’ [-Wimplicit-int]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:311:1: aviso: nombres de parámetros (sin tipos) en la declaración de la función [activado por defecto]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:348:1: aviso: la definición de datos no tiene tipo o clase de almacenamiento [activado por defecto]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:348:1: aviso: el tipo de dato por defecto es ‘int’ en la declaración de ‘EXPORT_SYMBOL’ [-Wimplicit-int]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:348:1: aviso: nombres de parámetros (sin tipos) en la declaración de la función [activado por defecto]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:410:1: aviso: la definición de datos no tiene tipo o clase de almacenamiento [activado por defecto]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:410:1: aviso: el tipo de dato por defecto es ‘int’ en la declaración de ‘EXPORT_SYMBOL’ [-Wimplicit-int]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:410:1: aviso: nombres de parámetros (sin tipos) en la declaración de la función [activado por defecto]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:608:1: aviso: la definición de datos no tiene tipo o clase de almacenamiento [activado por defecto]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:608:1: aviso: el tipo de dato por defecto es ‘int’ en la declaración de ‘EXPORT_SYMBOL’ [-Wimplicit-int]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:608:1: aviso: nombres de parámetros (sin tipos) en la declaración de la función [activado por defecto]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:644:1: aviso: la definición de datos no tiene tipo o clase de almacenamiento [activado por defecto]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:644:1: aviso: el tipo de dato por defecto es ‘int’ en la declaración de ‘EXPORT_SYMBOL’ [-Wimplicit-int]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:644:1: aviso: nombres de parámetros (sin tipos) en la declaración de la función [activado por defecto]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:665:1: aviso: la definición de datos no tiene tipo o clase de almacenamiento [activado por defecto]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:665:1: aviso: el tipo de dato por defecto es ‘int’ en la declaración de ‘EXPORT_SYMBOL’ [-Wimplicit-int]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:665:1: aviso: nombres de parámetros (sin tipos) en la declaración de la función [activado por defecto]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:676:1: aviso: la definición de datos no tiene tipo o clase de almacenamiento [activado por defecto]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:676:1: aviso: el tipo de dato por defecto es ‘int’ en la declaración de ‘EXPORT_SYMBOL’ [-Wimplicit-int]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:676:1: aviso: nombres de parámetros (sin tipos) en la declaración de la función [activado por defecto]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:688:1: aviso: la definición de datos no tiene tipo o clase de almacenamiento [activado por defecto]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:688:1: aviso: el tipo de dato por defecto es ‘int’ en la declaración de ‘EXPORT_SYMBOL’ [-Wimplicit-int]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:688:1: aviso: nombres de parámetros (sin tipos) en la declaración de la función [activado por defecto]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:706:1: aviso: la definición de datos no tiene tipo o clase de almacenamiento [activado por defecto]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:706:1: aviso: el tipo de dato por defecto es ‘int’ en la declaración de ‘EXPORT_SYMBOL’ [-Wimplicit-int]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:706:1: aviso: nombres de parámetros (sin tipos) en la declaración de la función [activado por defecto]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:714:1: aviso: la definición de datos no tiene tipo o clase de almacenamiento [activado por defecto]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:714:1: aviso: el tipo de dato por defecto es ‘int’ en la declaración de ‘EXPORT_SYMBOL’ [-Wimplicit-int]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:714:1: aviso: nombres de parámetros (sin tipos) en la declaración de la función [activado por defecto]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:720:1: aviso: la definición de datos no tiene tipo o clase de almacenamiento [activado por defecto]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:720:1: aviso: el tipo de dato por defecto es ‘int’ en la declaración de ‘EXPORT_SYMBOL’ [-Wimplicit-int]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:720:1: aviso: nombres de parámetros (sin tipos) en la declaración de la función [activado por defecto]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c: En la función ‘memstick_init’:
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:727:2: error: declaración implícita de la función ‘create_freezeable_workqueue’ [-Werror=implicit-function-declaration]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:727:12: aviso: la asignación crea un puntero desde un entero sin una conversión [activado por defecto]
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c: En el nivel principal:
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:755:15: error: expected declaration specifiers or ‘...’ before string constant
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:756:16: error: expected declaration specifiers or ‘...’ before string constant
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:757:20: error: expected declaration specifiers or ‘...’ before string constant
/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.c:758:16: error: expected declaration specifiers or ‘...’ before string constant
cc1: some warnings being treated as errors
make[2]: *** [/home/carlos/Descargas/MS+XDdriver/jmb38x/memstick.o] Error 1
make[1]: *** [_module_/home/carlos/Descargas/MS+XDdriver/jmb38x] Error 2
make[1]: se sale del directorio «/usr/src/linux-headers-3.2.0-24-generic-pae»
make: *** [all] Error 2

---

### Post by sulliwane on 2012-05-08
it seems related to this bug report : [https://bugzilla.kernel.org/show_bug.cgi?id=40802](https://bugzilla.kernel.org/show_bug.cgi?id=40802)

The solution is more a workaround than a real fix, but it makes the trick :

#sudo echo 1 > /sys/bus/pci/rescan

It will detect the SD card, until next reboot. Unless the sdcard is inserted when booting, and in this case it will be well detected without the above command...

PS : ubuntu 12.04 !

---

### Post by Flynsarmy on 2012-05-10
> **sulliwane said:**
> #sudo echo 1 > /sys/bus/pci/rescan

Sulli what are your kernel boot options? I've attempted this on 12.04 and it still doesn't pick up the card. I checked your link and it seems to have something to do with some grub settings. Here's mine:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force acpi=noirq pciehp.pciehp_force=1 i915.semaphores=1"
```

Also for reference the card I'm using is a Verbatim 4GB class 6 - not that that should make a difference.

---

### Post by sam81 on 2012-05-28
The sudo echo 1 > /sys/bus/pci/rescan trick doesn't seem to work for me either. I am booting with the following: 
GRUB_CMDLINE_LINUX="acpi=noirq i915.semaphores=1 pcie_aspm=force pciehp.pciehp_force=1"

---

### Post by qubical on 2012-06-01
Strange things happen...
My card reader on my XPS15z (Ubuntu 12.04) is still not detected unless I insert a card when booting. However until I was working on this issue my USB sticks were not loading when inserting either and now they are.

added to /etc/rc.local:
```
modprobe pciehp
```

---

### Post by alord90 on 2012-06-28
When I run the command $- sudo make
it produces a ton of errors and so cannot make, which then means cannot perform make install either. This is with Ubuntu 12.04 on Dell XPS 15z.

Here is the errors sudo make produces:

make -C /lib/modules/3.2.0-23-generic/build M=/home/andrew/Downloads/jmb38x
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-23-generic'
  LD      /home/andrew/Downloads/jmb38x/built-in.o
  CC [M]  /home/andrew/Downloads/jmb38x/memstick.o
/home/andrew/Downloads/jmb38x/memstick.c:28:27: error: expected ‘)’ before ‘uint’
/home/andrew/Downloads/jmb38x/memstick.c:240:1: warning: data definition has no type or storage class [enabled by default]
/home/andrew/Downloads/jmb38x/memstick.c:240:1: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL’ [-Wimplicit-int]
/home/andrew/Downloads/jmb38x/memstick.c:240:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/andrew/Downloads/jmb38x/memstick.c:272:1: warning: data definition has no type or storage class [enabled by default]
/home/andrew/Downloads/jmb38x/memstick.c:272:1: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL’ [-Wimplicit-int]
/home/andrew/Downloads/jmb38x/memstick.c:272:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/andrew/Downloads/jmb38x/memstick.c:286:1: warning: data definition has no type or storage class [enabled by default]
/home/andrew/Downloads/jmb38x/memstick.c:286:1: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL’ [-Wimplicit-int]
/home/andrew/Downloads/jmb38x/memstick.c:286:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/andrew/Downloads/jmb38x/memstick.c:311:1: warning: data definition has no type or storage class [enabled by default]
/home/andrew/Downloads/jmb38x/memstick.c:311:1: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL’ [-Wimplicit-int]
/home/andrew/Downloads/jmb38x/memstick.c:311:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/andrew/Downloads/jmb38x/memstick.c:348:1: warning: data definition has no type or storage class [enabled by default]
/home/andrew/Downloads/jmb38x/memstick.c:348:1: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL’ [-Wimplicit-int]
/home/andrew/Downloads/jmb38x/memstick.c:348:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/andrew/Downloads/jmb38x/memstick.c:410:1: warning: data definition has no type or storage class [enabled by default]
/home/andrew/Downloads/jmb38x/memstick.c:410:1: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL’ [-Wimplicit-int]
/home/andrew/Downloads/jmb38x/memstick.c:410:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/andrew/Downloads/jmb38x/memstick.c:608:1: warning: data definition has no type or storage class [enabled by default]
/home/andrew/Downloads/jmb38x/memstick.c:608:1: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL’ [-Wimplicit-int]
/home/andrew/Downloads/jmb38x/memstick.c:608:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/andrew/Downloads/jmb38x/memstick.c:644:1: warning: data definition has no type or storage class [enabled by default]
/home/andrew/Downloads/jmb38x/memstick.c:644:1: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL’ [-Wimplicit-int]
/home/andrew/Downloads/jmb38x/memstick.c:644:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/andrew/Downloads/jmb38x/memstick.c:665:1: warning: data definition has no type or storage class [enabled by default]
/home/andrew/Downloads/jmb38x/memstick.c:665:1: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL’ [-Wimplicit-int]
/home/andrew/Downloads/jmb38x/memstick.c:665:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/andrew/Downloads/jmb38x/memstick.c:676:1: warning: data definition has no type or storage class [enabled by default]
/home/andrew/Downloads/jmb38x/memstick.c:676:1: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL’ [-Wimplicit-int]
/home/andrew/Downloads/jmb38x/memstick.c:676:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/andrew/Downloads/jmb38x/memstick.c:688:1: warning: data definition has no type or storage class [enabled by default]
/home/andrew/Downloads/jmb38x/memstick.c:688:1: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL’ [-Wimplicit-int]
/home/andrew/Downloads/jmb38x/memstick.c:688:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/andrew/Downloads/jmb38x/memstick.c:706:1: warning: data definition has no type or storage class [enabled by default]
/home/andrew/Downloads/jmb38x/memstick.c:706:1: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL’ [-Wimplicit-int]
/home/andrew/Downloads/jmb38x/memstick.c:706:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/andrew/Downloads/jmb38x/memstick.c:714:1: warning: data definition has no type or storage class [enabled by default]
/home/andrew/Downloads/jmb38x/memstick.c:714:1: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL’ [-Wimplicit-int]
/home/andrew/Downloads/jmb38x/memstick.c:714:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/andrew/Downloads/jmb38x/memstick.c:720:1: warning: data definition has no type or storage class [enabled by default]
/home/andrew/Downloads/jmb38x/memstick.c:720:1: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL’ [-Wimplicit-int]
/home/andrew/Downloads/jmb38x/memstick.c:720:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/andrew/Downloads/jmb38x/memstick.c:758:15: error: expected declaration specifiers or ‘...’ before string constant
/home/andrew/Downloads/jmb38x/memstick.c:759:16: error: expected declaration specifiers or ‘...’ before string constant
/home/andrew/Downloads/jmb38x/memstick.c:760:20: error: expected declaration specifiers or ‘...’ before string constant
/home/andrew/Downloads/jmb38x/memstick.c:761:16: error: expected declaration specifiers or ‘...’ before string constant
make[2]: *** [/home/andrew/Downloads/jmb38x/memstick.o] Error 1
make[1]: *** [_module_/home/andrew/Downloads/jmb38x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-23-generic'
make: *** [all] Error 2

Does anyone know what I can do to get the card reader working?


> **Ramon444 said:**
> Please refer to the attached file of the latest MS+xD card driver that is updated to support kernel version 2.6.38.

Support Kernels:
2.6.22~2.6.38

Support Chips:
JMB38x MS/xD Host Controller [DID: 2383/2384, 2388/2389, 2393/2394]

Support Memory Cards:
MemoryStick Standard/Pro/Pro-HG Card
xD-Picture Card

Install Requirement:
1. Kernel srource HEAD
2. Compiler

Install Process:
1. Decompress jmb38x_xxxxxxxx.tbz2
   # tar xjvf jmb38x_xxxxxxxx.tbz2
2. Change directory to jmb38x
   # cd jmb38x
3. Compile drivers with root permission
   # make
   # make install

Known Issues:

Also i added - "modprobe acpiphp"  to /etc/rc.local

So now cards(SD, XD) work fine and have automount in Natty too. MS i don't have to test.

---

### Post by miketowninc on 2012-07-08
I have the same problems as alord

---

### Post by marfy on 2012-07-22
Hi folks,

it seems there are some issues with the newer kernel sources. I have googled a bit and fix an original jmb38x driver that I have found on a blog support page.
After building and running the l.sh script my xD card was automated mounted instantly.

I have added a Changelog with the thinks I have fixed.

Mit freundlichen Grüßen
Marfy

---

### Post by Flynsarmy on 2012-07-23
Marfly,

I compiled, installed then ran l.sh. During compilation I got the depmod error mentioned [here]("http://ubuntuforums.org/showpost.php?p=11585821&postcount=31") but ignored it - figured you knew about it as you didn't fix it in your updated script. Rebooted and still no working SD Card.

I confirmed that /etc/rc.local contains:
> modprobe jmb38x_ms
modprobe mspro_block
modprobe flash_bd
modprobe xd_card
modprobe jmb38x_xd

and *ls /lib/modules/3.2.0-26-generic/kernel/drivers/jmb38x/* shows all the relevant .ko files.

Running 12.04 64-bit.

---

### Post by Jedcurtis on 2012-07-25
Hi all,
I've done everything since post #10! Also took all the other steps mentioned above and still no love. 

Running stand-alone 12.04 Precise LTS 64bit with latest kernel 3.2.0-27.  This is a laptop I bought in Feb this year.  It is a Dell XPS 15z.

I take lots of pic's, and would like to be able to use the cardreader without having to reboot in order to see it.  (With my SSD drive, and about a 12 second boot time, I'm just being picky picky picky!)  Yes, if I boot with it inserted, when Ubuntu logs in (whew, a whole 12 seconds later!) there it is!  The laptop came with a plastic fake insert that I've since misplaced.  I have a feeling that if I find that little bugger and reboot with it inserted (the little fake plastic piece that is) this will all be moot.  I'll bet it will then auto mount my sd card!  I'll let you all know if and when I find it.

I've been perusing the forums and some other not so tasty linux sites, and the Ubuntu Forums community is, hands down, the most helpful anywhere!

Anyway, long story short (hehe) I'm basically same as Flynsarmy.   Any help appreciated...

Jed

---

### Post by Jedcurtis on 2012-08-04
O.K., so I found the plastic insert that goes into the SD slot when it is not being used.  Didn't make any difference.  Still have to re-boot to get it to see a card...

Jed

---

### Post by nemarona on 2012-08-19
The solution no longer works for Ubuntu 12.04, kernel version 3.2.0.29.

---

### Post by chrizzler on 2012-08-29
.

---

### Post by apienk01 on 2012-09-30
Just found a Gentoo forum [thread]("http://forums.gentoo.org/viewtopic-t-918232-start-0.html") with a tip that worked for me. After issuing this command **as root** the JMicron multimedia card reader is automagically detected, and automounts inserted cards:

```
echo 1 > /sys/bus/pci/rescan
```

Hope it works for you.

---

### Post by Flynsarmy on 2012-10-02
> **apienk01 said:**
> After issuing this command **as root** the JMicron multimedia card reader is automagically detected, and automounts inserted cards:

```
echo 1 > /sys/bus/pci/rescan
```

Doesn't work on 12.04 64-bit 3.2.0-31-generic. Attempted both using the command with an SD insert and with the slot empty then plugging one in. No detection in either case.

---

### Post by apienk01 on 2012-10-04
> **Flynsarmy said:**
> Doesn't work on 12.04 64-bit 3.2.0-31-generic. Attempted both using the command with an SD insert and with the slot empty then plugging one in. No detection in either case.

I'm using 3.2.0-32-generic 64-bit on Dell XPS L502x, and after forced rescan detection works either with the card or without. However, before I found this workaround I mailed JMicron, and today got a new driver. Here it is, attached. Didn't try compiling it because I'm pretty happy activating the reader with the command.

---

### Post by raelgc on 2013-04-08
> **apienk01 said:**
> I'm using 3.2.0-32-generic 64-bit on Dell XPS L502x, and after forced rescan detection works either with the card or without. However, before I found this workaround I mailed JMicron, and today got a new driver. Here it is, attached. Didn't try compiling it because I'm pretty happy activating the reader with the command.

I tested on Kubuntu 12.04 LTS with 3.2.0-39-generic.
I followed the instructions in the readme file.
The driver works fine, just giving me errors on the mspro driver (I just commented it on /etc/rc.local):

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.


#exit 0
# remove modules in initramfs 
rmmod jmb38x_ms
#rmmod mspro_block
rmmod flash_bd
rmmod xd_card
rmmod jmb38x_xd
modprobe jmb38x_ms
#modprobe mspro_block
modprobe flash_bd
modprobe xd_card
modprobe jmb38x_xd

```


Automounting working fine.

Additionally, I was not able to compile the patch: it's throwing source code errors. As the driver is working fine, fine by now.

---

### Post by b3ta on 2013-04-22
> **apienk01 said:**
> I'm using 3.2.0-32-generic 64-bit on Dell XPS L502x, and after forced rescan detection works either with the card or without. However, before I found this workaround I mailed JMicron, and today got a new driver. Here it is, attached. Didn't try compiling it because I'm pretty happy activating the reader with the command.

Hi

Just tried this driver on Ubuntu 13.04 beta2 and does not seem to work. Guess it's the new kernel? Readme says supported kernel up to 3.2.0.

```
patrik@patrik-laptop:~/Downloads/jmb38x_20120501/jmb38x$ sudo make
echo /home/patrik/Downloads/jmb38x_20120501/jmb38x
/home/patrik/Downloads/jmb38x_20120501/jmb38x
make -C /lib/modules/3.8.0-19-generic/build M=/home/patrik/Downloads/jmb38x_20120501/jmb38x
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-19-generic'
  CC [M]  /home/patrik/Downloads/jmb38x_20120501/jmb38x/xd_card_blk.o
/home/patrik/Downloads/jmb38x_20120501/jmb38x/xd_card_blk.c: In function &#8216;xd_card_copy_tmp&#8217;:
/home/patrik/Downloads/jmb38x_20120501/jmb38x/xd_card_blk.c:778:25: error: &#8216;KM_BIO_SRC_IRQ&#8217; undeclared (first use in this function)
/home/patrik/Downloads/jmb38x_20120501/jmb38x/xd_card_blk.c:778:25: note: each undeclared identifier is reported only once for each function it appears in
/home/patrik/Downloads/jmb38x_20120501/jmb38x/xd_card_blk.c:778:3: error: too many arguments to function &#8216;kmap_atomic&#8217;
In file included from include/linux/pagemap.h:10:0,
                 from include/linux/blkdev.h:13,
                 from /home/patrik/Downloads/jmb38x_20120501/jmb38x/linux/xd_card.h:15,
                 from /home/patrik/Downloads/jmb38x_20120501/jmb38x/xd_card_blk.c:16:
include/linux/highmem.h:66:21: note: declared here
/home/patrik/Downloads/jmb38x_20120501/jmb38x/xd_card_blk.c:792:44: error: macro "kunmap_atomic" passed 2 arguments, but takes just 1
/home/patrik/Downloads/jmb38x_20120501/jmb38x/xd_card_blk.c:792:3: error: &#8216;kunmap_atomic&#8217; undeclared (first use in this function)
/home/patrik/Downloads/jmb38x_20120501/jmb38x/xd_card_blk.c: In function &#8216;xd_card_check_ecc&#8217;:
/home/patrik/Downloads/jmb38x_20120501/jmb38x/xd_card_blk.c:832:26: error: &#8216;KM_BIO_SRC_IRQ&#8217; undeclared (first use in this function)
/home/patrik/Downloads/jmb38x_20120501/jmb38x/xd_card_blk.c:832:4: error: too many arguments to function &#8216;kmap_atomic&#8217;
In file included from include/linux/pagemap.h:10:0,
                 from include/linux/blkdev.h:13,
                 from /home/patrik/Downloads/jmb38x_20120501/jmb38x/linux/xd_card.h:15,
                 from /home/patrik/Downloads/jmb38x_20120501/jmb38x/xd_card_blk.c:16:
include/linux/highmem.h:66:21: note: declared here
/home/patrik/Downloads/jmb38x_20120501/jmb38x/xd_card_blk.c:835:46: error: macro "kunmap_atomic" passed 2 arguments, but takes just 1
/home/patrik/Downloads/jmb38x_20120501/jmb38x/xd_card_blk.c:835:5: error: &#8216;kunmap_atomic&#8217; undeclared (first use in this function)
/home/patrik/Downloads/jmb38x_20120501/jmb38x/xd_card_blk.c:840:45: error: macro "kunmap_atomic" passed 2 arguments, but takes just 1
/home/patrik/Downloads/jmb38x_20120501/jmb38x/xd_card_blk.c:857:4: error: too many arguments to function &#8216;kmap_atomic&#8217;
In file included from include/linux/pagemap.h:10:0,
                 from include/linux/blkdev.h:13,
                 from /home/patrik/Downloads/jmb38x_20120501/jmb38x/linux/xd_card.h:15,
                 from /home/patrik/Downloads/jmb38x_20120501/jmb38x/xd_card_blk.c:16:
include/linux/highmem.h:66:21: note: declared here
/home/patrik/Downloads/jmb38x_20120501/jmb38x/xd_card_blk.c:859:45: error: macro "kunmap_atomic" passed 2 arguments, but takes just 1
/home/patrik/Downloads/jmb38x_20120501/jmb38x/xd_card_blk.c: In function &#8216;xd_card_update_extra&#8217;:
/home/patrik/Downloads/jmb38x_20120501/jmb38x/xd_card_blk.c:909:26: error: &#8216;KM_BIO_SRC_IRQ&#8217; undeclared (first use in this function)
/home/patrik/Downloads/jmb38x_20120501/jmb38x/xd_card_blk.c:909:4: error: too many arguments to function &#8216;kmap_atomic&#8217;
In file included from include/linux/pagemap.h:10:0,
                 from include/linux/blkdev.h:13,
                 from /home/patrik/Downloads/jmb38x_20120501/jmb38x/linux/xd_card.h:15,
                 from /home/patrik/Downloads/jmb38x_20120501/jmb38x/xd_card_blk.c:16:
include/linux/highmem.h:66:21: note: declared here
/home/patrik/Downloads/jmb38x_20120501/jmb38x/xd_card_blk.c:912:46: error: macro "kunmap_atomic" passed 2 arguments, but takes just 1
/home/patrik/Downloads/jmb38x_20120501/jmb38x/xd_card_blk.c:912:5: error: &#8216;kunmap_atomic&#8217; undeclared (first use in this function)
/home/patrik/Downloads/jmb38x_20120501/jmb38x/xd_card_blk.c:917:45: error: macro "kunmap_atomic" passed 2 arguments, but takes just 1
make[2]: *** [/home/patrik/Downloads/jmb38x_20120501/jmb38x/xd_card_blk.o] Error 1
make[1]: *** [_module_/home/patrik/Downloads/jmb38x_20120501/jmb38x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-19-generic'
make: *** [all] Error 2
```

Anyone sitting on any newer driver? :)

Dell XPS 15z

---

### Post by navcar on 2013-07-02
Same problem here - I'm on 13.04 with my Lenovo Y560 notebook (same JMB38x card reader issue with XD Cards)

Update: I emailed JMicron, they replied that they don't have a Linux driver for kernel versions higher than 3.2 (JMB38x)

---

### Post by b3ta on 2013-08-29
No more news? :-)

---

### Post by maxim7 on 2014-03-13
Hello everybody. I'm using BM ware ubuntu 10.0.04I'm trying to install JMICro card reader driver downloaded from the link above and I don't know how to compile it. Could you help me to realise it?

---

