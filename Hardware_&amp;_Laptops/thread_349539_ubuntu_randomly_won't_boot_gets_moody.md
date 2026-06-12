---
title: "ubuntu randomly won't boot? gets moody?"
date: 2007-01-30
forum: Hardware &amp; Laptops
---

### Post by fiveryanfrenzy on 2007-01-30
i run ubuntu all the time and i love it and it seems to be working so smoothly then... all the sudden... seemingly randomly, i go to boot my system and...

it fails at 'Loading Hardware Drivers...'

and starts spitting out things like

I/O Buffer Error HDA something over and over...

I think it fails at

waiting for sys/devices/platform/i8042/serio0/serio2/bus' failed

or something

running in recovery mode the same thing happens and it says things like

hda: lost interupt
ide: failed opcode was: unknown

WHY is this happening? why does it boot fine most of the time and then some days it randomly just won't boot and if I let it run it just keeps doing the I/O buffer error at logical block 0 then 1 then 2 and goes for a long time, going through things like RAID, LVM Volume Groups, Enterprise Volume Management Systems (which took the longest)

I have not been able to figure out what would cause this it always seems so random!

please help as I am sick of waiting for windows to catch up with me already.

---

### Post by fiveryanfrenzy on 2007-01-30
like im in ubuntu now but there is no telling when this will happen again?

should i try reinstalling grub?

---

### Post by K.Mandla on 2007-01-30
It's gotten past the Grub boot sequence, so whatever is happening here is probably not grub's fault.

When you get to the next good boot, enter the command *dmesg* in a terminal and paste the results here. (It will be big; use the <code> tags so it's in a scrollable box for us. ;) )

Hopefully if there's an error, it will come through in the dmesg output.

By the way, you should take this as a sign to start backing things up. Better safe than sorry.

---

### Post by bb002 on 2007-01-30
I've had this problem twice before. This first time was with a cdrom drive that was failing, the drive would lock up whenever it couldn't properly read a cd.

The second time was with a really old laptop and that one turned out to be a BIOS DMA setting. The HDD supported up to DMA 5 while the laptop only went to DMA 2. They would randomly quit working. Everything would *appear* to be right in the BIOS but I would have to load the defaults and correct the bios boot order. Everything would start working again for another couple of weeks.


Your case maybe different. My case was a with laptop made in 1996 and a 60GB HDD made in 2006....the same machine that housed the troublesome cdrom drive above but I still believe it to be a failing drive since some cds would work and others wouldn't. Most of the cds i tested were manufactured so i don't know if they were 650MB cds or 700MB cds. It could be that the cd that didnt work were 700MB cds...anyways. good luck!

---

