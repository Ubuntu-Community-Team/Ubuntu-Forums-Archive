---
title: "IBM T23 Lucent 56 Winmodem drivers? FIXED!!"
date: 2005-11-01
forum: Hardware &amp; Laptops
---

### Post by jradford on 2005-11-01
In upgrading to breezy I lost my ltmodem drivers in the restricted 686 section, this modem worked
perfectly in hoary.  Does anyone know why they decided to remove these?

In Adept looking at linux-restricted-modules-2.6.12-9-686 it lists ltmodem (Winmodem) but they
seem to not be anywhere...

I use dialup internet on the road and need this functionality.

So to fix this I did the following:

1. Grab [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/ltmodem-2.6-alk-7b1.tar.gz](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/ltmodem-2.6-alk-7b1.tar.gz)
2. ln -s /usr/bin/gcc3.4  gcc   (This might be different for others)
3. untar the file tmodem-2.6-alk-7b1.tar.gz and do a make
4. create the directory /lib/modules/2.6.12-9-686/other (kernel version in /lib/modules might be different)
5. copy ltmodem.ko ltserial.ko to /lib/modules/2.6.12-9-686/other and run depmod -a
6. To make sure /dev/modem is linked when the module is inserted create a file in /etc/udev/rules.d called 10-local.rules and put it in this:

#ltmodem
KERNEL="ttyLTM0", SYMLINK="modem"

7. modprobe ltserial
8. kppp and dial in 

(Note I had to change /etc/ppp/options auth to noauth to get ppp working
and add "route add default ppp0" to end of /etc/ppp/ip-up since kppp doesnt add default route correctly)

Use dmesg to see if the modules are loaded.

I hope this helps someone, it's got my modem working on my T23 thinkpad.  The only thing I havnt fixed is I have to manually do a 'modprobe ltserial' even though I added 'ltserial' to /etc/modules.  

Anyone know how to automate this?

-Jason

---

### Post by jradford on 2005-11-03
As a reply to myself, it looks like the /etc/modules entry works now on a reboot for me.

---

### Post by don_m on 2006-01-13
I never could get this to work with my T23. I am running Ubuntu 5.10 as well.

I seem to get stuck on the "Make". 

Here is what I did:
vp@ubuntuIBMT23:~/Desktop/ltmodem-2.6-alk-7c$ ls
DEFINES  docs  gcc  gcc4.0  linuxif.h  ltmdmobj.o  ltmdmobj.o-8.31  ltmdmobj.o-pre-8.31  lt_modem.c  Makefile  serial.c
vp@ubuntuIBMT23:~/Desktop/ltmodem-2.6-alk-7c$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/vp/Desktop/ltmodem-2.6-alk-7c modules
make[1]: Entering directory `/lib/modules/2.6.12-9-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.12-9-386/build'
make: *** [module] Error 2


For new users like myself, I would rewrite the instructions more along the lines of the following:

1. Download [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/ltmodem-2.6-alk-7b1.tar.gz](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/ltmodem-2.6-alk-7b1.tar.gz)

2. Use file-rollover to unpack the ltmodem-2.6-alk-7b1.tar.gz. You might have saved the file on the desktop and the extraction will end up under the "Desktop" directory unless you select another location.

3. Type : cd / <Enter>(go to root directory). Type: cd lib/modules/ <Enter> Type: sudo mkdir 2.6.12-9-686/other <Enter> It will ask for the root password.

4. Type: sudo ln -s /usr/bin/gcc3.4 gcc <Enter> while still in the same directory.

5. ...... anyway some of these details were important to the procedure.

---

### Post by don_m on 2006-06-11
I did a fresh install over Ubuntu 5.10 with Ubuntu 6.06 and found that it is now able to detect the modem and surf the web.

Go to System->Administration->Networking and select the modem to set up dial up number, password, and whether it is the default connection to the network.

I need to add an icon to the desktop to activate the modem and maybe find an utility that shows the baud rate.

Anyway, I am now able to surf the web with a dial-up connection if necessary.:lol:

---

