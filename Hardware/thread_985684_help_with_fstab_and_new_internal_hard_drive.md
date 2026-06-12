---
title: "help with fstab and new internal hard drive"
date: 2008-11-17
forum: Hardware
---

### Post by drmoqu on 2008-11-17
Hello,

I just added a new internal HD to my ubuntu 8.04 machine. It has been partitioned and I am able to mount it manually using the following command:
sudo mount -t ext3 /dev/sda1 /media/backup

However that appears to be the only way to mount it. 

I modified my /etc/fstab as follows:

/dev/sda1 /media/backup ext3 default 0 0
169.254.244.97:/replicate /media/Snap410 nfs defaults 0 0
169.254.244.98:/replicate /media/Snap4100 nfs defaults 0 0

When I startup the two nfs mounts automatically appear on my desktop but not the new one.

Also if I try the command: sudo mount /media/backup 
I get the following error message:

mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


I am at loss to explain what I am doing wrong. You help would be appreciated.

-Dr Q

---

### Post by taurus on 2008-11-17
There is a typo for the /dev/sda1 entry in /etc/fstab.

```
/dev/sda1 /media/backup ext3 default**[COLOR="Blue"]s[/COLOR]** 0 0
```

---

### Post by drmoqu on 2008-11-18
LOL. After staring at that line for so long, you would think I would have noticed the typo. Thank you so much.

---

