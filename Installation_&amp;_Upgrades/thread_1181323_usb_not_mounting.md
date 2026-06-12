---
title: "usb not mounting"
date: 2009-06-07
forum: Installation &amp; Upgrades
---

### Post by kjh_ngisd on 2009-06-07
Help!? :D
 
I'm trying to set up Jaunty, since Hardy crashed hard the other day. 
And everything looks amazing -- graphics, sounds... etc. 
 
*Except*
that i cannot get my usb ports to work. This is kinda important, since my wifi is usb. But external hard drives, thumb drives, etc. don't auto mount. The wifi card is listed, but I can't connect to anything. 
 
I've read a lot about usb drives not auto mounting correctly under Jaunty, but none of the recommendations make sense to me. One of them said that I had to add the hal user to the right group. Only, I can't even find the hal user. 
 
Another said that I need to run sudo hotplug restart, but hotplug isn't found. 
 
Anyone have any thoughts that may help?

---

### Post by merlinus on 2009-06-07
Have you made sure the correct boxes are ticked in System/Preferences/Removable Drives and Media?

---

### Post by kjh_ngisd on 2009-06-07
> **merlinus said:**
> Have you made sure the correct boxes are ticked in System/Preferences/Removable Drives and Media?
 
 
thanks for the reply merlinus. 
 
Umm.. there is no  System/Preferences/Removable Drives and Media 
 
Is there a command line for that?

---

### Post by merlinus on 2009-06-08
Have you installed 9.04?  If so, and this is not in the menu as indicated, you should be able to add it from System/Preferences/Main Menu, and then System/Preferences in the window that opens.

---

### Post by kjh_ngisd on 2009-06-08
> **merlinus said:**
> Have you installed 9.04?  If so, and this is not in the menu as indicated, you should be able to add it from System/Preferences/Main Menu, and then System/Preferences in the window that opens.

yes, 9.0.4. 
maybe that's my problem. I can't add it - or at least it's not on the list when I go to system/preference/main menu. 

I'm not much of a Gnome expert though. I'm more used to KDE3x. I'm actually switching because I thought Gnome would be easier, but so far.. not so much...

so, what would be the command line syntax for this?
thank you.

---

### Post by merlinus on 2009-06-08
You are correct.  I use thunar as my file browser rather than nautilus, and when installing it via synaptic there was also a volume manager available, which put this on the menu.

---

### Post by kjh_ngisd on 2009-06-08
> **merlinus said:**
> You are correct.  I use thunar as my file browser rather than nautilus, and when installing it via synaptic there was also a volume manager available, which put this on the menu.

ahhh so you're saying i should do an apt-get install on  thunar-volman ....?
I'm willing to give it a try. 
I'll let you know...

---

### Post by merlinus on 2009-06-08
I used synaptic, but apt-get should work, as long as the program name is correct.

---

### Post by kjh_ngisd on 2009-06-08
> **merlinus said:**
> I used synaptic, but apt-get should work, as long as the program name is correct.
 
well, thanks again merlinus, but this didn't help. 
 
Got it installed, got the spiffy little boxes and made sure they're all checked, but ...nothin'. 
 
I tried manually mounting the usb drives and I can't seem to do that either -- they're just not in /dev. 
I turned off the spash screen to see if I was getting any errors on boot, but I didn't see anything. 
 
I'm thinking it's not the drives, but the usb drivers that aren't getting loaded. Didn't have this issue at all with Hardy... maybe I should go back, I suppose, but I don't want to and it's actually more complex than that. 
 
Anyone have any thoughts on why the usb ports would be totally unavailable to me in Jaunty?
 
thanks

---

### Post by merlinus on 2009-06-08
I assume you tried different usb ports?  Also, mounted media should appear in /media, not /dev.

Are you using an external usb hdd?

Also, this command will let you know about usb ports:

```

lsusb

```

---

### Post by kjh_ngisd on 2009-06-09
> **merlinus said:**
> I assume you tried different usb ports?  Also, mounted media should appear in /media, not /dev.


after it's mounted, it should be in media (which it's not). But I don't even see anything in /dev to mount for the usb drives. ... maybe I'm just missing it. 


> **merlinus said:**
> I assume you tried different usb ports?  


yes. 


> **merlinus said:**
> 
Are you using an external usb hdd?


I'm not able to use a usb anything. It's booting from the internal, but plugging in a hdd or jump drive or anything else doesn't seem to work. 

[QUOTE=merlinus;7424751]
Also, this command will let you know about usb ports:

```

lsusb

```

I'll check that out. I've been using Linux for a while, but never really had to mess with usb issues before. 
thanks.

