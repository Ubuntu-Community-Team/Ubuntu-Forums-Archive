---
title: "viewing/mounting window's drives"
date: 2005-03-09
forum: Hardware &amp; Laptops
---

### Post by eraos on 2005-03-09
I'm trying to view my second hard drive, based on the instructions from the Unofficial Ubuntu Starter Guide.  
But this is what happens:

root@Ubuntu:/dev # mount /dev/hdb /mnt/gdrive -t ntfs -o umask=0222
mount: /dev/hdb already mounted or /mnt/gdrive busy


When I open up the /dev folder in nautilus, there are red X's on the right hand corners of the hard drive icons.

I'm not sure what else to explain.

Thanks

---

### Post by bored2k on 2005-03-09
[QUOTE=eraos]I'm trying to view my second hard drive, based on the instructions from the Unofficial Ubuntu Starter Guide.  
But this is what happens:

root@Ubuntu:/dev # mount /dev/hdb /mnt/gdrive -t ntfs -o umask=0222
mount: /dev/hdb already mounted or /mnt/gdrive busy


When I open up the /dev folder in nautilus, there are red X's on the right hand corners of the hard drive icons.

I'm not sure what else to explain.

Thanks[/QUOTE]
 It means it is mounted as superuser , wich means you can hardly access it .

In the same guide you're reading, [http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs) automount it and reboot . If any more problems, repost .


You can view with 
sudo fdisk -l the partitions found by linux, and what type they are and theyre /dev file so you dont have problem knowing what to mount.

---

### Post by eraos on 2005-03-09
Yeah, that worked, thanks

After the first reboot, it didn't... but that was because I typed Ntfs as nfts.

Then on the second reboot it still didnt' work.  But that was because I only typed hdb instead of hdb1

---

### Post by bored2k on 2005-03-09
[QUOTE=eraos]Yeah, that worked, thanks

After the first reboot, it didn't... but that was because I typed Ntfs as nfts.

Then on the second reboot it still didnt' work.  But that was because I only typed hdb instead of hdb1[/QUOTE]
 Silly rabbit, trix are for kidz ^_^

---

