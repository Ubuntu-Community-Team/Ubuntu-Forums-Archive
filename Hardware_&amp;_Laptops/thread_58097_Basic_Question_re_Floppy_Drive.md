---
title: "Basic Question re: Floppy Drive"
date: 2005-08-18
forum: Hardware &amp; Laptops
---

### Post by howard on 2005-08-18
I'm almost embarrassed to ask, but I didn't see any comparable posts so here goes.

Just downloaded the newly released "breezy" live and am playing around with it on a desktop computer. So far it looks like it might be a good fit for my vintage Thinkpad iSeries laptop.  I plugged in a USB memory stick and wham... it was mounted and the file contents displayed.  Great!  How many other distros have done that on my lappy so far... maybe just two.

But what about the floppy drive?  I have navigated the desktop and cannot find a selection that will allow me to access the floppy. In fact, the only reference to floppy I found was a 'floppy formatter'.

So where is the floppy access?  I can't believe that a Linux distro as mature as Ubuntu appears to be will require me to mess around in /fstab to get the floppy drive working.  Any assistance appreciated.

---

### Post by David Haas on 2005-08-20
Howard--Floppies work fine on Ubuntu. Because I don't know how much you've done with the floppy so far, I'll go through all the steps. First, format the floppy with the terminal command "fdformat /dev/fd0" (without the quotes). Then add the Linux filesystem to it with the command "mke2fs /dev/fd0". Then you can mount the floppy. Since you know about /etc/fstab, I'd change to the directory /etc in your terminal and at this directory enter the command "gedit fstab" to open the fstab file in the editor. Then you can change (edit) the /dev/fd0 line to "/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0". The /media/floppy0 is the directory where you will mount the floppy (this is just a convenience). Make sure that you have the floppy0 directory in the /media directory--it should be there by default in Ubuntu. After editing fstab as above, you can then mount the floppy with the command (as root--"sudo -s") "mount /media/floppy0" (again, without the quotes). WhenWhen finished storing stuff on the floppy, unmount as root with the command "umount /media floppy0' (it is "umount", not "unmoun"). Of course, once you've edited fstab and have the floppy formatted and with the filesystem on it, mounting is quick with "mount /media/floppy0".

I hope this helps.

Enjoy Ubuntu!

David

---

