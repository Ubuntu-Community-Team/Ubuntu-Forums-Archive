---
title: "Anyone using 'Crossover' to run TomTom Home, with the model 720T..?"
date: 2010-04-21
forum: Hardware
---

### Post by liviococcia on 2010-04-21
Hello Members

I'm just wondering if there are any Ubuntu 9.10 with a TomTom 720T satnav or other models, running the latest TomTom Home software through the latest 'Crossover Linux' application.

Have you had any success?, does the 'Crossover Linux' software see the correct satnav hardware drivers?, and if TomTom Home is working for you, do you manage to update all the different aspects and of a 720T, even things like 'Map share' and 'Security camera's' updates.

I am a complete novice regarding Ubuntu, but i have fully installed it on one of my other computers, and it works great.
 
I'd like to now do a complete installation of Ubuntu 9.10 across the whole partition on a Dell Inspiron 1720 computer that i use for other tasks including the updating of my TomTom 720T satnav, the computer is currently running Vista OS.

All members help, and experience would be grateful.

Kind regards
Livio

---

### Post by P4man on 2010-04-21
crossover is just a commercial implementation of wine, which you can install for free (its in the repository).

The problem is the same though, tomtom home works on wine (and crossover), but it doesnt support USB, so it doesnt see your GPS, which kind of defeats its purpose.

I once read somewhere someone worked around that, but I dont remember how. I think he could mount the tomtom harddrive as USB device, and then point tomtom home to the new mount point, or something like that, but I dont remember and didnt try.

---

### Post by liviococcia on 2010-04-22
Thanks P4man, during my web searches i've read a lot regarding the fact that the TomTom Home app works using Wine, or Crossover, and as you said it, the problem is that it's not seeing the device.

I did pick this link up during my enquirers...
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=5367](http://appdb.winehq.org/objectManager.php?sClass=version&iId=5367)

..and it seems to mention in 'Selected Test results' that someone had managed to do as you suggested, but i don't really understand the directions given in the statement.

So if there's anyone out there that has the solution, again i'd be grateful for the info.

regards

---

### Post by P4man on 2010-04-22
That solution is for tomtom home 1.x, but that version doesnt support your tomtom device if I understand correctly. For tomtom 2.x it looks rather desperate:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=10219](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10219)

Call up customer service and complain, its all we can do, make ourselves heard. Its kind of ironic tomtom devices run on linux yet you cant use them with linux.

Another thing you can do is install windows under virtualbox (you must download it from virtualbox website or repositories, the OSE version which is in the ubuntu repository doesnt support USB devices either).

If anyone has another solution, Id gladly hear it, but I just dont think there is one :(

---

### Post by liviococcia on 2010-04-23
Thanks P4man, ok i understand, until TomTom sort out something for Linux users we're knackered, i've signed the partition and sent them an email.

But in the meantime, would it be possible to successfully run a slimmed down version of Windows (say XP) on a memory stick purely so that i can still update the TomTom, and would running it in this way mean that my USB ports would still be seen by either OS when XP is being used.

It's crazy!, because this TomTom issue is the only thing i can find no way of getting around, also, i know there are virtual softwares that can run in Ubuntu, but i'm trying to keep well away from any Microsoft OS within the main laptop itself.

regards

---

### Post by P4man on 2010-04-23
You could try making an XP boot stick with bart's PE builder. Here is a link that may help:
[http://articles.techrepublic.com.com/5100-22_11-5928902.html](http://articles.techrepublic.com.com/5100-22_11-5928902.html)

But honestly I think virtualisation it is the way to go. When you run windows in a virtual machine (VM) it really cant do anything bad to your host (ubuntu), it has no access to your drive or files (unless you give it that specifically through shared folders). Its actually safer, because if you boot from a stick, windows will have access to your drives (even if it cant read them, it can format them). So even if your VM would get infected by viruses and malware and other rubbish, its not going to affect anything outside the VM. And you can launch windows in a window just like any app and have it run in seconds, rather than having to reboot, you can make snapshots so if your windows gets hosed, you just load a previous snapshot etc.

Virtualization is not just the big hype right now, its damn useful!

---

### Post by liviococcia on 2010-04-24
Thanks again P4man, i think i'll do as you've suggested, but i will keep a watchful eye on this issue and TomTom's shortfall in providing compatibility accross the entire OS customer spectrum.

Thanks for all your help

Kind regards
Livio

---

