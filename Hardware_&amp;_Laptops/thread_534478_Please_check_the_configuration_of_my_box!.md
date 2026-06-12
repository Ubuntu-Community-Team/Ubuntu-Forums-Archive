---
title: "Please check the configuration of my box!"
date: 2007-08-25
forum: Hardware &amp; Laptops
---

### Post by DamjanDimitrioski on 2007-08-25
[LEFT]I have:
[/LEFT]
[RIGHT]            MB> Asrock Via Hyperion 4 in 1 [SIZE=-1]P4VM800 Dual Memory.[/SIZE]

[SIZE=-1]            Processor> Intel Pentium Celeron D 2350 Mhz.[/SIZE]
[SIZE=-1]Ram Mem> 256 Mb.[/SIZE]
[SIZE=-1]Video> Nvidia Ge Force 4400 MX, with AGP 8X.[/SIZE]
[SIZE=-1]Audio> Internal C-Media.[/SIZE]
[SIZE=-1]Modem> Intel soft modem 537 ( code  name Tiger networks) incompactible.[/SIZE]
[SIZE=-1]Other> Q-tec web cam (Flyes).[/SIZE]
[SIZE=-1]Monitor> LG Flatron 17". (Works)[/SIZE]

[LEFT][SIZE=-1]Now, do i need any drivers for the MB?[/SIZE]
[/LEFT]
[/RIGHT]

---

### Post by Sepero on 2007-09-24
You ever get this worked out guy?
You can get an Intel 537EP modem driver for Feisty here:
[http://ubuntuforums.org/showthread.php?t=552090](http://ubuntuforums.org/showthread.php?t=552090)

What is the output of this on the commandline:
lspci | grep 537

---

### Post by DamjanDimitrioski on 2007-09-26
I installed the driver, by it says> fails booting 537 or something like that.
on the third attemp, it was successfull, but there were kernel module errors.
But stll it can't connect, i right clicked in gnome on network, the manual, enable modem, then i entered calling number and stuff usr and pass. and clicked close, then i left clicked and clicked on connect modem, then nohing happend, then no fax sound, not a single sound from the modem.
  I tried to change the PCI slot, but no change.
The modem is working on stupid win, or on  another win box.

What shall i do?
And why the modem driver is restricted?
I don't like restriction, i hate rebooting.

P.S> I need the modem less for connectiong to the internet, i need it for simple  
        telephone dialing, with my special modem programs, that i builded.

---

### Post by Sepero on 2007-09-26
The driver sounds like it is not correct for your modem. I asked you before, what is the output of this on the commandline:
lspci | grep 537

For the driver to work, the output should have the string "537EP" in it.
If it says "537AA" or something else, then it won't work.
If there is no output, then you don't have a 537* modem at all.


The modem driver is "Restricted" because it's not Open Source. (ALL software that is not Open Source is considered restricted, because no one can modify or improve it.)

The core of the driver was written by Intel Corporation and is Closed Source (proprietary).

PS.
I normally reply to posts asap, but I'm gonna be outta town for the next few days. So if I don't immediately reply, you'll know why.

---

### Post by Sepero on 2007-09-26
Here's more help on getting your modem running:

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by DamjanDimitrioski on 2007-09-26
I have done already all of that steps.

Here is my pci list or sort off>

00:00.0 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0b.0 Communication controller: Tiger Jet Network Inc. Tiger3XX   Modem/ISDN interface #Here is it, my stupid winmodem.
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a2)

---

