---
title: "Installing 8.10 on EPIA ME6000 based system"
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by Scampy71 on 2009-01-20
Hi -

I currently have an old Fedora 8 based system running on an EPIA ME6000 Mini ITX system, with 512Mb.

Now that Fedora 8 is EOLing, and given that my recent attempt at a "yum update" resulted in RPM database panics, I figure its time to upgrade to something more recent.

I remember having a lot of grief in the past trying to get linux to install on these boards. Will Ubuntu install ok on it, or are there some gotchas I need to be aware of?

Thanks

---

### Post by davemar on 2009-02-03
I'm also trying the same at the moment, with not of joy. I've tried the alternative CD and that fell over at the installation stage. The server CD seemed to install but doesn't boot, which maybe be a kernel problem. 

I am trying to squeeze a minimal (non-desktop) 8.10 onto a 512MB flash drive, which is maybe the problem I'm having with the alternative CD.

Did you make any further progress?

---

### Post by glmeece on 2009-02-10
I've got a CLE...something-or-other Mini-itx board.  I've used it as a file and test server over the years.  I, too, had a world of hurt trying to get Intrepid installed on it.  ](*,)I finally got server installed, so maybe I can save you guys a bit of pain.

[LIST=1]
[*]Install the Intrepid Server.  This should work all the way through until you reboot.
[*]When you get to the partitioning part, it is important to have your **/boot** and **/** slices on the same partition.  Otherwise, it is really difficult to fix the kernel issue when you reboot (and you *will* have a kernel issue!). So, you can have up to 3 manual partitions if you wish (if you don't use automatic partitioning) - base/root (it'll be just '/'), /home, and swap. If you use automatic, it'll take care of this for you.
[*]When you are all done installing, you'll find you can't boot. Still got that server install CD?  Good - put it back in and boot from it, telling it you want to "Rescue a broken system".
[*]You'll think you're going through install all over again with all the questions it asks you. Wait until you finally see it ask you for the root file system.  This is where you specify your root slice.
[*]Select the first item "Execute a shell in /dev/whateveryourpartitionis/".
[*]Since you're running as root, you don't need to use sudo. Just execute:
[FONT=Courier New]apt-get update
apt-get install linux-386
apt-get remove linux-server[/FONT]
[*]Type exit and then reboot the system. It's possible that you may still have to edit grub to get rid of the reference to the old kernel.  However, using grub you should be able to select your 386 kernel.
[*]Once you've rebooted, if you want to install all the gnome goodies, you'll want to apt-get update again, and then the following for the full effect:
[FONT=Courier New]sudo apt-get install x-window-system-core xserver-xorg gnome-desktop-environment[/FONT]
[/LIST]
The above worked for me.  YMMV. \\:D/

---

### Post by davemar on 2009-02-10
Thanks for those instructions, gleece. I'm trying to install 8.10 from the mini.iso using the cli-expert boot option. I got it all installed, but it fell over when booting for real for the first time. I realised I'd selected the linux-generic kernel. So I followed your instructions and replaced it with the linux-386 kernel...

Unfortunately this still doesn't work. After the first few lines of booting up, the screen turns green then blank and hangs. Unless it's doing stuff, and I'm just not waiting for it?

---

### Post by davemar on 2009-02-10
To answer my own question. It looked like linux-generic wasn't completely removed as it was still in /boot/grub and menu.lst still had as a default. Once I rebooted and hit esc to get into the grub menu I could boot with the 386 kernel, and it works!

---

### Post by glmeece on 2009-02-11
A few additional comments:

[LIST=1]
[*]You may also install **linux-generic** instead of **linux-386**.
[*]I, too, had to edit grub to get rid of references to the old/unusable server kernel.
[*]Whatever you do, don't install the **ubuntu-desktop** meta package. There's something in it (relating to the HAL demon) that hoses this series of motherboards pretty badly. You'll get 90% of the way through booting and it freezes up. #-o So, if you want a Gnome desktop, go ahead and install just **gnome** or **gnome-core** (minimal).
[/LIST]
HTH!

- Greg

---

