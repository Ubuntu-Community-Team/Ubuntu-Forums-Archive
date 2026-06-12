---
title: "Problem while mounting a floppy drive"
date: 2009-03-24
forum: Hardware
---

### Post by jotavrj on 2009-03-24
Hello! I'm not so new in Ubuntu, but i had a vry bad problem.

There's a long time i don't use the floppy drive, but today my father needed to use it, and i couldn't access the floppy content.

And, to make it worse, my parents are complaining 'cuz i removed Microsoft Windows from PC.

I tried to use mount this way:

root@vicente:/home/jota# mount /dev/fd0 /dev/floppy
mount: there isn't mounting point /dev/floppy

root@vicente:/home/jota# mount /media/floppy
mount: unable to find /media/floppy on /etc/fstab or /etc/mtab

i tried to use pmount too, but it didn't work.

Please help me, it's serious!

---

### Post by plucky on 2009-03-24
> **jotavrj said:**
> Hello! I'm not so new in Ubuntu, but i had a vry bad problem.

There's a long time i don't use the floppy drive, but today my father needed to use it, and i couldn't access the floppy content.

And, to make it worse, my parents are complaining 'cuz i removed Microsoft Windows from PC.

I tried to use mount this way:

root@vicente:/home/jota# mount /dev/fd0 /dev/floppy
mount: there isn't mounting point /dev/floppy

root@vicente:/home/jota# mount /media/floppy
mount: unable to find /media/floppy on /etc/fstab or /etc/mtab

i tried to use pmount too, but it didn't work.

Please help me, it's serious!



Are you using 8.10 Intrepid? If so see this [Bug report and workaround](https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/255651/+viewstatus) or ```
sudo modprobe floppy
``` in a terminal will load the floppy driver.

Use the workaround in the bug report to load the floppy driver on every reboot.

Also add the line ```
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
``` to your /etc/fstab file and make sure your user is in the floppy group.


Good Luck

---

### Post by jotavrj on 2009-03-24
How can i add my user on the floppy group? I tried entering in System > Administration > Users and groups and there isn't anything about 'floppy drive' here.

And I got an error when i tried to access the floppy disk: 

mount: there isn't any mounting point on /media/floppy0

---

### Post by plucky on 2009-03-24
> How can i add my user on the floppy group?


From a terminal,what does the command ```
id
``` produce.


> mount: there isn't any mounting point on /media/floppy0 

Create a mount point using ```
sudo mkdir /media/floppy0
```

Just checked my 8.10 system and found there is no group called floppy under "Users and Groups",but my user shows "25(Floppy)" when I use the ID command.

---

### Post by jotavrj on 2009-03-27
Thanks, now i can see the floppy's content.

But I need to type 'mount /media/floppy0' everytime i wanna activate the floppy drive. what can i do to force the system mount the floppy drive everytime i insert the floppy ?

and, when i type 'id', returns:
jota@vicente:~$ id
uid=1000(jota) gid=1000(jota) grupos=4(adm),20(dialout),24(cdrom),26(tape),29(audio),46(plugdev),104(scanner),106(fuse),108(lpadmin),123(admin),124(sambashare),1000(jota)

How can i add the floppy's option by COMMAND LINE?

and I can't create documents in the floppy.

thanks for all.

---

### Post by jotavrj on 2009-03-31
up !

---

### Post by plucky on 2009-04-01
> How can i add the floppy's option by COMMAND LINE?

Not sure by command line,but try this

Open **System > Administration > Users and Groups**

Select **Unlock**  and input login Password.

Select **Add Group** and input **Floppy** in the group name and **25** in the Group ID, and tick the box with your username.


Exit out of the GUI.Then logout and log in again and your terminal window should now show you added to the floppy group.

Also did you add the **/dev/fd0** line in /etc/fstab as specified in the previous post?

After all that,your user should then be able to mount the floppy by selecting it in the Places menu.


Good Luck

---

