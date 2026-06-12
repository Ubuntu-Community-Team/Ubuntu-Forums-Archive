---
title: "How to install Ubuntu on geforce+nforce chipset"
date: 2006-02-21
forum: Hardware &amp; Laptops
---

### Post by chiesaitaly on 2006-02-21
(hi,i am from china, my english level is just so so.)

i use tforce6100,which uses geforce+nforce chipset:

video card is GeForce&#8482; 6100,
sound card is Realtek® ALC655,
network card is Realtek® RTL8210B/RTL8201BL.

i install ubuntu 5.10.

1.install ubuntu

2.install gcc-3.4 without internet
please see [http://ubuntuforums.org/archive/index.php/t-79896.html](http://ubuntuforums.org/archive/index.php/t-79896.html)

3.install network and sound driver

go [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) to download nforce driver

sudo apt-cdrom add(add cdrom to apt source.list&#65292;remember to insert ubuntu install cdrom to the cdrom driver)

sudo apt-get update

sudo apt-get install build-essential gcc 

sudo apt-get install linux-image-386 linux-headers-386(the default kernel is 386)

cd &#8220;directory where you have the nvidia installer&#8221;
su
CC=gcc-3.4
export CC
exit
CC=gcc-3.4
export CC


sudo sh NForce-Linux-x86-XXXXX.run&#65288;run the driver we download from nvidia website to install network and sound driver)

modify /etc/modprobe.d/aliases( you can create a new file in that directory too),add&#65306;

alias eth0 nvnet
alias forcedeth off 

(If your configuration file already contains an entry for the forcedeth driver (an open-source network driver that supports the nForce network controller), that entry needs to be commented out with a # or removed:
)

how to config sound card? please see [http://download.nvidia.com/XFree86/nforce/1.0-0310/ReleaseNotes.html#Configuration](http://download.nvidia.com/XFree86/nforce/1.0-0310/ReleaseNotes.html#Configuration)

restart your machine.i find the network driver work,but the sound card don't work.

4.install video card driver

please see [http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074) (i use method 2)

the end:

i got my network and video card work,but the sound card failed.

---

### Post by kennedymat on 2006-02-23
I followed the same instructions.

My video is working great (THANKS!), but the OS is not recognizing any soundcard (I did update the configuration files and documented in the file that came with the installer).

Also, I don't THINK my network card is using the nForce driver.  How can I be sure it isn't using forcedeth?

Thanks in advance.

---

### Post by chiesaitaly on 2006-02-27
run lsmod ,u will see the mod loaded and find if forcedeth is in the list.

my sound card fail to work too.:)

---

### Post by kennedymat on 2006-03-02
Thank you for all of the help.  I took the discussion to the nVidia board and here is the link:

[http://www.nvnews.net/vbulletin/showthread.php?t=57791&page=23](http://www.nvnews.net/vbulletin/showthread.php?t=57791&page=23)


I basically found out that you may need to jump through some serious hoops to get sound:

Hi Kennedy,

>From the report log you sent -

/proc/pci
Bus 0, device 16, function 1:
Class 0403: nVidia Corporation MCP51 High Definition Audio (rev
162).
IRQ 10.
Master Capable. No bursts. Min Gnt=2.Max Lat=5.
Non-prefetchable 32 bit memory at 0xf5100000 [0xf5103fff].


Scanning kernel log file for nvsound messages:
Feb 22 17:56:50 localhost kernel: [ 753.982904] Nvsound: Nvidia Audio
Init Module, 17:56:47 Feb 22 2006 version 1.0-7


It looks like you are using HD azalia controller.
nvsound driver that comes with the NFORCE package doesnot support this.

The support for this added from 2.6.15 Kernel version.

-vinod

---

### Post by m.musashi on 2006-03-05
I'm using Dapper flight 4. Do I need to change any of the steps you outlined? I tried just as you have it but got this error:
```
  gcc-version-check failed:

  ./nvnet/conftest.sh: line 9: gcc-3.4: command not found
  Could not compile gcc-version-check.c

  If you know what you are doing and want to ignore the gcc version check,
  select "No" to continue installation.  Otherwise, select "Yes" to abort
  installation, set the CC environment variable to the name of the compiler
  used to compile your kernel, and restart installation.  Abort now?
```
Any suggestions?

---

### Post by chiesaitaly on 2006-03-07
[QUOTE=m.musashi]I'm using Dapper flight 4. Do I need to change any of the steps you outlined? I tried just as you have it but got this error:
```
  gcc-version-check failed:

  ./nvnet/conftest.sh: line 9: gcc-3.4: command not found
  Could not compile gcc-version-check.c

  If you know what you are doing and want to ignore the gcc version check,
  select "No" to continue installation.  Otherwise, select "Yes" to abort
  installation, set the CC environment variable to the name of the compiler
  used to compile your kernel, and restart installation.  Abort now?
```
Any suggestions?[/QUOTE]


i have no experience at using Dapper flight 4.

you must check if gcc-3.4 is installed and the CC env var is seted to gcc-3.4.

remember to use:

su
CC=gcc-3.4
export CC
exit
CC=gcc-3.4
export CC

these steps are used to set the CC env var to gcc-3.4.

---

### Post by Ptero-4 on 2006-03-07
Hi chiesaitaly. Great howto you got there. But you shouldn't need to add the ubuntu install cdrom through apt-cdrom. IIRC, that step is done automatically during the installation.

---

