---
title: "HP dv2225nr, no sound, no wireless... help please!"
date: 2007-05-17
forum: Hardware &amp; Laptops
---

### Post by omarxcs on 2007-05-17
Hi to all,

I came from another forum as I was (and am) honestly intimidated since I am a complete noob on linux. I have been troubleshooting windows for a couple of years now, but my college education was not on anything computer/programming related, and since all my work experience has been with windows, you can imagine how "complicated" some things seems...

Case in point: DRIVERS!

On my hp I'm running Kubuntu (Feisty), it all works fine except the broadcom wireless card and the conexant hd sound card.

I did some search in the forums, but all I see is stuff like:

"I had a problem with the broadcom card, but after running the "******" [insert name] package it now works..."

I also get this a lot:  "...you might have to use ndiswrapper or madwifi"

My question is 'how'?

I just recently started to "get" the whole apt system to finally get some apps to install, but finding the drivers i need/or making my hardware work has been extremely daunting. Any help will be greatly appreciated.

---

### Post by phetre on 2007-06-06
Hi Omarxcs! I hope this reply isn't too late to help you. A friend of mine just got wireless working on her dv2225nr (Kubuntu Feisty) by installing ndiswrapper as described here: [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

As for sound, there's no complete solution yet. It seems that booting into Windows Vista can screw up sound in Linux on subsequent reboots; you can fix it temporarily by shutting down completely, unplugging the AC power cord, and booting into Linux. Even then, it might take several tries. There's lots of information in this thread: [http://ubuntuforums.org/showthread.php?t=455147](http://ubuntuforums.org/showthread.php?t=455147)

---

### Post by Acglaphotis on 2007-06-09
I have the same laptop, i got working everything:

For sound follow this link
[URL="http://ubuntuforums.org/showthread.php?t=455147"]
http://ubuntuforums.org/showthread.php?t=455147
[/URL]
And remember to unplug when booting from vista to ubuntu

and about wireless is real easy

just do a 

```
sudo aptitude install bcm43xx-fwcutter wifi-radar 
```

and your done, just use wifi radar to use wireless.

Hope i helped.

---

### Post by Galguera on 2007-08-21
hey, i have the same laptop and the command sudo aptitude install bcm43xx-fwcutter wifi-radar doesn't work... the message says that the package can't find 
 and i'm trying to install the nVidia Driver but i can't.... some help.????
Sorry, but my english is so bad!! jajaja xD:lolflag:

---

### Post by A3sthetix on 2007-08-21
> **Galguera said:**
> hey, i have the same laptop and the command sudo aptitude install bcm43xx-fwcutter wifi-radar doesn't work... the message says that the package can't find 
 and i'm trying to install the nVidia Driver but i can't.... 

This link might help:
[https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu](https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu))

The dv2xxx, dv6xxx and dv9xxx series are similar in many ways. From what I gather, much of the hardware is the same... it's just the screen/laptop size that differs.

---

### Post by domoikane on 2008-04-26
Hello, if someone is still looking for a solution and have the HP DV2225nr with Ubuntu 8.04, when you do a fresh install the wireless is not recognized, the drivers are wrong installed what you must do is the following:

cd ~
mkdir b43-temp
cd b43-temp
wget [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
wget [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.80.53.0.tar.bz2
sudo b43-fwcutter -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta.o
sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy

after this and a few seconds later the network light should turn blue. This is an issue with the installer of the drivers, hopefully will be fixed on the final version. Thank you to everybody for giving solutions, they helped me to find this solution.
:guitar:

---

