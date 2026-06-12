---
title: "[SOLVED] Bizarre CD-ROM behavior - Can't boot from CD"
date: 2008-04-03
forum: Hardware &amp; Laptops
---

### Post by aysiu on 2008-04-03
This has me a bit baffled. I'm thinking of getting rid of my desktop (donating to a worthy organization / selling for cheap), and I want to be able to wipe the drive for XP or for an XP dual boot with Ubuntu or whatever (in other words, flexibility on what's installed).

When I tried to reboot with a Ubuntu CD I've used in the past and know works, the bootup went straight to Grub. So I thought it might be the CD drive and tried the other drive. No luck there, either. So I thought maybe it was the CD, so I tried two other CDs (one Knoppix, the other the restore CD for my computer for XP) and no luck on either drive. The drives spin up as if to read the CDs but then the computer doesn't actually boot from any of them.

So I thought maybe something was wrong with the BIOS. Nope. It was set to boot from CD. So I set the BIOS settings to the default and saw the default also was set to boot from CD first. Still no luck on any of the CDs.

The next possibility was that the some connection was loose, so I opened up the computer and checked all the cords. Everything seemed fine.

Here's the baffling part: I would have just concluded that my CD drives were both busted (odd that they'd both break at the same time) except that music CDs work just fine once I'm booted into Ubuntu. No operating system CDs are recognized by Nautilus, though at all.

These CDs have no scratches, and I know they work, as I've used them before.

What is going on? Has my computer just gone nuts? Is it possible that Grub has somehow taken over and bypassed what the BIOS wants to do? I'm using Hardy, by the way, but I don't think this is a Hardy issue, since the problem appears to happen even before Ubuntu boots up.

---

