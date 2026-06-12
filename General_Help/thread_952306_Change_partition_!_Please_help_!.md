---
title: "Change partition ! Please help !"
date: 2008-10-19
forum: General Help
---

### Post by infantiablue on 2008-10-19
I am quite new to Ubuntu, and now I must work on a 64 bit Ubuntu system. It has the hard disk structure like below

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              19G  272M   18G   2% /
varrun               1012M   48K 1012M   1% /var/run
varlock              1012M     0 1012M   0% /var/lock
udev                 1012M   60K 1012M   1% /dev
devshm               1012M     0 1012M   0% /dev/shm
/dev/sdb5             148G  188M  141G   1% /backup
/dev/sda2             950M   35M  867M   4% /boot
/dev/sda8              78G  184M   74G   1% /home
/dev/sda5             950M   18M  885M   2% /tmp
/dev/sda7              19G  411M   18G   3% /usr
/dev/sda3              28G  361M   26G   2% /var

How can I reduce size for sdb5 (backup) and increase sda3(var)

Pleaes, I really need any help

Thank you so much

---

### Post by CharonM72 on 2008-10-19
If you haven't already, look into GParted (sudo apt-get install gparted, or search "gparted" in Synaptic)
It might be able to help, but then again, maybe not. Never hurts to try...

---

### Post by infantiablue on 2008-10-19
Hi CharonM72,

Thanx for your quick reply. I have heard about GParted, but it is program with GUI, right ? I am using a 64 bit server edtion, and I am controlling via SSH, so I can't install it to use. Is there another solution ?

---

### Post by infantiablue on 2008-10-19
I found this configuration in fstab (quota configuration)

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=94a3632d-5008-4985-b93b-bd51ce038988 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=90324203-161f-49f9-96f0-78d1dd127416 /var        	  ext3    relatime        0       2
# /dev/sda2
UUID=e4d7a394-db6c-4ce0-8660-485a45c55fbc /boot           ext3    relatime        0       2
# /dev/sda8
UUID=f32c69b4-1590-49a2-b1f6-edeb0713e502 /home           ext3    relatime        0       2
# /dev/sda5
UUID=5da945ce-57e4-4b40-be86-7e5ed7d47b53 /tmp            ext3    relatime        0       2
# /dev/sda7
UUID=63bc8469-8535-474a-8df7-ede0e8ab0fe1 /usr            ext3    relatime        0       2
# /dev/sda3
UUID=a256a176-a3b0-4d98-b436-45fe8a82e90b /var         ext3    relatime        0       2
# /dev/sda6
UUID=c685f53f-6cc5-43f0-b69b-e32d3d6b762e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


```

I have tried to reconfig, and use following commands
```

touch /quota.user /quota.group
chmod 600 /quota.*
mount -o remount /
quotacheck -avugm
quotaon -avug

```

But useless.

Is there any idea ?

---

### Post by CharonM72 on 2008-10-19
In that case it'll be a bit tougher... It probably depends a fair amount on the type of partition. parted (with libparted1.7-1, and optionally libreiserfs0.3-0 for ReiserFS partitions) looks like a fairly good bet, but not 100% that it's not GUI-based.

I'm looking through Synaptic and see some other specific tools like fatresize (if for some odd reason you're using FAT partitions), ex2resize (for ex2 partitions), ntfsprogs, etc. util-linux appears to have a partitioner too (which may happen to be parted). Unfortunately, you're kinda on your own as for using them. I'd try a -h, --h, -help, etc. argument or some internet research to get more info.

EDIT: OK so they're ext3. Then I'd start with parted, and if not, i guess just search Google or Synaptic if you have access to it for command-line partitioners. It's the same as what I would do.

---

### Post by infantiablue on 2008-10-19
Gr8, thank for your tips, I will try util-linux, it sound goods.

---

