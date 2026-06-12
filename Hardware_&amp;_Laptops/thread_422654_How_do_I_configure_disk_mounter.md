---
title: "How do I configure disk mounter"
date: 2007-04-25
forum: Hardware &amp; Laptops
---

### Post by stuart.crouch on 2007-04-25
I have a cheap external 7 in 1 USB card reader.  It doesn't automatically get mounted (although I get a lovely useless icon under computer:// that display an error box for me) but I have enough linux knowledge under my belt now to realise that entering "sudo mount -t vfat /dev/sdd1 /media/mmc" will mount the drive and I can unmount with a similar command.  

I have a laptop that has a samba connection in the fstab, and this samba connection appears automatically on the disk manager applet.  I can use the disk manager to mount and unmount the samba connection.  Putting 2 and 2 together I thought I could use the disk mounter to mount and unmount the card in my card reader.  I loaded the disk mounter applet, and it only shows me my floppy drive.  How do I get it to show the multimedia card?

Here are the two relevant lines from my /etc/fstab
/dev/fd0	/media/floppy0	auto	rw,user,noauto	0	2
/dev/sdd1	/media/mmc	vfat	defaults	0	2

The floppy drive shows up as an icon on the disk mounter, the mmc drive doesnt.  Both directories under /media have full read, write and execute permissions and are both owned by root.

Any help on how to fix this (or get the icon under computer:// working instead) would be greatly appreciated.

---

### Post by stuart.crouch on 2007-05-01
Fixed my own problem. Damn Im getting good at this

To make things appear in diskmounter (also seems to apply to mount points on the desktop) just replace "defaults" with "user" 

so I went from

/dev/sdd1 /media/mmc vfat defaults 0 2
/dev/sdd1 /media/mmc vfat user 0 2

and I now have an extra icon that gives a tool tip of /mmc 8)

---

