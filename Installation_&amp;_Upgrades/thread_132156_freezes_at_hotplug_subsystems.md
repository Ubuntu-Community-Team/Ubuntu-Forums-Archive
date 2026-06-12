---
title: "freezes at hotplug subsystems"
date: 2006-02-17
forum: Installation &amp; Upgrades
---

### Post by regnez on 2006-02-17
how do I make it not freeze?

---

### Post by jsestri2 on 2006-02-18
Hi, I have the exact same problem. Here are some more stats on my system though.

I have an Intel P4 3.0ghz processor, on my motherboard which has onboard LAN and Sound.
I have an Nvidia GeForce 6600 graphics card.
As for drives I have an IDE DVD-ROM
and a SATA seagate 250GB hdd.

From google/searching these forums, i have turned up evidence that failure at this step in the startup may have to do with various unrecognized plug and play devices or onboard LAN features. I have tried removing everything possible to boot the system with the bare minimum show above, and it still hangs in the same place.

I'd really love to be able to start the system up, but the only solutions i've seen involve turning off hotplug which i read turns off network support. Without network support, the computer is really fairly useless to me, so is there a solution to this problem? judging from google it seems fairly common, but i have not seen a reasonable solution as of tonight...

---

### Post by cronholio on 2006-02-18
Does it really freeze completely or can you go on by pressing Ctrl-C?

---

### Post by jsestri2 on 2006-02-18
I would say complete freeze because Ctrl+C does absolutely nothing for me. After Ubuntu has been booted, and its in the splash screen thats loading various things with a progress bar, it gets up to "starting hotplug subsystem." Holds for a while. Then all of a sudden bails out into a text version with a bunch of lines that appears to be the non-graphical version of the start-up text. A bunch of lines with [ok]'s next to them. It will then hang right there (it could be an infinite loop for all I know). However, Ctrl+C has no effect, and the only keyboard thing i have noticed does anything is Alt+F1, which brings back the original boot-up text when ubuntu is first starting.

Another option I have read is that if you turn off pci support this problem might be avoided, but since i have no on-board video, my pci express video card is the only option for starting the system. Any suggestions for a real resoltion to this problem would be greatly appreciated.

---

### Post by jsestri2 on 2006-02-18
does anyone know if this is a problem that developers might need to fix? or is it a personal hardware problem?

---

### Post by global_dev on 2006-02-18
i have the same issue on 2 of my computes (exact same thread issue from yesterday) . I have searched to no answer. Dapper loads fine on both of my systems were breezy can not. sad as i owuld like to try ubuntu.

---

### Post by jsestri2 on 2006-02-18
Well, if nobody has a fix for this problem, can anyone suggest an older release of ubuntu that may not have this problem???

---

### Post by jsestri2 on 2006-02-19
I have discovered that my onboard Sound may have been the source of the problem (Disabling it via BIOS allowed it to boot fully.) Now I've got issues with the network and XWindows. Woot!

---

### Post by jsestri2 on 2006-02-19
After a bunch of work and talking with people on the IRC support channel I have finally gotten it to work! Ask anymore questions here if you need any clarification as to what exactly i did.

---

### Post by global_dev on 2006-02-19
what exactly did you do? did you have to mess with the networking or x server?

do you no longer have sound? or did you reenable it?

---

### Post by renzokuken on 2006-02-19
i once had this problem because i left an unrecognised USB IR device plugged in on boot. simply removed it, rebooted and hey presto.

---

### Post by jsestri2 on 2006-02-19
Alright, so initially to get the system to start up all nice and boot up X and Gnome etc. I had to disable my onboard sound, and network. At this point if i was to enable onboard network, my X would not startup correctly, but it still booted to a terminal with internet access, just no graphics. I talked with a guy on the irc support channel, and i got this set of commands to reconfigure Xorg:

cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
dpkg-reconfigure xserver-xorg

After doing this everything works except sound, which i am now working on. If you want to leave the sound enabled, I have found that with mine, adding "snd_hda_intel" and "snd_hda_codec" to /etc/hotplug/blacklist, will allow the system to boot, but you will still lack sound. I'll post back  if i find the solution to my audio problem.

I have a Realtek Audio ALC880 chip on my motherboard, what do you have global_dev?

---

### Post by global_dev on 2006-02-19
the device manager says Intel HD 82801FB/FBM/FR/FW/FRW (ICH6

howvever, the website says realtek HD audio drivers

apparently it is not recognized exactly, any suggestions to exactly see? the computer is real small with heatsinks on everything, so a visual is likely no possible.

edit: the hp page had everything, unbelievable, my sony has none of that

Integrated Intel High Definition(TM) audio (Azalia)
     ** Realtek ALC 880 chipset**
      THX certification support
      8-channels for Full Dolby 5.1/6.1/7.1 surround sound support with Dolby Pro Logic IIx

[http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&lang=en&cc=us&softwareitem=pv-35408-2&os=228&dlc=en&product=1137824&docname=c00498299](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&lang=en&cc=us&softwareitem=pv-35408-2&os=228&dlc=en&product=1137824&docname=c00498299)

---

### Post by ConfidentiaL on 2006-02-20
I have the same problem(have just installed it).

Im just wondering, how do I disable the onboard sound?(I cant find it in the BIOS):-k 

I have an Asus A6Va laptop with an onboard Realtek sound controller(or w/e its called)

---

### Post by jsestri2 on 2006-02-20
Ok, so upon further investigation, and asking questions on the IRC support channel, there are two otions:

1. Go without sound:
If you don't want to hear any sounds except the internal beep of your computer, then it should be easy enough to disable the onboard sound via BIOS and boot ubuntu up fine. EDIT:  (I can't tell you exactly where in BIOS this is...For me i have an ASUS mb, and its under the tab "Advanced" and the item "Onboard Devices."  Other than that, all i can say is search all the menus, BIOS is a fairly small maze, so you should be able to search it by brute force if it is not quickly apparent where it is.) If you would like to disable loading the sound device so that you can leave your onboard sound enabled, and it won't freeze hotplug (enabled dosent mean sound will work, it won't!) then edit the file /etc/hotplug/blacklist and add 

(these _'s might be -'s. I forget exactly, but just stick with the going format in the file.)
snd_hda_intel
snd_hda_codec

2. To go with sound you can try, upgradeing your kernel to the newest revision 2.*.*-10. If that dosen't work, you can turn on the universe repositories, and upgrade alsa. And if that dosent work, Breezy Badger isn't for you, go get a new Dapper Flight 4 CD (hopefully you haven't done too much with the computer yet, and a fresh install is possible. Otherwise i was told an upgrade from breezy to dapper was possible without a fresh install, but it will be more work.)

I was also told that the sound *can* be made to work under breezy by editing certain files manually. But the amount of work to fix those, and the stuff you break by messing with those files, is aparently a lot more than just upgrading to dapper flight4.

B.T.W. If you have any IRC know-how, or are just bored of waiting for responses in the forum, the irc support channel is a much quicker way of obtaining help.

---

### Post by pizzach on 2006-03-20
I'm using an Asus.  I need to disable my audio in hotplug.  But I don't do it in the bios.  When the computer freezes, just press Alt + Sys Rq (Pri Sc) + E.  Then go to the terminal, cd /etc/hotplug.  Then add snd-hda-intel to the the blacklist.  I read this on another thread here.

Gl

---

