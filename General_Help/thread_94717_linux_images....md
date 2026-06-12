---
title: "linux images...?"
date: 2005-11-24
forum: General Help
---

### Post by aran384 on 2005-11-24
hey when i boot up in my grub menu ive got about 3-4 linux images that i can choosen from and run... ??

how come when am updating my system and new linux images are out its not deleting the older ones...

am sure this is gonna be using up the what little hdd space i got up... 

any help please :)...

---

### Post by tomwell on 2005-11-24
Aran,

There is a thread on that over here...

[http://www.ubuntuforums.org/showthread.php?t=94075](http://www.ubuntuforums.org/showthread.php?t=94075)

I myself have just added the #  to the kernel, i dont want showing up i dont have space probs... but they do tell you how to remove the extra Kernel...
Its to do with having your older kernel in case somethings dont work right with the new one...

Peace 

Tom

---

### Post by metoo on 2005-11-24
All for the same kernel version?

It's not a bug, it's a feature. The new kernel might not work well for you and so you can still boot into your old kernel.
2 boot options per kernel version. Normal and recovery.

You may de-install older versions via apt-get or synaptic.
It's not much space so, see /boot .
Only an issue if you have a separate boot partition. I make it 64MB these days, to be able to run different distros with different versions each.
(Is it about 8MB each? Normal and recovery use the same image, just different boot parameters)

---

### Post by aran384 on 2005-11-24
i read though some of the posts but didnt really see anything on removing them unless am blind which i think i am.. so...

i went into my /boot folder in terminal and did a ls -al and this is what was outputted 

```
total 21616
drwxr-xr-x   3 root root    4096 2005-11-23 08:01 .
drwxr-xr-x  21 root root    4096 2005-11-23 08:01 ..
-rw-r--r--   1 root root  239811 2005-11-18 13:29 abi-2.6.12-10-386
-rw-r--r--   1 root root  239770 2005-10-10 14:16 abi-2.6.12-9-386
-rw-r--r--   1 root root   59868 2005-09-23 15:13 config-2.6.10-5-386
-rw-r--r--   1 root root   64125 2005-11-18 11:48 config-2.6.12-10-386
-rw-r--r--   1 root root   64135 2005-10-10 13:12 config-2.6.12-9-386
drwxr-xr-x   2 root root    4096 2005-11-23 08:01 grub
-rw-r--r--   1 root root 4403200 2005-09-26 08:07 initrd.img-2.6.10-5-386
-rw-r--r--   1 root root 5297804 2005-11-23 08:01 initrd.img-2.6.12-10-386
-rw-r--r--   1 root root 5297619 2005-10-19 19:00 initrd.img-2.6.12-9-386
-rw-r--r--   1 root root   94664 2005-06-30 16:49 memtest86+.bin
-rw-r--r--   1 root root  845016 2005-09-23 15:48 System.map-2.6.10-5-386
-rw-r--r--   1 root root  897419 2005-11-18 13:29 System.map-2.6.12-10-386
-rw-r--r--   1 root root  897159 2005-10-10 14:16 System.map-2.6.12-9-386
-rw-r--r--   1 root root 1188570 2005-09-23 15:48 vmlinuz-2.6.10-5-386
-rw-r--r--   1 root root 1207001 2005-11-18 13:29 vmlinuz-2.6.12-10-386
-rw-r--r--   1 root root 1206555 2005-10-10 14:16 vmlinuz-2.6.12-9-386

```

does this look bit big or werid to any one?

btw i would like to remove 1 or maybe 2 of these...

---

### Post by sapo on 2005-11-24
just remove the old ones via synaptic or apt-get, i never had problems removing then..

---

