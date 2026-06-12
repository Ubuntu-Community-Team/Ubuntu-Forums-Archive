---
title: "Crash, semi reboot, but not a complete restart"
date: 2008-10-18
forum: General Help
---

### Post by citro_cell on 2008-10-18
(SOLVED - see my last post) My ubuntu has been "crashing" recently when I seem to be overloading the system with input (like scrolling too fast down a page or opening too many windows at once).  When this happens, the screen goes blank and then pops up a gnome login window.  It is not a complete reboot of my computer, i think, because it all loads so quickly (maybe 10 seconds).  I have been reading other people's issues with crashes and someone suggested that the RAM could be bad, but I ran the mem86 test with 0 errors.  Thank you in advance to anyone that can provide some input.  Also, I thought it was related to firefox, or possibly flash, but the last time it crashed I just opened a pdf file and scrolled down quickly (with no other programs running).  Here is the sys log for 3 crashes in a row:

syslogd 1.5.0#1ubuntu1: restart.
kernel: [  547.380858] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
kernel: [  547.380885] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
kernel: [  547.380911] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
pulseaudio[7825]: pid.c: Stale PID file, overwriting.
pulseaudio[7825]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 48000 Hz.
pulseaudio[7825]: alsa-util.c: Cannot find fallback mixer control "Mic".
kernel: [  798.395222] audit(1224368499.841:3): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=8401 profile="/usr/sbin/cupsd" namespace="default"
kernel: [  955.418372] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
kernel: [  955.418399] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
kernel: [  955.418425] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
pulseaudio[8873]: pid.c: Stale PID file, overwriting.
pulseaudio[8873]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 48000 Hz.
pulseaudio[8873]: alsa-util.c: Cannot find fallback mixer control "Mic".
kernel: [ 1000.733650] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
kernel: [ 1000.733678] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
kernel: [ 1000.733704] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
pulseaudio[9255]: pid.c: Stale PID file, overwriting.
pulseaudio[9255]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 48000 Hz.
pulseaudio[9255]: alsa-util.c: Cannot find fallback mixer control "Mic".

---

### Post by Sef on 2008-10-18
> I have been reading other people's issues with crashes and someone suggested that the RAM could be bad, but I ran the mem86 test with 0 errors.

How long did you run this test?  It needs to run about 8 hours, so it can be most accurate.  However, even a 0 does not mean that the ram is necessarily good.

---

### Post by citro_cell on 2008-10-18
Thanks for the quick reply - I ran the test for about 65 hours!!  I thought it took that long to complete but then I read somewhere that it is a never-ending test.  So I stopped it. I believe it ran 76 complete times.

---

### Post by citro_cell on 2008-10-22
I recently reinstalled Ubuntu 8.04.1 and within a few hours I was experiencing crashes, freezes, and black screens.  However I did some (not extensive) testing by running Ubuntu from the cd and experienced no such problems.  I am considering reinstalling windows to see if this is a hardware or software problem.  Any suggestions would be greatly appreciated.  Another possibly related issue - after a clean reinstall I went first to system-administration-login window.  The password prompt popped up and I enter mine, then the login window popped up for 1/2 second before disappearing.  Thanks to any/all who can help!!

---

### Post by citro_cell on 2008-10-22
Bumpdate - Just installed windows again, multitasking as much as possible using flash etc. with no issues.  I am wondering if it has to do with the nvidia driver for Ubuntu.

Thanks to anyone who can help!!

---

### Post by citro_cell on 2008-10-24
Ok this is the last update/bump.  I had my first crash in windows.  Same exact situation that appears to be happening under Ubuntu - so I must assume it is a hardware problem.  I took apart the entire computer about a month ago and I believe the problems must have started after that.  My question is could this be related to the graphics card or is this a memory issue - or something entirely different?  Also I have noticed a slight correlation with scrolling through large documents and crashing.  Could a graphics card or other peripheral piece of hardware cause a restart?  Is scrolling especially taxing on the computer or could it even have somthing to do with the mouse?  I suppose I will begin the process of elimination - but any insights would be greatly appreciated.  Thanks!!!

