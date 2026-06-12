---
title: "Access to Harddrive"
date: 2006-04-16
forum: Hardware &amp; Laptops
---

### Post by kitts on 2006-04-16
Strange thing about Ubuntu Live cd is it could detect almost all of my hardware including my 'intex Tv card' but i cannot have access to my hardrive and its NTFS partitions. Why ?
            When i start system>administaration>Disks> harddrive is shown ..it is partitions are also shown. But when i try to 'enable' them i am not able to?
is it because they are 'NTFS' filesytem or i need administrative privileges (whcih means i need to use some sudo command on the terminal.????
](*,) ANy help here is appreciated and it will go a long way in promoting 'Ubuntu'.

---

### Post by frodon on 2006-04-16
All is explained in this link about how mounting NTFS partitions : [http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)
Once your fstab line is written, you will never bother again with your NTFS partition.

---

### Post by taurus on 2006-04-16
Open a terminal (Applications -> Accessories -> Terminal) and type
```

sudo mkdir /mnt/windows
sudo mount -t ntfs /dev/hda1 /mnt/windows <-- assuming first partition of the first harddrive is where your Windows is...
df -h <-- you should see your Windows mounted on /mnt/windows

```
And if you need to read it or access it, you need to put sudo in front of a command like
```

sudo cd /mnt/windows

```

---

### Post by gm__ on 2006-04-16
Hi!

I have the same problem, and when i type
sudo mkdir /mnt/windows
it tells me that " cannot create directory:file exists"

so i type 
sudo cd /mnt/windows

and it goes "cd:command not found"

Could anyone help me with that?

Thanks a lot!

---

### Post by aysiu on 2006-04-16
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by gm__ on 2006-04-16
Wow :) that was fast!

Thanks Aysiu , i give it a try,  it seems that i have to unmount it before...

Cheers!

---

### Post by kitts on 2006-04-16
well it works fine..but i am able to only read the partitions..
how about writing anything to the hda1,hda2 etc...?
i am not able mount 'etended partiton' with the same commands?

---

### Post by kitts on 2006-04-16
Why do i need to use Terminal at every stage to copy, to paste, To access hardrive? when there is GUI?
This is annoying as i need to find commands for everyaction i do.
Is there a way to login as 'root' with total command over what i do?

---

### Post by aysiu on 2006-04-16
In answer to your questions:

1. NTFS is read-only from Linux. There are programs that enable you to write, but they're still experimental.

2. You can do things in GUI by typing ```
kdesu konqueror
``` in KDE or ```
gksudo nautilus
``` in Gnome. If you find yourself doing this often enough, create a launcher for the command.

3. If you don't like having to edit /etc/fstab to get your Windows partitions, Ubuntu is not the distro for you. Try Knoppix.

---

### Post by kitts on 2006-04-17
Can u write on fat32?

---

### Post by taurus on 2006-04-17
[QUOTE=kitts]Can u write on fat32?[/QUOTE]
Yes, you can write to fat32 from either Linux or Windows...

---

