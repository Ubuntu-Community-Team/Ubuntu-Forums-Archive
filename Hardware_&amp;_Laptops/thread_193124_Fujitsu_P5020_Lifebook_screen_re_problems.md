---
title: "Fujitsu P5020 Lifebook screen re problems"
date: 2006-06-09
forum: Hardware &amp; Laptops
---

### Post by Jubalgunn on 2006-06-09
I have a Fujitsu P Lifebook P5020 and have been using Ubuntu with it since Breezy.
However I have Never been able to get the screen resolution above 1024 x768.
Has anyone got any ideas/methods of how i can get the diplay working at its native resolution of 1280 x 768.

Would be most grateful for some help!!

---

### Post by manonabus on 2006-09-06
I also have a P5020 and I have just worked out how to do this. I am using Dapper Drake.

First, I installed 915resolution using the Synaptic Package Manager (System > Administration > Synaptic Package Manager). I selected a package at random from the  top right-hand section of the window, then typed 915resolution. This took me through to the synonymous package. I right-clicked on 915resolution and selected 'Mark for Installation'. Then I clicked the Apply button at the top and waited for the dialogue box to tell me when everything was complete.

Next, I used the 915resolution program to check that the desired resolution was available. I used the Terminal program (Applications > Accessories > Terminal) and typed the following command: 

[COLOR="Sienna"]sudo 915resolution -l[/COLOR]

After entering my password I got the following output:


[COLOR="Navy"]Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 855GM
BIOS: TYPE 2
Mode Table Offset: $C0000 + $3c3
Mode Table Entries: 21

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 36 : 1024x600, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1280x768, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 47 : 1024x600, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1280x768, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 56 : 1024x600, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1280x768, 32 bits/pixel[/COLOR]


Mode 5c had the resolution I wanted, so there was no need to change any of them. Hopefully you will find the same thing on your P5020.

Next I changed my xorg.conf file, using the Terminal program again. First I backed up the original file using the following command:
[COLOR="Sienna"]
sudo cp /etc/X11/xorg.conf /etc/X11/xorg_old.conf[/COLOR]

Then I opened the xorg.conf file in an editor:
[COLOR="Sienna"]
sudo gedit /etc/X11/xorg.conf[/COLOR]

There was a section in the file that looked like this:


[COLOR="Navy"]Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection[/COLOR]


I added a line and saved the file so that the above section looked like this (note the line beginning 'Option')


[COLOR="Navy"]Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
[COLOR="Sienna"]Option "ForceBIOS" "1024x768=1280x768"[/COLOR]
EndSection[/COLOR]


Finally,I edited the 915resolution init script. I backed it up first in Terminal like this: [COLOR="Sienna"]sudo cp /etc/default/915resolution /etc/default/915resolution_old[/COLOR]

Then I opened it like this: [COLOR="Sienna"]sudo gedit /etc/default/915resolution[/COLOR]

The file when opened looked like this:

[COLOR="Navy"]#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
MODE=auto
#
# and set resolutions for the mode.
#
XRESO=
YRESO=
#
# We can also set the pixel mode.
# Please note that this is optional,
# you can also leave this value blank.
BIT=
[/COLOR]

I changed the file, editing the MODE, XRESO and YRESO settings so that after I saved it the file looked like this:

[COLOR="Navy"]#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
MODE=[COLOR="Sienna"]5c[/COLOR]
#
# and set resolutions for the mode.
#
XRESO=[COLOR="Sienna"]1280[/COLOR]
YRESO=[COLOR="Sienna"]768[/COLOR]
#
# We can also set the pixel mode.
# Please note that this is optional,
# you can also leave this value blank.
BIT=[/COLOR]


Then I rebooted....problem solved.

I used the following link to help me out: [https://help.ubuntu.com/community/i915Driver](https://help.ubuntu.com/community/i915Driver)

---

### Post by waitingallday on 2006-09-07
Hi,

I'm also running Dapper Drake on a P5020. I agree with manonabus, 915resolution is definitely the go, but I only needed to change xreso=1280 and yreso=768 to the file

/etc/default/915resolution

---

### Post by Jubalgunn on 2006-09-24
Thanks very much for the help, absolutely fantastic. :)

---

### Post by echo6 on 2006-09-25
You can also add a modeline entry for xorg.conf or XF86 config file.   Try the online modeline generator [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

This sometime helps with awkward gfx cards that don't wanna play nice :-)

```
Section "Monitor"
        Identifier      "Monitor"
        HorizSync       28-49
        VertRefresh     43-72
        Option          "DPMS"
        Modeline "1024x768"    65    1024 1032 1176 1344   768  771  777  806 -hsync -vsync
EndSection
```

---

