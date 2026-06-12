---
title: "Support for Logitech g910 ??? Russo's Gnome 15 files down ??"
date: 2015-04-07
forum: Hardware
---

### Post by SpindizZzy on 2015-04-07
Hi all,


I recently aquired a Logitech G910 keyboard. I was wondering if anyone has it up and running on **Ubuntu 14.04 LTS 64bit** ??


I know it is not natively supported, and I found that previous versions of the keyboard (g510) were fully functional by using "Russo's Gnome 15 Drivers"

Sadly, Russo's website (the one containing the project) has been down for a while. I did find the files, posted by the nice Mr. Michael J. Ford on his blog here [http://www.slashetc.us/2015/02/russos-gnome15-files-pulled-from-working-install/](http://www.slashetc.us/2015/02/russos-gnome15-files-pulled-from-working-install/), but I can't figure out how to get them running.

Can anyone help me please ??

EDIT: I did encounter this thread too [https://bbs.archlinux.org/viewtopic.php?id=182335](https://bbs.archlinux.org/viewtopic.php?id=182335), but it only speaks of Archlinux. Posters there are wondering if it will work on Ubuntu. Did someone try already ?? If not, I will look into it soon and post back here. :p

---

### Post by Radall on 2015-10-05
Hi,

wondering the same thing and I'm also running Ubuntu 14.04 LTS 64bit.

I have a dual boot with Win 8 and I don't know what the key coloring depends on, but sometimes if I boot in Ubuntu it either uses the standard blue or the "rainbow" scheme, which is a little disturbing to work with over time xD

---

### Post by SpindizZzy on 2015-10-05
Hi Radall (and others coming here for help),


I booted in Win once, installed the G910-Logitech software there and configured my keyboard. Since then, whenever I reboot into Linux the colour scheme is shown like I configured it in Win (I'm guessing the config is stored in memory on the hardware). I am not using the G-keys atm, so I have no idea if the macros work. Same goes for the M1-M4 keys top left. I just use this keyboard to type in the dark, basically :grin:


I did (re)try those drivers I mentioned above as well, but that didn't work out :(

So, I guess we are stuck with this workaround :)

---

### Post by Radall on 2015-10-06
This is interesting, but would explain why my keyboard was going all rainbow only sometimes.
So when you say "configured", do you mean you changed the color pattern and when you booted into Ubuntu the colors stayed the same?
If so, how is your dual boot set up then and respectively, where did you install the Logitech Gaming Framework to?

---

### Post by SpindizZzy on 2015-10-12
Sorry for the late reply, Radall, I was travelling :)

Yes, indeed: In windows i adjusted the colors of the keys and the brightness to fit my personal preference and when I boot in Ubuntu the configuration is exactly the same. I used the standard software package (it's called ' Logitech Gaming Support') and installed into the default location (I believe c:/program files) To be clear: i never installed a driver under Ubuntu. It just  'works' without.

My dual boot is as follows: I  had a WIn 7 on that PC, and installed Ubuntu 12.04 LTS on top of it (and i upgraded later to 14.04 LTS) The GRUB-bootloader made the dual boot run smoothly from the beginning. I love Linux :p

---

### Post by Radall on 2015-10-13
Alright, lucky you.
Got basically the same set up (8.1 instead of 7) and it's doing nothing.

What about your profile management?
Did you just use the standard profile? Did you mark it as permanent? (I mean, the priority setting that's on top of all other profiles. Sorry, I got the software in German, so Idk if it's called 'permanent')
Or do you only have one profile?

Thanks for understanding my curiosity ;)

---

### Post by SpindizZzy on 2015-10-14
Ok, so I wanted to boot into Win to formulate answers to your questions, and I found out that I completely erased the HD Win 7 was sitting on 8-). I sort of forgot, but then recalled that I did this a few weeks ago, in order to do a ' fresh' install :p.
That fresh install never happened, but the keyboard works as it always did. This makes me believe even stronger that the configuration (once set) is stored onboard the G910.

I did use the default profile to configure, yes (so I only had one profile). I cannot remember if I marked it 'permanent' or not, sorry. I would kindly suggest you try both :)

---

### Post by SpindizZzy on 2015-11-08
I found out how this 'on board memory' works, so I will post it here as a reference for others (and, yes, myself as well :))

I reinstalled a Win 7 on my PC and that made my nice G910 colour scheme disappear. It just went to the default ocean greenblue :( 

I googled and bumped into this post, which is an effective workaround:
[https://forums.logitech.com/t5/Logitech-G-Keyboards/Why-does-the-G910-Orion-reset-to-green-from-custom-colors-when/td-p/1350151](https://forums.logitech.com/t5/Logitech-G-Keyboards/Why-does-the-G910-Orion-reset-to-green-from-custom-colors-when/td-p/1350151)

Basically, you install Logitech Gaming Software, and define the colouring profile. Then ctl+alt+del and end the "LCORE.EXE" process. When you then shut down windows the LGS does not send a 'return to ocean colour on all keys'-message to the G910.

Upon reboot in Linux after that the last known colour profile (the one you defined in LGS) is kept as default, allowing you to see all those nice colours you chose :)

It could even be that the colouring profile is persistent when you unplug the keyboard and use it on a different PC/laptop, but I haven' t tested that yet.

---

### Post by Radall on 2015-11-08
Nice, gotta try this when I'm home tomorrow. Thanks for further investigating! :D

---

### Post by Wes_Eason on 2016-02-24
Sorry, lost network connection for a bit and somehow posted twice.

---

### Post by Wes_Eason on 2016-02-24
> **SpindizZzy said:**
> Hi Radall (and others coming here for help),

I am not using the G-keys atm, so I have no idea if the macros work. Same goes for the M1-M4 keys top left.



Does killing the program make the G-keys work?  I do not have windows to test atm.  Without trying the thing where
you kill the software on windows (i.e. with the ocean blue keys), the G-keys send key codes as if they were F-keys.  
G5 refreshes webpages as if it was F5.  Also, xev produces this output when the keys are pressed 
(I added the comments though):

```

# F5 key pressed
KeyPress event, serial 37, synthetic NO, window 0x3c00001,
    root 0xf3, subw 0x0, time 6075543, (-246,275), root:(739,327),
    state 0x10, keycode 71 (keysym 0xffc2, F5), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

# F5 key released
KeyRelease event, serial 37, synthetic NO, window 0x3c00001,
    root 0xf3, subw 0x0, time 6075597, (-246,278), root:(739,330),
    state 0x10, keycode 71 (keysym 0xffc2, F5), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

# G5 key pressed
KeyPress event, serial 37, synthetic NO, window 0x3c00001,
    root 0xf3, subw 0x0, time 6077762, (-246,276), root:(739,328),
    state 0x10, keycode 71 (keysym 0xffc2, F5), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

# G5 key released
KeyRelease event, serial 37, synthetic NO, window 0x3c00001,
    root 0xf3, subw 0x0, time 6077856, (-246,277), root:(739,329),
    state 0x10, keycode 71 (keysym 0xffc2, F5), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

The M-keys trigger no events from xev. This could mean either that the keyboard is sending F-key codes
to the computer, as if it was in some kind of compatibility mode, or that the key codes it is sending 
are mapped to the F-keys.  It's been a while since I read up on xev, but I believe the first case is more
likely.

---

### Post by mohamadsaada on 2017-02-08
Hi, to control the leds you can use LogiGSK, which can be found at [https://github.com/MohamadSaada/LogiGSK](https://github.com/MohamadSaada/LogiGSK)

---

### Post by SpindizZzy on 2017-02-08
Too cool !!

Thank you very much Mr. mohamadsaada :D

---

