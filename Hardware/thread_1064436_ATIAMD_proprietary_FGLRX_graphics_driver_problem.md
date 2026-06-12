---
title: "ATI/AMD proprietary FGLRX graphics driver problem"
date: 2009-02-08
forum: Hardware
---

### Post by black445 on 2009-02-08
When install my graphics card with the stated driver, after reboot nothing will show because it changes my screen resolution to a point where I can't see and change it.

Any help?

---

### Post by theApokalypsis on 2009-02-08
did you try:

aticonfig --initial -f

in the terminal. if you cant get in on boot try getting into a TTY terminal by hitting ALT + F2.

good luck

---

### Post by black445 on 2009-02-08
> **theApokalypsis said:**
> did you try:

aticonfig --initial -f

in the terminal. if you cant get in on boot try getting into a TTY terminal by hitting ALT + F2.

good luck
No, it will not allow me, my screen will go black, and say "incorrect resolution"

---

### Post by irongoliath on 2009-08-05
I'm in the same boat - installed the ATI video driver, and now after logging into Unbuntu, I can't even SEE the screen - it's a bunch of weird horizontal bands.  I can't SEE anything to change it...don't know what to do.

---

### Post by rizman on 2009-08-05
> **irongoliath said:**
> I'm in the same boat - installed the ATI video driver, and now after logging into Unbuntu, I can't even SEE the screen - it's a bunch of weird horizontal bands.  I can't SEE anything to change it...don't know what to do.

Looks like you have a GPU which is no longer supported by the proprietary ATI drivers. At least, what you describe is the same thing I got when I tried them with my old Mobility Radeon X700.

You will need to remove completely remove them. As, well obviously, you cannot access your X session, you will need to get to the command line somehow. 

So, start by booting your computer. When GRUB loads, hit escape to enter the GRUB boot menu. Select Ubuntu... (Recovery mode). 

Wait until you are presented with a menu. Select the option which says something like "Drop to root shell prompt" or similar.

You will be presented with a Shell. Then do:
```
sudo apt-get remove --purge xorg-driver-fglrx
```

This will remove the fglrx drivers. Reboot.

The system should now return to a usable state. I don't know wheter Ubuntu will automatically revert back to the ATI opensource drivers or to the default VESA drivers, but at least you should be able to see something.

---

### Post by theApokalypsis on 2009-08-07
Also, if its of any use, if you installed the driver yourself (this may be apparent with package manager installs too I dont know), AMD has a uninstaller as well in /usr/share/ati/fglrx-uninstall.sh 

(correct me if im wrong, im pretty confident thats the path and file name)

run that (sh) and it purges itself and even restores the xorg file it overwrote.

---

### Post by Yellow Pasque on 2009-08-07
If you're trying to get back to the open-source driver, see: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver?action=show](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver?action=show)

---

### Post by theApokalypsis on 2010-01-07
Figured I would update this thread to get word out.

Check out post [[COLOR="Red"]here[/COLOR]]("http://humphreybc.wordpress.com/2009/12/04/enable-3d-support-on-r600r700-with-the-open-source-radeon-driver/#comment-87"). 

Using a Radeon HD4870 on Karmic with full 3D working (for compiz and plugins at least). Seems very stable too. Finally, no more fglrx. 

:lolflag:

---

