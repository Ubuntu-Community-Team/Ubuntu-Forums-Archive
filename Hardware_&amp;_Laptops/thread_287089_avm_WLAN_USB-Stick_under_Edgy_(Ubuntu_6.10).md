---
title: "avm WLAN USB-Stick under Edgy (Ubuntu 6.10)?"
date: 2006-10-28
forum: Hardware &amp; Laptops
---

### Post by annuzzer on 2006-10-28
Hiya,

have this little problem after the in every other respect absolutely smooth installation of Edgy Eft (Ubuntu 6.10) on my laptop:

I'd like to establish connections to the WWW via WLAN, using my [avm FRITZ!WLAN USB-Stick](http://www.avm.de/en/press/announcements/2006/2006_07_11.php3). The only installation instruction I found was [this German one](http://wiki.ubuntuusers.de/FRITZ%21WLAN_USB_Stick).

Unfortunately after entering
```
cd fritz/src
sudo make
```
which - of course - is changing to the unpacked directory and starting the installation I got this error messages ('Fehler' is the German word for error as you may know):
```
ann@ubuntubox:~/fritz/src$ sudo make
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/ann/fritz/src modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/ann/fritz/src/main.o
In file included from /home/ann/fritz/src/main.c:31:
/home/ann/fritz/src/tools.h:75: error: expected identifier or ‘(’ before ‘typeof’
/home/ann/fritz/src/tools.h:75: error: expected ‘)’ before ‘__xchg’
/home/ann/fritz/src/main.c:65: error: unknown field ‘owner’ specified in initializer
/home/ann/fritz/src/main.c:65: warning: initialization from incompatible pointer type
make[2]: *** [/home/ann/fritz/src/main.o] Fehler 1
make[1]: *** [_module_/home/ann/fritz/src] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.17-10-generic'
make: *** [fwlanusb.o] Fehler 2
```

'Betrete Verzeichnis' means 'entering directory' and 'Verlasse Verzeichnis' at the end of the error message means 'leaving directory'.

Any ideas how to get ahead? If you need additional information please let me know.

Thanks in advance...

Ann

---

### Post by annuzzer on 2006-10-28
In addition to my previous posting:

Is it possible that the error-messages are the result of an 32bit/64bit-issue (drivers designed for a 32bit OS and me using the 64bit version of Ubuntu 6.10)?

Despite the concise interest in my problem, again: Thanks in advance!

Ann

---

### Post by littlespy on 2006-10-28
> Is it possible that the error-messages are the result of an 32bit/64bit-issue (drivers designed for a 32bit OS and me using the 64bit version of Ubuntu 6.10)?

Yes, I think so.  I've been having a hell of a time getting the rt73 driver to work with my 64-bit system.  I'm about to reinstall i386 and see if I can get networking to work.

---

### Post by FrodoB on 2006-11-09
I think that the issue is that you need to install the kernel source.  For Edgy you need to:

$ sudo apt-get install linux-source-2.6.17

from a terminal window. It may just work then.

---

### Post by rigol on 2006-11-22
I have the same problem using this wiki.

```
rigol@rigol-desktop:~/fritz/src$ sudo make
Password:
make -C /lib/modules/2.6.15-27-k7/build SUBDIRS=/home/rigol/fritz/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-27-k7'
  CC [M]  /home/rigol/fritz/src/main.o
  CC [M]  /home/rigol/fritz/src/driver.o
/home/rigol/fritz/src/driver.c: In function &#8216;usb_write_complete&#8217;:
/home/rigol/fritz/src/driver.c:492: warning: ISO C90 forbids mixed declarations and code
/home/rigol/fritz/src/driver.c: In function &#8216;usb_read_complete&#8217;:
/home/rigol/fritz/src/driver.c:534: warning: ISO C90 forbids mixed declarations and code
/home/rigol/fritz/src/driver.c: In function &#8216;usb_cmd_complete&#8217;:
/home/rigol/fritz/src/driver.c:619: warning: ISO C90 forbids mixed declarations and code
  CC [M]  /home/rigol/fritz/src/tools.o
  CC [M]  /home/rigol/fritz/src/lib.o
/home/rigol/fritz/src/lib.c: In function &#8216;os_protect_lock&#8217;:
/home/rigol/fritz/src/lib.c:402: error: incompatible type for argument 1 of &#8216;_spin_lock_irqsave&#8217;
/home/rigol/fritz/src/lib.c: In function &#8216;os_protect_unlock&#8217;:
/home/rigol/fritz/src/lib.c:426: error: incompatible type for argument 1 of &#8216;_spin_unlock_irqrestore&#8217;
make[2]: *** [/home/rigol/fritz/src/lib.o] Error 1
make[1]: *** [_module_/home/rigol/fritz/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-27-k7'
make: *** [fwlanusb.o] Error 2

```

I installed the linux-headers for my kernel and the other packages. And I DON'T use the 64bit Ubuntu.

---

### Post by rigol on 2006-11-22
Well, mabye this [http://wiki.ubuntuusers.de/Baustelle/WLAN/Treiber/FRITZ_WLAN_USB_Stick_2](http://wiki.ubuntuusers.de/Baustelle/WLAN/Treiber/FRITZ_WLAN_USB_Stick_2) will help you? I managed to get the stick installed, but still can't figure out how to get connected to an open wlan.

---

### Post by jbtito03 on 2006-11-22
if everithing else fails.... use ndiswrapper :D 


cheers


JB

---

