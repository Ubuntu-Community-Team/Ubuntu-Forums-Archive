---
title: "Ubuntu 5.10 Smart Link driver install problem"
date: 2005-11-27
forum: Hardware &amp; Laptops
---

### Post by jimcser on 2005-11-27
Hello-
I have Ubuntu 5.10 installed on a Dell Inspiron 5100, and I'm trying to get the modem driver installed.

I ran scanModem, and got the following:
> Class 0703: 8086:24c6   Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02) (prog-if 00 [Generic])
  SubSystem 14e4:4d64  Broadcom Corporation: Unknown device 4d64
	Flags: medium devsel, IRQ 7
 Checking for IRQ 7 sharing with modem.
      XT-PIC  Intel 82801DB-ICH4

  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 8086:24c6 14e4:4d64 debian 2.6.12-9-386  3.4.5     i686
              From records, 14e4:4d64 has soft modem codec BCM64
 The Subsystem PCI id identifies a Broadcom BCM64 codec
Use the slmodemd in ALSA mode for support
Download the SLMODEMD.gccN.tar.gz from [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)
Checking for autoloaded ALSA modem drivers

  Driver snd-intel8x0m  may enable codec acquisition 

I then downloaded SLMODEMD.gcc4.tar.gz as instructed, but I could not compile it, since there was no makefile (it was not clear what to do).  From the Smart Link site I got the driver slmodem-2.9.10, but when I tried to compile that, I got:
> make -C modem all
make[1]: Entering directory `/home/jimcser/slmodem-2.9.10/modem'
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem.o -c modem.c
modem.c: In function ‘modem_reset’:
modem.c:1701: error: invalid storage class for function ‘sregs_init’
modem.c:1713: warning: implicit declaration of function ‘sregs_init’
modem.c: At top level:
modem.c:1727: error: static declaration of ‘sregs_init’ follows non-static declaration
modem.c:1713: error: previous implicit declaration of ‘sregs_init’ was here
make[1]: *** [modem.o] Error 1
make[1]: Leaving directory `/home/jimcser/slmodem-2.9.10/modem'
make: *** [modem] Error 2

And now I'm lost.  Any suggestions?  Thanks.

---

### Post by jimcser on 2005-11-27
I finally RTFM and figured out that SLMODEMD was already an exectutable, and I was able to launch it successfully.  However, when I test it with wvdial, the modem is recognized, but I get a busy signal.  I added the 'X3' in wvdial.conf, but that did not help.

I also found in slmodem.txt :
>  Special cases:
  ---------------------------   
 For BCM64/Broadcom and ATI softmodem support, ONLY the slmodem-2.9.9x-alsa.tar.gz can serve. 
 Kernel versions of 2.6.6 or later are necessary for Broadcom BCM64 modems.
 Within the Modem/ folder output by scanModem, browse Slmodem.txt, Slmodem-ALSA.txt and Testing.txt
 There have been a few reports of problems being solved by using Bootup options:
              noapci and/or apci=off
 thus dropping back to the APM power management mode.
       Success Report - [http://linmodems.technion.ac.il/archive-fifth/msg02486.html](http://linmodems.technion.ac.il/archive-fifth/msg02486.html)
 Solution of a CONNECT problem has been achieved by specifying a slower V32 modulation 
       see  [http://linmodems.technion.ac.il/archive-fifth/msg00137.html](http://linmodems.technion.ac.il/archive-fifth/msg00137.html)


Does the pre-compiled SLMODEMD.gcc4 retain this compatability, or do I need to compile 2.9.9x?

---

### Post by jimcser on 2005-11-28
I got it working after all-- I was using wvdial, and probably just messed up the config file somehow.  I certainly learned a lot more about linux, and I can verify for other users that the SLMODEMD.gcc4 driver suggested by scanModem indeed works with this chipset/modem combo.

---

