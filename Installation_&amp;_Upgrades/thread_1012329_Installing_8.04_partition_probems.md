---
title: "Installing 8.04 partition probems"
date: 2008-12-15
forum: Installation &amp; Upgrades
---

### Post by hd79 on 2008-12-15
I'm upgraded my system from ubuntu 7.10 to 8.04 LTS. Now when I boot I get a Busybox initramfs prompt, so I thought I would download the 8.04 distro from ubuntu.com and just install it. When I try to install , I get to Step 4 0f 7, which has a window fo the partition manager on it. The window is blank----that is I can't see my hard drive, or choose any partitions, everything in the window just stays blank. I am on the Live CD right now, so I could get to this forum.

Can anyone advise me as  to what I need to do to get my hard drive to show up in the partition window?

.

---

### Post by falcon61102 on 2008-12-15
You can use gparted on the live CD to set up your hard drive partitions and then the installer should see them when you go to intall.

---

### Post by hd79 on 2008-12-15
thanks for the message. I went to System->Administration->Partition Editor. On the top fo the window it says GParted, but nothing shows up in this window either.

I guess I'll try to modify the /boot/grub/menu.lst file and boot into the 2.6.22-16-generic kernel, instead of the 2.6.24 kernel, and then see if the installer sees my hard drive partitions.

It's really weird---its as if its not seeing my hard drive at all, but I know it's there, cuase if use the 2nd choice in the GRUb screen, my desktop comes up ok.

Really Weird.

Well, if editing the menu.lst file does not work, I'm sure I'll be back on here with more questions.

thanks for the Help.

---

### Post by falcon61102 on 2008-12-15
Make sure that when you open up gparted that none of your partitions are mounted.  I remember reading briefly about a bug that caused the drives to not show up if any of your partitions are mounted.

---

### Post by hd79 on 2008-12-15
When I boot inot the Live Cd, I don't think my hard drie is mounted. I can't see it on the desktop, at any rate.

I tried editing the /boot/grub/menu.lst fiel, and I am booting up ok into the 2.6.22-16-generic kernel now, and I can log in ok, but when I start the installer up from the Live CD, it still doe snot see my hard drive partitions, and GParted is still blank.

I guess I'll try to install it after I log in, instead of booting from it, but I still think its really weird that it does not see my hard drive at all.

Is there some sort of command line version to sue to partition the hard drive?

---

