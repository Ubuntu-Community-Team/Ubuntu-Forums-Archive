---
title: "Windows XP won't load after Ubuntu 8 Hardy Heron install"
date: 2008-08-07
forum: General Help
---

### Post by Sunflare670 on 2008-08-07
Hello,

I am completely new to Ubuntu. I have always been a Windows user (mostly XP), and I thought it might be cool to fiddle around with another operating system. I am very much enjoying my Linux experience!

However, I am running into an issue. I used partition editor to shrink the size of my Windows partition, and used the resulting free space to create 3 Linux partitions: a 1 gig linux swap-space, an 8 gig '/' ReiserFS, and a 30 gig '/home' ReiserFS. The install went just fine, and I have had very few issues with the Ubunutu side. However, when I try to load into my Windows side, it gets stuck at the blue Windows XP splash screen. I can move my mouse, but the blue screen doesn't go away to reveal my background. Also, when I try to open up my NTFS drive in windows, it generates an error saying 'Cannot mount volume.' The details say '$LogFile indicates unclean shutdown (0.1) ... Operation not supported Mount is denied because NTFS is marked to be in use...' and tells me to go to Windows, when obviously I can't.

I tried to go through GRUB and have it boot straight to windows, but no such luck.

Help!

---

### Post by eriqjaffe on 2008-08-07
You should try booting into the Recovery Console from your XP disc and run a chkdsk /f on your C: drive.

---

### Post by david819 on 2008-08-07
I agree, chkdsk is probably the correct route.  Did you defragment your hard drive before partitioning and installing ubuntu?

---