### Post by TheLions on 2008-04-04
[QUOTE=aysiu;4647448
.... Is it possible that Grub has somehow taken over and bypassed what the BIOS wants to do? I'm using Hardy, by the way, but I don't think this is a Hardy issue, since the problem appears to happen even before Ubuntu boots up.[/QUOTE]

does BIOS recognize the cd-rom drives?

try disconecting your HDD from computer and see if it would boot from cd-rom

also try booting from usb keydrive    

also try to check cables that don't have broken wire and check for bended pins on your cd-rom and mainboard. also check jumper settings

---

### Post by aysiu on 2008-04-04
Thanks for the reply, TheLions.

The BIOS does recognize the drives, and I've checked the cables already. I'm not sure what bent pins look like or what jumper settings are.

My next experiment will be to disconnect the hard drive--I don't think that'll work, but at least it might give me a helpful error message.

And, unfortunately, I don't have any USB drives to boot from.

---

### Post by PmDematagoda on 2008-04-04
aysiu, do you mean that the CD-ROMs can read all other media except for ones containing Linux OSes?

---

### Post by aysiu on 2008-04-04
> **PmDematagoda said:**
> aysiu, do you mean that the CD-ROMs can read all other media except for ones containing Linux OSes?
I haven't tried all other media, but audio CDs appear to work.

And it's not limited to Linux OSes. They won't read the restore CDs to my computer either (the restore CDs use Norton Ghost to restore Windows XP home to the computer).

The really odd thing is that not only will they not boot from the CDs, but they won't even be read or mounted.

---

### Post by lavinog on 2008-04-04
do you know the last time you booted from cd?

have you tried blowing any dust out of the drive(s)

did you ever remove or change the cd drives from the original setup...if so how are the MA/SL/CS jumpers setup?

does your POST screen say anything about the cdrom drives? Does it say BOOT FROM CD: at all before grub loads?

grub should not override bios.

lastly is it possible that there is a firmware update for your bios or cdrom drives (i recently had to do a flash update to enable booting to usb floppies..but had to boot from floppy to do the flash...argh)

---

### Post by aysiu on 2008-04-04
> **lavinog said:**
> do you know the last time you booted from cd? Unfortunately, no. It could have been broken for a really long time. I've upgraded Ubuntus since Edgy, I think. So if it is a hardware issue, the hardware might have been broken for over a year.

> have you tried blowing any dust out of the drive(s) Yes, I did try this.

> did you ever remove or change the cd drives from the original setup...if so how are the MA/SL/CS jumpers setup? No.

> does your POST screen say anything about the cdrom drives? Does it say BOOT FROM CD: at all before grub loads? What's the POST screen? How do I get to it?

And, no, I get no message saying it's booting from CD before Grub, but Grub does not show up right away (I get a blank screen with a small white cursor at the top) while the CD spins, as if it's *trying* to boot from CD. This spinning happens for about ten or fifteen seconds. Then Grub loads up.

> grub should not override bios. I thought so, but thanks for the reassurance.

> lastly is it possible that there is a firmware update for your bios or cdrom drives (i recently had to do a flash update to enable booting to usb floppies..but had to boot from floppy to do the flash...argh) I can look into that.

---

### Post by PmDematagoda on 2008-04-04
aysiu did you check the CDs that did not work with your CD-ROMs with CD-ROMs on another PC that are known to work properly?

---

### Post by aysiu on 2008-04-04
> **PmDematagoda said:**
> aysiu did you check the CDs that did not work with your CD-ROMs with CD-ROMs on another PC that are known to work properly?
Yeah, I checked one of them (Ubuntu) on my work computer, and it booted the live session. I have no idea what's going on. I'm going to try disconnecting the hard drive to see what error message I get when I try to boot from CD.

---

### Post by lavinog on 2008-04-04
> **aysiu said:**
> 

 What's the POST screen? How do I get to it?

And, no, I get no message saying it's booting from CD before Grub, but Grub does not show up right away (I get a blank screen with a small white cursor at the top) while the CD spins, as if it's *trying* to boot from CD. This spinning happens for about ten or fifteen seconds. Then Grub loads up.


Power On Self Test:
It is the screen that shows a memory test, then usually shows a list of devices that BIOS detects like cdrom drives and HDs.
Many name brand computers don't show a POST screen, but may have a setting on bios to show it usually you have to disable quiet boot.
some computers let you press ESC during bootup to let you choose what device to boot from.

Can you change out the IDE cable to the cdrom drives? I had a computer once where the ribbon cable had a nick in it which caused unpredictable results.

Both drives being bad seems less likely than a bad cable or IDE channel.  If your CDROMs are on IDE1 and your HD is on IDE0 maybe you could try setting up one CDROM as a slave to the HD and see if it boots...if it works then it would seem the problem is either the cable to your CDROMs or the IDE channel
```


[Motherboard]=======--------
                    |       |
             [HD]---|       |---[CD2]
                    | 
             [CD1]--
 

```

---

### Post by aysiu on 2008-04-04
Ah, that's the POST screen--yes, it acknowledges both drives. I may try switching up cables.

In the meantime, I unplugged the hard drive and tried to boot from CD. It spun up and then gave me this error message: ```
DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER
``` **Edit**: Well, no luck using a different cable (same message about inserting a system disk). I'm going to remove the drives and see if there's other dust I can get out.

---

### Post by PmDematagoda on 2008-04-04
That looks very strange, so it is quite obvious that it is something wrong with the hardware or the BIOS.

Did you put another CD-ROM and try booting the PC with it by any chance?

---

### Post by aysiu on 2008-04-04
> **PmDematagoda said:**
> That looks very strange, so it is quite obvious that it is something wrong with the hardware or the BIOS.

Did you put another CD-ROM and try booting the PC with it by any chance?
I'm starting to come to that conclusion also, but I'm going to try some more things.

Unfortunately, I have only two CD-ROM drives (both of which display the same symptoms).

---

### Post by az on 2008-04-04
> **aysiu said:**
> Ah, that's the POST screen--yes, it acknowledges both drives. I may try switching up cables.

In the meantime, I unplugged the hard drive and tried to boot from CD. It spun up and then gave me this error message: ```
DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER
``` **Edit**: Well, no luck using a different cable (same message about inserting a system disk). I'm going to remove the drives and see if there's other dust I can get out.

Did you unplug the power supply from all other drives?

Also, have you tried resetting the BIOS setting to default?

---

### Post by aysiu on 2008-04-04
Yes on both counts. Thanks, Az.

So after experimenting with just about every configuration I could think of and cleaning out all the dust I could spray out, I've concluded that one of the drives is damaged, and the other one somehow lost sensitivity on reading CDs, but I managed to get some sensitivity back on it (it can now read the restore disks for Windows XP Home but not the Linux CDs).

Thanks to all for the helpful suggestions on things to try. I now know what the POST screen is. :)

---

