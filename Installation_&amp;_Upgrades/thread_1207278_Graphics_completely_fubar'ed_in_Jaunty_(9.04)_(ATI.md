---
title: "Graphics completely fubar'ed in Jaunty (9.04) (ATI R600 AGP)"
date: 2009-07-08
forum: Installation &amp; Upgrades
---

### Post by God Of Atheism on 2009-07-08
Hi, I just installed Ubuntu Studio 9.04 on my computer, and though the install process went fine, when booting the system, I get a screen with a few small scale copies of the logo at the top and a non-functioning log in form (which seems to have disappeared now). When switching to a terminal things worked, but X does not. I tried things such as installing fglrx and reconfiguring X but to no avail. I then proceeded to try regular Ubuntu 9.04 and got the same result when just choosing the install option. Do I need to go back to 8.10 or is there some way to fix this?

My system is:
gigabyte 7NNXP (nvidia nforce2 MCPT)
amd athlon XP 2500+
1GB (2x 512MB) OCZ PC3200 in dual channel mode
sapphire ati radeon 3650 AGP 512MB DDR2
237GB sata hd western digital 
113GB sata hd seagate (or the larger one is seagate and the other wd)
ide DVDRW drive (probably NEC, but not sure)
floppy drive (probably sony)
viewsonic VP930 LCD monitor 
logitech cordless trackman optical
logitech media keyboard
western digital mybook 465GB USB

---

### Post by God Of Atheism on 2009-07-08
I managed to solve this by using the following two steps:
1. Add xforcevesa to the boot up sequence when installing (for regular Ubuntu the safe graphics option might work, but that is absent in Ubuntu Studio).

After installation, upon restart you get again to a fubar'ed screen.
Now, press ctrl-alt-F1 to get to a terminal log in screen and log in (if this does not work, reboot and start in recovery mode and drop to a root terminal).

Then:
2. sudo dpkg-reconfigure xserver-xorg
3. sudo nano /etc/X11/xorg.conf
4. Add a line 'Option "UseInternalAGPGART" "no"' under 'Section "Device"' and save the file.
5. sudo reboot now

---

### Post by fly360 on 2009-07-08
I currently have the same problem with mine. I'm such a noob that I'm unable to do anything that was said in the last reply. I've tried to start off of the disk but I am unable to do or find anyway of stopping the ATI driver to start it. Someone's help would be appreciated greatly. I'm currently looking in other posts to try too resolve this.

---

### Post by fly360 on 2009-07-08
Bump, Need help on inserting the line in Nano.

---

### Post by fly360 on 2009-07-08
What I'm asking is how do I write it.
Like This?
<option>
UseInternalAGPGART
no
<section>
Device
Then control "O"?

---

### Post by God Of Atheism on 2009-07-10
> **fly360 said:**
> What I'm asking is how do I write it.
Like This?
<option>
UseInternalAGPGART
no
<section>
Device
Then control "O"?

Sorry for the late reply.

More like this (the below is taken straight from my xorg.conf, and the exact details appearing might be different on your machine):
```

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
        Option          "UseFBDev"              "true"
        Option          "UseInternalAGPGART"    "no"
EndSection

```

In nano, just go to the beginning of the EndSection line and press enter, this will add a new blank line. Then use tab to align things for later readability, although space should work as well.

Just note that the UseInternalAGPGART option especially applies to nforce2 motherboards, it might help for others as well, and it probably won't hurt to try especially if things are bad as they are, but it might also not work.

---

