---
title: "Feisty suspend and hibernate doesn't work"
date: 2007-04-30
forum: Hardware &amp; Laptops
---

### Post by arijel on 2007-04-30
I have installed Ubuntu Feisty (2.6.20-15 generic) on my HP nx6325 laptop (AMD Turion TL-52 x2, BIOS F.06 ). First I have tried the hibernation. The system hibernates ok, but when I resume from hibernation the cpu fan is not wokring - stays off.
Suspending the system work, but when I resume from suspend the keyboard is not responding, only the power key works.
Does anyone know how to fix these problems?

---

### Post by NIKOSHIBA on 2007-04-30
i've got same problem.
someone pls help. very important future, can't leave without!!!

---

### Post by county_bg on 2007-04-30
There used to be a problem with suspend/hibernate when using the proprietary driver "fglrx" for ATI video.
The following worked both in edgy and feisty for my HP with Turion ML-28, ATI Radeon XPRESS 200M:

Edit /etc/default/acpi-support and change:

SAVE_VBE_STATE=false #true is default

USE_DPMS=false #true is default


Post if you have any success.

---

### Post by tanguyr on 2007-04-30
Hello county_bg,

I'm having a similar problem with suspend not working when i use the fglrx drivers in feisty (well, suspend works, it's wake up that's busted)- i tried your suggestion abobe, but without effect.

just fyi.

/t

---

### Post by FrancoNero on 2007-04-30
i use a hp nx7400 ,and suspend works, but when i return from it, i have no keyboard (and sometimes no mouse), which means i'm locked out because i can enter no password.
hibernate doesn't work at all, i get lots of crazy errors about acpi and usb and such, and then that's that.....

i posted this in related topics, but so far i haven't seen an all-encompassing solution to those acpi problems. i have to say that i would not have released feisty without proper laptop support.... i hope there'll be some kind of official fix pretty soon

---

### Post by gldvxx on 2007-05-01
my computer won't wake up after possibly suspending (actually i'm not sure what happened, this is just a guess).  i can't boot anything....  :(

---

### Post by twoblackeyes on 2007-06-16
The config file tweak here didn't work for me (Thinkpad X31) - made the screen not go dark upon suspend and plenty of errors in console mode upon wake. Anybody have any other ideas?

---

### Post by Bluecircle on 2007-06-16
Have you guys tried my howto? 

[http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855)

See if that works for you.

---

### Post by CAsurfer on 2007-06-20
Bluecircle, I followed your howto, and now suspend and hibernate work perfectly.  Thanks!

---

### Post by poobslag on 2007-06-23
I have a very similar (or possibly) the same problem as described here. I have an Alienware running a 64-bit AMD chipset and after un-suspending, my monitor never wakes up. I am running Ubuntu Feisty Fawn.

I tried the suggestions here but they did not fix my problem.

---

### Post by goranpg on 2007-07-22
> **arijel said:**
> I have installed Ubuntu Feisty (2.6.20-15 generic) on my HP nx6325 laptop (AMD Turion TL-52 x2, BIOS F.06 ). First I have tried the hibernation. The system hibernates ok, but when I resume from hibernation the cpu fan is not wokring - stays off.
Suspending the system work, but when I resume from suspend the keyboard is not responding, only the power key works.
Does anyone know how to fix these problems?

I have same problem with my HP nx7300 Core2Duo T5500. 
I've tried already mensioned fixes with suspend2disk but still fan isn't working after restoring.
Did anyone find the solution - I've spent last couple of days reading launchpad and ubuntuforums and this is the only post i found that has fan problem (everybody else are stuck with keyboard and blak screen problems that i already managed to solve)

---

