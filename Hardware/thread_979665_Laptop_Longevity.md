---
title: "Laptop Longevity"
date: 2008-11-12
forum: Hardware
---

### Post by h4mx0r on 2008-11-12
I was hoping to start a faq about maximizing laptop uptime through software means and perhaps separately through hardware as well. Anything to reduce power consumption or heat production is a good suggestion. So far a few ideas come to mind:

~Software~
1. blackbox environment (perhaps openbox can do better though)
2. stick with open source video drivers (nv and ati, etc) 3d eats power
3. remove splash screen
4. grub boot profile
5. remove extra features of ext3 like atime and etc
6. put cpu governor in power save mode
7. tweak laptop-mode utils
8. dim the screen (should basic colors with more contrast be used for theme?)
9. fix something up with wicd like linux mint uses or perhaps some other wireless utility to keep network up
10. turn off unneeded services (update checks, bluetooth, printing, etc)
11. lighter choices in applications than normal
12. remove swap
13. if dual-core then get concurrency going for boot 
14. use 16 color depth in xorg
15. use ddcprobe to set proper refresh rates and resolutions in xorg
16. remove some ttys
17. login through terminal not through a *DM and get directed to graphical environment through a bash script.

~Hardware~
  -Remove-
1. cd drive
2. floppy drive
3. firewire
4. cardslots
5. led lights
6. webcam
7. ethernet
8. modem
9. speakers (everyone uses headphones with a laptop anyway because then it can have uptime in a library or otherwise)
    -Add-
1. better battery?
2. solid state drive (remove the old drive unless you were booting off usb which is a great idea!)


tips- fluxbox is just blackbox with transparency, window tabs, weird fonts, and icons on menu. All of which no one uses nor has any distro used properly so create a symbolic link between .fluxbox and .blackbox. Also any whining about suspend mode keep it to yourself so you don't get laughed at for your choice of hardware or file system topology.

---

