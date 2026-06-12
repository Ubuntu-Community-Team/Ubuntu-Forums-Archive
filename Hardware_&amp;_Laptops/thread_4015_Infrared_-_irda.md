---
title: "Infrared - irda"
date: 2004-11-11
forum: Hardware &amp; Laptops
---

### Post by steffen on 2004-11-11
How do I enable infrared/irda on my laptop? It seems it wasn't auto-detected when I first installed Ubuntu, and since my USB ports are broken, I need irda to synchronize my Palm.

Anyone know how to link the Palm to irda port to sync?

---

### Post by njreid on 2004-11-11
What kind of laptop are you using?

There are some tricks involved in getting IrDA to work, especially on HP & Toshiba laptops - have a look at 

[http://irda.sourceforge.net/smcinit/](http://irda.sourceforge.net/smcinit/)

for more details.

From the site:

The IrDA subsystem of the SuperIO chip is supported by the smc-ircc Linux kernel module. Unfortunately the BIOS neither configurates the SuperIO chip IrDA subsystem (SIR port, FIR port, dma, irq, IrDA mode, power) nor sets the PCI-ISA bridge to decode any usable port. Linux kernel is thus prevented to detect the second UART making impossible to use it in SIR mode. For the same reason, the FIR mode smc-ircc is able to detect the SuperIO chip but, once found the IrDA subsystem unconfigured, fails to install.

Good luck - hopefully this will be fixed in later kernel revs.

---

### Post by steffen on 2004-11-11
The infrared is actually usually autodetected - with Suse 9.1. it was. And it's a Fujitsu Siemens Amilo M, which is not on the list of laptops that has to be tweaked.

I actually think my problem is quite un-techy, it's just me who is not able to set up anything that doesn't auto-detect...  :-| 

It might actually be on my system as it is, but I'm just not able to find/activate it...?

---

### Post by steffen on 2004-11-14
Noone knows how to activate IR, or link IR to pilot?

---

### Post by TravisNewman on 2004-11-14
[QUOTE=steffen]Noone knows how to activate IR, or link IR to pilot?[/QUOTE]
 [http://howtos.linuxbroker.com/PalmOS-HOWTO.html](http://howtos.linuxbroker.com/PalmOS-HOWTO.html)

there's a section on IR there, this might help

---

### Post by vikram sai balaji on 2006-08-30
There is a similar problem in my laptop(hp compaq nc 6230) also. the ir device was detected by Fedora Core 5 but in kubuntu it did not. my lsmod says that irda_sir device is present but my laptop configurartion says that the ir  device is a Fast IR (irda_fir). i dont know how to proceed furthur.
will try the smscinit and let u know.
thanks
vikram

---

### Post by bluntz on 2007-08-10
Wow no posts in over a year...
anywho, I have a toshiba 1805-s274 and an IBM 560E that needs IR support.
Unfortunately, support is very thin in this area under ANY distro.
However, I think that the newer 2.6.2 kernel in feisty detects the IR correctly.
Being a edgy user (newbie at that) the kernel seems to detect but not set the irq correctly.
modprobe toshoboe

modprobe donaoboe

inserts the module it would seem,but same error occurs, find my relevent dmesg below.

[17181382.536000] setup_irq: irq handler mismatch
[17181382.536000]  <c0149767> setup_irq+0x127/0x140  <cf9dc2c0> smsc_ircc_interrupt+0x0/0x830 [smsc_ircc2]
[17181382.536000]  <c0149819> request_irq+0x99/0xb0  <cf9dbbef> smsc_ircc_net_open+0x4f/0x1c0 [smsc_ircc2]
[17181382.536000]  <c0272481> dev_open+0x31/0x70  <c0270e6c> dev_change_flags+0xfc/0x130
[17181382.536000]  <c02668b0> sock_ioctl+0x0/0x220  <c0272723> dev_ioctl+0x263/0x380
[17181382.536000]  <c0158ed1> __handle_mm_fault+0x211/0x900  <c02669c4> sock_ioctl+0x114/0x220
[17181382.540000]  <c02668b0> sock_ioctl+0x0/0x220  <c017d4bb> do_ioctl+0x2b/0x90
[17181382.540000]  <c017d57c> vfs_ioctl+0x5c/0x2b0  <c017d842> sys_ioctl+0x72/0x90
[17181382.540000]  <c0102fbb> sysenter_past_esp+0x54/0x79 
[17181382.540000] smsc_ircc_net_open(), unable to allocate irq=7

Any help would be appreciated.

---

### Post by Offoffoff on 2007-10-06
In Gutsy my system hangs when I have installed irda-utils. I use HP Comaq nc4000...
How to configure right my IrDA port in my model of notebook?

---

### Post by bluntz on 2007-10-11
This fellow seems to have success with lirc ,maybe helpful?
System is a Toshiba 1805-s274 laptop
My palms dead now so I gave up on it. Though I did manage to get it to run linux natively.
Tungsten E



Date: Thu, 10 Jul 2003
From: Chris (hiszpans at ugcs dot caltech dot edu)

Hi Pete,

I read your tutorial about the Toshiba Satellite 1805-S274 on linux laptops.

Since I am too lazy to write my own page and feel that yours is good in all
other areas, I would appreciate it if you could add experiences with IrDA to
your Epilogue.

I did manage to get IrDA to work. I was able to receive packets from my
Seimens S40 cellphone using IrLAN. I was also able to use the remote control
from walmart (One for All 4060) to control xmms.

The trick is that the IrDA port is not powered on by the BIOS. It needs to be
manually powered on. A program to do this is available at
[http://www.csai.unipa.it/peri/toshsat1800-irdasetup/](http://www.csai.unipa.it/peri/toshsat1800-irdasetup/)

Using that page, I was able to get IrLAN to work with my cellphone.

Then, using the LIRC Project, I was able to get the tv remote to work to a good
extend (I still have to hold down the button on the remote for as long as 10
seconds sometimes for the signal to register. I compiled the lirc-sir module
using lirc-0.6.6. Then I used the Philips VCR5 remote file and set my
One-for-All 4640 to VCR mode, code 1181 (Philips). Apparently the toshsat1800
program is created for the smc-ircc module because I had a difficult time to
get it to register on start up. Finally, I came up with this script that I
put in /etc/rc.d/rc.irda in Slackware 9:

--- cut here ---
#!/bin/sh
# Start/stop infrared port

irda_start() {
  echo "Starting IrDA..."
  /sbin/setserial /dev/ttyS1 uart none port 0x2e8
  /usr/sbin/irsetup --sirbase=0x2e8 --firbase=0x130 --irq=7 --dma=3 --device=0x2e

  # this is needed -- don't know why
  /sbin/modprobe smc-ircc
  sleep 3
  /usr/sbin/irattach irda0 -s
  sleep 3
  ifconfig irda0 down
  /sbin/rmmod smc-ircc
  /sbin/rmmod irport
  /sbin/rmmod irda

  /usr/sbin/irattach /dev/lirc -s
}

irda_stop() {
  echo "Stopping IrDA..."
  /sbin/rmmod lirc_sir
}

case "$1" in
'start')
  irda_start
  ;;
'stop')
  irda_stop
  ;;
*)
  echo "usage $0 start|stop"
esac

--- cut here ---

I added /etc/rc.d/rc.irda start to /etc/rc.d/rc.M as well.

Feel free to email me or have others email me with questions about this, but I
ask that if you publish my email address, please either display it as
'hiszpans at ugcs dot caltech dot edu' or as a small gif so that I don't
receive spam.

Thank you for your tutorial.

Chris

---

### Post by tdn on 2007-11-20
I also have an IrDA related problem.
I have an IBM Thinkpad T42, and I don't know how to enable the IrDA port.
I have tried the hints in this thread, but that did not help me.

When I type: sudo modprobe lirc_sir
I get: FATAL: Module lirc_sir not found.

I get the same "module not found" for all the modules I have tried.

---

### Post by bliffle on 2007-11-23
I haven't been able to get IR running on my T40. The modem is enabled, but when Itry installing IR I get a failure trying to install 'irda-utils'.

I tried uninstalling 'irda-utils' and then reinstalling, but got a problem with the postinstall script:

```
john@JHT40UUU:~$ sudo apt-get install irda-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgnucrypto-java gappletviewer-4.1 libkbanking1 libcairo-jni
  libgwenhywfar38 libflac++5c2 liboggflac3 libpostproc0d libqbanking4
  libktoblzcheck1c2a libgtk-jni libavformat0d libaqbanking16 libcairo-java
  libglib-jni cdw libbcprov-java libglib-java gcjwebplugin-4.1 libavcodec0d
  libmal1 libgtk-java libgwenhywfar-data libaqbanking-data linux-source-2.6.20
Use 'apt-get autoremove' to remove them.
Suggested packages:
  libgsmme1c102 liblinc1 obexftp
The following NEW packages will be installed:
  irda-utils
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/99.7kB of archives.
After unpacking 336kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package irda-utils.
(Reading database ... 182048 files and directories currently installed.)
Unpacking irda-utils (from .../irda-utils_0.9.18-6ubuntu1_i386.deb) ...
Setting up irda-utils (0.9.18-6ubuntu1) ...
udev active, devices will be created in /dev/.static/dev/
udev active, devices will be created in /dev/.static/dev/
Starting IrDA service: irattachUsage: irattach <dev> [-d dongle] [-s] [-b] [-v] [-h]
       <dev> is tty name, device name or module name
Dongles supported :
        esi
        tekram
        actisys
        actisys+
        girbil
        litelink
        airport
        old_belkin
        ep7211
        mcp2120
        act200l
        ma600
        toim3232

invoke-rc.d: initscript irda-utils, action "start" failed.
dpkg: error processing irda-utils (--configure):
 subprocess post-installation script returned error exit status 255
Errors were encountered while processing:
 irda-utils
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

