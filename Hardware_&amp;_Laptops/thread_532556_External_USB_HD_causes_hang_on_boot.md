---
title: "External USB HD causes hang on boot"
date: 2007-08-22
forum: Hardware &amp; Laptops
---

### Post by DanG12 on 2007-08-22
This is my first post to any type of forum, ever, anywhere online...

I recently installed Dapper Drake and it is working fine.  However, I have a 250GB Seagate FreeAgent external USB hard drive that, when plugged in on boot, will cause the system to hang a couple of seconds into the boot process, after the following line prints on the screen:

>> Uncompressing Linux... Ok, booting the kernel.

The boot up normally pauses at this point for a few seconds, the screen goes black for a split second, then comes back and continues booting.  When the external drive is attached, it hangs here.

I've spent a few hours now surfing the ubuntu forums and the web generally and haven't found a way to resolve this.  I will greatly appreciate any advice or info anyone here may have.

A little more background -
- I used to be a systems / network admin and had plenty of experience (10-15 hour days for 2 years +) working with Linux systems, but I haven't touched Linux at all since 2003.  I'm more than a little bit rusty... ;)
- The Seagate HD worked fine w/WinXP prior to reformatting it to ext3.
- I used Dapper Drake to format it to ext3 and can mount it easily AFTER booting
- I can create & delete files & directories once it is mounted
- The only thing I can't do is get the system to boot up with the external HD attached.
- This is the server edition, so I am working with the command line only...

Thanks again for any help,
Dan

---

### Post by pbcartwright on 2007-08-23
what I did was change the /etc/fstab entry to NOT try to fsck the external USB drive, by making the last entry a ZERO like this:
/dev/sdf5            /media/backup        ext3       acl,user_xattr        1 0

other than that, I have no insight:)

---

### Post by notwen on 2007-08-23
Doez your BIOS have an option to boot off a USB device in it's boot options?  If so try re-arranging or removing the USB device in the boot order.  I sometimes reboot, leaving my iPod plugged in and my system will hang here as well.  Hope this helps. =]

---

### Post by DanG12 on 2007-08-23
pbcartwright - I tried the same thing, but unfortunately, the system hangs well before it gets to the point of reading /etc/fstab.  It will hang no matter what I put into /etc/fstab regarding this drive, or if I comment the relevant line out completely.  I like the way you think, but that's not it.

notwen - my BIOS does list the Seagate as in its boot options, but it is 7th in the list of hard drives.  Just for kicks, I completely disabled the Seagate in the boot options, but that changed nothing...

Just so I'm clear, I am NOT trying to boot off of this drive.  This is actually why I've posted this question, because virtually every other post about an external hard drive is about booting from it.  I am using this solely as a backup storage device - no active data will ever be on this hard drive.

Thanks for the replies so far.  Even though a fix hasn't been found, I very much appreciate the fact that at least a couple of folks have tried to help.

---

### Post by DanG12 on 2007-08-23
I did some more research last night after my initial post and I ran across something which didn't help me, but might point in the right direction.  Is it possible that Dapper Drake (server edition) does not load the correct usb &/or scsi driver at boot time to be able to see this drive at all?  If yes, how can I fix this?  Will upgrading to Edgy or beyond resolve this problem?  If yes, please point me to instructions on how to do so, that will ensure none of my settings will be erased.

Thanks again,
Dan

---

