---
title: "Mounting Hidden Protected Area on Thinkpad"
date: 2012-04-06
forum: Hardware
---

### Post by fiestaforever on 2012-04-06
Hi, 

I'm doing some work with Linux (Xubuntu 11.10 Live system on a USB thumbdrive) on a Thinkpad R50e that has Windows XP SP3 on it. 
I need to access the [Hidden Protected Area]("http://www.thinkwiki.org/wiki/Hidden_Protected_Area") (which is basically a hidden FAT32 recovery partition with some additional tools on it). I cannot access it the "normal" way because of a stupid password I don't know (please note that I'm not talking about a BIOS or HD password - there are none of those here; this laptop is completely legit, and the original owner doesn't know the password either). 

Searching the net, I found out that this is a quite common problem, and can be solved by removing a file that is *on* the hidden partition. But for that, I need to mount it. 

I cannot find a way to do that. There is a little program called ['fiesta']("http://sourceforge.net/projects/fiesta/") to help with it, but I cannot compile it. Nor can I install any additional software in the first place.

There *must* be *some* way to mount that stubborn partition. I can see it in GParted as /dev/sda2, after all.

TIA

Update: Meanwhile, after a lot of searching the net, I found a way to get rid of the password by simply editing a file on the main partition. But I'm still interested in how to mount the service partition. just out of curiosity. :)

---

