---
title: "Gateway T-1616"
date: 2007-11-10
forum: Hardware &amp; Laptops
---

### Post by mntlasasin on 2007-11-10
I just purchased a Gateway T-1616 notebook (great deal). I installed Ubuntu, my favorite distro, 7.10 and the sound and the wireless will not work. The wireless signal indicator on the notebook is lit up but there is no where to configure the wireless setting. This notebook comes with the Realtek RTL8101E card. I used ndiswrapper to the install the correct Vista driver, XP doesn't work. Ubuntu still does not present an option for wireless in the networking option. Could anyone please help me to resolve this? Thanks.

---

### Post by kevins9 on 2007-11-19
Hi,

I just bought the same laptop, and I too have the same problem you are experiencing with the lack of wireless and sound. However, mine apparently has the Realtek RTL8187B wireless card in it, and not the 8101 that you mentioned yours having. I am a total and complete NEWBIE to Linux, so I'm not even familiar with how to install new drivers, etc., but I did find a linux driver for my card on the realtek site, so you might consider checking there for a driver for yours as well.

I think in the download information, or somewhere else that I was reading, it said something about the driver being good for the "8100 series" cards, so the same driver I found may apply to your card as well.

I am sorry I don't have an answer for you specifically, but hopefully this will help in some way. 

I'm just trying to find out how to either include the driver in the Ubuntu livecd to test it first, or how to install it after booting the livecd, so I can try this distro out before I decide if I want to actually install it. Being the newbie I am, I'm scared to load Linux permanently, and have heard nightmares about trying to install it on a Vista machine, this T-1616 was one specifically mentioned somewhere else. I won't hijack your thread and ask about doing this here, I'll create a new thread in just a few minutes to ask for help, or will SEARCH more on how to install the drivers. One site I read says one thing, another says something entirely different.

Anyway, good luck with yours, and let us know how it turns out, and how you like Ubuntu on it. I really want to run Ubuntu on mine, once I figure it all out.

---

### Post by memm on 2008-01-04
For anyone trying to make wireless and sound work in Gutsy, on a Gateway T-1616:

For wireless:
If your lsusb shows 0bda:8189 as the device id, the realtek driver for linux attached in this [page]("http://ubuntuforums.org/showthread.php?t=571046&page=4") works. The driver available for download at Realtek's page is an older one, and does not work.

For sound:
sudo apt-get install linux-backports-modules-generic

and then add the line
options snd-hda-intel model=dell-m42
to the end of the file /etc/modprobe.d/alsa-base .
And reboot.

---

### Post by option94 on 2008-01-07
I've been looking for this info for weeks.

---

