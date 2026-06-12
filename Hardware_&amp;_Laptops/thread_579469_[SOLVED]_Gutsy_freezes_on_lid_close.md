---
title: "[SOLVED] Gutsy freezes on lid close"
date: 2007-10-18
forum: Hardware &amp; Laptops
---

### Post by filiep on 2007-10-18
Hi,

I'm running Gutsy with the latest updates on my Dell d505
When I close the lid or when I touch the lid sensor, my portable freezes. I get a black screen with mouse pointer but I can not move the mouse. Even by pressing the powerbutton the system does not respond anymore. I have to power off to be able to reboot by pushing the powerbutton for 5 sec.

Anybody have similar problem?
Thanx,
F.

---

### Post by filiep on 2007-10-18
I found the problem: as my D505 is using a i810 graphics card, Gutsy installed the Intel Experimentel Driver.
By changing the driver to the i810 driver the lid problem is solved.

Rgrds,
F.

---

### Post by PiR2 on 2007-10-22
I had exactly this same problem on Gutsy with my Dell Latitude X300.  I switched the driver as you suggested and the problem has been resolved.

Thanks for your help!

---

### Post by derred on 2007-10-24
Same on Latitude D400 with 855GM

---

### Post by pawouk on 2007-11-15
Hello, could you please help me...  I am a linux newbie trying to run Kubuntu 7.10 on my Latitude D505. First of all I have a problems with bios - I think its all about the graphic card... (version A09 didnt work-black screen during loading live cd, A10/11 did work but freezed while powering it off, I only got it working when I installed Kubuntu on A11 and than changed it to A10, but still I get the problem with closing the lid mentioned above...) 

What version of bios did you use? How do you change the driver? 

Thanks for any reply. Lukas Pour

---

### Post by cptR3D on 2007-12-31
what command do i need to run to switch the driver??

---

### Post by olafurg on 2008-01-16
I'm having exactly the same problem as described on top and when I change the driver to i810 through System - Administration - Screens and Graphics and then reboot, my computer doesn't start up, just switches colors on the screen and I need to reboot in recovery mode and restore the old /etc/X11/xorg.conf file.

Is there some other way you guys switched the driver to i810 than using the GUI?

Thanks in advance from Iceland, ÓG

---

### Post by jerrykenny on 2008-01-16
It might be safest to go to system/preferences/power management

Look at the settings for closing the laptop lid . . . . you might want to change this to do do-nothing

Its a kludge, but for the guys whose hardware isnt fully integrated into the kernel . . . .

---

### Post by olafurg on 2008-01-18
Thanks jerrykenny, but it doesn't work. Still get the freeze and need to reboot using the power button. Any other ideas or solutions? It's getting my girlfriend pretty annoyed and if I don't solve this I might be forced back to Windows :(

---

### Post by anneb on 2008-03-02
I am having the lid close freeze problem as well on my Dell Latitude D505 / Gutsy 7.10 / 1024 x 768 laptop screen.

I tried the following:

changed file /etc/X11/xorg.conf (made backup first!)

original:
```
Section "Device"
        Identifier      "Intel Corporation 82852/855GM Integrated Graphics Device"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection
```

new: 
```
Section "Device"
        Identifier      "Intel Corporation 82852/855GM Integrated Graphics Device"
        Boardname       "intel"
        Busid           "PCI:0:2:0"
        Driver          "i810"
        Screen  0
EndSection

```

After rebooting, the lid-close freeze no longer occurs. But in my case the display is shifted some 20 pixels downwards, the mouse pointer is not displayed and the top 20 pixel lines show strangely flickering pixels when I move the (now invisible) mouse pointer around the screen.

Any suggestions on how to get the i810 display driver working properly or other ways to get around the lid-close-freeze problem?

---

