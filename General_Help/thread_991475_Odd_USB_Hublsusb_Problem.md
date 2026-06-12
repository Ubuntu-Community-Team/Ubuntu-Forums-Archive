---
title: "Odd USB Hub/lsusb Problem"
date: 2008-11-23
forum: General Help
---

### Post by radioraheem on 2008-11-23
I just added a USB hub to my 8.04 machine, and I'm running into a really weird problem.  Tried searching, couldn't find much other than other generic usb mounting problems.

Basically if I plug a device into the hub (doesn't matter what it is) nothing will happen at all.  I can mount usb drives using sudo but drives that were previously used on the system fail to automount when plugged in.

Where it _really_ gets odd is if I just run lsusb all of a sudden everything fires up normally, printers and drives all mount correctly (just they like they should normally if plugged in).

lsusb has to be run every time I plug in a device as it stands right now.  Unmounting drives works correctly.

Anybody seen or heard of this before?

lsusb output, just the hub and keyboard/mouse connected:

```

Bus 002 Device 005: ID 050d:0304 Belkin Components 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:c512 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  

```

Thanks

---

### Post by jettero on 2009-01-01
bump.

I'm having this exact same "problem."  It isn't *really* a problem since I can just run lsusb to get the devices mounted, but it *really* is irritating to have to open a terminal and interact with it like that.

There must be some solution for it.

---

### Post by radioraheem on 2009-01-01
Actually I did find a solution.  I had a printer connected to my hub that was powered down.  As long as I leave the printer turned on the hub operates like it should.

If I turn the printer off then I get the problem I originally described, and only lsusb will cause it to see any changes.

---

### Post by jettero on 2009-01-01
> **radioraheem said:**
> Actually I did find a solution.  I had a printer connected to my hub that was powered down.  As long as I leave the printer turned on the hub operates like it should.

If I turn the printer off then I get the problem I originally described, and only lsusb will cause it to see any changes.


It sounds to me like a workaround of sorts... The printer must do something that gets dbus/hald (or whatever) to notice other things on the hub.  Too bad I don't have a spare printer around that could convince whatever subsystem to check the hub...

I could maybe make a while loop that runs lsusb every few seconds, but it seems like something I shouldn't have to do.

---

### Post by radioraheem on 2009-01-01
just to double check your setup, do you have _any_ powered devices attached to the hub that aren't turned on?

not doubting your abilities, just asking the same questions I asked myself when trying to figure it out on my end :)

also, if I disconnect the printer from the hub then the hub operates normally.  Just want to be clear on that bit.

---

### Post by jettero on 2009-01-01
> **radioraheem said:**
> just to double check your setup, do you have _any_ powered devices attached to the hub that aren't turned on?

not doubting your abilities, just asking the same questions I asked myself when trying to figure it out on my end :)

also, if I disconnect the printer from the hub then the hub operates normally.  Just want to be clear on that bit.


No.  Well, the usb hub is powered, but I know that's working.  None of the devices are powered or have switches, couple usb keychains, a low power usb hdd, a camera (which does have an on/off) and a quick cam.  They all work, but don't show up unless I lsusb first.

---

### Post by fragos on 2009-01-02
I would think this is a problem with the hub and not Ubuntu. I can't recall ever seeing this prblem discussed before. I have an irocks powered hub, very inexpensive, and it works correctly.

---

### Post by jettero on 2009-01-03
> **fragos said:**
> I would think this is a problem with the hub and not Ubuntu. I can't recall ever seeing this prblem discussed before. I have an irocks powered hub, very inexpensive, and it works correctly.


I don't think that's the case since a) it works fine in windows and b) it works in linux as long as I lsusb.  I find it more likely to be a problem with udev or a missing rule in udev than with the hub.

---

### Post by Ellaine on 2009-01-03
I.ve had this exact problem with a front panel 4 port hub made by Genesys Logic. This hub auto mounted and worked in 7.04, 7.10, but will NOT work in 7.10 updated to 8.04 or a fresh install of 8.04 unless I boot with a device installed in the hub (or run lsusb). All mobo usb ports work perfectly, and 2 PCI 4 port cards automount perfectly. I think something was left out of the kernel between 7.10 & 8.04.

---

### Post by fragos on 2009-01-03
> **jettero said:**
> I don't think that's the case since a) it works fine in windows and b) it works in linux as long as I lsusb.  I find it more likely to be a problem with udev or a missing rule in udev than with the hub.

You may be correct on the udev rules -- worth a look.

---

### Post by Ellaine on 2009-01-18
mc4man asked me to post my fstab on this thread so someone may help with this usb hub not mounting unless I boot with a device in the hub. Here is my fstab:

dick@dick-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=dfff10dd-305b-488b-88e1-2191a52b2159 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=161b9212-174c-422b-87c2-35b4c62f9242 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


Hope this helps!:(

---

