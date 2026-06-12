---
title: "Unresponsive Aiptek 12000U on a 08 Macbook"
date: 2011-03-19
forum: Hardware
---

### Post by Masquerade on 2011-03-19
Hey everyone.
So I have an Aiptek 12000U graphics tablet that used to work in Lucid.
I havent used it for a while and Im wanting to set it up on a fresh 10.10 installation (everything is up to date; this is a 2008 Model of a Macbook Pro.).

I followed the instructions in [this wiki article]("https://help.ubuntu.com/community/AiptekTablet"). However, the behaviour after is exactly the same before: The cursor moves as it should when i hover with the pen over the tablet but as soon as I click, the cursos becomes unresponsive to that "hovering" and I can only move the mouse by dragging it (holding the pen down on the tablet)

Does anyone have an idea what could cause this?
Thanks a lot in advance!

---

### Post by Masquerade on 2011-03-20
le bump

---

### Post by Favux on 2011-03-20
Hi Masquerade,

Well what model is it?  Enter in a terminal:
```
lsusb
```
We want to look at the output especially the line with the tablet.

---

### Post by Masquerade on 2011-03-20
Thanks a lot for the reply!
If you mean the tablet model, its an 12000U like mentioned in the title...?
I will be pasting the output in a few hours.

---

### Post by Favux on 2011-03-20
We're interested in the actual manufacturer/chipset so we're sure of which driver to use.  The *lsusb* will give us the vendor and product IDs.  Lots of tablets are rebranded and we want to know the OEM.

---

### Post by Masquerade on 2011-03-20
Aaah, I didnt know this.
Thats the lsusb *without* the tablet plugged in
```

benjamin@benjamin-MacBookPro:~$ lsusb
Bus 007 Device 003: ID 05ac:0231 Apple, Inc. Internal Keyboard/Trackpad (MacBook Pro 4,1) (ISO)
Bus 007 Device 002: ID 05ac:8242 Apple, Inc. IR Receiver [built-in]
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 05ac:820f Apple, Inc. Bluetooth HCI
Bus 003 Device 003: ID 046d:c051 Logitech, Inc. G3 (MX518) Optical Mouse
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05ac:8502 Apple, Inc. Built-in iSight
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
benjamin@benjamin-MacBookPro:~$ 

```
dont know if thats of any use for you.

and thats *with* the tablet
```
benjamin@benjamin-MacBookPro:~$ lsusb
Bus 007 Device 003: ID 05ac:0231 Apple, Inc. Internal Keyboard/Trackpad (MacBook Pro 4,1) (ISO)
Bus 007 Device 002: ID 05ac:8242 Apple, Inc. IR Receiver [built-in]
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 005 Device 002: ID 08ca:0010 Aiptek International, Inc. Tablet**
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 05ac:820f Apple, Inc. Bluetooth HCI
Bus 003 Device 003: ID 046d:c051 Logitech, Inc. G3 (MX518) Optical Mouse
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05ac:8502 Apple, Inc. Built-in iSight
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
benjamin@benjamin-MacBookPro:~$ 

```

---

### Post by Favux on 2011-03-20
Good, so it is an Aiptek tablet and wants the Aiptek driver.  Let's just verify what the system is calling it so we're sure of our keywords when we try to do a match in the aiptek.conf.  So enter in a terminal *xinput list* and post the output.

Check in Synaptic Package Manager or the Software Center that you have the Aiptek driver installed.  The package is called something like xserver-xorg-input-aiptek.  The problem is the driver package does not contain the aiptek.conf like it should, so there is nothing to configure the tablet, i.e. match to the tablet and place it on the Aiptek driver.  So we have to do that.  I think we've already filed a Launchpad bug report on that.

---

### Post by Masquerade on 2011-03-20
thanks for the fast reply

```
benjamin@benjamin-MacBookPro:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse         	id=10	[slave  pointer  (2)]
&#9116;   &#8627; bcm5974                                 	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Aiptek                                  	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Apple, Inc. Apple Internal Keyboard / Trackpad	id=11	[slave  keyboard (3)]
    &#8627; Built-in iSight                         	id=13	[slave  keyboard (3)]
benjamin@benjamin-MacBookPro:~$ 
```

xserver-xorg-input-aiptek *is* installed.

---

### Post by Favux on 2011-03-20
OK, it looks like our keyword is "Aiptek".  Let's use the wiki suggestion and call it 50-aiptek.conf.  So enter in a terminal:
```
gksudo gedit /usr/share/X11/xorg.conf.d/50-aiptek.conf
```
and add in the empty file the following contents:
```
Section "InputClass"
        Identifier "Aiptek class"
        MatchProduct "Aiptek|AIPTEK|aiptek"
        MatchDevicePath "/dev/input/event*"
        Driver "aiptek"
        Option "USB" "on"
        Option "Type" "stylus"
        Option "Mode" "absolute"
        Option "zMin" "0"
        Option "zMax" "511"
EndSection
```
Save and reboot.

Check in /usr/share/X11/xorg.conf.d that there isn't an aiptek.conf first, but I don't think there is one.

The:
```
        Option "SendCoreEvents" "true"

```
should have been deprecated by X server 1.7 (Lucid).  We might need to play around with some of the other options.  For example do you know how many pressure levels your tablet is suppose to have?

---

### Post by Masquerade on 2011-03-21
512 pressure levels. Ill reboot now, will edit post.

YAY it works. With pressure, at last the basic stuff as far I can tell.
Thank you a lot!

---

### Post by Favux on 2011-03-21
Good!  Nice work.

Use 511 in the aiptek.conf, because 0 is a level.  So 512 levels is 0 to 511.

---

