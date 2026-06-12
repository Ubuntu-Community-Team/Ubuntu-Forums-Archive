---
title: "After new istall of 9.04 no windows boot/partition"
date: 2009-09-17
forum: Installation &amp; Upgrades
---

### Post by penchev on 2009-09-17
Hello people
after new install of Ubuntu 9.04 it is unable to detect my vista and even it's partition 

i got the message:
**$MFTMirrdoes not match $MFT(record 0) Failed to mount dev/sda1** etc

with advise to checkdisk /f ou window and restart windows twice.

Eventually I am unable to start the windows.

Some advise? Thanks in advance

---

### Post by penchev on 2009-09-19
Is there no one able to help?:confused:

---

### Post by Bartender on 2009-09-19
Well, without more details from you, such as the output of 

```
sudo fdisk -l
```

the obvious assumption is that you installed Ubuntu right over the top of Windows.

---

### Post by Mark Phelps on 2009-09-19
How did you install UBuntu? Did you do a side-by-side install using the Ubuntu installer and shrink the Vista partition to make room for Ubuntu? Or did you shrink the Vista OS using the Vista Disk Management utility?

---

### Post by penchev on 2009-09-19
Thanks for asking. Non of both. I have installed ubuntu after grub failure (grub installed by Suse). Unfortunately I was unable to mount/read my windows partition and vista loader was not detected. After several intentions I have installed again Suse 11.1 and it has detect the vista partition. Now I am stuck with suse despite I like more ubuntu.

However yesterday I have installed ubuntu side by side on my friends laptop (same like my) without any problems. Obviously the problem is with my hard drive with various partitions and several instalations of different systems.

Thanks

---

