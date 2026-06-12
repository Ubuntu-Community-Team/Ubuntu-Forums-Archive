---
title: "Hard drive not seen by bios, how to boot?"
date: 2008-07-19
forum: Hardware
---

### Post by Gryffon on 2008-07-19
I hope this is in the right place and labeled right!  Suffice it to say my old hard drive bit the dust; got a new one, but it's SATA and I'm using an adapter...and the bios doesn't recognize the new drive in boot up.  Sometimes *within* bios it'll pop up, though (seems random)...but never during bootup.  Anyway...

However, a live CD had no problem seeing the new drive, and was able to install Ubuntu 8.04 just fine to it.  It also looks like I can mount and read/write to the drive from the live CD.

Is there some work around to boot the drive either from within the live CD, or another bootable CD?

Mainly wondering as I'd rather not get a new motherboard/CPU just yet if there's some way around it.  I was planning to get a new laptop about now (just need to choose and buy! :lol: ), then wait till sometime next year for the rest of the desktop.

And thanks for any help/thoughts!

---

### Post by logos34 on 2008-07-20
Get the [Super Grub Disk]("http://supergrub.forjamari.linex.org/?section=download")--burn a cd, make a floppy or use the USB tar.gz if your Bios support USB boot.  Maybe it can see the disk on boot.

Post back with the results.

---

### Post by Gryffon on 2008-07-20
SGD doesn't seem to help any (tried it initially, and again today) -- it doesn't seem to see the drive either (I get "Error 15: File not found").  Granted, I might be doing something wrong as I've not done much with SGD before.

---

### Post by argosreality on 2008-07-20
When you say you're using an adapter are you using an adapter that converts the SATA to PATA IDE connectors or are you using an addin card to give you SATA ports?

Can you install ubuntu, boot to it and actually use the system or does it only install and then become unusable?

---

### Post by logos34 on 2008-07-20
> **Gryffon said:**
> SGD doesn't seem to help any (tried it initially, and again today) -- it doesn't seem to see the drive either (I get "Error 15: File not found")

Then the next thing I'd do is try making a Grub boot CD (basically copy the kernels to the CD where they can be found and loaded at boot)

If you're interested let me know--I've got a howto somewhere.

---

### Post by Gryffon on 2008-07-21
argosreality -- I'm using an adapter (not a PCI card), and yep, can install it but not do much with it after (from the live cd can read files, but don't have permission to write).

logos34 -- Yes, if you happen to have it or a good link handy, that'd be great!

---

### Post by logos34 on 2008-07-21
Ok, I found it.  

Since you need to make and burn a grub cd, you obviously can't do that while running the ubuntu live cd in the cdrom drive.  The easiest way to do this is to use the [Parted Magic rescue cd ]("http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads")(45 MB download).  It runs entirely from the ram after boot, freeing up the cdrom drive.  So I suggest you use that.  (unless you have a usb stick to transfer the copied files to another machine to make the cd)

---

