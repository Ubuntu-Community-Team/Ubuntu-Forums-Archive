---
title: "No type of linux will boot on computer"
date: 2007-02-14
forum: Hardware &amp; Laptops
---

### Post by savagenator on 2007-02-14
Hello all,

i  want to start using linux, but i found out that whenever i load any linux (including ubuntu 6.10 x64, ubuntu 6.10 x86, ubuntu 6.06 x86, suse10.1 x64, suse10.0 x86, and redhat fedora x64) none of the CD's can load to live CD's or any GUI with a mouse. On all versions there is a about a cm thick artifact line in the center of the screen, and it stays that way. I cannot do anything to make any of the linuxs' to work.

I know all the CD's are good becuase all of them work on my secondary computer (P4 2ghz, 768mb of RAM, DELL)

My primary computers specs are:
gigabyte ga-k8n-sli mobo
AMD 4400+ X2
2x512 XMS corsair + 2x1gb corsair ram (yes they work together perfectly, i use windows with them)
EVGA 7800GT
1x20gb backup, 1x200gb HDD with windows XP and a 40gb empty partition, 1x320gb HDD with vista

i upgraded the bios from k8n-sli.f1 to k8n-sli.f9 beforehand due to OCing issues, but currently my system is at stock clocking.

Please tell me what i can do to make linux work on my machine.

---

### Post by PurplePenguin on 2007-02-14
If I were you, I'd try the [Alternative Installation]("http://www.ubuntu.com/products/GetUbuntu/download#currentrelease") disc.

---

### Post by ehowell on 2007-02-14
I have a similar setup (AMD 4200+ X2 with a 6800GS) and I cannot use live CDs. none of them give me a gui since the default nvidia drivers on the live CDs don't seem to work.

for me I used the alternate CD to install Ubuntu. You download the alternate CD from the same place as the live CD. That should work to get you a gui, but you will have to install the latest nvidia drivers. I use the program Envy ([described here]("http://www.xenocoder.com/blog/archiveposts/52")) to do this.

You may still have problems after installing with the alternate CD, but you can Ctrl-Alt-F1 to a command line and had edit your /etc/X11/xorg.conf file if that happens.

Before we jump too far ahead I would suggest the alternate CD route as I think you may have the same problem with all live CDs based on your setup (I may be wrong though!)

Curious to hear how this turns out for you :)

---

### Post by savagenator on 2007-02-14
thank you for your responses. I am downloading the iso at this moment (6.10 alternate amd64). I hope this one will work as you said, but it also seems strange to me that all those CD's do not work, some of which are DVD's. I would think that at least one of them should have the driver i need.

---

### Post by savagenator on 2007-02-15
i've got a nice little update: ubuntu has been installed, but with a price. i get a Error Loading OS error message right after my comptuer looks at the CD drives. I am thinking that grub has conflicted with the Vista bootloader, but i am not sure.

here is my HDD setup: 
Master IDE 20gb drive
a Sata 200gb with windows Xp and a 20gb empty partition
a Sata II 320gb with windows vista ultimate

i dont know what to do now, i've tried reinstalling a few times, but it seems like nothing is working. Grub and lilo do nothing as i can tell. Luckily i have a leptop i can use, but i cannot boot into any operation system on the HDDs.

---

### Post by highneko on 2007-02-15
It simple but I don't see it mentioned. Make sure you have your bois set to boot from cd.

---

### Post by savagenator on 2007-02-15
sorry, i forgot to mention it, but i can only boot from the CD, and i cannot boot from any of the drives whatsoever. I am using the 20gb partition in the 200gb sata drive for the instal, and 300mb in the 20gb ide HDD for swap space. now it says that "select and install software" has failed to install.

---

### Post by PurplePenguin on 2007-02-15
If you're having problems booting into your partitions, you might want to try using another computer to download and burn a [Super Grub Disc]("http://supergrub.forjamari.linex.org/").

---

### Post by savagenator on 2007-02-15
thank you for your posts. So far from this grub i still cannot boot into anything. No matter what i try i cannot boot. I am thinking the Vista boot has messed something up, but i am unsure what and why. Please tell me what i can do using anything to restore my system. i do not want to resort to formatting any of the drives

---

