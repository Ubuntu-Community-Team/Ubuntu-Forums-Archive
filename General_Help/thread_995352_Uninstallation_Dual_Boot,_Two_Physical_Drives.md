---
title: "Uninstallation: Dual Boot, Two Physical Drives"
date: 2008-11-27
forum: General Help
---

### Post by HF_TKD on 2008-11-27
I pretty recently installed Ubuntu as a total newcomer to really just "tinker" with it. I didn't install on a partition, I just used a separate physical hard drive that until now I didn't have any use for. Now I'd like to remove Ubuntu in order to utilize that disk space with Vista.

I did some searching and I found some other threads where people have the same exact situation as I do, but I'm not very experienced when it comes to working with operating systems and I want to confirm that I have a good understanding of what I need to do.

The easiest way to do this is by burning a live CD of gparted, and with that remove my linux installation... Then run my Vista disk and use fdisk mbr to remove grub?

Essentially, I *think* this is the solution, but I'm a noob and I would like some confirmation that these steps are correct. Thank you very much.

---

### Post by thomas228 on 2008-11-27
> **HF_TKD said:**
> I pretty recently installed Ubuntu as a total newcomer to really just "tinker" with it. I didn't install on a partition, I just used a separate physical hard drive that until now I didn't have any use for. Now I'd like to remove Ubuntu in order to utilize that disk space with Vista.

I did some searching and I found some other threads where people have the same exact situation as I do, but I'm not very experienced when it comes to working with operating systems and I want to confirm that I have a good understanding of what I need to do.

The easiest way to do this is by burning a live CD of gparted, and with that remove my linux installation... Then run my Vista disk and use fdisk mbr to remove grub?

Essentially, I *think* this is the solution, but I'm a noob and I would like some confirmation that these steps are correct. Thank you very much.

Hi
Relative newbie here but your method will require that you format the ubuntu disk to ntsf. Why not use your ubuntu live CD to do what you're trying to do since it contains gparted?

Sorry to see you leave ubuntu but maybe you'll be back:)
Good luck
Tom

---

### Post by TeXtonyx on 2008-11-27
If you were dual booting, Vista and Ubuntu, use Vista to delete
the Ubuntu partition and you can create and format a ntfs partition
and if this is a standalone drive in a system you will need to boot, 
install Vista to boot so delete the partition then. And if you want
to add this drive to a system with a Vista drive already, connect the
drive as slave, and then delete the partition from Vista and format.
Use a Windows tool designed for Vista and a Linux tool for Linux.
Windows has proprietary code which is why Wine sometimes falls short.
You will need to run Vista bootrec, fixmbr and fixboot, if grub is
in the MBR, unless you are installing Vista, then it does it for you.
Your second drive can either be bootable ntfs, or a data drive ntfs.

ntfsprogs,
TeX

---

