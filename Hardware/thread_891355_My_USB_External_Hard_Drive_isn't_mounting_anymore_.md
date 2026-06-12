---
title: "My USB External Hard Drive isn't mounting anymore ever since Ubuntu had crashed!"
date: 2008-08-16
forum: Hardware
---

### Post by s3a on 2008-08-16
When I try to go into the external hard drive it says:

[I]Details:
$LogFile indicates unclean shutdown (0, 0) Failed to mount '/dev/sdb1': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action: Choice 1: If you have Windows then disconnect the external devices by clicking on the 'Safel Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly. Choice 2: Ig you don't have Windows then you can use the 'force' option for your own repsponsibility. For example type on the command line: mount -t ntfs-3g/dev/sdb1/media/250 GB Ext. - force OR add the option to the relevant row in the etc/fstab file: /dev/sdb1/media/250 GB Ext. ntfsa-3g force 00[/I]

---

### Post by s3a on 2008-08-16
I did *sudo gedit /etc/fstab* and added */dev/sdb1/media/250 GB Ext. ntfs-3g force 00* then saved and it still doesn't mount! Windows had solved this problem for me before by following those instructions but, it would take a whole weekend to do this on my Windows computer since it still uses USB 1.1!

---

### Post by cdtech on 2008-08-16
Try Running "ntfsfix /dev/**sdb1**" in a terminal which will reset the NTFS journal on the external device.

---

### Post by s3a on 2008-08-16
I entered that command, it said I was missing something I got it from repositories like it said and then did that command and now I can use my hard drive!!!! You have no idea how long I was trying to get this to work!!! Thank you sooooooooooooooooooooooooooooooooooooooooooo much!

---

### Post by cdtech on 2008-08-16
Very welcome....

---

### Post by finlost on 2008-08-18
I ran into the same problem this evening.  

I am in the process of cleaning up an old Windows laptop that I am going to dump on eBay.  I was using my external USB HDD that I typically run on my Ubuntu box to transfer files.  I was going back and forth between Windows and Ubuntu to get the files from my Windows laptop to my Ubuntu box.  Somewhere along the way, Ubuntu would no longer mount the external USB HDD.

I tried the above solution, but that didn't solve the issue.  I then connected the external USB HDD drive to my Windows laptop again and ran a Check Disk.  I must have created some volume errors when I unplugged the external USB HDD from Windows.  I did not use the unmount/safe to disconnect utuility in Windows.  Check Disk solved the issue.

Thought I would post my experience so someone else may benefit without going crazy.

---

