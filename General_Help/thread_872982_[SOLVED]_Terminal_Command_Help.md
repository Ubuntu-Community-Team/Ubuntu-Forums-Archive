---
title: "[SOLVED] Terminal Command Help"
date: 2008-07-28
forum: General Help
---

### Post by greenco on 2008-07-28
I have placed a jpg file on my storage space, that shows the message I am getting, when I start X-Plane 9. Would one of you Linux gurus look at the command (shown in this picture), and tell in plain language what it is asking me to do. Is it something that could be broken down into smaller steps? I am brand new to the Linux world, so a lot of the Terminal codes are strangers to me. I have also asked the X-Plane folks for some help, but it is slow coming.

[http://home.comcast.net/~flt-simmer/Mount-udf.jpg](http://home.comcast.net/~flt-simmer/Mount-udf.jpg)

Thanks

---

### Post by Potatoj316 on 2008-07-28
it tells you to run a command in the terminal.  Try running the command in the terminal.  Applications->accessories->terminal

---

### Post by dexter.deepak on 2008-07-28
well , the information is preety simple.
you have tried to mount the dvd (i hope you understand what mount means) , but the system wants you to mount the dvd as a filesystem of the type  : UDF. 
you have to execute all these stuff as root..meaning you have to prepend 'sudo' in front of these commands....or you can simply do:
```
sudo bash
```
and execute all these commands without sudo..but then you have to carry on all the steps in a single terminal.
so first you unmount the dvd:```
umount /dev/dvd
```
then you make a mount point directory, to hold the device:
```
mkdir -p /mnt/dvd
```
this makes a directory /mnt and then another one in it ...so /mnt/dvd

next step is about mounting with UDF filesystem:
```
mount -t udf /dev/dvd /mnt/dvd
```

the '&&' specifies that all this should be done in a procedural way,like:
A && B && C
if A then B and only then C

---

### Post by kool_kat_os on 2008-07-28
why is this thread marked as "0" posts?\

EDIT: well...either im on crack...or it felt like changing back to a real number

---

### Post by Zorael on 2008-07-28
```
umount /dev/dvd && mkdir -p /mnt/dvd && mount -t udf /dev/dvd /mnt/dvd
```
...breaks into the following:
```
# umount /dev/dvd
# mkdir -p /mnt/dvd
# mount -t udf /dev/dvd /mnt/dvd
```
[list=1][*]Unmounts your dvd drive, *provided* it is represented by the [device node](http://www.answers.com/device%20node) **/dev/dvd**
[*]Creates the directory **/mnt/dvd**, also creating parent directories if necessary, and not outputting any errors if it exists ([man page](http://unixhelp.ed.ac.uk/CGI/man-cgi?mkdir))
[*]Mounts (the device node) **/dev/dvd** to **/mnt/dvd**, explicitly telling it to use the **udf** filesystem[/list]

Do note that you need superuser permissions to perform those commands.
```
$ sudo umount /dev/dvd
$ sudo mkdir -p /mnt/dvd
$ sudo mount -t udf /dev/dvd /mnt/dvd
```

---

### Post by cpetercarter on 2008-07-28
The command:

unmounts the dvd from the dev directory, where it is at present

creates a new directory at /mnt/dvd

and mounts the dvd atthis new directory, specifying the udf file system type

You can always check what an unknown command is about by typing ```
man <command>
``` in the terminal.

---

### Post by greenco on 2008-07-28
Here is the results of my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=27617bf9-d6c2-403e-bfc5-23ba4685b4d5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=3dfd545a-0a0e-43af-a9d2-d92630900627 /home           ext3    relatime        0       2
# /dev/sda3
UUID=3ab89527-46fd-47ba-9150-e029080af56f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


The " dev/scd1 " is the dvd drive that I am having problems with. Would one of you nice people use this info in the sudo commands, exactly like I would need do it. In your examples wouldn't the "DVD" need to be changed to something else to correctly identify my drive info. When I get ready to try this, should I remove the game DVD from the drive or leave it in?

---

### Post by greenco on 2008-07-29
**HELP !!!**

Would some one read post 7 and help me write the correct strings to run these sudo commands.

# umount /dev/dvd
# mkdir -p /mnt/dvd
# mount -t udf /dev/dvd /mnt/dvd

$ sudo umount /dev/dvd
$ sudo mkdir -p /mnt/dvd
$ sudo mount -t udf /dev/dvd /mnt/dvd

What is the correct text, that should be used in the places where it say " dvd "?

---

### Post by geirha on 2008-07-29
Try these two. 
```
umount /dev/scd1
mount -t udf /dev/scd1 /media/cdrom1

```

If you get messages saying you don't have permission, put sudo in front of the command.
If you get any other error messages, post them here.

---

### Post by greenco on 2008-07-29
Before I try these, should I remove the game's DVD from the drive?
In the line with mkdir, should the "dvd" text be changed to "scd1"?

I want to be sure that I am using the correct statements, because if it fails I may need to buy a new DVD drive.
Thanks

---

### Post by geirha on 2008-07-29
No, the DVD should be inside all the time. You don't need the mkdir-command, because you allready have a mount-point at /media/cdrom1 (which I read from your /etc/fstab above)

---

### Post by greenco on 2008-07-29
The first command worked but I got this on the second one.

coleman@coleman-desktop:~$ sudo mount -t udf /dev/scd1 /media/cdrom1
[sudo] password for coleman: 
mount: block device /dev/scd1 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by geirha on 2008-07-29
That error message says it can't find any UDF filesystem on the DVD ... Are you sure it's the correct DVD?

---

### Post by greenco on 2008-07-29
Are you talking about the DVD drive itself or are you referring to the game DVD, that is in the drive? The Linux folks at the X-Plane forum says that the game disk is in "udf" format and that is why my DVD drive must be mounted as "udf" for ths game to use it.

There is a link, on the first post, that shows the message I am getting when I start the game.

---

### Post by geirha on 2008-07-31
I'm referring to the DVD, yes. Mounting it with the option "-t udf" should force the DVD to be mounted as an UDF-DVD, but the error message you got when you attempted this, suggests that the DVD does not contain and UDF filesystem (only ISO9660 filesystem). Did you burn the DVD yourself?

However, the error message could mean something else. Try the commands one more time, then run "dmesg | tail" as the error message suggests, and paste the output here.

---

