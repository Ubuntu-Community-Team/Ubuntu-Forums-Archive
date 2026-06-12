---
title: "Edgy &amp; external ext3 USB drive"
date: 2006-12-14
forum: Hardware &amp; Laptops
---

### Post by aweller on 2006-12-14
(In relation to the thread: [http://ubuntuforums.org/showthread.php?t=318116](http://ubuntuforums.org/showthread.php?t=318116))

My external ext3 USB drive currently auto-mounts (no fstab entry) as /media/usbdisk. As I use several "usbdisks" on this machine (flash drives, etc) - is it possible to create a fstab entry that mounts this drive permanently as '/media/xyz'?

What is the best fstab entry to allow different users read/write access to  - i.e. relaxed permissions/flexibility?

Thanks, Andy

---

### Post by mcduck on 2006-12-14
you could give the drive a name. Then it would automount using that name instead of just 'usbdisk'..

```
sudo tune2fs -L newname /dev/sda1
```
(replace name and device with the right ones)

edit: for example I've named my portable HD as 'Hyperion', so now Ubuntu automounts it as /media/Hyperion

---

### Post by aweller on 2006-12-14
Thanks.

How would I create a fstab entry to allow different users read/write access to this drive at the same time - i.e. relaxed permissions/flexibility?

---

### Post by mcduck on 2006-12-14
> **aweller said:**
> Thanks.

How would I create a fstab entry to allow different users read/write access to this drive at the same time - i.e. relaxed permissions/flexibility?

I think you can just 'sudo chmod a+rw /media/drivename'. Automatic mounting of removable drives is not handled with fstab. I've never tried this though so I'm not sure if that would work.

---

### Post by mcduck on 2006-12-14
Ok, if that doesn't work you can also do it with fstab, as long as you use the UUID number or label of the disk to do the entry. See here for more help: [http://www.ubuntuforums.org/showthread.php?t=283131&highlight=removable+ext3+drive+permissions]("http://www.ubuntuforums.org/showthread.php?t=283131&highlight=removable+ext3+drive+permissions")

---

### Post by aweller on 2006-12-15
If I alter permissions for things in Nautilus, then once connected, all users can see/read this music. Perhaps this is a chown/chmod thing?!

Once I have copied all my music across to this ext3 USB drive (user: aweller, group: users), how do I chown/chmod so that all users can see/read the music folders/files?

Thanks, Andy

---

### Post by aweller on 2006-12-16
In addition, is it possible to run chmod/chown on just folders or files? So for example, if I:

sudo chmod -R 777 /media/xyz

for folders, and

sudo chmod -R 755 /media/xyz

for files.

Thanks

---

