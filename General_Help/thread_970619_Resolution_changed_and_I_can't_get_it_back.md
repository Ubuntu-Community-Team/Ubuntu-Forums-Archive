---
title: "Resolution changed and I can't get it back"
date: 2008-11-04
forum: General Help
---

### Post by Auslegung on 2008-11-04
I have an HP widescreen LCD 1440x900 display and it was working fine when I upgraded to 8.10.  Then, this morning after logging in, the resolution changed to 1200somethingx800something.  Now the closest I can get to 1440x900 is 1360x768, and instead of it detecting my screen as HP like it used to, it now says "unknown."  I've done all I know to do and nothing's helped.  Thanks in advance for your vastly superior knowledge.

---

### Post by pedro_orange on 2008-11-04
Hmmm! Strange one!

The new XServer auto-detects your display. So it must be detecting it incorrectly, or something more sinister is going on.

Whats going in your Xorg.0.log / xorg.conf and xrandr outputs?

You may be able to force a certain resolution using your xorg.conf under the screen section.

---

### Post by Auslegung on 2008-11-04
The output of xrandr is:

Screen 0: minimum 320 x 200, current 1360 x 768, maximum 1360 x 1360
VGA connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8* 
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9 

I don't know how to find the output of those other things.  Thanks for the prompt reply.

---

### Post by Peter09 on 2008-11-04
do
```
lshw -C display
```

---

### Post by pedro_orange on 2008-11-04
For the log file (Xorg.0.log):

```
sudo nano -w /var/log/Xorg.0.log
```

For the xorg.conf file:

```
sudo nano -w /etc/X11/xorg.conf
```

---

### Post by Auslegung on 2008-11-04
lshw -C display:

 *-display UNCLAIMED     
       description: VGA compatible controller
       product: 82945G/GZ Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0

sudo nano -w /var/log/Xorg.0.log:

very very long, you want me to paste the whole thing?

sudo nano -w /etc/X11/xorg.conf:

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection


Again, thanks for the help both of you.

---

### Post by Peter09 on 2008-11-04
Are you running Hardy or Intrepid, you graphics card has not got the right driver installed.

---

### Post by Auslegung on 2008-11-04
I'm running Intrepid and I've already gone to System-Administration-Hardware Drives and it gives me nothing.

---

### Post by Adriweb on 2008-11-04
Did you check to see if there is a backup xorg.conf file from before the problem started? It may help to restore that one.

---

### Post by Peter09 on 2008-11-04
Boot into recovery mode and when the menu comes up choose the xfix option. It has worked for a number of people.

---

### Post by Auslegung on 2008-11-04
Tried restarting into recovery mode and choosing xfix and it did nothing.

I don't know much about xorg.conf, but I have 5 different files, one actually named "xorg.conf" and the others names "xorg.conf.20081104######" where # is a random number.  It seems weird that they're all dated today, the day it all went wrong....  Anyway, here's what they look like.  The red text is the only difference in any of them, and it's only added in one of the files.

Section "Device"
	Identifier	"Configured Video Device"
	[COLOR="Red"]Option		"UseFBDev"		"true"[/COLOR]
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

---

### Post by Adriweb on 2008-11-05
Those are the backup files. The numbers are the date and time. 

Try copying the text from one of the files **[B]from before the failure**[/B] and paste it (replacing the text already there) to the xorg.conf file. Save, then log off then back on again.

---

### Post by Auslegung on 2008-11-10
Sorry it took so long for me to reply, the forums never emailed me to say anyone had replied.  Anyway, replaced my xorg.conf with the only different version, restarted and it did nothing.  I just checked the xorg.conf to make sure it's still the "new" version and it is.

---

