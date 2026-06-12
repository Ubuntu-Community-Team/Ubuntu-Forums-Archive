---
title: "Intel graphics media accelerator drvier"
date: 2012-08-15
forum: Hardware
---

### Post by tanics on 2012-08-15
Hello Friends,
I am using ubuntu from 2k9. Due to some software requirement I have to reinstall WINDOWS XP, dual booting with Kubuntu-12.04 in May. But I have been plagued with different problems since then.

My system -> INTEL MOTHERBOARD - D945GCNL with integrated Graphics;
1 GB RAM; INTEL-CORE2DUO PROCESSOR - SEGATE SATA HDD;

1)Internet via PPPoE - found that once I connect to internet in kUbuntu by setting up [ sudo pppoeconf] usb interface, I can't connect internet after rebooting to Windows.
2) To connect Internet to Windows I have to again boot kubuntu Live CD & connect to internet via ppoeconf then rebooting and connecting to the internet in Windows as usual.
3) But in case of Kubuntu I have to run [sudo pppoeconf] every time I want to connect to Internet. Even after running [poff] command if I want to connect net I can't do that by usual [pon dsl-provider].

[U][B]Possible Graphics driver problem:
[/B][/U]
4) Few days after installing both systems I use the motherboard CD and  install INTEL GRAPHICS MEDIA ACCELERATOR DRIVER. Possibly since then I can't log in normally to kubuntu with Monitor On.
5) Whenever I try to log into kubuntu by selecting Grub option - the Monitor gets itself disconnected but system boots into log-in screen. 
6) Can shutdown/reboot the system by selecting tty - entering commands. But can't see anything as if monitor is not connected.
7) After shutting down the system (not rebooting) can log in to WINDOWS normally.
8)Happening with other distros too(SL6.1, Opensolaris-2009.6)
Kindly help me. Love Ubuntu/Linux but can't use it now.
Thanks for any reply.

---

### Post by tanics on 2012-09-06
Well with no reply until now - I would like to add how I am using kubuntu12.04  currently.

Don't know the difference though (even after googling) - from grub2 menu - I am selecting *_**kubuntu (recovery mode) **_*  - then few seconds later they ask to BOOT NORMALLY with a warning some VIDEO DRIVER MAY BE DISABLED.

Then every thing works normally without any problem mentioned above.

But as soon as I choose the first entry in grub2 menu i.e Kubuntu without RECOVERY MODE - the aforementioned problem i.e. NO DISPLAY returns.

ANY SUGGESTION ?
Thanks for any reply.

---

### Post by Epodx64 on 2012-09-07
I have an integrated GMA 4500 and I found I got the best support from the x-swat x-org updates here's a link to there PPA add the PPA then run 

sudo apt-get update
sudo apt-get upgrade

and it will install the newest Intel drivers and Intel-xorg-server

---

