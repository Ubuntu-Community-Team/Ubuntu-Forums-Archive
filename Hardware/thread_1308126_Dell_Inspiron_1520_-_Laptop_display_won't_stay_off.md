---
title: "Dell Inspiron 1520 - Laptop display won't stay off when lid is closed"
date: 2009-10-31
forum: Hardware
---

### Post by pi.boy.travis on 2009-10-31
I have a Dell Inspiron 1520, currently running Ubuntu 9.10.  I have gnome-power-manager configured to turn the display off when the lid is closed, however, the display only stays off for about two seconds, then comes back on with the backlight on 100%.  I can use 

```
xset dpms force off
```

to turn off the display.  The display stays off if I kill gnome-power-manager.  

This is a potentially dangerous issue.  I don't want the heat to damage the keyboard, or worse.  None of my other laptops, Dell or otherwise, have this issue.  This started around Karmic alpha 4/5.  I filed a bug a few weeks ago, but it has received no attention whatsoever.

Does anyone else have this issue?  With any other laptops?  Does anyone have any fixes/workarounds/solutions?

Thanks

---

### Post by Hakkatuka on 2009-10-31
Same issue here on 2 laptops: dell xps m1330 and hp mini 5101. No fixes.

---

### Post by pi.boy.travis on 2009-10-31
After further observation, I'm seeing that the display will stay off for about 5 minutes after awakening from sleep of hibernate.  Other than that, there is about a 15% chance that it will work.  Sometimes a reboot helps, sometimes it doesn't.  It's almost random.  I can't pin down one variable that causes the display to malfunction.  Only killing gnome-power-manager reliably solves the problem. . .

---

### Post by Capissen on 2009-11-01
I have an Inspiron 1420 (aka Vostro 1400) that is experiencing the exact same behavior.  Backlight shuts off for approximately two seconds, then comes back on.  Killing gnome-power-manager forces the proper behavior.  Problem was not experienced in Jaunty.  I've tried messing around with BIOS power settings, etc., but no luck.

Hopefully a patch is forthcoming.

---

### Post by pi.boy.travis on 2009-11-03
I have installed all updates as of Nov. 3rd, and now the backlight stays off the first time I close the display, but if I reopen then re-close it, it returns to the incorrect behavior.  If I logout and log back in, the display works properly one more time, then returns to the incorrect behavior.  This is a weird bug. . .

---

### Post by pi.boy.travis on 2009-11-10
I think [this]("http://blogs.gnome.org/hughsie/2009/08/17/gnome-power-manager-and-blanking-removal-of-bodges/") patch might be of help?  I'll test and report back, but this serious issue needs to be resolved.  I have been reading about people that are getting burn-ins because of this bug.  

*This bug is damaging user's hardware!*

---

### Post by bpeyser on 2009-11-17
This is something I only noticed after upgrading to 9.10. My screen also does not blank when the lid is closed. Also, my computer fails to suspend when on battery and the lid is closed, as it is set in gnome-power-manager. However, sometimes it will suspend. Strange, and I'm thinking about restoring my 9.04 install. Things used to work for me.

Some info:
I'm using a Dell Latitude D820
I use a port replicator with external monitor when I'm in the office. The external LCD monitor uses the same native resolution as my LCD screen (1920x1200). Also, I'm using DVI for the external LCD.
I have removed gnome-screensaver and use xscreensaver instead.
I have nVidia driver version 185.

I saw this:
>  				 				**Re: Dell Inspiron 6400 - backlight stays on when the lid is closed** 			
 			 			 		   		 		 		Comment out the 9th line (the one that says "if [ `CheckPolicy` == 0 ]; then exit; fi") of /etc/acpi/lid.sh. I hope that works!

from xodis [here]("http://ubuntuforums.org/showthread.php?t=970347")

I gave that a try and it did indeed blank the screen. When I opened the lid, the screen came back on and the screen was locked by xscreensaver (seems good). However, if I am using the external monitor, it is blanked also! So I couldn't close my laptop while using an external monitor. That will not work at all. I wonder if any of this hads to do with my nVidia X server settings--the displays are set to "Twinview" and are clones. I'll give it a try with separate X displays too.

---

### Post by pi.boy.travis on 2009-11-21
> **bpeyser said:**
> This is something I only noticed after upgrading to 9.10. My screen also does not blank when the lid is closed. Also, my computer fails to suspend when on battery and the lid is closed, as it is set in gnome-power-manager. However, sometimes it will suspend. Strange, and I'm thinking about restoring my 9.04 install. Things used to work for me.

Some info:
I'm using a Dell Latitude D820
I use a port replicator with external monitor when I'm in the office. The external LCD monitor uses the same native resolution as my LCD screen (1920x1200). Also, I'm using DVI for the external LCD.
I have removed gnome-screensaver and use xscreensaver instead.
I have nVidia driver version 185.

I saw this:

from xodis [here]("http://ubuntuforums.org/showthread.php?t=970347")

I gave that a try and it did indeed blank the screen. When I opened the lid, the screen came back on and the screen was locked by xscreensaver (seems good). However, if I am using the external monitor, it is blanked also! So I couldn't close my laptop while using an external monitor. That will not work at all. I wonder if any of this hads to do with my nVidia X server settings--the displays are set to "Twinview" and are clones. I'll give it a try with separate X displays too.

Since you aren't using gnomescreensaver, I am thinking that the issue must be with X11.  I would guess that the DELAY parameter in the Xlog that screen blanking relies on is in-face reset by the screen blanking, this turning the screen back on. . .  I'll have to see if I can find a bug report. . .

---

### Post by bpeyser on 2009-11-22
Well I had too many small problems, so I went back to Jaunty. That was interesting, since I had to re-install grub from the live CD after restoring from Clonezilla. After about 10 attempts I finally got it working again.

Maybe I'll try Karmic again next year.

-bpeyser

---

### Post by mgol on 2009-11-23
See this bug report:
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/449188](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/449188)
I suggest You to subscribe to it, it has not bring too much attention so far. And bugs should definitely be fixed on launchpad, not ubuntuforums. :)

---

### Post by Daniel Browne on 2010-01-12
I have the same problem on an HP 6730b. All power settings are correct, when I close the lid the screen goes off for a second then comes on again. Running Karmic.

---

### Post by DodgeV83 on 2010-01-26
Just got an update in gnome-power-manager: (proposed)

+ Fix gpm_button_is_lid_closed to return an updated value from
      DeviceKit-Power instead of its own locally stored value which may be
      outdated 

Can anyone confirm if this solves the problem?  I'm running Ubuntu in Virtualbox now to avoid this issue...

---

