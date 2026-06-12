---
title: "Macbook Pro - dead hard drive + new SSD = misery"
date: 2011-12-30
forum: Hardware
---

### Post by arcticaribou on 2011-12-30
I'm sorry if this specific problem has been addressed here already, but I couldn't find it. Here's the problem in a nutshell:

My wife's Macbook Pro's hard drive failed and I decided to replace it with a SSD. Since our OSX DVD is MIA, and, as an Ubuntu user, I decided to at least try Ubuntu first before buying a new copy of Lion ($30 is cheap, but free is much better). The Ubuntu installer recognizes the disk, seems to partition it and install software on it, but at the end, around or right before it puts GRUB on, it fails. 

So, I tried Debian in the hope that the more verbose installer would give me some hint as to where the problem was. The Debian installer said the installation succeeded, but the disk wouldn't boot.

Here's my question: has anybody out there tried to install Ubuntu (/Debian/any other Linux) on a bare Macbook? 

I've tried both Intel- and OCZ-brand SSDs on the computer, and both fail. There could be another problem with the computer, but it does happily boot and run an Ubuntu live CD. I have a good bit of experience running Linux on Intel Macs, so I know (or think) it's not some stupid mistake. I've been wondering if refit could help, but without OSX, I don't think I can install it.

Anyone? Please? I've been scratching my head over this for months. One other thing ... when I did have the OSX DVD handy, I tried installing it on an Intel SSD (I can't remember the model number, but it was something like x<number> or v<number> "value". I did read that the "value" trimline was problematic, but I'm surprised I'm having the same trouble with a completely different brand if there was some brand-specific problem with the Intel drive.

Thanks!

---

### Post by 2F4U on 2011-12-31
I installed Xubuntu on a MacBook which had OSX on it (I replaced OSX with Xubuntu) and this worked without problems. I may be wrong but I think MacBooks need an EFI partition on the disk since they don't have a normal BIOS to boot from. How did you manage to get EFI on the SSD?

---

### Post by arcticaribou on 2012-01-01
> **2F4U said:**
> I installed Xubuntu on a MacBook which had OSX on it (I replaced OSX with Xubuntu) and this worked without problems. I may be wrong but I think MacBooks need an EFI partition on the disk since they don't have a normal BIOS to boot from. How did you manage to get EFI on the SSD?

Ahh, I didn't. That could be the problem. Any idea how to put one on? Would I need an OS X install DVD?

---

