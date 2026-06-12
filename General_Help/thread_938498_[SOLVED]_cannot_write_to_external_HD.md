---
title: "[SOLVED] cannot write to external HD"
date: 2008-10-04
forum: General Help
---

### Post by mobiblu on 2008-10-04
I use the following command to mount my external HD
```
sudo mount -t vfat /dev/sdb1 /media/sdb1
```

but I am not able to write to the ext HD. Here is my output:
```
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4797ace4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         170     1365493+  82  Linux swap / Solaris
/dev/sda2   *         171        4864    37704555   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x04bbe564

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       32301   244195528+   c  W95 FAT32 (LBA)

```

Also I would get error when trying to unmount:

---

### Post by heikor on 2008-10-05
Try adding the -rw option (sudo mount -rw -t vfat /dev/sdb1 /media/sdb1).
To umount, use "sudo umount /dev/sdb1". I think, the graphical unmounting from Nautilus only works when your external HD was automatically mounted, but I don't really know how I made that work ;-).

---

### Post by capnlester on 2008-10-05
Hi. When i first mounted an external drive i had same problem. it is automatically assigned to ROOT as owner. so first check the permisions on drive after mounting. open terminal and change directories to get to the drive folder. type ls -l to get listing of drives w owner listed as well.
you need to use chown (change owner) and chmod (changes RW permissions) so that you are owner and have given yourself permission to write to drive
Les

---

### Post by mobiblu on 2008-10-05
Thank you all for the reply.
heikor:
I try the command (sudo mount -rw -t vfat /dev/sdb1 /media/sdb1) but still get permission denied. But the (sudo umount /dev/sdb1) command work :)

capnlester:
Can you be more specific. I'm don't even know what directory the ext HD will be.

---

### Post by scouser73 on 2008-10-05
To write you need to log in as **root**, to do this, go to **Terminal**, type **gksudo natuilus**. You will then be prompted for your password, enter it, then Nautilus will start, make your way to your external drive, once in your drive, right click, scroll to **Properties**, then select the **Permissions** tab. You can change who has access to write & delete, and so on.

---

### Post by mobiblu on 2008-10-05
scouser73:
I ran Nautilus as root, but when i try to change permission in the property window, i get an error that i don't have permission.:lolflag:

capnlester:
After some tinkering I was able to follow you instruction. I change to root in terminal. Did (cd /media/sdb1) did (ls -l) and behold--all the file are set to root--no surprise. Next I enter the command  (sudo chown -R userd /media/sdb1) all in vain-- "Operation not permitted"

What am i doing wrong? :confused:

Thanks you again for all the helpful suggestion.

---

### Post by heikor on 2008-10-07
I think there is another solution:
When mounting, use "sudo mount -t vfat /dev/sdb1 /media/sdb1 -o rw,uid=AAA,gid=BBB", where AAA is your User-ID (type "id -u" to find out, probably 1000) and BBB is your group-ID (type "id -g", probably 1000, too). That should set the permissions for the mounted files so that you can access them as a normal user (without starting nautilus as root).
I'm not an expert, but at least this seems to works for me.

---

### Post by mobiblu on 2008-10-07
heikor, you are amazing! that work! :KS

---

### Post by castrogeneris on 2008-10-23
It worked indeed! Thanks heikor...

---

