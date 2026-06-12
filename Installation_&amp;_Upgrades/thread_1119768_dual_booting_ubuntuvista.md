---
title: "dual booting ubuntu/vista"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by SnickerSnack on 2009-04-08
I installed ubuntu on my new tablet yesterday evening.

I booted into ubuntu from a usb drive and used GParted to resize the windows partition and then create an extended and several logical partitions.  Installing ubuntu went smoothly.

But, when I restarted and tried to boot windows, I got an error.  GRUB worked fine, but some windows files were missing or corrupted, so apparently the resizing went badly.  I've reinstalled windows on the resized partition, and now I'm ready to reinstall ubuntu.

It would be easy just reinstall the way I did before since all of the partitioning is done.  But, can I just put GRUB on the MBR?  I have one usb drive with ubuntu on it and one usb drive with my files backed up.

Thanks.

Edit: I saw another thread that mentioned the Super Grub Disk.  My laptop doesn't have an optical drive, so I'd have to wait until I got home to do that.

---

### Post by Spunkbubble on 2009-04-08
> **SnickerSnack said:**
> I saw another thread that mentioned the Super Grub Disk.  My laptop doesn't have an optical drive, so I'd have to wait until I got home to do that.
Although I'm afraid I don't know how to solve your problem, you can also use a super GRUB floppy instead IIRC.

---

### Post by SnickerSnack on 2009-04-08
> **Spunkbubble said:**
> Although I'm afraid I don't know how to solve your problem, you can also use a super GRUB floppy instead IIRC.

It doesn't have a floppy drive either.  It has: usb, sd, firewire, and pci.

Unless someone thinks that the problem was caused by installing ubuntu, I'll just reinstall it since that would be easier than manually installing grub.

---

### Post by ronparent on 2009-04-08
Yes, And the ubuntu install should rewrite the mbr and configure grub properly. If you were comfortable using the terminal from you usb installed ubuntu, a grub reinstll would be easy, but you are probably already underway with the reinstall so I won't confuse the issue.

---

### Post by SnickerSnack on 2009-04-08
> **ronparent said:**
> Yes, And the ubuntu install should rewrite the mbr and configure grub properly. If you were comfortable using the terminal from you usb installed ubuntu, a grub reinstll would be easy, but you are probably already underway with the reinstall so I won't confuse the issue.

Actually, I was about to reinstall ubuntu, but I remembered that the usb installer doesn't seem to work (I borrowed this).  So I *did* install from a cd yesterday.  So, I will have to wait until later today to fix the mbr.



Thanks for the replies.

---

