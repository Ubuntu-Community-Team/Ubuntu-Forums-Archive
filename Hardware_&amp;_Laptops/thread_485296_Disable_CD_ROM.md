---
title: "Disable CD ROM?"
date: 2007-06-26
forum: Hardware &amp; Laptops
---

### Post by Stex on 2007-06-26
Is there a way to completely disable my CD/DVD drive? It seems to be the cause of frequent crashes of my system and, as I can't fix it, disabling it is the next best thing. I can't remove it in any bios settings. I've disabled it in my windows boot and it's done wonders. I just can't find any way to get rid of it in ubuntu.

Sorry for the blunt post, but the crashes it cause really limit the time I can spend on my laptop :P Very grateful to any replies, command line ones that I can do through the Recovery Mode may be best as this problem only seems to be getting worse.

Thanks

---

### Post by elsaturnino on 2007-06-27
You should try removing it from your /etc/fstab but I doubt that will accomplish what you are looking for. Why not just physically remove it from your system if you are having that many problems with it?

---

### Post by Stex on 2007-06-27
> **elsaturnino said:**
> You should try removing it from your /etc/fstab but I doubt that will accomplish what you are looking for. Why not just physically remove it from your system if you are having that many problems with it?

Doesn't seem to have helped, unfortunately.

Problem is this is a laptop, and a very well sealed laptop at that. I simply can't get to the thing to remove it.

---

