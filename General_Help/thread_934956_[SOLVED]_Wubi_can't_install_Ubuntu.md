---
title: "[SOLVED] Wubi can't install Ubuntu"
date: 2008-10-01
forum: General Help
---

### Post by frost151n on 2008-10-01
Hello,

I try to install Ubuntu 8.04.1 using Wubi 8.04.1

I have the 32bit ISO and used this method to install successfully on my home comp. (assembled)

However it won't work on my laptop. (with proxy net server)

It tries to connect to releases.ubuntu.com and cdimage.ubuntu.com then says 'Could not retrieve some essential files'

Why does it try to download stuff wen i have provided it with the ISO???

---

### Post by gnuvistawouldbecool on 2008-10-01
it could be that it is trying to do it 64 bit, if your laptop is 64 bit.  if you change the parameter used to open Wubi, you should be able to make it do the 32 bit install.  To quote the wiki:

> Can I force Wubi to download and install a 32 bit version of Ubuntu?

Yes either pre-download the appropriate 32 bit ISO manually and place it in the same folder as Wubi.exe or start Wubi with the "--32bit" argument.


Also, if you mount the iso with something like Daemon tools (don't know of a free software equivalent) and then auto run the disc, you should be able to do it that way.

---

### Post by ago on 2008-10-02
There is a log in your user temp folder that will have an explanation. Usually the reason is that the ISO is wrong type/version or is corrupted

---

### Post by frost151n on 2008-10-14
I downloaded the ISO again, from a different location. Placed it in the same folder as Wubi yet I am having the same problem.
I thinking about waiting for the 8.10, see if that'll install.

---

### Post by Sketches on 2008-10-27
> **frost151n said:**
> Hello,

I try to install Ubuntu 8.04.1 using Wubi 8.04.1

I have the 32bit ISO and used this method to install successfully on my home comp. (assembled)

However it won't work on my laptop. (with proxy net server)

It tries to connect to releases.ubuntu.com and cdimage.ubuntu.com then says 'Could not retrieve some essential files'

Why does it try to download stuff wen i have provided it with the ISO???
i have the exact same problem and tried an early one of 8.10 but no such luck...

Anyway any suggestions in english?

---

### Post by ago on 2008-10-27
if you have proxy server, provide the ISO yourself, and run wubi with the argument --skipmd5check, or alternatively disconnect the computer from the network momentarily while the installer is in use (windows side only)

---

### Post by frost151n on 2008-10-28
I tried it with no active net connection. No luck.
can you give me a lil more detail about the argument thing? please.

---

### Post by ago on 2008-10-28
you need to have the right ISO (and only 1 iso) as well as wubi.exe in the same folder

In the dos command prompt go to the dir conatining wubi and run:

wubi.exe --skipmd5check

---

### Post by riahc3 on 2008-10-28
Why don't you let Wubi download it and then install it?
Or use the wubi.exe inside the CD's ISO?

---

### Post by frost151n on 2008-10-29
i'll try the command prompt thing.
India has a slow net connection, it'll take me 7.5hrs to dawnload it.
the cd image has the 505rev, which causes problems.

---

### Post by ago on 2008-10-29
rev505 mostly create issues when uninstalling, otherwise it's ok (see wubiguide for uninstaller instructions).

Also note that there is usually a log in your user temp folder (type %temp% in windows explorer).

Finally if you download from scratch, go for 8.10 it is the final release in practice.

---

### Post by frost151n on 2008-10-30
the command prompt thing didn't work.
8.10 should release today. I'll let y'all know if that goes better!
umm... do you want me to attach the temp file??? coz i can't make heads or tails of that!!!!
i forgot to mention, when i did it in the command prompt, it didn't try to connect to anything, it just said it failed to download some essential files.

---

### Post by ago on 2008-10-30
It is better if you use 8.10 now, since the files are already the same as the final. If you wait the servers are going to be very busy...

---

### Post by frost151n on 2008-11-01
Imagine my dismay, when i downloaded the 32bit iso installed it successfully with wubi then rebooted in to ubuntu.
the progress bar almost reaches the end, then the screen goes blank with the msg 'no signal'.
Rebooting and re-installation didn't work.

System specs: AMD 64 3500+, RAM 2GB, ATI HD 3450 graphic card, asus mother board, its a 2 yr old board so i don't know the model no.

---

### Post by ago on 2008-11-03
This is likely due to an incompatible video driver. Press esc at boot and select safe graphic mode. You will have to uninstall and reinstall first.

---

### Post by frost151n on 2008-11-03
Thnx ago, it worked. 
Now im off to find games.

---

### Post by jrsmk1 on 2009-03-03
I am a complete Linux novice but come from a CP/M DOS and Windows background.
I downloaded Wubi and what I thought was a suitable ISO, followed all of the above advice and decided that wubi was not responding to the --skipmd5check command.
However, in the %TEMP% folder (to get there goto Start>Run>*(type)*%TEMP%*(press enter)* I found the wubi.log and noticed that WUBI had commented that the ISO version number was not the same as the WUBI version number.
"different version 8.10 != 8.04.1"
If you read the guide @ [http://wubi-installer.org/faq.php ]("http://wubi-installer.org/faq.php") and go to the para "Can I use an existing ISO/CD" it states that WUBI 8.10 must have the corresponding 8.10 distro. There is a link there to download it.
Once I had got these basics sorted it all worked like a dream. 
Now to sort out why UBUNTU prints a test printer page but otherwise cannot see the printer.
jrsmk1

---

### Post by saul11 on 2009-03-07
I'm having troubles booting into Ubuntu 8.10 whcih I installed with Wubi. After the installation completed I'm left with a black screen with a cursor blinking top left and my laptop doen't react anymore. When I reboot I end up in a shell. I posted my problem at [http://ubuntuforums.org/showthread.php?t=1087722](http://ubuntuforums.org/showthread.php?t=1087722)

I have also an ATI video card an have read that they can cause problems, so I tried pressing esc at boot and select safe graphic mode, but that option isn't there. There a recovery thing and normal boot (giving the shell again), but I don't see the safe graphics mode.

What can I do?

---

