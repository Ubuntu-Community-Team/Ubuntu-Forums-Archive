---
title: "Problem upgrading to server 9.04"
date: 2009-06-14
forum: Installation &amp; Upgrades
---

### Post by steves06 on 2009-06-14
I had 8.10 server installed.   On top of that I had added a Gnome desktop using apt-get.  All worked fine for several months.  I chose the Synaptic 9.04 upgrade.  The install went well (no errors) but on reboot I got a "bad file or directory" error.  I tried reinstalling grub using a 9.04 server install CD I created.  No changes there.  In all cases, I could boot to the old kernel but networking was completely hosed.  I then tried a full reinstall from the CD with manual partitioning.  That gave me a "can't remove existing system files" error.  
So on to a full install.  That goes well with a few notes:  I have hardware RAID 10 and trying to use LVM with that gives errors on the grub install.  No big deal ... I don't need LVM.  However, now adding any desktop causes the modified kernel to revert back to the "bad file or directory" error.  e.g., installing gnome-desktop-environment does this.  Since that install doesn't save the kernel, I end up starting over (I know, I can save it ...).

My immediate question is:  Can I somehow install 9.04 server and add a desktop and get a usable kernel?   All was fine here with 8.10 but now I'm stuck.

The second issue is a longer term note for someone to look at why the server upgrade via Synaptic fails.

---

