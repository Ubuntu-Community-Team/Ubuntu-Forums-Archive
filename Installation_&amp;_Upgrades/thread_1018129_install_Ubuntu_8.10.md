---
title: "install Ubuntu 8.10"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by fauna on 2008-12-21
I installed Ubuntu 8.10-a couple times-on two computers-an Everex with Linux already on it and on a old Dell to replace Windows ME.All went well and they run fine but trying to get Intrepid on my newer Dell dual booted with XP has always got to that Busy Box and nothing gets around it.Ubuntu 8.03-Heron- runs fine off disk on this computer and Wubi ran just so-so on it,but neither of the two copies I have of 8.10 will load.I read that 20% of installs fail-my rate is higher but I don't want to get stuck with a version I can't upgrade.Installation was so easy on the other machines;empty hard drives,Windows,other Linux were no problem but the Dell with better processor (2.00AMD Athlon 64) and an extra hard drive stops Intrepid cold.I'll probably get rid of XP down the line but need the dual boot for now.I am obviously not very experienced and could use some cut and paste fixes.  fauna  :confused:

---

### Post by jeffsilverm on 2008-12-21
Fauna,

In reading through various forums and some Google searching, I found two ideas, neither of which helped me with my problem but which may help with yours.

When going through the installation process, after selecting a language, you will have a menu of several options, one of which is install Ubuntu.  There are also 6 options selected by function keys.  Select option F6.  That will allow you to edit the boot command line.  One thing I added was all_generic_ide .  That didn't help me.  Another thing I tried was rootdelay=130.

I suspect that my hardware (IDE controller) is too old.  It works fine under 7.10.  I have a  IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)

If/when you come up with a solution, please write me and let me know what you found out.

---

