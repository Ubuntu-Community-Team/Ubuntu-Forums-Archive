---
title: "OS Detection and GRUB"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by Gwasanaethau on 2009-01-14
Howya!

I was wondering: when installing Ubuntu, the CD is able to detect what OSs are installed on other partitions, and what versions they are (for example, it can not only detect that I have Windows installed, but specifically XP Home Edition). How does it do this? I assumed it had something to do with GRUB, as it automatically adds Windows and Linux versions to its menu, but I had a look at the source code and couldn't find anything in it; though I have to admit my knowledge of C is limited!

Any ideas?

Thanks in advance!

---

### Post by logos34 on 2009-01-14
I thought it was this program:

> Package: os-prober (1.26ubuntu2)

utility to detect other OSes on a set of drives

This package detects other OSes available on a system and outputs the results in a generic machine-readable format.
Packages providing os-prober

os-prober-udeb
    utility to detect other OSes on a set of drives


included in the [ubiquity live cd installer pkg]("http://packages.ubuntu.com/intrepid/ubiquity")

---

### Post by monikersupreme on 2009-01-14
I was curious about this too... 

I have a workstation with 2 x 250GB SATA drives. The former drive has XP installed and last night I attempted to install Ubuntu v8.10 on the latter drive, however the installation failed due to a corrupt install CD. 

After the first install failed, I booted into XP, re-formatted the latter drive, and burned a new Ubuntu install CD. 

On my second attempt to install Ubuntu on the latter drive, the installer no longer recognizes XP on the former drive.

I haven't attempted to actually install yet, I'm worried that GRUB will not recognize my XP installation and thus will not allow me to dual boot my installation. I would also like to be able to import my XP settings / configurations (this was an option offered during my first abortive Ubuntu install)...

I thought that reformatting the latter drive would have fixed this issue but now I'm worried that my XP MBR might have been modified during my first failed Ubuntu install attempt, however if this were the case it seems unlikely that I would be able to boot into XP at all...

( BTW, ignore my sig - those details are for my laptop installation, my current specs are:
MSI K9MM-V / 2GB DDR2 / AM2 5200+
TrendNet Wireless-N PCI card
BFG 7800GS AGP card
2 x 250GB Hitachi SATA150 drives )

---

### Post by Gwasanaethau on 2009-01-14
That looks like what I was looking for. Thanks a million!

---

### Post by Gwasanaethau on 2009-01-14
I don't know much about the Windows MBR, but I'd say that if it was destroyed you probably wouldn't be able to boot into Windows at all. You can try repairing it with the Windows XP CD or a Windows 98 floppy (if you have one) - as to actually *how* to do it, I can't remember off the top of my head (I had to do it once a long time ago). However, if you're going to attempt to install Ubuntu again anyway, there probably isn't any point in repairing the Windows MBR as GRUB will end up overwriting it when you install Ubuntu.

If GRUB doesn't detect your Windows installation after installing Ubuntu, you can always edit GRUB manually. There are loads of posts about how to do that, so I won't mention it here. I'd go ahead and give it a try - can't be any worse than the first attempt! ;)

You might want to check the Ubuntu disc you burned before installing, just to see if it's burned correctly. You can do this from the boot menu of the CD.

Best of luck with it now!

---

### Post by kikizing3 on 2009-01-16
Almost the same thing is happening to me but I cant boot into Ubuntu at all. It goes straight to windows even booting from the hard drive that ubuntu is installed on. More about my setup [here]("http://ubuntuforums.org/showthread.php?t=1040578").

---

