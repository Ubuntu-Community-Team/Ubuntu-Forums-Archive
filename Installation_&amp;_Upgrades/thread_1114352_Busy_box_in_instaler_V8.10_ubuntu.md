---
title: "Busy box in instaler V8.10 ubuntu"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by flamingsnake on 2009-04-02
when the computer boots it goes to the menu as it should i select english as my languege then i select "install Ubuntu" next it goes to a ubuntu loading screen withe the progress bar then a screen comes up with

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter help for a list of built-in comands.
(inframs) [    64.72063] ata1.00

it does go on but you get the idea my specs are
AMD semperon processor
Asrock k8n(or something like that) mainboard
1gb of ram
40gb hard drive
DVD rom
any help would be greatly appreciated thanks to anyone that can help
 Flamingsnake (Im a Ubuntu noob ;)  so hi)

---

### Post by taurus on 2009-04-02
1.  Did you remember to run checksum to check the integrity of the ISO image.

2.  Did you burn it at a slow speed, 4x?

3.  Did you run the check cd for defects option at the initial screen to check the CD first before you used it?

---

### Post by flamingsnake on 2009-04-03
sorry to be a pain but how do i do number 1?
and no i didnt burn it at 4x is that a bad thing?

---

### Post by taurus on 2009-04-03
1.  [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

2.  Try to burn it again but use the slow speed.

---

### Post by flamingsnake on 2009-04-04
thanks for the reply but after running some checks i have concluded it aint the cd i used another pc to boot with the cd and it worked fine so other causes are?

---

### Post by airphoto1 on 2009-04-04
What did you do with cookies?  I am having the same problem.  Please share your successes.

---

### Post by taurus on 2009-04-04
You can always try the alternate CD to install Ubuntu on your machine.

---

### Post by airphoto1 on 2009-04-04
Got frustrated with unsuccessful download after another.  So, I ordered a ubuntu CD from eBay.  It too gets hung up on BusyBox.  How do I get it to load properly?  Would like to take a tour on this linux system.  Any help would be appreciated.  Thanks.

---

### Post by flamingsnake on 2009-04-04
Ok so whats the difference beetween the normal cd and the alternate one?

---

### Post by taurus on 2009-04-04
[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

### Post by flamingsnake on 2009-04-09
thanks a load taurus the alternate install disc worked and im posting from the computer now :D and already love ubuntu

---

### Post by flamingsnake on 2009-04-09
one other thing does ubuntu support the nvidia 6600gt graphics card cos i have one spare and wanted to test it ps oops double post

---

### Post by taurus on 2009-04-09
When you install your nvidia card, make sure you go into the BIOS and turn off the onboard integrated graphic controller.  Then boot your machine with the add-on nvidia card.  Now, go into System -> Administration -> Hardware Drivers and install nvidia driver for your graphic card.

---

