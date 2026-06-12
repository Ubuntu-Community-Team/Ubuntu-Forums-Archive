---
title: "Cannot enter passphrase to unlock encrypted root partition"
date: 2009-07-31
forum: Installation &amp; Upgrades
---

### Post by Torrey on 2009-07-31
Hi.  I just installed Jaunty from the alternate ISO (64 bit) with the fully encrypted LVM option.  (This is a fresh install on a computer which was running 64-bit Intrepid with no problems - but the Intrepid install did not have the encrypted disk)

When the freshly installed Jaunty boots from the encrypted disk, I get the "Enter passphrase:" prompt to unlock sda1_crypt.  But when I type on my USB keyboard, nothing happens.

I know the keyboard works -- I can enter the GRUB menu, edit the kernel command line to remove the "splash" and "quiet" options.  That results in a text mode boot, but the exact same problem happens... when it asks me to enter the passphrase, nothing I type does anything.

I have a USB keyboard.  I've already tried both enabling and disabling "Legacy USB Support" in the BIOS and it made no difference.

Please help.

---

### Post by Torrey on 2009-07-31
I have been searching more and found that this is not a problem unique to Ubunutu.  Several people at this thread report a similar problem:
[http://bugs.archlinux.org/task/12867](http://bugs.archlinux.org/task/12867)

Seems to be an issue with not having all the USB modules loaded, perhaps?

When I did the install (expert mode - long story, other Jaunty bugs...) I used the "use minimal initrd" option.  I will try using the all-modules initrd and see if that helps, perhaps with the addition of a "MODULES=..." bit to the kernel command line.

---

### Post by Torrey on 2009-07-31
It works!  The problem was the minimal initrd.  I re-ran the (custom, expert-mode) installation exactly the same as before, but this time selected the "complete" all-drivers initrd, instead of the "minimal" (only required drivers) initrd.

And at boot, I was able to enter the password and log in.

So (I'm trying to hit all the keywords here so future Google searches find this):

If the keyboard doesn't work for entering the LUKS full-disk-encryption passphrase in Jaunty, try reinstalling with the all-modules version of the initrd.

I will look into filing a bug for the initrd pointing out that their "minimal" drivers selection is a little TOO minimal.

---

### Post by xand on 2009-11-21
Hello, your post have been helpful for me. Have you found the place to fill the bug ? I'm looking for a solution that does not involve a system reinstall.

Thanks

---

