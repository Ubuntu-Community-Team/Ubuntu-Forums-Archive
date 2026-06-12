---
title: "no kernel upgrade after switching to 9.04"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by reallove on 2009-04-27
Hello,
I just upgraded kubuntu 8.10 to 9.04 via the automatic update process. All went ok,just the new kernel 2.6.28-11 is not in the grub menu.lst . 
```
dgherman@Pooh:~$ uname -a
Linux Pooh 2.6.27-11-generic #1 SMP Wed Apr 1 20:57:48 UTC 2009 i686 GNU/Linux
dgherman@Pooh:~$

```
And also, not the modules,it's still mounted /lib/modules/2.6.27-11-generic/ . 
```

dgherman@Pooh:~$ mount | grep modules
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)

```
In the /boot folder,I do have the config and initrd image for the kew kernel :
```

dgherman@Pooh:~$ ls /boot/
abi-2.6.27-11-generic     config-2.6.28-11-generic      initrd.img-2.6.28-11-generic  System.map-2.6.28-11-generic  vmlinuz-2.6.27-11-generic
abi-2.6.28-11-generic     grub                          memtest86+.bin                vmcoreinfo-2.6.27-11-generic  vmlinuz-2.6.28-11-generic
config-2.6.27-11-generic  initrd.img-2.6.27-11-generic  System.map-2.6.27-11-generic  vmcoreinfo-2.6.28-11-generic

```
How can I fix that ?
Thank you !

---

### Post by EvilPixieMan on 2009-04-27
I stumbled over your post 'cause I had the same issue.
This is what did it for me -
> $ sudo dpkg-reconfigure linux-image-2.6.28-11-generic

Please chack you have the same kernel installed first, hope this helps.
Cheers.

---

### Post by snowpine on 2009-04-27
If that doesn't work, try 'sudo update-grub'... good luck!

---

### Post by reallove on 2009-04-28
Hi,
Thank you all for the replies.
In my case,the kernel 2.6.28-11-generic was successfully installed,and it seemed that only grub did not configured to load it .
I modified menu.lst according to the new kernel and it worked .
Thanks !

---

