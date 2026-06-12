---
title: "hard drive won't mount at startup"
date: 2012-02-17
forum: Hardware
---

### Post by steveray100 on 2012-02-17
My second internal hard drive which would mount automatically at startup has stop doing that. Can anyone help me with a fix? Thanks.

---

### Post by ahallubuntu on 2012-02-17
Can you still mount it manually?

If so - it's in your /etc/fstab file right?  Can you post the contents of that file here?

What happens if you do

sudo mount -a

in a terminal?

Any warnings or errors?

---

### Post by steveray100 on 2012-02-18
nothing happen with the terminal command, I just go back to the prompt.
here is the contents of the fstab file:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=3b7add99-94ae-4de1-a161-7b14afb520c2 /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda5 during installation
UUID=d210b20c-40ea-429c-bf35-b0265a7930bc none            swap    sw              0       0

---

### Post by ahallubuntu on 2012-02-18
Only one hard drive, /dev/sda, is referenced in your /etc/fstab file.  So a second internal drive is not going to be mounted automatically.

Perhaps you meant something else - that your second drive used to be OFFERED in say the Places menu to be mounted for you?  And now it isn't?  How would you have accessed the second drive before?

If you do this command in a terminal

ls /dev | grep sd

what are the results?

If you see only sda there and no sdb, then the hard drive is not visible to Ubuntu anymore and then maybe there's a hardware issue.

---

