---
title: "x fails to start on dell latitude D620"
date: 2006-04-14
forum: Hardware &amp; Laptops
---

### Post by dragonflyFZX on 2006-04-14
hi,

just bought a new laptop and installed kubuntu dapper on it (it was running fine on my previous laptop, so).  The install seemed to go ok, but after rebooting, when it is time to start the x server, the kubuntu bootsplash appears again, and nothing happens.  I can login pressing ctrl-alt-f1.  Typing startx at the command prompt results in:

```
(WW) I810: No matching Device section for instance (BusID PCI:0:2:1) found
(EE) GARTInit: Unable to open /dev/agpgart (No such file or directory)
(EE) I810(0): No video BIOS  mode for chosen depth
(EE) Screen(s) found, but none have a usable configuration

Fatal server error:
no screens found
XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0"
after 0 requests (0 known preocessed) with 0 events remaining
```

I have an integrated graphics card (GMA 950).  I tried to run 

sudo dpkg-reconfigure xserver-org (was suggested on another forum), but that returns that the package 'xserver-org' is not installed and no info is available.

---

### Post by mscman on 2006-04-14
[QUOTE=dragonflyFZX]
sudo dpkg-reconfigure xserver-org (was suggested on another forum), but that returns that the package 'xserver-org' is not installed and no info is available.[/QUOTE]
the correct command you're looking for is
```
sudo dpkg-reconfigure xserver-xorg
```
you need to add 'x' before the 'org'

---

### Post by noch on 2006-04-21
Hey, I just bought the same laptop as you and I am having the same problem as you are. The errors in my log says this:

(WW) I810: No matching device section for instance (BudID PCI:0:2:1) found

(EE) No devices detected

Fatal server error:
no screens found

---

### Post by dragonflyFZX on 2006-04-22
ha, dont worry my friend, you made a good choice.

I already found how to get it working just fine.  Just have a look at this post:

[http://www.ubuntuforums.org/showthread.php?t=160521]("http://www.ubuntuforums.org/showthread.php?t=160521")

---

### Post by pchristen on 2006-04-30
Hi,

I have the same problems as described, followed all the suggestions given in this and other relevant threads but X only works for me when I use the 'vesa' driver.

If I activate 915resolution I do get the higher 1440x900 resolution but only
in black/white wth strips and the left ~1/4 of the screen copied on the right side.

So at the moment I run it with 1024x768 resolution (using the vesa driver).

Anybody else with the same problems and possible solutions? I'm new with Ubuntu and using 5.10.

Thanks,
Peter

---

### Post by pchristen on 2006-05-01
OK... I finally got it to work partially, still using the 'vesa' driver (but not the i810 driver), following the instructions here:

[http://users.skynet.be/thomasvst/linux-on-laptop/#wide](http://users.skynet.be/thomasvst/linux-on-laptop/#wide)

For some resons, using

915resolution 1440 900 24

didn't work, but using only 

915resolution 1440 900

works!

With the i810 driver X still doesn't start up (still the error message 'no screen found').

Any ideas?

Peter

---

