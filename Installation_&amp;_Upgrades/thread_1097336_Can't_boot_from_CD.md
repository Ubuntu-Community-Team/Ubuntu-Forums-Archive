---
title: "Can't boot from CD"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by thenocturnalhoodie on 2009-03-15
Hey all
So i've got two hard drives, both running ubuntu (I found a spare one, and decided to run ubuntu on it, why not, right?)

So I guess I've got the GRUB boot loader installed on 'em as well.

Well, I'm building another computer, and I decided to take out the second drive and just use it in this new computer.

However, when I took it out, and booted up the old computer, I got GRUB error 21. After doing some research, I figured what happened was that a lot of the /boot files were stored on the second HD. So I popped in the second HD. It works fine when they're both plugged in. (Btw, they're both IDE, I dunno if that'll make a difference). 

So i took out HD #1. Then i got some DHCP error with only the second one.

Basically, i think what might fix my problems would be to uninstall the GRUB loader? How would I go about doing that?

Also, back to my original topic title:
I decided that I'd try and boot from a Debian CD, and just load that on HD#1, and maybe avoid messing with GRUB. However, when I go to boot options from the start up menu, and I select to boot from the CD, it doesn't. It'll just go to one of my Ubuntu disks. So now, not only can I *not* boot with just one HD, I cannot even boot from a separate disk.

I am in a conundrum.

---

### Post by taurus on 2009-03-16
Why don't you just reinstall GRUB to MBR with Ubuntu LiveCD again with only the first harddrive in your computer?

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by thenocturnalhoodie on 2009-03-16
> **taurus said:**
> Why don't you just reinstall GRUB to MBR with Ubuntu LiveCD again with only the first harddrive in your computer?

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I didn't think that would work.
I don't have windows on anything.

---

### Post by taurus on 2009-03-16
Use the steps in that guide to reinstall GRUB to MBR.  You don't have to have windows.

---

