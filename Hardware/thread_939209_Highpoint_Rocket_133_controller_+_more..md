---
title: "Highpoint Rocket 133 controller + more."
date: 2008-10-05
forum: Hardware
---

### Post by Dumain on 2008-10-05
Greetings.
I'm considering switching from Win XP to Ubuntu (Hardy, then to 8.10-whatsitsname when It's released the 30th this month), going for the newest at all times) but I'm wondering if I can still use my controller card?
It's a (fairly old) IDE RAID-controller (Highpoint Rocket 133 as in the title).
At their site I couldn't really find any Ubuntu-specific drivers, so I guess the question is, is it supported "out of the box" so to speak,? or do I have to get the source (if I'm not mistaken that's available) and somehow compile it myself?
I'm quite the newbie with Linux so bear with me.

I'd be running Ubuntu from a SATA drive (Raptor if that matters), and only using the IDE ones for storage.

Also there is the other hardware I have, which is an Abit IP35 Pro with a Sapphire Radeon HD3870 and an old Soundblaster Live! soundcard. Am I right to assume that this will/should work ok? Just asking as I don't have any really obscure hardware.

Lastly (this is maybe out of bounds considering this is the hardware portion of the forum), my 2 ide drives (both connected via controller card) is running NTFS, but as I understand it Ubuntu doesn't come with NTFS support out of the box? If so, is this an easy task for a newbie to take care of?

---

### Post by nixscripter on 2008-10-06
First question: yes, there is a driver. Yes, you have to compile it yourself. Yes, doing that is a process which is quite messy. And even when you're done, your mileage may vary.

The source of the driver (which is probably the one you found): [http://www.highpoint-tech.com/BIOS_Driver/rr133/Linux/hpt37x2-opensource-v2.1-0717.tgz](http://www.highpoint-tech.com/BIOS_Driver/rr133/Linux/hpt37x2-opensource-v2.1-0717.tgz)

Second question: NTFS is not well supported on Linux (at least not without a lot of work). You would be well-advised to repartition the disks in question instead.

---

### Post by splbound on 2008-10-31
Hi,

I too have this card and am trying to get it working. Using the new 8.10 ubuntu server.

I have downloaded the headers using apt-get and am now stuck with make errors when I try to make the driver.

It seems as though it cannot find some files namely linux/config.h

I can get around this by symbolic linking autoconf.h to config.h but then I run into further problems with mach_apicdef.h not being found. The line with the error is:

/usr/src/linux-headers-2.6.27-7-server/include/asm/smp.h:187:28: error: mach_apicdef.h: No such file or directory

This is where I am stuck.

Any help with what I should possibly ln now?

---

### Post by psusi on 2008-10-31
It looks like this is a fakeraid controller supported by dmraid.  You don't need any special drivers.  Boot the livecd and it should see each physical disk.  Install the dmraid package and run dmraid -ay and the array should show up in /dev/mapper.

---

### Post by splbound on 2008-11-03
Thank you PSUSI. Will give that a go .. had to use Vista x64 in the meantime *Yuck* now to try and migrate the data over from NTFS.

---

### Post by splbound on 2008-11-04
Have to report a no show with the controller and drives using the livecd. The card I have is the non raid highpoint rocket 133 and is probably using a different chipset.

My other option is to just ditch the board and try out using some IDE to SATA converters and use the recognized controllers on the motherboard.

Or just stick with vista x64. The machine will only be used to fileserve anyway.

---

