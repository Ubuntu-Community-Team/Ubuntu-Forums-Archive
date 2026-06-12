---
title: "Tri-Boot"
date: 2005-12-01
forum: General Help
---

### Post by Hybridx0 on 2005-12-01
Hey, i am a newb to linux and so i think this it is a good idea to get some consultation before installing ubuntu with GRUB. My situation is like this:

I have 2 hard drives, c:\ and e:\

c:\ is where my MBR and NTLDR are located, along with a winxp home
e:\ is where my winxp pro is located and which i am currently running from

I want to no how i can install ubuntu on a seperate partition and arrange i so grub can boot both winxp os's.

How would i go about doing this?

Any help GREATLY appreciated.

---

### Post by amohanty on 2005-12-01
When you install Ubuntu, it automagically detects any existing OSs and prompts you to confirm the addition of those OSs to the grub menu. As long as GRUB is installed in the MBR (default) it will be able to detect the existing OSs.

To create a partition on E:\ use something like PartitionMagic or boot from the live cd and use parted to do it.

HTH
AM

---

### Post by Hybridx0 on 2005-12-01
I will attempt this after i finish downloading the new 5.10, but i have seen some information regarding dual-booting and that GRUB should not be installed in the MBR, is there any relevant reason for this?

---

### Post by kairu0 on 2005-12-01
Some distros don't add other operating systems very well when they install GRUB. For example, I installed Mepis last week and it missed adding Ubuntu.

But from my experience, Ubuntu does a pretty good job of adding all of your OS's, so it shouldn't be a problem.

If you absolutely don't want to install GRUB in the MBR that is still an option, though.

---

### Post by Hybridx0 on 2005-12-01
I have created a backup of the NTLDR, boot.ini and ntdetect.com files onto a floppy disk, so in the worst case scenario i have a way to boot my xp partition, now that i have this safeguard i may try my luck.

---

