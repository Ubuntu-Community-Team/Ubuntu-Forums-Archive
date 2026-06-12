---
title: "No Sound/Audio Lenovo T60"
date: 2008-10-31
forum: Hardware
---

### Post by pcmartinex on 2008-10-31
Hello All, 

I am at a lost.  I did an update from 8.04 to 8.10 the other day and everything works well except that I do not have any sound/audio.  I have the basic beeps but anything beyond that nothing - MP3s, web audio etc.  I have installed the latest Flash player 10.  I have search the forums and can't find anything to address this problem.  

I have a Lenovo T60 with the Ubuntu 8.10 with all the latest updates.  I am very new to ubuntu so I am unsure about the troubleshooting steps to fix this; other than go to the GUI for sound and everything is set to autodectect.  

Any help would be wonderful!!

Thank you!

---

### Post by ardvark71 on 2008-10-31
> **pcmartinex said:**
> Hello All, 

I am at a lost.  I did an update from 8.04 to 8.10 the other day and everything works well except that I do not have any sound/audio.  I have the basic beeps but anything beyond that nothing - MP3s, web audio etc.  I have installed the latest Flash player 10.  I have search the forums and can't find anything to address this problem.  

I have a Lenovo T60 with the Ubuntu 8.10 with all the latest updates.  I am very new to ubuntu so I am unsure about the troubleshooting steps to fix this; other than go to the GUI for sound and everything is set to autodectect.  

Any help would be wonderful!!

Thank you!

Hi...

I can't guarantee a solution but we can try. :) Please open a terminal window and type in the command...

```
lspci
```

Please post the results.

Also, please see this thread for additional help...

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Best Regards...

---

### Post by pcmartinex on 2008-11-01
ardvark71,

Thank you for the reply!!  Here is the results:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc M52 [Mobility Radeon X1300]
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller

Again, thank you very much!!

---

### Post by ardvark71 on 2008-11-01
Hi...

See if the link I provided above can solve your problem. If not, post back and perhaps I, or someone else, can try to help. :)

Best Regards...

---

### Post by pcmartinex on 2008-11-01
Will do! 

I'll let you know either way.

Thank you!

---

### Post by ardvark71 on 2008-11-01
> **pcmartinex said:**
> Will do! 

I'll let you know either way.

Thank you!

You're welcome! :)

---

### Post by pcmartinex on 2008-11-02
So I went through and did everything in the link you provided and still did not have any sound.  BUT I did find a reference to PCM and the gnome-volume-control applet.  So I went into my terminal window and typed

gnome-volume-control

At that point I noticed that PCM was set to mute.  I had some music playing in the background (with no sound) and at the moment that I selected unmute, the speakers were blasting (Had everything on 100%).  

I am unsure if all that I did with the link you provided PLUS the gnome-volume-control application resolved the problem, but at this moment my sound works.  

Thank you for your time and I hope this info can help someone else.  For I had sound with 8.04 but lost it with the upgrade to 8.10.  

THANK YOU!!

---

### Post by ardvark71 on 2008-11-02
> **pcmartinex said:**
> So I went through and did everything in the link you provided and still did not have any sound.  BUT I did find a reference to PCM and the gnome-volume-control applet.  So I went into my terminal window and typed

gnome-volume-control

At that point I noticed that PCM was set to mute.  I had some music playing in the background (with no sound) and at the moment that I selected unmute, the speakers were blasting (Had everything on 100%).  

I am unsure if all that I did with the link you provided PLUS the gnome-volume-control application resolved the problem, but at this moment my sound works.  

Thank you for your time and I hope this info can help someone else.  For I had sound with 8.04 but lost it with the upgrade to 8.10.  

THANK YOU!!

Hi...

You're more than welcome, glad I could help, even if indirectly! :)

Actually, you've discovered an aspect that I had forgotten about (unmuting in "gnome-volume-control") that should be very helpful in assisting others with sound problems. :)

So, thank you, too! :KS 

Best Regards...

---

### Post by Narkolas on 2008-11-03
I have the smae hardware and same problem, also te PCm was muted, but that didn't do it for me, so i will try the link mentioned, and see if it's actualy a combination.

:confused:

---

### Post by mcclown on 2008-11-03
> **pcmartinex said:**
> So I went through and did everything in the link you provided and still did not have any sound.  BUT I did find a reference to PCM and the gnome-volume-control applet.  So I went into my terminal window and typed

gnome-volume-control

At that point I noticed that PCM was set to mute.  I had some music playing in the background (with no sound) and at the moment that I selected unmute, the speakers were blasting (Had everything on 100%).  

I am unsure if all that I did with the link you provided PLUS the gnome-volume-control application resolved the problem, but at this moment my sound works.  

Thank you for your time and I hope this info can help someone else.  For I had sound with 8.04 but lost it with the upgrade to 8.10.  

THANK YOU!!

Good work, there's a lot of other threads on here with the same problem. There's something that seems to break when upgrading to Intrepid from Hardy for some cards....and you've found it

---

### Post by yuesefa on 2008-11-05
I have the same problem here. Any clues on this thread?

---

### Post by Narkolas on 2008-11-06
> **Narkolas said:**
> I have the smae hardware and same problem, also te PCm was muted, but that didn't do it for me, so i will try the link mentioned, and see if it's actualy a combination.

:confused:

Two things i had to make the sound work again.

1. Add "snd-hda-intel" to the "/etc/modules"
2. type "gnome-volume-control in console and unmute PCM


I still have problems playing sound in flashplayers, so if anyone has a clue to this please hint me up :)

---

