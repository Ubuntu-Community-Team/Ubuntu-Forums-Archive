---
title: "Fan Maxes Out and Battery Status Indicator Flashes"
date: 2013-12-08
forum: Hardware
---

### Post by nick48 on 2013-12-08
I have recently installed Ubuntu on my Asus UX301LA which has raided SSDs and is in UEFI. Install is fine and everything works, however sometimes when I boot my fan maxes out and my battery status indicator on the power cord flashes. I'm not really sure how to troubleshoot as I'm fairly new.
If I were to boot into windows with the LED blinking it would say plugged in but not charging.
This laptop is brand new just received it about 3 days ago and hasn't always had these symptoms. 
The symptoms started after booting to ubuntu. 
Also the fan doesn't max out every time. 
I know the laptop isn't hot since it's just booting so there is no need for the fan.
Any help is greatly appreciated! Thank you!

---

### Post by codenine75a on 2013-12-09
I think that is a kernel panic indicator when your OS crashes and blinking lights show up like a good vegas casino.

---

### Post by nick48 on 2013-12-10
Thank you for your reply!

The OS isn't crashing at least it doesn't appear to be.
It's just the fan that's being maxed out and then the led indicator on the power cord flashing.

---

### Post by pantale on 2013-12-12
Hi,

I have tested for one day the 13.10 Kubuntu distribution on an ASUS UX301LA-DE002H and have encountered the same symptoms as you hve described.
Unfortunately for me, after a day of ubuntu testings, the computer never restarted and I had to return it to Asus for an exchange !

The fact that battery isn't charging seems to be related to a well known bug in Asus computers (UX31A serie). Some says yhat you have to open the back cover of the lapto and unplug the battery for a moment to overcome this. Some other says that using Ubuntu with some kernel arguments through grub can correct this.

As I don't have received the replacement laptop, I cannot test it for now.

Have you ever be able to activate bluetooth on the laptop ?
What about Brightness functions keys ?

Kindly Regards,

Olivier

---

### Post by kifer on 2014-05-08
It is a BIOS problem. Upgrade to v206 and both problems will be gone.

---

### Post by Ripp_Steakface on 2014-05-08
Interesting thing to note: On some computers, if you force them to shut down, upon restart the fan will spin at full speed momentarily until the system starts operating again. This may have something to do with what's going on; in other words, your computer isn't getting past the very basic boot procedure.

---

