---
title: "HP 2133 + Battery problem under U 10.10"
date: 2010-10-13
forum: Hardware
---

### Post by LuisitoRito on 2010-10-13
Recently I installed Ubuntu 10.10 (Desktop Edition) on an HP Mini  2133... everything is working fine, except for a weird thing... the  battery isn't working well... it only work for 6 seconds, and before  that the HP shutdown... It isn't a battery problem because under Windows  works well (stand for 1:30 h approx.)
Any suggestion to this particular problem???...

Luis Andrés Alcalá Díaz, Barcelona, Venezuela
Thanks for your Time

---

### Post by gwiltgen on 2010-10-16
idem for medion laptop p8610

---

### Post by jamesblonde on 2010-10-16
Same problem here for an Asus iCore 3 laptop.
Just unplug power and it dies, battery is fine under windows.

---

### Post by LuisitoRito on 2010-10-19
People try this: 
Charge the Battery, turn off all power management to stop it entering  sleep mode -then allow it to discharge fully using the machine without  mains, then charge the battery fully again. Calibrate the battery using  the HP Battery Check Tool under Windows.
The problem can occur because HP don't give full details of the ACPI, so  the Linux generated DSDT Tables are not always accurate, and things get  misreported. This means the machine can on certain machines report that  the battery is fully discharged, when it isn't - calibrating the  Battery under Windows is your best bet to solve the issue.

If your system is not HP... well search if your manufacturer has some utility like HP Battery Check..

Ccalibrating the battery helps a bit, now Ubuntu works with the PC  Battery as power source, but Ubuntu acts weird, I mean: If I start the  system unpluged if works perfectly, but If I plug the PC, and for some  reason unplug again the problems appeart for a while (the system suspend  or hibernated) but when i restard if works again.... I have notice that  when I unplug the system from the power grid it tray to calculated the  stimated time of the battery life, i think that the problem is here...

PD.: The HP Battery Check tell me that my battery is fine... and if  works fine under windows.... I will try to download the CD image again  (just to discard that my downloaded image is wrong....) if the problem  persist i will go back to U 10.04

---

### Post by samjam on 2010-11-10
If I suspend (not hibernate) I can then remove the power cord and un-suspend.

If I remove while active the machine will immediately hibernate

---

### Post by erichhaubrich on 2010-11-18
Same issue here. I also cannot use the keyboard or trackpad on the HP 2133. I am able to use a USB Mouse, but I have to type my password into the calculator app then copy/paste it into the password field in order to do anything requiring Admin credentials.

This deal-breaker issue. I just wish I knew beforehand that U 10.10 would practically brick my wife's netbook and waste hours of my time.

Perhaps there should be a 'Known Incompatibility' link on the download or features page. (I retract this comment if it's there and I just overlooked it.)

I think I speak for anyone with these issues that I'd love to see a fix in an update or patch....really soon.

Other than not being able to use the machine in any useful way, I love UBUNTU! ;)

If anyone has a fix for this, please PM me or send me an email. I'm on borrowed time because my wife is computer-less until this is fixed.

***ALSO NOTE:*** I don't know if it's due to the fact that the system doesn't recognize the keyboard, but the onscreen keyboard appears at the login prompt.

---

### Post by erichhaubrich on 2010-11-18
Thanks guys, good looking out. 

Wow, 30 seconds after I posted my issue, the developers fixed it.
THAT'S SUPPORT!! :popcorn:

The jury is still out on the battery.

---

### Post by samjam on 2010-11-19
> **erichhaubrich said:**
> Thanks guys, good looking out. 

Wow, 30 seconds after I posted my issue, the developers fixed it.
THAT'S SUPPORT!! :popcorn:

The jury is still out on the battery.

I installed 10.4 plus al the wii fixes for alsa, via graphics drivers, etc, and NOT the STA wlan drivers (which are rotten on 10.10 anyway).

I'm very happy with 10.04

Sam

---

### Post by Smtpflash on 2011-01-16
Have same problem on hp2133 when unplugged AC.
Check this. Sad.

[http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c01480001&lang=en&cc=us&taskId=101&prodSeriesId=3687084&prodTypeId=321957](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c01480001&lang=en&cc=us&taskId=101&prodSeriesId=3687084&prodTypeId=321957)

> **LuisitoRito said:**
> Recently I installed Ubuntu 10.10 (Desktop Edition) on an HP Mini  2133... everything is working fine, except for a weird thing... the  battery isn't working well... it only work for 6 seconds, and before  that the HP shutdown... It isn't a battery problem because under Windows  works well (stand for 1:30 h approx.)
Any suggestion to this particular problem???...

Luis Andrés Alcalá Díaz, Barcelona, Venezuela
Thanks for your Time

---

