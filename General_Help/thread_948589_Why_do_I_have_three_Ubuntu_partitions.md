---
title: "Why do I have three Ubuntu partitions?"
date: 2008-10-15
forum: General Help
---

### Post by compnut41 on 2008-10-15
This morning I booted up and grubs loaded as usual, but when I look at the load screen it has somewhere around 8 things I can load. There is windows on the bottom then above that there are three sets of Ubuntu and Ubuntu recovery mode options. Anybody know how I can fix it it is beginning to bother me.

-Thanks

---

### Post by jARLAXL on 2008-10-15
Obviously you upgraded your kernel (with the last updates i guess).
therefore if you dont like the options you can edit the grub menu:
/boot/grub/menu.lst
check it here:
[http://ubuntuforums.org/showthread.php?t=169234](http://ubuntuforums.org/showthread.php?t=169234)
and here:
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by Sam on 2008-10-15
These are no partitions but different kernels to boot with. If the latest work with no issues, you can freely remove the old ones. In Synaptic, remove all the packages:
```
linux-headers-2.6.X-Y
linux-image-2.6.X-Y
linux-ubuntu-modules-2.6.X-Y
```
where 2.6.X-Y is different from the output of terminal command```
uname -r
```


EDIT: Note about jARLAXL's post: If you remove the old kernels in Synaptic, the menu.lst file will be automatically updated.

---

