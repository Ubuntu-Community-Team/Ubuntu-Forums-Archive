---
title: "no sound in saa7134 tv card"
date: 2005-05-02
forum: Hardware &amp; Laptops
---

### Post by abandoned_hussam on 2005-05-02
I have a saa7134 tv card.
I loaded the driver using: modeprobe saa7134 card=11 tuner=2
The video works but without sound. Linein volume is set correctly and all sound cables are set up correctly. The used to work in fedora and it still works in WindowsXP.
Even if I hookup the tv card directly to the speakers, no sound comes out.
any idea?

---

### Post by abandoned_hussam on 2005-05-03
[QUOTE=ht990332]I have a saa7134 tv card.
I loaded the driver using: modeprobe saa7134 card=11 tuner=2
The video works but without sound. Linein volume is set correctly and all sound cables are set up correctly. The used to work in fedora and it still works in WindowsXP.
Even if I hookup the tv card directly to the speakers, no sound comes out.
any idea?[/QUOTE]
 anybody can help?

---

### Post by emperor on 2005-05-03
My saa1733 based Asus TV card was loaded automaticly by the kernel, no manual modprobe was required. The sound from my card is connected to line1 internally, so. as a result, TVtime must be directed to use line1 for sound. There are 2 ways to do this,  via the "tvtime-configure" utility once or you can pass the commandline option: --mixer=/dev/mixer:line1 when you start tvtime. I still have a problem with video in that the CPU and X server are not allocating enough time to the video service; even when running as root and/or setting the rtc. This is a new problem that happened on March 23, 2005 with update to Hoary. I submitted a bug report, but Ubuntu refused to look into the problem since they do not support tvtime. xawtv has the same video problem too! The problem could be the kernel or X server, not sure which! Let me know if you have the same problem.

---

### Post by abandoned_hussam on 2005-05-04
[QUOTE=emperor]My saa1733 based Asus TV card was loaded automaticly by the kernel, no manual modprobe was required. The sound from my card is connected to line1 internally, so. as a result, TVtime must be directed to use line1 for sound. There are 2 ways to do this,  via the "tvtime-configure" utility once or you can pass the commandline option: --mixer=/dev/mixer:line1 when you start tvtime. I still have a problem with video in that the CPU and X server are not allocating enough time to the video service; even when running as root and/or setting the rtc. This is a new problem that happened on March 23, 2005 with update to Hoary. I submitted a bug report, but Ubuntu refused to look into the problem since they do not support tvtime. xawtv has the same video problem too! The problem could be the kernel or X server, not sure which! Let me know if you have the same problem.[/QUOTE]
 I don't get video error nor are there performance issues with tvtime.
But even if I run tvtime --mixer=/dev/mixer:line1 , I still get no sound.
I even tried connecting the tv card directly to the speakers but that didn't help either.

---

### Post by emperor on 2005-05-04
run  "alsamixer" from a terminal and see if turning up or on one of the sliders helps!

---

### Post by abandoned_hussam on 2005-05-05
[QUOTE=emperor]run  "alsamixer" from a terminal and see if turning up or on one of the sliders helps![/QUOTE]
 they are on and up. Even if I connect the tv card directly to the speakers, there is no sound , so it is probably and issue with the saa7134 kernel module. any other ideas?

---

### Post by emperor on 2005-05-06
Is your card listed in here?  [http://www.bttv-gallery.de/](http://www.bttv-gallery.de/)

Also, take a look in the source code for your card:
[http://dl.bytesex.org/releases/video4linux/](http://dl.bytesex.org/releases/video4linux/)

I recently tried to compile the saa1734 kernel module for Hoary but it fails with an error.  The maintainer did not respond to my e-mail concerning the problem. The actual code used to make the kernel module packaged with the kernel may have additional patches that are not reflected in the source here.

What version of Fedora were you using when the card worked in Linux?
My saa1733 card works fine in Fedora Core 2.

The saa1734 module should load automaticly in Hoary without the need for modprobe. Are you sure the parameters you are passing to the saa1734 module are correct?

---

### Post by abandoned_hussam on 2005-05-07
[QUOTE=emperor]Is your card listed in here?  [http://www.bttv-gallery.de/](http://www.bttv-gallery.de/)

Also, take a look in the source code for your card:
[http://dl.bytesex.org/releases/video4linux/](http://dl.bytesex.org/releases/video4linux/)

I recently tried to compile the saa1734 kernel module for Hoary but it fails with an error.  The maintainer did not respond to my e-mail concerning the problem. The actual code used to make the kernel module packaged with the kernel may have additional patches that are not reflected in the source here.

What version of Fedora were you using when the card worked in Linux?
My saa1733 card works fine in Fedora Core 2.

The saa1734 module should load automaticly in Hoary without the need for modprobe. Are you sure the parameters you are passing to the saa1734 module are correct?[/QUOTE]
 It was fedora core 3, but it previously worked on fedora core 1 and 2. 
I'm using the same parameters I used on fedora
modprobe saa7134 card=11 tuner=2

this is the manufacturer's site [http://www.kworld.com.tw/en/](http://www.kworld.com.tw/en/)

---

### Post by emperor on 2005-05-07
I haven't looked in the source yet, but many of the saa1734 cards require that tda7432, tda9875, tda9887, or tda9840 be loaded as well. Check with lsmod and see if a tda???? is loaded. The tuner. tda???? and the saa1734 are all supporting modules for v4l support.

The v4l modules are on your machine in (for example): :/lib/modules/2.6.10-5-k7/kernel/drivers/media/video

---

### Post by abandoned_hussam on 2005-05-07
[QUOTE=emperor]I haven't looked in the source yet, but many of the saa1734 cards require that tda7432, tda9875, tda9887, or tda9840 be loaded as well. Check with lsmod and see if a tda???? is loaded. The tuner. tda???? and the saa1734 are all supporting modules for v4l support.

The v4l modules are on your machine in (for example): :/lib/modules/2.6.10-5-k7/kernel/drivers/media/video[/QUOTE]
 tda9887 is loaded.
could it some kind of debian bug that made it into the ubuntu kernel?

---

### Post by emperor on 2005-05-09
There were some patches applied to the saa1734 modules directly at kernel.org that are not reflected in the source code. Your problem and my problem with video performance may both be side effects of this. However, I would still take a look at the saa1734 source code and search it for your particular card.

---