---

### Post by sedawk on 2009-06-09
Boot your computer without the "fancy" usb devices connected
(keep keyboard and mouse connected if they are USB).

Login and open a terminal.
Clear the message buffer with
```

sudo dmesg -c

```

Connect one usb device, e.g. a hard disk.
Wait 10 seconds.
Check the output of
```

dmesg 

```

E.g the device should be detected, and if it is a disk
you should see the associated device (e.g. /dev/sdX with
partitions /dev/sdX1, /dev/sdX2, ...).

If this looks fine, the error is somewhere else.

I have a laptop where I have to add the kernel parameter
"acpi=force" to make USB properly work. Whenever the kernel
is updated I have to remember to edit /boot/grub/menu.lst again...

---

### Post by kjh_ngisd on 2009-06-09
> **sedawk said:**
> Boot your computer without the "fancy" usb devices connected
(keep keyboard and mouse connected if they are USB).

Login and open a terminal.
Clear the message buffer with
```

sudo dmesg -c

```

Connect one usb device, e.g. a hard disk.
Wait 10 seconds.
Check the output of
```

dmesg 

```

E.g the device should be detected, and if it is a disk
you should see the associated device (e.g. /dev/sdX with
partitions /dev/sdX1, /dev/sdX2, ...).

If this looks fine, the error is somewhere else.

I have a laptop where I have to add the kernel parameter
"acpi=force" to make USB properly work. Whenever the kernel
is updated I have to remember to edit /boot/grub/menu.lst again...


I'll check when I'm in front of it. I don't know why i didn't think of dmsg.. well, i did think of it, then forgot. :D

Good to know about the kernal parameter. I remember the ole' days when the kernel needed a recompile for some of the drivers, but didn't think I'd need to worry about parameters now .

thanks.

---

### Post by kjh_ngisd on 2009-06-09
> **sedawk said:**
> Boot your computer without the "fancy" usb devices connected
(keep keyboard and mouse connected if they are USB).
 

Actually, I haven't tried using a usb mouse... hmm... I'd bet it won't connect. 
 
> **sedawk said:**
> Boot your computer without the "fancy" usb devices 
Login and open a terminal.
Clear the message buffer with
```

sudo dmesg -c

```
 
Connect one usb device, e.g. a hard disk.
Wait 10 seconds.
Check the output of
```

dmesg 

```
 
 
E.g the device should be detected, and if it is a disk
you should see the associated device (e.g. /dev/sdX with
partitions /dev/sdX1, /dev/sdX2, ...).
 
If this looks fine, the error is somewhere else.
 

 
notta. Nothin. No errors, but the device isn't there. Just as before, it's not in /dev at all. The only sdX's are my 2 hard drive partitions -- sda1 and sda2.
 
 
> **sedawk said:**
> Boot your computer without the "fancy" usb devices 
 
I have a laptop where I have to add the kernel parameter
"acpi=force" to make USB properly work. Whenever the kernel
is updated I have to remember to edit /boot/grub/menu.lst again...
 
I'm guessing this is it. I tried adding it during the boot from the grub menu (as a side note, I don't think I've ever done that from grub before... Done it from lilo a few times... ah... those were the days :D )
 
but it didn't work. Of course, I may have mistyped it. It's not like I can copy/paste while the thing is booting. I guess I'll just modify the menu.lst file. Or it could be that I need another parameter. 
 
Let me do a little leg work on this and see what I can find. 
 
thank you.

---

### Post by kjh_ngisd on 2009-06-09
some new info.  If I do this:
 
--shutdown
-- remove usb devices
-- reboot (with or without kernel parameter)
-- insert usb stick
 
result: nothin'
 
-- open bash window
-- run lsusb
 
result: usb stick found. 5 seconds later, the window pops with to the device and everything is golden. 
 
-- remove usb stick
-- run lsusb again
 
result: usb stick still found in the output of lsusb. 
 
I've an old internal Wifi card that seems to be part of the mix. It's not usb, but is broken. And Jaunty seems like maybe it's seeing it as a usb device. Hardy completely ignored it, so it didn't cause an issue. 
 
I may try to pull it out tonight, if I get time, to see if that helps. 
 
 
I'll keep you posted. 
 
thank you again.

---

### Post by kjh_ngisd on 2009-06-12
GOT IT!!

I was (basically) right. 
I ended up not being able to pull the card, since it's *really* hard to get to. 

BUT  I disabled the internal wifi using
sudo modprobe -r rtl8187

Pugged in my usb drives and cards and I'm happily camping :D

Thanks for all your help.

---

