---
title: "HELP!! HP Mini 110 1020LA"
date: 2009-07-26
forum: Hardware
---

### Post by Luca_turicci on 2009-07-26
Hi, i just got a HP mini 110 1020LA yesterday, and i immediately installed Ubuntu 9.04 with an USB CD-ROM, so, it runs pretty smooth, i only have 2 significant problems:

1.- No sound from built in speakers, headphones work ok.
 
2.- Ethernet port doesn's seem to work, i've been trying to connecto via Ethernet and even if I boot the computer with the cable in it, it doesn't work.
 
I've been "googling" for the whole night and day and found many "solutions" but nothing worked this far =(.
 
I've installed 9.04 twice, then installed Netbook Remix, but nothing works =\
 
Anyone HELP!!!

---

### Post by jerrrys on 2009-07-27
# 1  are they muted?

System>Preferences>Volume

#2  better for someone to answer running 904

---

### Post by Luca_turicci on 2009-07-27
Hi, i'm desperate, not dumb, of course they were not muted, otherwise i wouldn't have posted here.

I've been trying a few more stuff and finally got my sound to work, haven't tested the mic, but all the keys, pad, card reader, usb ports, speakers, headphones, wireless, everything works, except for the Ethernet. Somebody PLEASE help me!

---

### Post by jerrrys on 2009-07-27
and I don't own a crystal ball so I got to ask

---

### Post by Luca_turicci on 2009-07-27
Ok, good point, i was a little mad. I just need help, Sound is now working, but wired connection doesn't.

---

### Post by Luca_turicci on 2009-07-29
Hey there, just did some updates on my lap, and now i don't have sound again :) and still don't have ethernet port

---

### Post by eighthave on 2009-07-29
Could you post how you got audio working? I have the same problem with my HP Mini 110 and haven't found an answer.

Thanks!

---

### Post by Luca_turicci on 2009-07-30
Sure Buddy, the thing is i've followed a series of instructions from different posts, and I don't remember wich one was the one that solved it, here i'll post the links to all the solutions I found.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269027](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269027)
[https://bugs.launchpad.net/netbook-remix/+bug/318942/comments/11](https://bugs.launchpad.net/netbook-remix/+bug/318942/comments/11)
[https://bugs.launchpad.net/netbook-remix/+bug/318942/comments/63](https://bugs.launchpad.net/netbook-remix/+bug/318942/comments/63)

Another thing is you must check here [http://www.linuxant.com/alsa-driver/downloads-ubuntu-x86.php](http://www.linuxant.com/alsa-driver/downloads-ubuntu-x86.php) and download the latest driver (1.0.20.23), and you must remember that this works in Kernel 2.6.28-13 or lower, be sure to download the right driver for your kernel, if you don't know what you're kernel is, open a terminal and type "uname -r", if it's 2.6.28-14 it won't work, i've tested it, you must have 2.6.28-13 or lower.

As a tip, if you hear a *beep* when rebooting it means it worked, so don't mess around and just unmute everything (except the PC beep)

If anyone knows anything about how can I make my ethernet port work, pleeeease tell me.

---

### Post by JQN on 2009-07-30
Hi Luca

The first time you solve it you tried any of those 3 links??

I have the same problem, can't get any sound from my mini 110-1020

---

### Post by Luca_turicci on 2009-07-30
yeah, i tried those 3, but, as i said, i've noticed a couple things:

*You must have kernel 2.6.28-13 or lower
*download the latest driver from linuxant website and make sure it's for you're same kernel
*I've tried it on a couple distros, UNR and HP Mini Remix didn't worked, i had to install Jaunty desktop (normal) version.

About the ethernet connection, (remember it doesn't work for me yet?) i checked with hwinfo and got this:

> 
network:
                       Attansic Ethernet controller
  eth0                 Broadcom BCM4310 USB Controller
network interface:
  pan0                 Ethernet network interface
  eth0                 Ethernet network interface
  lo                   Loopback network interface
Any ideas? according to my research, Broadcom BCM4310 is only wireless, so what do i do?

---

### Post by don_pucci on 2009-08-04
> **Luca_turicci said:**
> yeah, i tried those 3, but, as i said, i've noticed a couple things:

*You must have kernel 2.6.28-13 or lower
*download the latest driver from linuxant website and make sure it's for you're same kernel
*I've tried it on a couple distros, UNR and HP Mini Remix didn't worked, i had to install Jaunty desktop (normal) version.

About the ethernet connection, (remember it doesn't work for me yet?) i checked with hwinfo and got this:

Any ideas? according to my research, Broadcom BCM4310 is only wireless, so what do i do?

I have an HP Mini 110 1030 and have the sound issue as well.  I have tried UNR and the Remix and both have this issue.  Are you saying that you need to use Jaunty Desktop full version or that your fix works for UNR.

---

### Post by Luca_turicci on 2009-08-11
Hi there, I tried the fixes on Netbook Remix and HP Mini Remix, and it did not work, i don't know why, i didn't have much time to test them properly.

I suggest using Ubuntu Jaunty Desktop version because that's what worked out for me, maybe HP mini remix and netbook remix may work as well but with different methods. But if you're like me and don't want to take too many risks, install Jaunty Desktop version until Karmic Koala and it's netbook version are out.

i'd like to ask all of you guys running ubuntu on Mini 110, DOES YOUR ETHERNET ADAPTOR (WIRED CONNECTION) WORKS??

---

### Post by Luca_turicci on 2009-08-11
Hi!, it's me posting again, i just updated to 2.6.28-14 kernel after finding the proper version of the alsa driver on linuxant.com.... hehe, but i'm not getting sound again... and... you remember my ethernet connection was not working? well, so i can't do exactly follow the steps to solve it again.... PLEASE ANY INFO ON THE ETHERNET ISSUE WILL BE WELCOME!!!
 
By the way, i'm about to try Karmic netbook remix alpha 3 on my mini =D wish me luck.


---- today at 00:02 hours i finished installing Ubuntu Netbook Remix 9.10 alpha 3. SOUND WORKS OUT OF THE BOX!!! and ETHERNET DOES TOO!!!, everything is functional, except the wireless, but everything else is working out-of-the-box!!!----

---- GENTLEMEN, today at 04:52, after installing and uninstalling one OS after another, i have finally got my Mini to work at it's 100% , installed Karmic Alpha 3, desktop version, updated everything i could and selected STA wireless driver. FINALLY, EVERYTHING WORKS!!! sound, wireless, ethernet, VGA OUTPUT, card reader, usb ports, bluekeys, pad, EVERYTHING!!!... i need a blog... and i think i will sleep all this day...

---

### Post by PhilMize on 2009-09-05
How about the Mic? Does it work with skype?

---

