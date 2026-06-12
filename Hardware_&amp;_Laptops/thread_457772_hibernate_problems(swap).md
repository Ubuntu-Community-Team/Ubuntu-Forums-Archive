---
title: "hibernate problems(swap)"
date: 2007-05-29
forum: Hardware &amp; Laptops
---

### Post by wastedfluid on 2007-05-29
hi guys.

I read a post about this, but I don't have any UUID numers in my fstab.

I click on hibernate(I deleted and re-sized my partition), and I get this:

[I]wsusp: cannot find swap device, try swapon -a.

Typing swapon -a in a console outputs[/I]



So..

fstab:

[I]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0[/I]


Tried 'sudo swapon -a' and I get:
[I]
wastedfluid@wastedfluid:~$ sudo swapon -a
swapon: /dev/hda5: Invalid argument
[/I]


Any ideas? >:|
[I]
wastedfluid@wastedfluid:~$ free
             total       used       free     shared    buffers     cached
Mem:        904644     456132     448512          0       4632     227636
-/+ buffers/cache:     223864     680780
Swap:            0          0          0
wastedfluid@wastedfluid:~$
[/I]


GParted sohws this as a 1.83gb swap partition formatted as linux swap.

---

### Post by wastedfluid on 2007-05-29
bump..

anyone? >:|

---

### Post by mikewhatever on 2007-05-29
Which partition have you deleted and which resized? If swap has been deleted you can't hibernate, because the content of RAM is copied to swap prior to hibernation.

---

### Post by wastedfluid on 2007-05-30
hda5 was my swap.  I deleted it, and re-sized it. 

hda5 is still there.  The size is different.  I can occasionally get swap to work with sudo swapoff -a and then a qucik sudo swapon -a

It's as if Ubuntu doesn't recognize it.. or something.

---

### Post by mikewhatever on 2007-05-31
I think you need to edit the /etc/fstab file. Try this link [https://help.ubuntu.com/community/SwapFaq?highlight=%28swap%29](https://help.ubuntu.com/community/SwapFaq?highlight=%28swap%29)
It shows how to add more swap and edit the fstab.

---

### Post by wastedfluid on 2007-05-31
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0


Is my fstab.  I looked at it when I first re-partitioned.

wastedfluid@wastedfluid:~$ sudo swapon -a
swapon: /dev/hda5: Invalid argument
wastedfluid@wastedfluid:~$

---

### Post by wastedfluid on 2007-05-31
Well, this worked for me:

```

sudo swapoff -a
/sbin/mkswap /dev/hda5
sudo swapon -a   

```

```

wastedfluid@wastedfluid:~$ free
             total       used       free     shared    buffers     cached
Mem:        904644     860132      44512          0      12048     633676
-/+ buffers/cache:     214408     690236
Swap:      1919728          0    1919728
wastedfluid@wastedfluid:~$


```

Sweetass. 

Thanks!

---

### Post by akudewan on 2007-05-31
Try this:
```

sudo swapon -v /dev/hda5

```

Also, can you give the output for *sudo fdisk -l*

Edit: Oh, your problem is solved. No probs then :)

---

