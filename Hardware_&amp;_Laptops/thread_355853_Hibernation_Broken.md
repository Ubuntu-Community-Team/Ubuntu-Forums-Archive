---
title: "Hibernation Broken"
date: 2007-02-07
forum: Hardware &amp; Laptops
---

### Post by brettr on 2007-02-07
Hello, Hibernation just broke. It seems to close down alright, but when i boot up again the usplash screen shows, then a horizontal gray bar appears at the top of the screen. Next the screen goes black (All of this used to happen when it was working). After this the cursor appears and then instead of getting the lock screen enter password prompt, i the cursor changes to the please wait circle thing(windows hourglass equivalent) and then back to a cursor, and then this repeats until the laptop shuts itself off. 

I have tried changing to a different terminal but nothing happens

I am running A Dell Inspiron 6000, Pentium M 1.6 Ghz, Intel 915G video card, IPW2200
I added ipw2200 to the /etc/default/acpi-support file in the modules to unload and reload field because the wireless was not working properly on resume before. This fixed the problem and it was working fine for a while after that

The last thing i remember doing was installing vim-full

If anybody could point me to some other posts or has any suggestions, please reply i really need the hibernate function.

---

### Post by zardoz on 2007-02-13
I get a similiar problem here (but on a desktop system).

But for me it hangs completely with that gray horizontal bar (are you sure about the vertical?).

Here my system:
Mainboard: Gigabyte GA-965P-DS4 (Intel P965 Chipset)
CPU: Intel Core 2 Duo
Graphics: GeForce 7600 GT
Samsung HDD and DVD-Burner both on SATA
HDD in IDE Emulation Mode
Ubuntu 6.10

---

### Post by link141 on 2007-02-14
Me three (I've also got a desktop system)

The system boots through grub, the loading screen comes up (the first one on boot), that darn gray horizontal bar comes up, and it locks.  I then have to reboot.

Here's my system specs:
Motherboard: ASUS P4V8X-MX 
    Chipsets: VIA P4M800 and VIA 8237R PLUS (the second is the sound mixer)
CPU: Intel Pentium4 3.0GHz with HT
Kubuntu 6.10  

I also have another (better supported) system that has Kubuntu 6.10 on it, so I should see if it has this same problem.

---

### Post by hardyn on 2007-02-14
i have had to deal with this a fair bit, fun of a notebook...

you almost invariably have to add vga=791 (or 780) to the boot string, its solves the problem 90% of the time.

definitely with X series ATIs and fglrx and nvidias using nvidia-glx
'radeon' seemed to be good out of the box, and is actually my preferred driver (from ATI) despite it not benching as well as fglrx, i find it to be much more stable!

let me know if this works for you

---

### Post by brettr on 2007-02-15
Actually, i have the vga=791 in my boot string, i added it so i could use a different usplash screen, i think this actually solved the horizontal bar problem(have not tried suspend/hibernate in a couple of days) but it did not solve the black screen with the please wait thingy leading to reboot. I could try 780.

---

### Post by brettr on 2007-03-15
Yes i am responding to my own post again, hopefully somebody will find any of this useful. Okay, So i am still trying to track this down. I have tried a few more things. I set 

```

SAVE_VBE_STATE=true

POST_VIDEO=true

``` to false in /etc/default/acpi-support

I have tried to boot with vga=791 in the boot string and without it. I have also done a 

```
dpkg-reconfigure xserver-xorg
``` To make sure everything was default

I am finding errors such as ```
(WW) I810(0): Bad V_BIOS checksum
```

I have no idea what this one is about.

also

```
(WW) I810(0): xf86AllocateGARTMemory: allocation of 16 pages failed
        (Cannot allocate memory)
```

I have read that this can be solved by adding a "VideoRam <somevalue>" directive to the driver section of xorg.conf, although i don't know how to see just how much memory i should put there, so i will try that.

When i do load AIGLX i get a whole slew of these errors which i have read means, that  my video card cannot display truecolor in 32 or more planes. This is a hardware limitation and afaik cannot be overcome by changing your settings.

```
(WW) AIGLX: 3D driver claims to not support visual 0x23
```

and there is the ```
(WW) I810: No matching Device section for instance (BusID PCI:0:2:1) found
```

Which i think is the whole problem in the end anyways.

I also am still getting all of those font path does not exist things

I would also like to note that if i leave it for long enough the screen will get squished to 1/4 of the size of the panel,at the top, with 3 or 4 copies showing something, probably the BusID error. And i can go to a virtual terminal and login and shutdown, although i can't see what i am doing.

So Alas i am going to continue to try and figure this out, the worst part is, that it was working originally. Last resort might be to do a fresh install, which i don't really want to do but i might consider it.

oh and here is one of the logs if anybody is interested:

---

### Post by zardoz on 2007-10-24
I just want to report, that this problem still remains also in Gutsy.
Still that damn horizontal grey bar at startup after a hibernate with a complete hangup (only hard reboot possible).

---

