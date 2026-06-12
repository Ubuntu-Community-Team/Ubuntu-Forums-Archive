---
title: "ntfs fix, cant read ntfs drive"
date: 2007-03-27
forum: Hardware &amp; Laptops
---

### Post by LSparky on 2007-03-27
im using ntfs3g, 
my internal ide hd's work, 
i pluged an external through usb,
then i recieved this message,
and i cannot read or write to the drive
nor do i know the name of the device
which makes things hard to fix

any suggestions would be very much appreciated! =)


$logfile indicates unclean shutdown (0, 0)

failed to mount '/dev/sda5': operation not supported

mount is denied because ntfs logfile is unclean. choose one action:

   boot windows and shutdown it cleanly, or if you have a removable

   device then click the 'safely remove hardware' icon in the windows

   taskbar notification area before disconnecting it.

or

   run 'ntfsfix' on linux unless you have vista, then mount ntfs with

   the 'force' option read-write, or with the 'ro' option read-only.

or

   mount the ntfs volume with the 'ro' option in read-only mode.

error: could not execute pmount

---

### Post by desicratn on 2007-03-28
> nor do i know the name of the device


failed to mount '/dev/sda5': operation not supported

mount is denied because ntfs logfile is unclean. choose one action:

   boot windows and shutdown it cleanly, or if you have a removable

   device then click the 'safely remove hardware' icon in the windows

   taskbar notification area before disconnecting it.

or

   run 'ntfsfix' on linux unless you have vista, then mount ntfs with

   the 'force' option read-write, or with the 'ro' option read-only.

or

   mount the ntfs volume with the 'ro' option in read-only mode.

error: could not execute pmount
I have this same issue but with an internal SATA drive that has windows on it. 
1)You can either boot into windows twice and shut down properly as well as using the safely remove device in windows since its usb.

2) Or to try the ntfs fix try this:
sudo ntfsfix /dev/sda5    
(since the output you posted said you cant mount that device) and see what it says.
I tried it for mine but I still have to boot into windows or force mount to get the drive to automount so....?

3)You can also try the force mount option:
sudo mount -ao force 
 (sudo mount /dev/sda# /media/??? -o force) If you only wanted to mount a specific drive or the -a for the lazy [like me]
but you will get a "dirty" volume warning...so far so good. So take it for what it is worth.

---

