---
title: "Issue Installing on Acer Aspire One D250"
date: 2009-12-04
forum: Hardware
---

### Post by mahimahi42 on 2009-12-04
Hi everybody!

Recently I received an Acer Aspire One D250 for my birthday, and am itching to try Ubuntu out on it. I prepared the USB stick with UNetBootin, plugged it in, and tried restarting.

At boot-up, it says "Press <F2> for options", and I do, but it doesn't do anything but continuing booting into Windows XP. I've read some other sites for answers, and they all say to change BIOS setting, but I can't seem to get into the BIOS. I've tried F2, F12, F10, Del, and Alt+F10.

Any suggestions?

---

### Post by teward on 2009-12-04
Try hitting the correct keys **the moment after you hit the power button**.

If that doesn't work, go into the BIOS and make your USB listed first on boot order (might be "Removable Drives"), then hope it works.  Not much we can do past that.

---

### Post by mahimahi42 on 2009-12-04
Thanks. I flashed the most recent BIOS, and I got it installed. But when I tried to boot into Ubuntu, I just had a blinking underscore. I'm going to try booting into recovery mode, and go from there.

---

### Post by mahimahi42 on 2009-12-04
Got it working, just need a wireless driver! Time to Google...

---

### Post by mahimahi42 on 2009-12-04
Does anyone have a copy of AR813X-linux-v1.0.0.8.tar.gz? From what I can find on Google, this is what I need to get wireless working on my Ubuntu install.

Many thanks!

---

### Post by JBAlaska on 2009-12-04
From what I can Google, that driver went OS and is available [Here](http://sourceforge.net/projects/madwifi/)

Hope this helps.

---

### Post by mahimahi42 on 2009-12-04
Found this too, but I wasn't sure. I'm going to try it out though, will post results/lack thereof.

---

### Post by mahimahi42 on 2009-12-04
Followed the instructions from: [http://ubuntuforums.org/showthread.php?t=1141529](http://ubuntuforums.org/showthread.php?t=1141529), but with no luck.

Has anyone had any luck with trying to use a Linux driver for one of Acer's other netbook on the D250?

---

### Post by 00b00nt00 on 2009-12-04
Your wireless driver should be available to install within Ubuntu via the (I forget) 'hardware' preferences pane. just install and re-start.

Bear in mind that the microphone won't work and that the D250 has a BIOS bug which prevents the processor from working above 1.33 GHz.

---

### Post by mahimahi42 on 2009-12-04
I went to the Hardware Drivers app, but it said "No Proprietary Drivers Are In Use On This System".

Am I doing something wrong?

---

### Post by mahimahi42 on 2009-12-08
I tried following the directions on the Ubuntu wiki page for my model, but when I try to compile the driver, I get errors on the make. Any suggestions?

---