### Post by elsaturnino on 2007-06-27
This thread might be of interest to you: [http://ubuntuforums.org/showthread.php?t=479467](http://ubuntuforums.org/showthread.php?t=479467)

---

### Post by MattDTownsend on 2007-06-27
Sounds like you've been having the same problem I have.  Is it that SATA-related bug?  You get about 30 or 40 minutes before the system locks and prints ATA errors?

Have you thought about just physically removing the drive?  What model of laptop do you have?

---

### Post by Stex on 2007-06-27
> **elsaturnino said:**
> This thread might be of interest to you: [http://ubuntuforums.org/showthread.php?t=479467](http://ubuntuforums.org/showthread.php?t=479467)
I tried that before but it only seems to disable startup services and I can't find one for CD, presumably it's too core.

> **MattDTownsend said:**
> Sounds like you've been having the same problem I have.  Is it that SATA-related bug?  You get about 30 or 40 minutes before the system locks and prints ATA errors?

Have you thought about just physically removing the drive?  What model of laptop do you have?
I don't get any errors, it just turns off and reboots. I'd be happier with half an hour, I don't get much more than 3 minutes as it is.

I really can't find a way to get to the CD drive, removing all the screws and pulling at every possible angle yielded no results. The access panel is on the other side of the laptop to the drive and I just can't find a way to get the rest of the casing off. It's a siemens Amilo PI.

Thanks all

---

### Post by pxwpxw on 2007-06-27
If you could locate which modules are used for the CD (and not required for other drives) ie. scsi  modules if your main drive is ide,  then it might be possible to blacklist the module, but might kill usb as well.
lsmod. lspci. 
But I might be off track, i use applemacs mostly.

---

### Post by MattDTownsend on 2007-06-27
> **Stex said:**
> 
I really can't find a way to get to the CD drive, removing all the screws and pulling at every possible angle yielded no results. The access panel is on the other side of the laptop to the drive and I just can't find a way to get the rest of the casing off. It's a siemens Amilo PI.


On several laptop models I've seen, screws holding in the optical drive are underneath the keyboard.  To access the keyboard, you've got to find what's holding it in.  If you are lucky, there will be screws on the underside that do that.  Probably not that lucky.

I'm looking at some photos of the Amilo, but it's a little hard to tell.  Often, access to the keyboard is granted by removing the button panel that's right in front of the LCD.  There appears to be three screws on the back of your laptop that may be holding this in place.  If you think you have it loose, drop the lid all the way, so the laptop is 180 degrees flat, and try lifting it.  It may have snaps, as well.  On HP's and Dells I've worked on, this strip usually ends at the keyboard F-keys.  However, it looks like on some Amilos it may be a panel that surrounds the keyboard.  So, before you start prying, you should make sure there aren't any screws on the belly that are securing it.

This may not be the way to lift your keyboard, but there HAS to be a way to lift the board.  I can't imagine another way to design it.  And 5 for 10 that after you lift it, you'll see whatever is holding the drive in place.  And maybe some other surprises.

[IMG]http://img508.imageshack.us/img508/9894/amilorearhw7.jpg[/IMG]

[IMG]http://img168.imageshack.us/img168/8628/amilofullnv0.jpg[/IMG]

[IMG]http://img245.imageshack.us/img245/5306/amilohpstylets2.jpg[/IMG]

What makes you think it's the CD-ROM, anyway?

---

### Post by Tachyon_ on 2007-06-27
pxwpxw's idea just might work, It might if disabling in windows helps, so you could try:

lsmod | grep cd
I get:
```
ide_cd                 32672  0
cdrom                  37664  1 ide_cd
ehci_hcd               34188  0
uhci_hcd               25360  0
usbcore               134280  7 xpad,usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd

```
Now, disabling ide_cd and cdrom, not usbcore might disable cd but not usb, to blacklist -prevent loading on boot- add them to /etc/modprobe.d/blacklist with blacklist ide_cd and blacklist cdrom at the end of the file.

If that doesn't help, one option might be to add boot parameters to the linux kernel, but I didn't find one that would do such stuff as disabling, most of them just load drivers.
Kernel has the startup file in /var/log/dmesg and system log in /var/log/syslog they might provide some info.

---

### Post by Stex on 2007-06-27
> **MattDTownsend said:**
> This may not be the way to lift your keyboard, but there HAS to be a way to lift the board.  I can't imagine another way to design it.  And 5 for 10 that after you lift it, you'll see whatever is holding the drive in place.  And maybe some other surprises.

What makes you think it's the CD-ROM, anyway?

It looks like my laptop's won again. The black keyboard casing is solid all the way round and there's no screws on the back of the machine either. The two caps on either side of the screen's hinges both clip off but I can't see the contained screws doing anything but holding down the screen's hinges. I found instructions on removing the keyboard: A long screw from underneath and then clips around the keyboard itself. Pried it off only to reveal another metal box, without screws, protecting the CD drive. This is so frustratingly ridiculous it's almost funny.... almost :p

I can't really be sure of the fault. The problem is that the laptop suddenly turns off and tries rebooting again, no warnings or errors at all. It started off small and got worse, as these things do. It happens with/without battery and power supply isn't dodgy. I used to think it was overheating but monitoring the CPU temperature showed that was fine. I don't have one on my hard drive though, but nothing seems to be corrupting through the crashes. I was adamant that it was due to heat as after a crash the laptop wont boot until it is completely cooled. When it tries to boot when warm both ubuntu and windows crash again or hang at the very early stages.

I noticed that ubuntu had lost my CD drive and windows wouldn't start at all. So after failed attempts to get to the drive, giving up and booting anyway the CD drive had obviously jiggled into place and I got it working again! (how ironic this turns out to be). The reboots then got really bad and then, when I disabled the CD drive in windows, the crashes died down greatly (but do still happen occasionally, used to crash after 3 minutes as ubuntu still does). Other problems I've seen are in my bios: sometimes, instead of announcing itself properly, the CD drive is printed with some corrupted letters and infrequently there's some kind of checksum error that resets my bios settings.

Thanks for the software tips too, I'll try them in the morning!

---

### Post by MattDTownsend on 2007-06-27
Could this be a southbridge problem?

---

### Post by Stex on 2007-06-30
> **Tachyon_ said:**
> Now, disabling ide_cd and cdrom, not usbcore might disable cd but not usb, to blacklist -prevent loading on boot- add them to /etc/modprobe.d/blacklist with blacklist ide_cd and blacklist cdrom at the end of the file.

The effects of that seem to have been quite strange. I didn't have ide_cd in my list so I just blacklisted cdrom. This has stopped the really frequent crashing but it still ceases up every half hour. Strange thing is it allows me to boot up ubuntu even when the laptop is warm but still crashes soon after unless it's completely cooled. Stranger still is that I'm still able to use my CD drive and mount discs from it.

I can only assume that all blacklisting did to it is stop it being loaded to begin with, only to have something else load it afterwards.

Matt: Hardware faults arn't out of the question at all. My laptops go through a lot of travelling, my last one only lasted about a year before something bridged and sent a charge right through the innards, wiping out the slot for my wireless card. And as it crashes even with the CD disabled it's probably more than a CD problem, but isn't the southbridge a bit core to a computer? Wouldn't I have to replace the whole motherboard for that kind of thing...

---

