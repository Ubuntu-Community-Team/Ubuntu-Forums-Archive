---
title: "Move GRUB to its own partition"
date: 2009-03-03
forum: Installation &amp; Upgrades
---

### Post by oxsyn on 2009-03-03
I've been testing out a lot of different OS's on my laptop.  And doing some things to my ubuntu install that make me worry a bit.  I'd like to move grub to it's own partition.

First, is this recommended?  Are there any drawbacks?  I'd like for it not to be tied to my installation of Ubuntu, since it could get hosed or I may want to install over it at some point.

Second, if I move grub, do I need to move the entire /boot partition (and subsequently the kernel images)?  If I move the kernel images I'm using with ubuntu, what about other distros?  Will I need to move those kernel images as well?

I'm probably over thinking this, no?  It should be as simple as creating a tiny ext3 partition at the front of the drive, copying grub from ubuntu to it, and then running the root command, and the editing menu.lst to point at the correct partitions ... right?

---

### Post by Anger 2 on 2009-03-03
Right.See
[http://www.linuxnewbieguide.org/content/partitioning-disk](http://www.linuxnewbieguide.org/content/partitioning-disk)

---

### Post by oxsyn on 2009-03-03
> **Anger 2 said:**
> Right.See
[http://www.linuxnewbieguide.org/content/partitioning-disk](http://www.linuxnewbieguide.org/content/partitioning-disk)

Broken link :/

---

### Post by Anger 2 on 2009-03-04
Sorry about that.
[http://www.linuxnewbieguide.org/content/partitioning-disk](http://www.linuxnewbieguide.org/content/partitioning-disk)

---

### Post by Anger 2 on 2009-03-04
Same again.the missing part is content/paritioning
[http://www.linuxnewbieguide.org/content/paritioning-disk](http://www.linuxnewbieguide.org/content/paritioning-disk)
I hope this works.

---

### Post by 4leite on 2009-03-04
hi that link should be:

[http://www.linuxnewbieguide.org/content/paritioning-disk]("http://www.linuxnewbieguide.org/content/paritioning-disk")

I'm guessing you didn't use the insert link button or copy and paste. Unfortunately the link is misspelled (paritioning). You used the correct spelling and thus the broken link.

In response to the original poster, I'm not sure whether this link will help you as it does not answer the question as to whether having grub on a separate partition is a good idea.

---

### Post by Anger 2 on 2009-03-04
The link in my second post works.Atfirst I made the same mistake as you.Paritioning  is the correct spelling and not partitioning,surprising as it might seem.Thanks for the input anyway.

---

### Post by Rallg on 2009-03-04
Consider using grub4DOS, on a bootable USB pendrive. Here is the concept: With grub4DOS on a USB pendrive, your hard drive's MBR is unchanged from what it was. So, if you start with a Windows computer, the MBR only boots Windows, as if Ubuntu did not exist. If your computer already boots some other Linux OS via grub, then it will continue to do so.

You need a blank USB pendrive (does not need to be large), and capability to boot from USB. What you do is make the USB pendrive bootable, then install minimal DOS files (this procedure is described elsewhere on the Internet). Then, you install grub4Dos, which is a DOS program, on the pendrive. Then, you modify its menu.lst file so that the choices point back to your hard drive (which will be hd1 as seen from the pendrive).

If the pendrive is inserted and you choose it at boot time, then you get its grub choices. If not, not.

Now, when you try a Linux distro (particularly Ubuntu), during installation you will NOT put the bootloader on the MBR of the hard drive. Instead, when the installer shows you a summary screen before beginning the install, choose the "Advanced" tab, and put grub on the SAME partition where you are about to install Ubuntu (not the default (hd0,0).

You won't be able to boot that OS from your hard drive. But with the USB pendrive inserted and booted, it can point to the partition on your hard drive.

Why grub4DOS, instead of other methods? Since the pendrive is still formatted as FAT, the large amount of space not needed for DOS can be used to store ordinary files readable by Windows or Linux.

---

### Post by oxsyn on 2009-03-06
Hmm, still working on this.  My partitioning scheme looks like this:
| grub-ext3 | data-ntfs| vista64-ntfs | EXTENDED -> | ubuntu-swap | ubuntu | big-unallocated-chunk | <- EXTENDED |

I'm installing vista right now.  Then I'm going to install ubuntu.  I've got an alt64 cd, and I'll do manual partitioning.  is there a way to force it to install grub onto the first partition, rather than on hd0,5?

---

