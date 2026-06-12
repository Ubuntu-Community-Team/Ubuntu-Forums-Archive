---
title: "Cant Read DVD unless root"
date: 2006-10-09
forum: Hardware &amp; Laptops
---

### Post by blackest_knight on 2006-10-09
I've had a few problems I installed a Sony DvD writer in my laptop 
unfortunately I had to change the HD to slave and change the Path in grub 
(hdb instead of hda) but everything mostly works except 

I now have a strange problem I created a DVD using k3b but it will not let me read the disk except as root and it will not let me expand permissions because it is read only. (I started k3b from the cli and not as root)

Everything seems fine on the laptop if i use osx or Xp as os 
any advise please. 

incidentally a message flashes by as grub loads prior to the grub1.5 loading message something comes up about a hd controller failure (sorry cant be precise as its on screen for a fraction of a second)
I think that message may be from grub

---

### Post by IoCaster on 2006-10-09
You could try it this way.


```
sudo nautilus --no-desktop --browser%U
```

Navigate to /media or wherever your drive is mounted. Right-click --> properties and change what you want. I use the 'plugdev' group setting myself, but it's up to you what you do there.

---

### Post by blackest_knight on 2006-10-09
it says can't change permissions because it is a read only disk strangely enough one of my usb hard drive partitions is saying the same thing and thats fat32

---

### Post by IoCaster on 2006-10-09
You can try taking the disk out and change permissions on the folder/drive itself. Maybe then you can put the disk back in and read it. I seem to remember that I had to do something similar recently. I changed owner and set plugdev for group. It worked for me.

<shrug>

---

### Post by blackest_knight on 2006-10-18
yes I had to change ownership and made myself a member of cdrom something 
sorry I meant to post when it was still fresh in my mind also the usb partition that was read only ahem it was ntfs and thus read only...

---

