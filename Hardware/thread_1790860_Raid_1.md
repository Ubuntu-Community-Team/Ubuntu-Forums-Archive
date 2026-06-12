---
title: "Raid 1"
date: 2011-06-25
forum: Hardware
---

### Post by kuloch on 2011-06-25
I have a RAID PCI card set up, which supposedly was set for mode 1 (mirror) before I installed Ubuntu (single-core CPU, so I used 10.04).  However, it appears that the installation was put directly on the first drive, ignoring the 2nd completely.

I was just looking through a [couple]("http://ubuntuforums.org/showthread.php?t=408461") of [tutorials]("https://help.ubuntu.com/community/Installation/SoftwareRAID?action=fullsearch&context=180&value=Convert+to+software+raid&titlesearch=Titles"), which seem very helpful for installing a software RAID setup.  One mentions that a hardware setup requires some sort of kernel compatibility for Ubuntu to use it, which seems likely to be the case as the card is about 7 years old.

So here I am with a pretty much fully configured Ubuntu system (mail/IMAP server, web server, and mail client) running on /dev/sda1.  I get the impression from the tutorials that after formatting your two equal-sized partitions, you then proceed to set up the software raid device and make that the boot partition.  My concern is that doing so with an existing system might be bad, if anything other than /etc/fstab refers to /dev/sda1.  Is this an unnecessary concern?  Can I happily follow the command-line tutorial steps and plug away at a new RAID 1 setup?

---

### Post by tgalati4 on 2011-06-25
What is the specific RAID card?  Is there a RAID BIOS that you can boot into (Control-R or Control-M at the PC boot splash)?  Normally you configure your hardware RAID in the RAID BIOS or you use a utility (loaded from floppy or CD).  Then you select the RAID parameters (RAID1 Mirror and you select strip size, chunk size, and any other parameters).  Normally you stick with the default parameters unless you know what you are doing.

After the RAID1 is configured then you proceed with installation.  In your case, since you have a working system on one disk, you may be able to extend the RAID to the second disk using the vendor-supplied RAID utility.  That utility will automatically copy the data over to the second disk and then you will have a functioning RAID1.

If you can't find the RAID BIOS or setup utility, then you can simply use software RAID and there are quite a few tutorials for how to do that.

---

### Post by kuloch on 2011-06-25
I wasn't personally the one who did the RAID setup, but the guy who went through the Ubuntu installer said that he booted into the RAID's setup beforehand to create the RAID 1 array.  He did so again after installation, when it looked like Ubuntu had somehow ignored the mirrored setup.

I don't have a good enough view of the card's bottom to see it at the moment, but it is a hardware RAID PCI controller, built for 0/1/0+1 modes.  I ran it in RAID 0 for a couple years, then we had it running in RAID 1 for a few years on a Windows box.  And yes, it does have its own BIOS, with the option to boot to its configuration tool between system POST and boot loading.

After I set up our backup program to make backups of all critical files, I'll try booting back into the configuration tool and setting up the RAID 1 again.

---

### Post by tgalati4 on 2011-06-25
As I recall, if it's an LSI/PERC/megaRAID card you need to specify the device using a special module.

[http://linuxmafia.com/faq/Hardware/perc.html](http://linuxmafia.com/faq/Hardware/perc.html)

---

### Post by dancho on 2011-07-11
If you are in the mood for software RAID, I would recommend it above some of the cheaper "RAID" cards out there.

Perhaps my guide on how to convert a running Ubuntu installation to RAID1/RAID10 will help:

[http://iiordanov.blogspot.com/2011/04/how-to-convert-your-single-drive-linux.html](http://iiordanov.blogspot.com/2011/04/how-to-convert-your-single-drive-linux.html)

If you choose to reinstall, you can try this guide for making a fresh installation on RAID10/RAID1:

[http://iiordanov.blogspot.com/2011/07/how-to-install-linux-ubuntu-debian-etc.html](http://iiordanov.blogspot.com/2011/07/how-to-install-linux-ubuntu-debian-etc.html)

---

