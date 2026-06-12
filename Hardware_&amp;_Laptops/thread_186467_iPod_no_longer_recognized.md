---
title: "iPod no longer recognized"
date: 2006-06-02
forum: Hardware &amp; Laptops
---

### Post by InsanePenguin08 on 2006-06-02
Not sure what I did, as it happened shortly after a failed Dapper install and slightly before my successful Dapper install.  

My iPod is no longer automatically recongnized and mounted, although I believe I can mount it manually (I don't know what the filesystem is, hence, can't mount it in terminal until I do)

Anyone experiencing similar problems?  Solutions?

Thanks in advance!

---

### Post by InsanePenguin08 on 2006-06-02
Alright, I can manually mount it now, using 

> sudo mount -t vfat /dev/sda2 /mnt/ipod

Any way I can set the computer to automount it like it used to do for me?

---

### Post by Edward The Bonobo on 2006-06-05
I'm having the same problem.  

Does automount work for anyone?

---

### Post by arguy337 on 2006-06-05
[QUOTE=InsanePenguin08]Any way I can set the computer to automount it like it used to do for me?[/QUOTE]

My 1st post (Hello everyone) 8-) 

I believe all you have to do is 
```
gksudo gedit /etc/fstab
```
then add this at the bottom:
```
/dev/sda2 /media/ipod vfat defaults 0 0
```

Replace the "/media/ipod" with wherever you want it mounted
Just remount everything and it should be all set!

---

### Post by InsanePenguin08 on 2006-06-05
*Shrugs* dunno what it was, but when I rebooted for the first time after I upgraded to Dapper, it worked just fine.

---

### Post by attiliok on 2006-06-06
I had the same problem... in my case the problem was this:

[https://launchpad.net/distros/ubuntu/+source/hal/+bug/44874](https://launchpad.net/distros/ubuntu/+source/hal/+bug/44874)

I hope is the same for you!

bye

---

