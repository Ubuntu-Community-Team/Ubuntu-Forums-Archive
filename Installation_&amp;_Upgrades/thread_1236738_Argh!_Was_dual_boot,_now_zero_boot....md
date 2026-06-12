---
title: "Argh! Was dual boot, now zero boot..."
date: 2009-08-10
forum: Installation &amp; Upgrades
---

### Post by starbase1 on 2009-08-10
Well, that's why I hate partitions and installing...

I did have a working PC, which would offer the options ofgoing into Ubuntu (Studio), which was happily booting into that or one of two flavours of XP, (vanilla or 64 bit).

I decided to get rid of the Ubuntu Studio, and used Partition Magic under windows to format the dedicated EXT3 partition I had been using for Ubuntu Studio, so as to clear for installing Ubuntu 64 bit there in it's place.

Now when I turn it on it just goes round and round in a reboot loop.
[SIZE="7"][COLOR="Red"]
Argh![/COLOR][/SIZE]

With hindsight, I am now guessing that the booter on my C drive was padding control to something on the wiped partition, (which then offered the choice between XP versions)

Does this make sense?

Can I get back my old operating systems, and restore my PC to life?

Nick

---

### Post by chessnerd on 2009-08-10
Pop in a live CD and see if your Windows partitions still exist. If they do you still have a chance of getting everything back. Otherwise, well, let's just hope Windows still exists...

---

### Post by merlinus on 2009-08-10
You can boot from the live cd and install linux into the partition where studio was, and then select advanced at the last screen and install grub to the mbr.

Everything should be working again after that.

It does not seem to me that anything was touched with your windows installation, but

```
sudo fdisk -l
```

will show whether that is true or not.

---

### Post by starbase1 on 2009-08-10
I seem to remember something from XP that would get things bootable, fixmbr? Would that be safe to use in this situation?

I'm reluctant to try and install something over the top of what I have until I have got a grip of things...

Nick

---

### Post by starbase1 on 2009-08-10
It gets worse...

The PC is not booting off the optical drive...

Correction, poking around boot sequence got it booting - I must stay calm!

---

### Post by ronparent on 2009-08-10
Don't panic yet. You probably just have to enter your bios at boot and change the boot order. Typically on recent motherboards, the bios will allow you to select the cd as the first boot device.

---

### Post by merlinus on 2009-08-10
You can use xp install cds -- select restore (or recovery) and then /fixmbr and/or /fixboot -- and then xp should boot.  Or you can use supergrub do the same thing:

[http://supergrubdisk.org](http://supergrubdisk.org)

---

### Post by starbase1 on 2009-08-10
> **merlinus said:**
> You can use xp install cds -- select restore (or recovery) and then /fixmbr and/or /fixboot -- and then xp should boot.  Or you can use supergrub do the same thing:

[http://supergrubdisk.org](http://supergrubdisk.org)

Do you know if fixboot / fixmbr will cope with more than one windows option?

I'm now looking at the C drive from the Ubuntu live disk.

Looking at the files, I see boot.ini containing this:
[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


Any clues here?

---

### Post by merlinus on 2009-08-10
IIRC, boot.ini info is needed in order for xp to run, but you will still need to get it to do so by restoring its bootloader to the mbr.

supergrub is your best bet, if you run into trouble using the xp install cd to do this.

If you hate partitioning, you can always install wubi after deleting all linux partitions with gparted.

---

### Post by starbase1 on 2009-08-11
> **merlinus said:**
> IIRC, boot.ini info is needed in order for xp to run, but you will still need to get it to do so by restoring its bootloader to the mbr.

supergrub is your best bet, if you run into trouble using the xp install cd to do this.

If you hate partitioning, you can always install wubi after deleting all linux partitions with gparted.

Thanks, I've just woken up, I think I will think about it and have another go when I get back from the day job.

I like wubi, and used it on the other PC, but thought as I had a partition already set up it would be safe enough to wipe that and use it!

---

### Post by starbase1 on 2009-08-12
OK! Thanks to everyone who contributed, things are coming back to life now.

In case it helps anyone else who gets stuck in the same way:

1. Stay calm, find some bootable CD's!

2. To be specific, a live disk to check the drive and data is OK, the super grubthingy for examining the stuff that is there, and a windows install disk that can take you into recovery.

3. For the windows part, you don't bneed any sort of activation code to get into recovery. Also note that in my case at least, it was able to recover BOTH the 64 and 32 bit options.

4. Windows will write over Linux. Linus is polite and respects other options. So I recommend restoring windows first - if you do it second, it may well trash all the good work you did in your Linux.

Thanks again,
Nick

---