---

### Post by nitrousoxide82 on 2008-10-24
From the looks of it I'd say it might be a hardware problem (as Windows does crash too). Scrolling a long list-control or the "smooth-scroll" of some Web pages can indeed raise CPU usage.

If Memtest86 reported good after so many hours running, then you might want to check the thermal status of your machine. Maybe the CPU and/or video card is overheating. To check that, you can get a monitoring utility on Windows (there are some out there, and maybe your motherboard shipped with a CD-ROM containing one), or a sensors application on Linux (lm-sensors and a client, there's ksensors for KDE and a panel applet for GNOME). 

Not all video cards have thermal sensors, but all the more recent NVIDIA (GeForce 6xxx and above) and ATI Radeons do, check the video driver control panel. Typically, temperatures above 70 degrees C for CPU or around 90 degrees C for video cards are bad signs. 

Here are some tips in case your machine is overheating:
- Clean all the fans. Dust can lower the spinning speed of the fans, and can also block air flow to the heatsink, resulting in higher temperatures.
- Check for ventilation of your case and the area where it's installed.
- Change the thermal compound between the cooler and the CPU. Remove the cooler, remove the old compound with isopropyl alcohol (I think some call it "rubbing alcohol" in English, it's not my native language so I'm sorry. Ask in your local electronics store - usually places where you can get thermal compound carry it too), apply a thin layer of compound covering the CPU, then put the cooler back.
- If none of this solves your problem, get a better cooler. This usually happens with Pentium D machines - it heats up a lot, and the stock Intel cooler can't take all that heat away from the CPU.

If you're not having thermal problems, I would suggest checking your power supply. Check the voltages supplied, and the change on them when you put the system under demand. If the voltage drops are large, especially in the +12V line (about 0,4-0,5 V) your power supply may not be giving enough juice to your hardware.

---

### Post by citro_cell on 2008-10-24
Hey thanks so much for the reply.  Under Ubuntu I was running a constant temperature check and for the most part all 3 temps that I could find were under 50C.  Last month I cleaned all internal components so I don't think heat is building up at the heatsinks (although they don't look very fancy).  However it is a sony vaio pcv-rx650 and I have heard on other sites that the power supplies are woefully inadequate.  I never had problems in the past but maybe the power supply is the problem - I will look into the voltage changes.  Thanks again!!

---

### Post by citro_cell on 2008-11-06
Thanks so much for your help - I got a new power supply and it is working flawlessly in both Windows and Ubuntu.  By the way I just installed 8.10 and I really like it.

---

### Post by citro_cell on 2008-11-07
WOW - I almost feel jinxed!  So Yesterday I posted that I haven't had any untoward problems with shut downs etc.  And today I started by experiencing firefox crashes (3) and then moments ago I got another semi-reboot (edit - I have had 3 reboots in 10 minutes now - all while trying to watch a youtube video) where the screen went black - it looked like it loaded some of the init (?) menu and then it went to the login screen.  It all happened very quickly so it definitely wasn't a complete reboot.  Weird - any thoughts???  Thank you to anyone who can help!!

---

### Post by citro_cell on 2009-01-16
SOLVED - Final thoughts on this problem: I do believe that sony's power supply was too small for any upgrades on this computer so I am happy that I got a new power supply.  Although memtest did not show any errors after many hours of tests - it was a problem with the memory (which had been running fine until I took everything out to clean the entire case.)  So I bought 1 gig of memory to test and it has been running like a scalded dog ever since.  THanks for your help SEF and NO82.  Hope this helps others with similar problems.

---

### Post by RJARRRPCGP on 2009-01-16
You may have installed the wrong video driver version, even when the symptoms don't occur in 2D. 

Symptoms to look for are a crash when you launch a 3D application, and you may see the keyboard lights blinking after launching a 3D application.

---

