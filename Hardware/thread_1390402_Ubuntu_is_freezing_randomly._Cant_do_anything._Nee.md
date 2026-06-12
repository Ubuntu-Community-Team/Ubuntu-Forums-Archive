---
title: "Ubuntu is freezing randomly. Cant do anything. Need help!"
date: 2010-01-25
forum: Hardware
---

### Post by lolboll on 2010-01-25
Hello all,

I've been back and forth with Ubuntu for a while now, mainly because some programs that I'm in need of doesnt work properly, like the Adobe Suite. Anyhow, I ran Windows 7 64bit just some days ago, and it worked well, until I didnt feel like trying to fix every single performance issue I had, so I thought; Ubuntu/Linux, come save me once again!

To the issue:

I've downloaded and installed the 32 and 64 bit versions of the latest Ubuntu.

I am performing a clean formatted install every time I try to fix my problem, and my whole computer is totally and 100% dedicated for ubuntu, so no dual-boot hax or anything like that.

Everything works fairly fine with the installation, and I enter the OS.

Now, during system updating, web browsing, exploring folders etc, the computer freezes. Nothing works except a reboot. Cant do ctrl-alt-F1 or anything else for that matter. 

It mostly happens during system updating or when I try to fetch a program via synaptic, like Wine or Compiz etc. 

The freezes is fairly random. Sometimes, it happens at the very initiation of the downloading of updates, and sometimes when its only a couple left of the 64 updates the comp is trying to download.

Any ideas of my problem?

Im running on a:

ASUS X71SLseries Laptop
Duo T5850
4gb RAM
GeForce 9300M GS 512 mb



Note: 

Im somewhat of a newb with Ubuntu. I know really basic commands like "sudo apt-get install xxx" and so on. So try to be gentle with me :P

Help is extremely appreciated! Extremely! :)


Thank you in advance, 

Niclas

---

### Post by jerrrys on 2010-01-25
for starters, i just go with 32bit.  its normally easer to get working than 64bit and then when you feel comfortable with 32 you can move on to 64. what ya think?

---

### Post by lolboll on 2010-01-25
Well, in my first post, I wrote that I've tried both versions, and Im fine with 32 bit.

But it doesnt work. Same problems

---

### Post by lolboll on 2010-01-26
I've tried to to use

sudo apt-get install upgrade / update

but the same problem occurs here.

---

### Post by lolboll on 2010-01-27
Got this from Ubuntu.se forums:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/426130](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/426130)

Might work!

---

### Post by lolboll on 2010-01-27
Confirming that it in fact DO work! :D

I uninstalled the network-manager and network-manager-gnome via the terminal, and installed WICD, and voila! Im happy soul once again =) 

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by AlexZaim on 2010-01-27
network-manager is truely not so succesfful with 9.10. i use wicd from the very beggining

---

