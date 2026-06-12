---
title: "Issue installing: &quot;No boot media or boot drive&quot;"
date: 2009-07-27
forum: Installation &amp; Upgrades
---

### Post by _greg on 2009-07-27
Hello, 

I'm attempting my first real foray into Linux and am trying to install Ubuntu on a computer a friend has given me.

Specs:
120GB HDD ATA
40GB HDD ATA
Plextor 40/12/40 CD-RW
DVD-ROM (Unsure of brand)
Nvidia GeForce 5900 Ultra
1GB RAM
Asus P4P800 Mobo

Issue:
I have the Ubuntu .iso that I downloaded from here and burned using OS X's Disk Utility in the CD drive and I am getting an error that says, "Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a key"

I've played around in the BIOS and set the boot order to place the CD drive first, with the 120GB HDD second (it won't allow me to add the DVD or 40GB HDD in at all, I'm guessing because they are slave drives).

Both hard drives are completely wiped.

I've tried the disc in both the CD-RW and the DVD drive and I get the same error, even after choosing to boot from the CD drive.

I tried the disc in my MBP and the disc worked fine in VM Ware Fusion.

Any ideas?

---

### Post by starcraft.man on 2009-07-27
A few quick diagnostics:

On the computer in question (the one your installing to), can you boot any other bootable media? i.e. a windows install disk, or some other live environment. You could try a [gparted]("http://gparted.sourceforge.net/download.php") disk for instance.

If you can't, then I think it's pretty clear your problem lies in the BIOS. That makes it difficult, BIOS are very different, but usually just setting the boot order should do it. Play around with the settings some more, if you can't boot anything its something in that menu.

I see you are a Mac user, is the computer in question an old mac? If so, then I assume it is using efi instead of BIOS, that could be the problem. You'll need to go in the options for it and check that it is supporting whatever legacy is possible, like MBR support or some option.

Tell me if that helps, if not I'll try and think of more.

---

### Post by _greg on 2009-07-27
Thanks for the quick reply!

The computer in question is a custom built PC (my friend formerly used it as a WinXP gaming box).  Along with it, he gave me some CDs, one of which is a burned copy of XP which is un-bootable also (but being a burned copy, I can't verify if it was done correctly).

You're probably right in that the problem lies in the BIOS, I can't see what the problem might be though.

I have the boot order setup how I want it (and either way, since there is no OS on the HDD, even if the HDD is first, shouldn't it auto-advance to the CD drive?).  I've noticed that while turning on and loading the CD, the drives don't seem to spin up or do anything with the CD.

---

### Post by starcraft.man on 2009-07-27
Hmmm, well, try gparted like I said. Ensure you sum check it after download of ISO and then again verify the burnt copy is correct. If a verified gparted disk isn't working, then ya, I'm pretty sure it's something with the bios OR hardware. Maybe a wire to the tray got loose or something like that.

You can always try [installing from a usb stick.]("https://help.ubuntu.com/community/Installation/FromUSBStick") The computer needs to be able to boot USB though, check boot options. Simple procedure otherwise. 

Just a thought, but perhaps some other option set in the BIOS is interfering with the regular boot. To rule out, I'd reset the BIOS (usually an option to do so from main menu) to factory defaults and then only change the boot order. Or, directly select the drive in question to boot after pushing the boot interrupt key (i.e. one says press F12 to choose boot device...). Also, ensure you remove any other USB device at the time of booting (i.e. external HDs, Wireless USB keys, ...).

Hope that helps.

---

### Post by _greg on 2009-07-31
So, I was able to get it installed.  It turns out that the computer, for one reason or another, doesn't spin up and check the CD drive for boot media, unless the tray is opened and closed during boot.

It was a total accident, but it allowed me to install.

My next step is mounting my NAS HDD so that I can stream movies (I have a 1TB HFS+ drive attached to my Airport via USB.  Ubuntu sees the Airport, but does not actually see the disk [when I click on it, it looks for Windows shares])

Thanks for your help!

---

