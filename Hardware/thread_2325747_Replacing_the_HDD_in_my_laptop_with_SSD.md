---
title: "Replacing the HDD in my laptop with SSD"
date: 2016-05-25
forum: Hardware
---

### Post by simonn on 2016-05-25
I have moved back from OSX on laptops (always had linux on a server since 2003) and I am currently running Xubuntu 16.04 and Win10 on a Lenovo Ideapad 300 15ISK Model # 80Q7. I also have Xubuntu 16.04 running on an HP Stream 14".

The Lenovo is way more powerful, but has a HDD so although orders of magnitude more storage it is very slow to start, slow for to start apps compared to the HP Stream. So, I have been toying with replacing the HDD with an SDD.

I'm not really a hardware guy though. The last time I played with hardware OSes came on CDs and... BIOS. UEFI was a new thing that only macs seemed to have. I have also never replaced a HDD in a (non-apple) laptop. I also need to keep windows 10 on it for itunes for my 4 year olds inherited iPad.

Is it simply a matter of just pulling the HDD out, installing the SDD, partition SDD, and installing the OSes? Is there anything I need to be aware of WRT UEFI compared to bios?

Probably the wrong place to ask, but can I just use the windows 10 restore disk to restore windows onto the SSD?

I know the last time I dual booted windows (2003?), you installed windows first and then installed linux. Is this still the case nowadays?

---

### Post by oldfred on 2016-05-25
I do not know all the answers on Windows.
But now Windows keeps its product key in UEFI, but that key is only good for your OEM or vendor version.
I think many use image software like Macrium Reflect to copy it.

I prefer new clean installs with Ubuntu and copy /home and data. I also as part of my normal rsync backup export list of installed apps to reinstall. So new install is pretty quick.

But if installing with UEFI, how you boot install media UEFI or BIOS is then how it installs. And if UEFI drive must be gpt partitioned.
You cannot use dd to copy a gpt partition as both primary partition table, backup table & partition have GUID/gpt data that must match. May be possible to repair with gdisk but best not to. You can dd an entire gpt drive, but unless SSD is same size as HDD not possible.

More info in link in my signature.

---

### Post by Mark Phelps on 2016-05-25
I've read that Macrium Reflect can image and restore Linux filesystem partitions, not just Windows -- and I tried it a while back and confirmed that it works!

What I would suggest is the following approach:
1) Boot into Win10, open Disk Management.
2) Using that, shrink down the Win10 OS partition until the combined capacity of ALL the partitions fits easily onto your SSD
3) Connect your SSD to the PC using a USB-to-Hard Drive cable
4) Run MR and choose the option to Clone the hard drive to the SSD
5) Shutdown the PC and swap the SSD for the HDD
6) Reboot the PC

It should then reboot without problems -- as I have done this on my desktop and it worked like a charm!

Good Luck

---

