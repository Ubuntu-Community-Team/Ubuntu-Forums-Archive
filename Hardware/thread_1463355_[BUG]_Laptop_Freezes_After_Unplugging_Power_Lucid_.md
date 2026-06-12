---
title: "[BUG] Laptop Freezes After Unplugging Power Lucid Lynx Release Canidate"
date: 2010-04-26
forum: Hardware
---

### Post by bird1992 on 2010-04-26
I am using 10.04 Release Canidate on a Sony VAIO Laptop (built for WINXP in 2005).  When I unplug my laptop the desktop environment and ubuntu freeze and the only way to exit this through a hard reboot.  Similarly, ubuntu won't boot (black screen after grub selection)if the laptop is not plugged in.  Win XP works fine without the power cord so I don't think it is a battery defect.  Any suggestions?  Or how do I submit this bug to the developers?

ADDITIONAL INFO:
I never had this problem with ubuntu 9.10

---

### Post by bird1992 on 2010-05-01
bump

---

### Post by sportnik on 2010-05-03
I also have this problem. It freezes when i unplug the cable and when i boot only on battery. I freshly instaled Lucid lynx. I have HP laptop 6735b.

---

### Post by sportnik on 2010-05-03
> **sportnik said:**
> I also have this problem. It freezes when i unplug the cable and when i boot only on battery. I freshly instaled Lucid lynx. I have HP laptop 6735b.

i solved the problem. I had to install the newest ATI drivers, the same as i had to to with wi-fi drivers.

Go to System -> Hardware drivers -> select or activate neccessary missing drivers (i selected wi-fi and ATI graphincs drivers) now ubuntu boots normally.

---

### Post by bird1992 on 2010-05-04
Sadly enough my computer is so old I guess that ati drivers for it do not exist.  I installed the fglrx packages and this fixed the problem, but it also broke my graphics card since there were no drivers for it.  So now I have to choose between a broken graphics card and a transportable laptop or a working graphics card and a laptop tethered to the wall.  I am using Sony VAIO VGN-AX570G with an ATI Mobility Radeon x700 graphics card.  Any more help would be greatly appreciated.

---

### Post by bird1992 on 2010-05-07
bump

---

### Post by bird1992 on 2010-05-09
bump

---

### Post by bird1992 on 2010-05-10
anyone???

---

### Post by Ryantoss on 2010-05-11
> **bird1992 said:**
> anyone???

i got very same problem and solved it with ATI driver.

As far as i remember ATI driver use very similar structure. You can try Sportnik's solution

---

### Post by bird1992 on 2010-05-12
I can't install the ATI driver because there is none for my graphics card.  But what is weird is that without the driver my graphics work flawlessly, but I can't unplug my laptop.

---

### Post by bird1992 on 2010-05-13
I solved this problem... I uninstalled Ubuntu 10.04 and reinstalled 9.10.  I hate to be disrespectful and I have always loved Ubuntu but this is the most buggy os I have ever used and 9.10 was much better.  Also my wifi in windows xp was broken and it turns out once I uninstalled 10.04 it started working again.  I have had multiple unsolvable issues with this os, I have sought help and received none.  And these haven't been small issues either; Not having wifi or being able to unplug your computer pretty much defeats the entire purpose of having a laptop.  I would strongly advise anyone who is considering upgrading to stay with 9.10 which I thought was a great os.

---

### Post by toph on 2010-11-27
I tried this and it worked for me. I can now boot from battery.

[http://ubuntu-tutorials.com/2010/05/...up-workaround/](http://ubuntu-tutorials.com/2010/05/...up-workaround/)

I hope it works for some of you.

Chris

---

### Post by DaveJ1337 on 2011-03-18
I installed 10.04.2 an hour ago on a new Dell Inspiron 11 and have this issue as well.  I'd much prefer not to use the fglx drivers, but it seems I don't have much of a choice.  Poop.

---

