---
title: "I want kubuntu only now..."
date: 2008-09-11
forum: General Help
---

### Post by Hyper Tails on 2008-09-11
hi i got vista and hardy now and i use Kubuntu all the time now and I want to know if i delete the windows partition and will it effect the boot loader by saying error 22?

My webcam and remote don't work on my desktop but all my hardware does on my laptop.

thank you.

Hardware and laptop info:
Laptop:acer apsire 5715-4740
Webcam:u-cam ne878
remote:asus digital home

if you know how to get these harware working please tell me

and again thank you

---

### Post by Iowan on 2008-09-11
Just my opinion, but removing the windows partition should only affect the boot loader if you select the windows option.  You should be able to clean that out of **/boot/grub/menu.lst**.

---

### Post by milasch on 2008-09-11
If you are using windows bootloader to boot you linux and windows OSs you'll likely be unable to boot again.

If you are using grub/lilo, this isn't suppose to affect anything since they're located in the MBR itself. But I can't guarantee because I had problems a few years back when I made partition changes..

But then you just boot with the cd, and install grub in the mbr again...

The best option though is to remove the partition from /boot/grub/menu.lst as Iowan recommended.

---

### Post by wolterh on 2008-09-11
No it will not. I installed ubuntu from the live CD and in the same session i formatted my harddrive to ext3, and I had no booting problems. Go ahead.

---

### Post by Hyper Tails on 2008-09-11
Is there anyway i can get my webcam and remote working before i do this?

just asking.

---

### Post by Hyper Tails on 2008-09-11
i use the grub loader

---

### Post by Hyper Tails on 2008-09-12
...........................................................................................................................................................................................................

---

### Post by Hyper Tails on 2008-09-14
.............................................help?

---

