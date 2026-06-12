---
title: "What is wrong with my hdd?"
date: 2009-06-07
forum: Hardware
---

### Post by Serdar.Osman.Onur on 2009-06-07
some time ago i started to get this message on my laptop:
"operating system not found".

i used to have a multi-boot system with ubuntu 7.10, solaris 10 and vista. now i can not get to grub menu.

bios shows no hdd, when i boot using ubuntu live cd gpedit shows no disks neither!

when i open a terminal and type "sudo fdisk -l" i get nothing

on device.map i have only "/dev/fd0" entry and nothing else.

and i had a message saying "failure fixed disk 0" not every time i try to but, just once.

is my hdd blown?

thanks...

---

### Post by quixote on 2009-06-08
It doesn't look good, but maybe it's the partition table and maybe it's recoverable.  Did you install Vista last?  If so, maybe it clobbered the boot record.  

I'd try testdisk.  Boot from a LiveCD, enable the universe repository in Software Sources if it's not already enabled.  Reload.  Testdisk should appear in the list.  Install.  (This isn't permanent since you're working from a CD.)

Then try the instructions here: [http://www.howtoforge.com/data_recovery_with_testdisk](http://www.howtoforge.com/data_recovery_with_testdisk) and/or here: [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step) and see what it tells you.  

Testdisk can change the low level formatting of your drive (the "geometry") so it's important NOT to experiment with settings unless you know what you're doing.  Following the instructions is safe, though.

---

### Post by damis648 on 2009-06-08
Unfortunately, since the BIOS cannot find it, it looks like you may be done for. If I were you, I would take it out and re-seat it, or at least try reading it via an external enclosure. If neither of those work, I'm sorra to say but your drive may be dead.

---

### Post by Serdar.Osman.Onur on 2009-06-08
@quixote
i didn't install vista last. vista came with the laptop and i put solaris and ubuntu on top of it and everything has been fine for months and i just dont know what went wrong, like this error came out of nowhere...i will try testdisk and let u know if it works.

@damis648
i was thinkin' about reading it through an external enclosure but i'd rather keep that as the last choice until i decide i can not recover the disk by any other way.

thank you both guys...

---

### Post by Serdar.Osman.Onur on 2009-06-20
took out the laptop's hdd, took out my external hdd from its case, put the laptop's hdd in external hdd case, plugged it in on another laptop and it said stg like "one of the usb devices has mulfunctioned, windows can not recognise it". there are 2 lights on the external hdd case, one red and one green. green shows that power is supplied to hdd, red indicates the hdd access (it blinks whenever the hdd is accessed). when i plug in the broken laptop hdd redlight stays on still with no blinking and hdd makes a strange sound constantly. 4-5 clicks and then some period of silence. and keeps repeating this cycle.

Now i am almost sure that hdd is dead....

---

### Post by quixote on 2009-06-21
That repeated cycle of a series of clicking-type noises is the drive head trying to read the drive and not doing it.  I think your diagnosis is correct: drive is gone. :shock:

If the data on there was critical, there are professional disk recovery companies that get data off even damaged drives, but they're pricey.  (Like several hundred dollars pricey.)

I guess, since there's nothing to lose, you could try another enclosure.

I feel bad there wasn't a better outcome! :(

---

### Post by markmckee601 on 2009-06-21
I have had a number of hard drives fail like that.
I have found that sometimes when windows can't recognize a usb device
like a hard drive linux does and most of the time you can recover at least some of the data.

It's times like this when we regret backing up and realise how important it is to backup.

I hope you can recover the data you need if you don't have a backup.

---

