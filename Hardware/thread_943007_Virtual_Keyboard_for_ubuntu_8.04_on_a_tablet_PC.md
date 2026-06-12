---
title: "Virtual Keyboard for ubuntu 8.04 on a tablet PC"
date: 2008-10-09
forum: Hardware
---

### Post by bintesla on 2008-10-09
Virtual Keyboard for ubuntu 8.04 on a tablet PC


Hello,

I have the M912 compeuter, which is a tablet PC

I use ubuntu 8.04, and the touch screen works very good!

There is an amazing virtual keyboard
[http://www.chessware.ch/virtual-keyboard/index.php?language=fr](http://www.chessware.ch/virtual-keyboard/index.php?language=fr)

But when I try to install the program with WINE it does not work :(

now I am looking for a vitrtual Keyboard with the same concept.


please help me

---

### Post by alexv75 on 2008-10-11
How did you manage to calibrate the touchscreen, and does your trackpad work ? I bought this today and decided to put Ubuntu (Intrepid) on it, but i have problems - the touchscreen  doesn't work at the edges, (about 0.5 cm), the trackpad does not work at all, neither does the wireless card - "ath5k phy0: failed to wakeup the MAC Chip". Other than these everything else seems to be ok...

---

### Post by k3rb on 2008-11-05
got the same problem with m912 screen not calibrated.

---

### Post by charlie763 on 2008-11-06
Same problems on my Gigabyte M912M running Ubuntu-UMPC 8.10.
[LIST]
[*]Wireless card not working
[*]Trackpad not working
[*]Touch screen not calibrated properly
[/LIST]

Any ideas?

---

### Post by alexv75 on 2008-12-03
@charlie763

After some fiddling around with it i got the wireless and touchpad working... So far there is no hope for the touchscreen, waiting for PenMount to release a driver, or the devs behind the calibration tool that comes with Ubuntu to add support for it.

The wireless
- download the linux-backports package for your kernel version from
```
https://ftp.usf.edu/pub/ubuntu/pool/main/l/linux-backports-modules-2.6.27/
```
- deactivate the atheros driver currently in use by Ubuntu (Support for Atheros 802.11 wireless LAN cards.)
```
Menu->System->Administration->Hardware Drivers
```
- install the backports package
- make sure that "Support for 5xxx series of Atheros 802.11 wireless LAN cards." is the active driver

The touchpad (involves editing the boot options)
```
gksudo gedit /boot/grub/menu.lst
```
add "i8042.noloop" in this line
```
kernel	/boot/vmlinuz-...
```
for example:
```
kernel	/boot/vmlinuz-2.6.27-10-generic i8042.noloop root=UUID=....
```

As for the virtual keyboard - CellWriter, it can be found in the repos.

---

### Post by charlie763 on 2008-12-03
@ Alexv75

Thanks for the information. I'll try it out later today. Are you using intrepid or jaunty?

---

### Post by alexv75 on 2008-12-03
I'm using intrepid, but it should work with jaunty too, if there is a package for it's kernel...

---

### Post by alexv75 on 2008-12-11
Bump :D

It seems we have a Christmas present - 

[http://www.penmount.com/Download/Driver/PenMount/PenMount%20Ubuntu%208.10%20Driver%20V2.3.0.15.tar.gz]("http://www.penmount.com/Download/Driver/PenMount/PenMount%20Ubuntu%208.10%20Driver%20V2.3.0.15.tar.gz")

a new driver for the touchscreen :guitar:


edit: Just tried it, works like charm...

---

### Post by charlie763 on 2008-12-11
> **alexv75 said:**
> Bump :D

It seems we have a Christmas present - 

[http://www.penmount.com/Download/Driver/PenMount/PenMount%20Ubuntu%208.10%20Driver%20V2.3.0.15.tar.gz]("http://www.penmount.com/Download/Driver/PenMount/PenMount%20Ubuntu%208.10%20Driver%20V2.3.0.15.tar.gz")

a new driver for the touchscreen :guitar:


edit: Just tried it, works like charm...

Great news! Looks like I'm switching to Ubuntu-umpc this weekend. Thanks.:p

---

### Post by charlie763 on 2008-12-11
Tested on ubuntu-umpc 8.04 and it works.

---

### Post by charlie763 on 2008-12-13
So the wireless and touch screen are both working using the instructions above. The touchpad, however, is not working using the instructions above. Has anyone recently found anything that works?

---

### Post by SaintDanBert on 2009-05-12
> **alexv75 said:**
> I'm using intrepid, but it should work with jaunty too, if there is a package for it's kernel...

All I've read says that intrepid and tablets do not play well due to changes
in X11 and xorg.  Please tell me (us) more or tell us where to find more.

I have Lenovo Thinkpad X61 tablet [Emperor Linux Raven Tablet] running
Ubuntu Hardy.  There are still parts of tablet operations that don't work
as desired.  I'll appreciate all that I can get.

Continuing troubles include:
1.  box has a jog-dial ... up, down, left, right, enter ... that does nothing under X11.  It pushes the cursor around on win-doze.
2.  stylus as mouse remains finicky.  Some X11 apps are fine; many don't behave well for right-click or eraser click.
3.  'cellwrite' does not play well with many applications
4. wish-list to share Xournal files with Win-doze Journal(tm) files.
[Better still run Xournal on win-doze native.]
5. wish-list for a good tao-tap keyboard.  There are times a tap-tap keyboard is faster than 'cell write' or other recognition.

Thanks,
~~~ Saint 0;-D

---

### Post by alexv75 on 2009-05-16
First of all you might want to try Jaunty or even Karmic.

1. I'm not sure if it'll help you but you might try the i8042.noloop trick as described above.
2. Dunno, i only use the touchscreen occasionally for tapping on buttons and other small things, i don't use it as a general replacement for a mouse/touchpad.
3. You might try OnBoard (it comes preinstalled with Intrepid and above, idk if Hardy has it.


Oh, btw. new PenMount driver for Jaunty - [http://www.penmount.com/download/driver/PenMount/PenMount%20Ubuntu%209.04%20Driver%20V2.4.1.tar.gz](http://www.penmount.com/download/driver/PenMount/PenMount%20Ubuntu%209.04%20Driver%20V2.4.1.tar.gz)

---

