---
title: "Strange problem - KBuntu 9.04 install"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by Krupski on 2009-05-07
Hi all,

I downloaded and burned an "alternate" (text based) install ISO of Kbuntu 9.04 and burned it to a CD. No problem.

I tried to install it to a Western Digital "Passport" 500 GB portable USB hard drive.

During install, I use manual partitioning, I can see the drive and at the end I install GRUB to (HD2) (there are two fixed drives in my PC... HD0 and HD1, so the USB drive is HD2).

It all LOOKS like it worked properly, but upon bootup all I get is a "GRUB error #2".

So, I did another install... this time to a Sandisk 8GB USB memory stick. Installed exactly the same way, set GRUB to HD2, etc...

THIS install boots and works properly.

So, lastly I booted KBuntu from the USB stick, plugged in the USB hard drive (which came up as /dev/sdd) and used "DD" to image the USB stick to the USB hard drive.

Plugged the USB hard drive in alone and now it boots up just fine (although it's still an 8GB install because it's an image of the USB stick). 490 some gigs are, of course, unused.

Obviously, this rules out the hard drive as being bad... so why doesn't a direct install work???

If I install an older CD to that drive (say Ubuntu 8.04), it works fine. But Ubuntu and Kbuntu 9.04 both DON'T install properly to that drive.

Any ideas???

Thanks!

-- Roger

---

### Post by decoherence on 2009-05-07
I'm going to assume that you're using the BIOS to select booting from your external USB device?

In that case, does it work if you tell grub to boot from hd0?

---

### Post by Krupski on 2009-05-07
> **decoherence said:**
> I'm going to assume that you're using the BIOS to select booting from your external USB device?

In that case, does it work if you tell grub to boot from hd0?

The BIOS is able to boot from USB devices, and I have it set to "Boot USB first".

When I installed KBuntu, I had to tell it to install itself to the MBR of disk #2 (which it did).

However, when it boots it looks for a UUID, so the drive number is irellevant. 

You are right though... in Ubuntu 8.04 it installs to (HD2) and sets "root" to HD2.

The first time around, I have to hit "E" during boot and change HD2 to HD0 to boot up, then I can edit menu.lst later.

Strange thing is, the USB stick boots fine, the IMAGE of the USB stick, copied to the external HDD also boots fine, but an install DIRECTLY to the external HDD fails.

Note that I get a GRUB Error #2... it doesn't even make it as far as to allow me to edit "HD2" to "HD0" (which isn't even necessary since it's using UUID anyway).

If it matters... I did a manual partition of the removable drive, using 95% of it for Linux and 5% for swap. I formatted the root partition as EXT3. Nothing at all unusual (except for the overly huge swap space of 25 GB).

Oh well... :confused:

---

