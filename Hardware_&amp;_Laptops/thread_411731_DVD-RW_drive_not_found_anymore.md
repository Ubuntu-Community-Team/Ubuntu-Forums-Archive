---
title: "DVD-RW drive not found anymore"
date: 2007-04-17
forum: Hardware &amp; Laptops
---

### Post by taiyo on 2007-04-17
Hello !

1:) I recently removed my windows partition with gparted and manually deleted its entry from fstab. My problem now is that I fiddled around with my DVD-Writer in fstab to get it to work properly, but I ended up having it not even recognized by the system anymore.

I need to know its location in /dev/ so I can properly link it (to /media/cdrom I assume?) and hopefully have it recognized again. I have got sda / sda1 / sda2 in /dev/ but these are my primary ext3, the swap and the now obsolete fat partition, so I have no idea what it's name could be. There is no cdrom or dvd entry, so I have no idea what to do. It's connected by IDE.

2.) A question probably not directly related to hardware, but I ask it here anyhow, since nobody in the general forum seems to know about/ the thread slips away too easily:

Here is something where nobody seems to know the answer. CNTRL+ALT+F* are somehow hardcoded into Xorg and work always... where can I set more functions of this kind (to alt-tab out of fullscreen keygrabbing 3D games for example?) ?

Thanks a lot, I really appreciate any try to help me resolve my issues!

---

### Post by pioo on 2007-04-17
Hi!

If You have a PATA DVD-RW then it must be something like hda, hdb, hdc or hdd. If the /proc/sys/dev/cdrom/info file exists, then it may contain a "drive name" entry. That's the name of Your drive, e.g.: it contains hda, then Your drive is /dev/hda.

Question #2: You can finetune Xorg trough /etc/X11/xrog.conf, "man xorg.conf" gives You more information, but the fullscreen 3D games does not allow to alt-tab out. It should be a windowmanager feature (gnome) to allow this kind of keyboard shortcuts. In gnome by default I think CTRL+ALT+d hides all windows, showing the desktop, I thinks it worths a try.

---

### Post by taiyo on 2007-04-17
Hello, thanks for your help so far, but I didn't find the solution yet...

#1: There is no hd* nor scd* in /dev/ whatsoever, and there is a /proc/sys/dev/cdrom/info file, but  without any variables.

#2: Tried this with beryl, but it didn't seem to work (hyper was interpreted as "control" by the game so it got caught, might try a different keyset)

---

### Post by pioo on 2007-04-18
Ok, then try this in command line:
dmesg | grep -i dvd

What does it show?

---

### Post by taiyo on 2007-04-19
it displays nothing, I tried searching dmesg recently...

Could there be a problem with the physical connection? I doubt this somehow because I recently ckecked it to make sure its plugged alright... The green light works and the eject button as well...

---

### Post by taiyo on 2007-04-19
I looked at the physical connection of my drive again and confirmed it by searching the BIOS (should have had that idea earlier)... it is properly recognized... 
I found another track then... there were no IDE modules loaded in the kernel, but the writer is connected by IDE (master). I just loaded the drivers but not much seemed to happen, I am not sure what I have to do to make it recognize the drive yet.
I used the /dev/ directory and the hardware information program to see if anything comes up... but nothing so far.

Any help is appreciated

DMESG is talking to me at least but doesn't seem to be too happy:
[  983.536000] ide0: I/O resource 0x3F6-0x3F6 not free.
[  983.536000] ide0: ports already in use, skipping probe
[  983.536000] ide1: I/O resource 0x376-0x376 not free.
[  983.536000] ide1: ports already in use, skipping probe

I don't have any other devices connected by IDE, so I wonder why there should be something blocked.

---

### Post by taiyo on 2007-04-20
update to kernel *20-15 brought an initial solution.... [close]

---

