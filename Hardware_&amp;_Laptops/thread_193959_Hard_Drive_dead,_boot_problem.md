---
title: "Hard Drive dead, boot problem"
date: 2006-06-10
forum: Hardware &amp; Laptops
---

### Post by rkoep on 2006-06-10
Hi guys,
I've got Ubuntu installed on a 10 Gb harddrive, and it works perfectly. Next to that 10 gb harddrive, I've got another 10 gb drive, but i fear that one is dead. I started my computer this evening, and it just freezed when i logged in. I couldn't fully reboot either, Ubuntu told me during te boot sequence that a Superblock had failed, and that /dev/hdb1/ could not be detected. If a valid drive was there, i should try to manually fsck it... Well i accepted the fact that it wasn't working any longer, so i hooked it off my pc, but each time i reboot now, Linux still searches for that harddrive, and if it doesn't find it (offcourse it doesn't), i have to point to it manually. Since i can't tell the system where it is, booting doesn't work.

Now I've gotten over that issue: I gave the 'shutdown -rf now' command, so that fsck would be skipped on reboot, but I'd like to know a permanent solution to my problem... And if anyone knows a way to check broken hd's for remaining bits that still work, I'd be very grateful.

Sorry for the lengthy explanation :)

---

### Post by 5-HT on 2006-06-10
Just to get things straight...Ubuntu is on the functioning 10 GB disk, but it hangs on boot when it's looking for the other drive since you've removed it?

If that's the case, you could either comment out (append a #) or remove the line in /etc/fstab referring to /dev/hdb1 to stop Ubuntu from trying to mount the drive. If you can get Ubuntu booted (seems like you can now from the post) that would be the easiest way to prevent Ubuntu from trying to mount the drive on boot. 

About trying to repair hdb1, you could try either fsck ('man fsck' for the manual) or Windows scandisk depending on what the filesystem is (Linux or Windows native).
A full reformat might help if the drive itself isn't dead, but from your description it looks like it may be.

It's a long shot...but you may try mounting the drive from a live CD if you have an install handy to try get a backup of the drive.

Hope you can repair it or don't loose much data if you don't have any backups!

---

### Post by rkoep on 2006-06-11
Thanks for your help, i could indeed still access ubuntu, so i threw hdb1 out of fstab.

Now I've gotten myself an external usb harddisk (160 Gb), but it is NTFS partitioned. When I open Gparted, the 'format as' option is greyed out, and there 's a lock next to the name of the disk (as with all my other hd's). How can I get my gparted to format it to fat32, or do I need another program for that?

[Edit] I've sorta figured it out now, it looks like gparted wouldn't read it because it was still active or something.. So i tried to make an ext3 filesystem via the terminal, as explained in another thread here. In terminal it said 'can't format active drives', so i detached on my desktop, and everything worked, i could even acces it with gparted.

If i want my external disk to be mounted on startup, what should i add to fstab?

---

### Post by 5-HT on 2006-06-11
[quote=rkoep]Thanks for your help, i could indeed still access ubuntu, so i threw hdb1 out of fstab.

When I open Gparted, the 'format as' option is greyed out, and there 's a lock next to the name of the disk (as with all my other hd's). How can I get my gparted to format it to fat32, or do I need another program for that?

[Edit] I've sorta figured it out now, it looks like gparted wouldn't read it because it was still active or something.. So i tried to make an ext3 filesystem via the terminal, as explained in another thread here. In terminal it said 'can't format active drives', so i detached on my desktop, and everything worked, i could even acces it with gparted. [/quote] 
The drive was most likely mouted, which was why gparted wouldn't let you format it. Glad you got it formatted.

[quote=rkoep] If i want my external disk to be mounted on startup, what should i add to fstab?[/quote] 
Something like this should work: 
```
<device>      <mountpoint>          ext3    defaults,user      0       2 
``` 
where;

i) <device> will be something like /dev/foo (enter 'dmesg' in a terminal just after you plug the drive in to see what it's being recognized as)

ii) <mountpoint> will be where you want the drive mounted. Something like 'data' or 'external' in /media would work, but it's up to you. You will need to create the directory though.

e.g. ```
 sudo mkdir /media/data 
``` 
You should get an icon on your desktop when the drive is mounted, and you can browse the drive in a terminal by going to the mountpoint.

Hope that helps.

---

### Post by charles nicholls on 2007-03-04
One thing you could try before giving up on the hd is to try a google for a prog called HDDRegenerator . Its a small iso that your burn to and boot from cd. works on any file system without damaging the data and will recover and repair bad sectors.

---

