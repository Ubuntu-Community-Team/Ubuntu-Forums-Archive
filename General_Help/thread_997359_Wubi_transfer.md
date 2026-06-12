---
title: "Wubi transfer"
date: 2008-11-29
forum: General Help
---

### Post by just_chris on 2008-11-29
Hello,

Have been using ubuntu now for about 1.5 months and love it.  In fact I just removed my windows part completely.  Anyhow I started with the wubi and when I transferred it to a dedicated partition, it seems the grub options are a bit messed up.

I have 2 drives, one for backups and one for the os.  /dev/sda has ubuntu and /dev/sdb has the backups.

well I had wubi installed on the backups drive /dev/sdb and when I xferred it I put it on /dev/sda.  Anyhow, booting shows root ()/ubuntu/disks which actually points to the original setup where I had ubuntu installed on the second.

I guess my question is, how do i correct grub so every time i boot i dont have to edit the bootloader and add (hd0,0)ubuntu/disks ( which is not right anyway.

Thank in advance

---

### Post by caljohnsmith on 2008-11-29
Basically you would want to modify your Ubuntu entries to look similar to:
```
title		Ubuntu 8.10, kernel 2.6.27-9-generic
root            (hd0,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=d0b10c15-66ed-4d1c-b7f6-c1fc131636f7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet
```
So (hd0,0) is the location of your main Ubuntu partition, or sda1, and the UUID above should also be for the sda1 partition. You can check for the correct UUID by doing:
```
sudo blkid
```
Let me know how it goes or if you run into problems.

---

### Post by just_chris on 2008-11-30
Worked like a charm thank you.

---

