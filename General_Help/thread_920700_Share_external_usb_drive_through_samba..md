---
title: "Share external usb drive through samba."
date: 2008-09-15
forum: General Help
---

### Post by quinnten83 on 2008-09-15
Im trying to share my external USB harddisk connected to my old XFCE machine.
I have already successfully shared a folder through samba.
I added the new folder to the smb.conf (/media/Philips\ external\ hard\ disk/). I can see the folder created when I surf the shares from my Ubuntu desktop, but I can't access it, I keep getting access denied. 
I thought I might be able to mount the contents of the USB drive in a different folder and then share that folder through samba, but that didn't work.
So my question is, how can you share an external usb harddrive through samba?

---

### Post by prince_niceguy on 2008-09-15
Mount your external drive using fstab and then share that folder using samba or nfs. I too do the same and it works without issue.

Ensure you give proper permission in samba share and fstab while mounting.

---

### Post by quinnten83 on 2008-09-17
Once connected the harddrive is automounted.
I then tried sharing the /media/philips..., but i kept getting errors.
I don't know what the harddrive is called in /dev, so it is a bit difficult for me to add it to fstab.
know how to figure that out? If you do, please tell me.


Best regards

---

### Post by prince_niceguy on 2008-09-17
actually if you open partition manager you will find that the the hard drive would be mounted as /dev/sdb or something. so you can mount using the same in fstab.  You can install partition manager by following command

```
sudo aptitude install gparted
```

Once you have identified the partitions mount it as usual in fstab.

---