### Post by Sepero on 2007-09-26
(I'm about 1hour from going out of town)

So this is your modem:
00:0b.0 Communication controller: Tiger Jet Network Inc. Tiger3XX Modem/ISDN interface

I'm not saying it's 100% not a 537* modem, but what makes you think it is? Did the 'scanmodem' tool tell you it was? I've never seen a 537* modem listed by that name before, and the '537EP' driver (that chuckman78 helped me package) will obviously not work with it.

---

### Post by DamjanDimitrioski on 2007-09-26
I have scan the modem two months ago, but the scan program, found it intel, and it gave me link to SuSe driver, although it didn't worked either,
i mean i couldn't ./configured the driver, it says config. , then make 537, and then error.

---

### Post by DamjanDimitrioski on 2007-09-26
Can you tell me if I find the drivers, a way to use the modem as a phone?

---

### Post by chuckman78 on 2007-09-26
Hi.

We need the result of this command:

```
lspci | grep 537
```

I also strongly recommend that you download a recent version of scanModem from here:

[http://132.68.73.235/linmodems/packages/scanModem.gz]("http://132.68.73.235/linmodems/packages/scanModem.gz")

And attached here the resulting Modem.txt file.


Regards,

Carlos.

---

### Post by DamjanDimitrioski on 2007-09-27
Hi, i don't quite understand you, cause I'm new to Ubuntu forums, I will send the data on to this thing.
Or you want me to upload them to the linmodem site, please correct me if I'm wrong.

---

### Post by Sepero on 2007-09-29
It appears that you correctly read your ModemData.txt file:
" Support type needed or chipset:	INTEL537"

The people who made the 'scanModem' tool know more than me, so I have to agree that it is an Intel 537 modem. Unfortunately, there are 537, 537AA, 537EA, 537EP, and 537SP models. The driver chuckman78 and I created only supports 537EP models. I have not yet incorporated the other models.

To get your modem working, you will need compile driver the yourself.
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)


"Can you tell me if I find the drivers, a way to use the modem as a phone?"
 With the efax/gfax programs, you can use your modem like a fax machine. I've never used any programs specifically for using the modem as a 'phone', but I would think that they probably exist. You may have to search [www.sourceforge.net](www.sourceforge.net) or other software locations.

---

### Post by DamjanDimitrioski on 2007-10-01
Compiling a driver it's not a problem, the problem is I need direct link to needed .tgz archive, which has my modem driver.

---

### Post by DamjanDimitrioski on 2007-10-01
I found and compile the .tgz source, but i got the same problem as I have in the deb package, the module wont load.
Here are the log messages that i captured:

=======================================================
root@KOLG:~/Desktop/Intel-537EP-2.70.95.0-for-2.6.20# make 537
   Module precompile check
   Current running kernel is: 2.6.20-16-generic
   /lib/modules...   autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: No such file or directory
   autoconf.h matches running kernel
diff: /boot/vmlinuz.version.h: No such file or directory
   version.h matches running kernel
2.6.20-16-generic
make[1]: Entering directory `/root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv'
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.o
/root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c: In function &#1074;&#1026;&#152;softcore_init_struct&#1074;&#1026;™:
/root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:341: warning: assignment from incompatible pointer type
/root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c: In function &#1074;&#1026;&#152;open&#1074;&#1026;™:
/root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:397: warning: passing argument 2 of &#1074;&#1026;&#152;request_irq&#1074;&#1026;™ from incompatible pointer type
/root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:409: warning: &#1074;&#1026;&#152;pm_register&#1074;&#1026;™ is deprecated (declared at include/linux/pm_legacy.h:15)
/root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c: At top level:
/root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:770: warning: initialization from incompatible pointer type
/root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:771: warning: initialization from incompatible pointer type
/root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/coredrv.c:872: warning: initialization makes integer from pointer without a cast
  CC [M]  /root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/clmmain.o
  CC [M]  /root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/rts.o
/root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/rts.c:80: warning: initialization from incompatible pointer type
  CC [M]  /root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/task.o
  CC [M]  /root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/uart.o
  CC [M]  /root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/wwh_dflt.o
  CC [M]  /root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/locks.o
  CC [M]  /root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial_io.o
  CC [M]  /root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial_ioctl.o
  CC [M]  /root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial.o
/root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial.c: In function &#1074;&#1026;&#152;softserial_register_tty&#1074;&#1026;™:
/root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial.c:127: warning: assignment from incompatible pointer type
/root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial.c:128: warning: assignment from incompatible pointer type
/root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial.c:151: warning: assignment from incompatible pointer type
/root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial.c: At top level:
/root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/softserial.c:190: warning: initialization from incompatible pointer type
  CC [M]  /root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/afedsp_int.o
/root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/afedsp_int.c:39: warning: initialization makes integer from pointer without a cast
/root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/afedsp_int.c:48: warning: function declaration isn&#1074;&#1026;™t a prototype
/root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/afedsp_int.c:60: warning: initialization from incompatible pointer type
/root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/afedsp_int.c:61: warning: initialization from incompatible pointer type
/root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/afedsp_int.c:65: warning: function declaration isn&#1074;&#1026;™t a prototype
/root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/afedsp_int.c:446: warning: initialization from incompatible pointer type
  LD [M]  /root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/Intel537.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/.537core.lib.cmd for /root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/537core.lib
  CC      /root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/Intel537.mod.o
  LD [M]  /root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv/Intel537.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: Leaving directory `/root/Desktop/Intel-537EP-2.70.95.0-for-2.6.20/coredrv'
root@KOLG:~/Desktop/Intel-537EP-2.70.95.0-for-2.6.20# make install
rm -f /etc/hamregistry.bin
bash 537_inst
running kernel 2.6.20-16-generic
chmod: cannot access `usrsound': No such file or directory
installing hamregistry, used for persistant storage
installing usrsound, a soft buzzer
install: cannot stat `usrsound': No such file or directory
installing 537 module
debian 537_boot rc2.d and rc3.d scripts
starting module and utilities
#Now eternal waiting.
=======================================================
Help me or else if will commit suicide, just joking.

---

### Post by Sepero on 2007-10-01
This is the driver source file you need:
[http://linmodems.technion.ac.il/packages/Intel/537/Intel-537EP-2.70.95.0-for-2.6.20.tar.gz](http://linmodems.technion.ac.il/packages/Intel/537/Intel-537EP-2.70.95.0-for-2.6.20.tar.gz)


Before building the source, you may have to run this on the commandline:
export MODEM_TYPE=537


If after all that, it still doesn't work, I can only suggest that you get a hardware modem. (Or maybe get a cheaper Intel 536EP modem and the driver I have compiled for it.)

---

### Post by DamjanDimitrioski on 2007-10-02
Look I only need the modem for phone, that means if I need to buy a new modem, I rather then buy a new telephone.
Cause I can't wait a file or a page to be loaded one hour through a modem.

---

### Post by DamjanDimitrioski on 2007-10-02
I just remembered that this is the same file source that I compiled yesterday, the log that I send to you was in fact Intel-537EP-2.70.95.0-for-2.6.20.tar.gz.

So that means that it require other drivers, in stupid windows, the modem was working, but i got drivers with the modem for win, but there were not for Linux.
Do you need the drivers cd informations or something like that?

---

### Post by Sepero on 2007-10-02
> **DamjanDimitrioski said:**
> Do you need the drivers cd informations or something like that?
I can't tell you much about Microsoft, I haven't had it installed on my computer in years. Unless the CD documentation says the modem is not an Intel 537, then the CD won't help you.


After you 'make install' it says this:
chmod: cannot access `usrsound': No such file or directory
installing hamregistry, used for persistant storage
installing usrsound, a soft buzzer
install: cannot stat `usrsound': No such file or directory


Did you look into that? Perhaps the file usrsound wasn't copied over correctly, or it wasn't where it was supposed to be? I dunno if that's the problem or not, but it's the only thing that stands out to me.

---

