---
title: "MBR error loading GRUB on Dell Latitude D800"
date: 2005-12-26
forum: Hardware &amp; Laptops
---

### Post by obitori on 2005-12-26
I had partitioned my D800 into various configurations and found that whatever I do, I run into problems with my /dev/hda MBR.  The Latitude has a 40 gig HD.  I had broken it up into approximately 1.5gig swap area, a 12gig BSD partition, a 10gig windoze NTFS partition, and a 12gig logical partition with 200m /boot, 500m /tmp, and 11300m / partitions.  

Everything was working fine.  I cut and pasted a BSD's command from the Internet.  I could boot into everything.  I added a 'bootsplash=(hd0,4)/grub/tuxbsdxp.xpm.gz' and it worked fine with a cool splash image.  Then, I started getting a "MBR Error 1" error.  

I've tried various solutions...

dd if=/dev/zero of=/dev/hda bs=446 count=1
(This should wipe grub and leave the partition table)

Then, I launched grub and ran
root (hd0,4)
setup (hd0)
quit

I also tried "update-grub".  I also ran the FreeBSD boot CD and loaded its MBR boot binary.

I also tried installing LILO which kicked back an error--
install-mbr failed.

NONE OF THE ABOVE WORKED.

Here is the kicker.  I can reinstall and get grub working again, if I reinstall windows and wipe everything off the hard drive, then reinstall linux over top that.

I also found that my D800 will successfully load GRUB if I have the bootable Windows 2003 server cd in the CD drive.  That CD loads one of those "press a key to boot from CD" timeouts and goes to the HD if no key is pressed.  Well, when that happens and no key is pressed, the D800 successfully loads GRUB.

I have experienced the problem with a splash image, without one, with BSD and Windows and without, with a menu.lst that I configured and without.

#(*@)$%)@#$%@)(!!!!!!!!!!!!!!!!!!!!!

What's going on?  Anybody have a solution?  I like having a triple-boot laptop.

---

### Post by kenweill on 2005-12-26
I haven't experience that one in Ubuntu. Neither I havn't tried using FreeBSD.

But I have experience that problem before when I was using Red Hat Linux 9.
What I did is boot from my boot diskette(created under RedHat Linux 9 during installation).

When I succesfully logged in to RedHat, I just do:
grub-install
or
install-grub

Something like that. I'm not sure. I forgot.
You can try it with your OS.

---

