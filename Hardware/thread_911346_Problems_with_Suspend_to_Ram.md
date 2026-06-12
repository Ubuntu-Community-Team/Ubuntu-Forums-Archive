---
title: "Problems with Suspend to Ram"
date: 2008-09-05
forum: Hardware
---

### Post by superuser on 2008-09-05
Hello!

I have a problem with my laptop (HP nx6110) trying to recover from a "Suspend to Ram" event. After the notebook has successfully suspended to ram - as it always does btw. - sometimes during the wake-up process the whole OS gets stuck. It doesn't even turn on the monitor's back light and neither does the USB port get power. No keys are working, so I have to hard-reboot the system by pressing and holding the power button. A file-system check is being performed upon reboot. My ubuntu installation (Ubuntu 8.04 - the Hardy Heron) is relativley new and clean (give it 6 weaks).

It would be very nice of you to help me solve this problem!

superuser

---

### Post by Rowie1 on 2008-09-06
I've found the suspend to ram and hibernate feature to be very flakey with Ubuntu.
I use a toshiba L30 101 laptop, that's set to suspend to ram when the lid is shut, but when I open the lid, I very often have to wait a few minutes for the login screen to appear. Sometimes I don't get anything and have to re-boot.

---

### Post by andrewkirk on 2008-09-06
I also have problems with Suspend to RAM (standby) and Suspend to Disk (hibernate). I have two PCs and two laptops, all running ubuntu 8.04. 
The older PC does both beautifully, including waking up. This is better than Windows, which has trouble waking up on this PC if it's been on standby for more than 10 minutes.
The older laptop (Compaq Armada 500 c.2001) goes to sleep very nicely and wakes up OK but takes about 30 seconds to do so. 
The newer PC tries to go into standby but immediately bounces back out again and, after a little think, presents me with a login screen. For Hibernate it goes into a complete hang, sends me nasty messages and trashes the swap partition. 
The newer laptop (HP Intel) goes to sleep nicely for standby, but won't wakeup, so needs a complete reboot, which kinda defeats the purpose of standby!  

For me, this is a sufficiently important issue to prevent me from using Ubuntu on most of our computers because, in these days of concern about carbon footprints, I can't accept having to leave a computer running all the time (at about 50-60W) just to get rapid access to it.

I hope somebody has a solution :confused:

---

### Post by superuser on 2008-09-07
Hi,

I can now confirm that it always stalls on the third wake-up of the system -- i.e. I can safely do two suspend-to-rams and after the third, it won't wake up properly.

You might want to change the settings in /etc/default/acpi-support.

/Edit: You might also find this [https://wiki.ubuntu.com/HoaryPMResults](https://wiki.ubuntu.com/HoaryPMResults) interesting!

superuser

---

