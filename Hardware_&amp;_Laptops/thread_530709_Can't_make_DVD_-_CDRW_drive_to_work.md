---
title: "Can't make DVD - CDRW drive to work"
date: 2007-08-20
forum: Hardware &amp; Laptops
---

### Post by pinga on 2007-08-20
Hi, it's been two or three months since I upgraded to Feisty, and since then, I can't mount any disc. I've tried many different solutions that helped people with similar problems, but nothing helped me. 

Can anyone help me? What kind of information would be the best to provide in order to make the issue more understandable?

Thanks in advance!

---

### Post by s3a on 2007-08-20
Go to the terminal and type "sudo mount -a" to mount it as well as every other device and "sudo umount -a" to unmount the devices...I hope this works because it's all I know since I am not very advanced in Linux myself.

Hope this helps!

---

### Post by aldenhg on 2007-08-21
Can you tell us what brand and model your drive is? Some drives need the piix module to work properly, so try entering this into a terminal:
```
sudo modprobe piix
```

---

### Post by pinga on 2007-08-21
Thanks, s3a, but it's not mounting. 

I tried the modprobe, but it didn't do anything, either. 

The drive is a Samsung CDRW/DVD SM-332B.             SCSI Connection

Thanks again!

---

### Post by krazyman on 2007-09-08
I have the same problem. I wanted to load Feisty from the CD, but had to load Edgy, then do online upgrade to get it on, as the CDROM wasn't recognised by the Feisty boot CD either. Now Feisty is working OK but I can't read or write with the drive :(

---

### Post by pinga on 2007-10-20
7.10 upgrade- Gutsy fixed it. It's all fine, now...

---

