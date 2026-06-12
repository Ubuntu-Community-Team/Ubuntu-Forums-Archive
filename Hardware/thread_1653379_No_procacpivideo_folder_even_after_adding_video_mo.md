---
title: "No /proc/acpi/video folder even after adding video module to kernel"
date: 2010-12-26
forum: Hardware
---

### Post by soulspit on 2010-12-26
Hi everyone,

I'm trying to set up a crappy laptop (an Acer TravelMate 2310) for my grandmother, who is rather bad with computers - I'm setting it up mainly for Skype.  The problem is, sometimes, for some reason, the brightness goes all the way down, and this is an issue for her because her eyesight is bad.  I was going to make a startup script that made sure it was full brightness every session, using, (this is what works my own laptop),```
echo -n 100 > /proc/acpi/video/M86/LCD/brightness
```However, on my grandmother's laptop, there is no "video" folder in /proc/acpi.  I tried ```
sudo modprobe video
```but it still wasn't there.  Nor was it there after restarting.  I've searched for "brightness" everywhere in /proc but there is nothing.  How can I figure this out so that I can change the brightness in a script?  Or, any pointers on where to go to find the answer?

Thanks so much for your help!

*Edit:* adding the video module with modprobe seemed to be a waste of time - it's not in /etc/modules, but lsmod shows module called "video" already.

---

### Post by Ceyx on 2010-12-26
Try the ole wild card method:

ls /proc/acpi/video/*/LCD/brightness

and it will return the directory instead of a star, if you know what I mean...

Good Luck.  Your grand mother must have done something right !

---

### Post by soulspit on 2010-12-27
Thanks for the reply, but when I do that, I get```
ls: cannot access /proc/acpi/video/*/LCD/brightness: No such file or directory
```There simply is no folder called "video" in /proc/acpi.  This is what I've got:```
clarice@5tilney:~$ ls /proc/acpi
ac_adapter  dsdt                 fadt  power_resource  thermal_zone
battery     embedded_controller  fan   processor       wakeup
button      event                info  sleep
clarice@5tilney:~$ 


```This is such a tiny thing, but it's really bugging me!  Any other thoughts?

Thanks again!

---

### Post by uyuy on 2010-12-27
All I am able to tell you is this being a HAL dependent issue. So it differs from one laptop to another. Laptops have a different display adapters so different folders in /proc. You can try your luck with different linux distributions / version using live-CDs. Some may offer you similar brightness control. Good luck.;)

---

### Post by soulspit on 2010-12-27
Ah, that's what I feared.  I've searched for "backlight" and "brightness" in /proc and /sys (on my own laptop, for example, brightness can also be controlled through /sys/devices/virtual/backlight/acpi_video0/brightness) but on the laptop I'm trying to get this to work on, I can't find anything anywhere.  I also tried (as per [this other thread]("https://wiki.archlinux.org/index.php/Samsung_N140#Backlight_Brightness")'s suggestion)```
sudo setpci -s 02:00.0 F4.B=FF
```where 02:00.0 is the address of the VGA controller (and I guess F4.B locates a brightness property?), but that did nothing.  I tried a program called xbacklight but got the error "no outputs have backlight property."

It's not really worth switching to another Linux distribution, so I think I'm going to have to give up on this.  Ah well, I'll see if I can get my grandmother's arthritic hands to remember how to change the backlight brightness, haha.  Thanks for the help though!

---

### Post by Ceyx on 2010-12-27
I'd look for a stuck key - like a stuck brightness key......

Also, try turning off acpi in grub -

---

### Post by soulspit on 2010-12-28
Hmm, I tried turning off acpi in grub but no luck - all of my methods  for controlling brightness from the command line still failed, and I  still couldn't find a video folder in /proc or /sys nor any brightness  file to write to anywhere.

As for a stuck key - the brightness keys work fine, and don't seem  stuck.  The problem is that my grandmother, who this laptop is for, has  awful eyesight, arthritic hands, and a bad memory.  I wanted a way to  ensure the screen is at full brightness (for some reason it seems to  spontaneously be dimmer sometimes when you start it up - I've ruled out  power management etc. as an issue, everything is set to full brightness  always) so that she can see what's going on when we Skype her.

Seems like a dead end, though =(  Thanks everyone for their help.

---

### Post by aasdfasdfg on 2012-02-05
Probably too late to help you but at least it may [help]("https://bbs.archlinux.org/viewtopic.php?id=113476") others:
> 
/proc/acpi is being deprecated. Find the equivalents of what you want to  do in /sys. Backlight stuff is in /sys/class/backlight. Or you compile  your own kernel, it's still possible to activate the deprecated  /proc/acpi stuff.For instance,
```
echo $BRIGHTNESS > /sys/class/backlight/acpi_video0/brightness
```

---

