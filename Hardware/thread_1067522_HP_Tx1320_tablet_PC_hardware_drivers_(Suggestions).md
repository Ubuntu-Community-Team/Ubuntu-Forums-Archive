---
title: "HP Tx1320 tablet PC hardware drivers? (Suggestions)"
date: 2009-02-11
forum: Hardware
---

### Post by Scott Howard on 2009-02-11
I decided to give Ubuntu a second chance, I got really fed up with Vista. Everything seems to be working for the most part except a few things.

**My Laptop:**[http://h10025.www1.hp.com/ewfrf/wc/product?lc=en&dlc=en&cc=us&lang=en&product=3548576#]("http://h10025.www1.hp.com/ewfrf/wc/product?lc=en&dlc=en&cc=us&lang=en&product=3548576#")

[IMG]http://h10032.www1.hp.com/ctg/Images/c00777650.jpg[/IMG]

**I need help with a few things:**

- Tablet PC function? (screen rotate button)?

- Media Remote?

- Webcam? **(Solved)**

- Built-in fingerprint scanner?

- ActiveSync or substitute to sync my Windows Mobile Treo700wx?

--------------------------------------------------------

Any help would be appreciated!

Thanks,
Scott Howard

---

### Post by Favux on 2009-02-11
Hi Scott Howard,

To get tablet function you need to install evtouch.  It's in Synaptic Package Manager and configure xorg.conf.

There are several great threads.  Search TX1000.  A couple are:

[http://ubuntuforums.org/showthread.php?t=1040872&highlight=TX1000]("http://ubuntuforums.org/showthread.php?t=1040872&highlight=TX1000")

[http://ubuntuforums.org/showthread.php?t=442483&highlight=TX1000]("http://ubuntuforums.org/showthread.php?t=442483&highlight=TX1000")

Also some help on rotation can be found:

[http://ubuntuforums.org/showthread.php?p=6274392#post6274392]("http://ubuntuforums.org/showthread.php?p=6274392#post6274392")

I hope this helps.

---

### Post by Scott Howard on 2009-02-12
Thanks, I assume all those drivers and stuff work on any of the "tx" series laptops?


Can anyone else shed some light on any of my other issues/questions?

---

### Post by Favux on 2009-02-12
Hi Scott,

No the TX2000, TX2500, and TX2z use the linuxwacom drivers.

The threads might have the answers to some of your other hardware questions.

---

### Post by Scott Howard on 2009-02-12
- ActiveSync or substitute to sync my Windows Mobile Treo700wx?

---

### Post by Favux on 2009-02-12
My suggestion would be to start a new thread in the appropriate forum with:
> ActiveSync or substitute to sync my Windows Mobile Treo700wx?
as the title.

---

### Post by cta16 on 2009-02-12
For the Webcam, install something called Cheese. For the touchscreen,  I hear many people have success with evtouch but it didn't work for me. So I used Egalax's Touchkit which works perfect. As for the fingerprint, I have never tried but there is a beta program called Fprint that might do the job.

---

### Post by Scott Howard on 2009-02-12
I installed FPrint and enrolled my finger prints. Now how do I make that work as a log in when I turn on the laptop?

Also I got evtouch installed and calibrated my screen, it was picking up my input. How do i activate it? It does seem to do anything unless i'm on the calibration screen. Is there somewhere where it has to be turned on?

Thanks..

---

### Post by Favux on 2009-02-12
Hi Scott Howard,

I'm not sure, that's why I recommended reading through a few threads.  From the first thread I referenced:
> Touchscreen: It's an eGalax. Please, do yourself a favor and if you are using Ubuntu Intrepid Ibex, do not follow those eGalax howtos, do not install proprietary drivers, do not configure your xorg.conf, let the Ibex do all the work. Simply issue this:

$ sudo apt-get install xserver-xorg-input-evtouch

and restart X. If you don't have luck, you'll have an uncalibrated touchscreen; if you have luck, you'll have an autocalibrated touchscreen, if you don't have luck, run ev_calibrate and FOLLOW CAREFULLY THE INSTRUCTIONS.

Pay attention: the touchscreen behaviour when the screen is rotated is BUGGY. The upcoming evtouch 0.8.8 will make, at last, an usable rotated screen.

But this is one users opinion.  You might want to check a few of the other threads.  As you saw cta16 is using the proprietary Egalax drivers with success.

---

### Post by Scott Howard on 2009-02-12
Touchscreen works now! I just need to install the screen rotate function.

I'm still confused on how to use my registered fingerprints as a login now?

---

### Post by Favux on 2009-02-12
Hi Scott Howard,

Good deal.  To help others out you might want to explain what you  did to get touchscreen working.

Fprint is a tricky issue, apparently because some of the fingerprint reader manufacturers haven't been very helpful.

I believe master_kernel has the best fprint thread.  That may address your issue.

---

### Post by antokhio on 2009-02-13
Hello guys, i have really strange issue with my tx1320, the model dosn't have a touch-screen, but i'm expiriencing some kind of issues with video card or something like this... The problem is that if set screen to turn off i won't get in a normal condition i have already recorded a three or 4 types of different halucinations with different video cards and nForce drivers. After hunting down this issue i found inside coupple of unseen devices. I already don't know what to do, but the last time (Nearly a year ago) i solved this with quick lunch utility that looks like a rocket in right bottom screen, but after that this utillity never worked agin. I'll try to work out drivers from youre posts hopefully thay will help... The problem is still...

---

