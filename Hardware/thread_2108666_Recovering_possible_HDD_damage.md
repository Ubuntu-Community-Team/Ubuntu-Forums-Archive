---
title: "Recovering possible HDD damage"
date: 2013-01-25
forum: Hardware
---

### Post by SteveTyrer on 2013-01-25
I have 12.04 lts running on a Toshiba NB510-10D, Ubuntu has been running for a long time and was stable, the Toshiba was dropped on to hard surface and will no-longer boot.
the machine starts up  the BIOS okay.  But then I just get a blank screen, I think the head could have crashed in to the HDD.

I have booted from a USB stick with 12.04, but don’t know how to use the recovery tools.

Can someone please give me some guidance 
Thanks Steve

---

### Post by tgalati4 on 2013-01-25
Open a terminal:

```
sudo fdisk -l
```

That is a lower-case L not a 1.  See if the operating system can enumerate the drives.

If /dev/sda1 etc is found then you can do the next step.

It's possible that the ribbon cable has come loose inside.  You might want to open the hard disk bay and reseat the connections.

The next step is to get a large USB flash drive and use testdisk and photorec to recover files to your blank flash drive.

While still booted in Live Mode off of USB:

```
sudo apt-get install testdisk
man testdisk
man photorec
```

Of course this will only work if you can see the drive with fdisk.  If you can't then you may have to remove the drive, put it in a USB enclosure and plug it into another machine.  It's possible there is internal damage to the laptop that is preventing boot--in addition to damage to the drive.

---

### Post by SteveTyrer on 2013-01-25
Thanks for your help, it looks like I have a damaged disk, and now I know how to check things out :p

---

