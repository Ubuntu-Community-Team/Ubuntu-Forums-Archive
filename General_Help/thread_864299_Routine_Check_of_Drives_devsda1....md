---
title: "Routine Check of Drives /dev/sda1..."
date: 2008-07-19
forum: General Help
---

### Post by WeEatVista on 2008-07-19
Every time I start up my Ubuntu laptop, Ubuntu always tries to have a 'routine check of drives /dev/sda1..' and it always fails, restarting my computer. Then this whole process starts over again. The only way I can boot up this computer is when I get the splash screen and it says 'press esc to skip.' (I get the splash scren only 75% of the time) Is there any way I can skip this routine check? Or is there a way to complete this check? Any help would be appreciated.

Thanks in Advance,

We Eat Vista

---

### Post by damis648 on 2008-07-19
Boot up in recovery mode. If you see the scan message, skip it. You will be greeted by a dialog that asks what to do. Choose you want a root prompt. In the prompt, enter:
```
umount /dev/sda1
```
then
```
fsck -p /dev/sda
```
and wait until it finishes. When it does, type
reboot and see if that works.

---

### Post by WeEatVista on 2008-07-20
I can't get into recovery mode at all. While trying to boot into recovery mode it tries to do the check, but I can't hit esc to skip the check like I can with the splash screen. Then the check fails - but it does give me a prompt to type in exit to restart the computer. Any ideas?

Thanks,

We Eat Vista

---

### Post by Titan8990 on 2008-07-20
Try the same thing mentioned before from the Ubuntu Live CD.

---

### Post by munkyeetr on 2008-07-20
Just curious, have you tried testing your hard drive to see if it passes manufacturer diagnostics? It's possible that your drive is on it's way out.

---

### Post by mcduck on 2008-07-20
Are you dual-booting? What file system you have on that partition? It might be a good idea to post the contents of your /etc/fstab here..

---

### Post by WeEatVista on 2008-07-20
> Just curious, have you tried testing your hard drive to see if it passes manufacturer diagnostics? It's possible that your drive is on it's way out.

Thanks for the reply, but I hope that's not the case. This laptop is brand new. :)

> Are you dual-booting? What file system you have on that partition? It might be a good idea to post the contents of your /etc/fstab here..

Thanks for the reply, but no I am not dual booting. I only have ubuntu 8.04 on my system. Here is the contents of my /etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3163e166-be88-4f23-bd8c-6e4a3b85b5c3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b9a47eff-4881-4050-91ad-e8db9ed65a0d none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Any suggestions?

Thanks!

We Eat Vista

---

### Post by drs305 on 2008-07-20
An app that I like and could actually help you (in a way) is autofsck. It tailors fsck checks to your specifications. You can set it to check at a certain number of boots. There are other apps/commands that can do this, such as tune2fs, but autofsck also allows you to complete the check at shutdown rather than at boot. At least you could try to get a complete fsck when you aren't trying to use your computer.

Autofsck isn't in the repositories but there is a deb file so all you have to do is download and click on it. It will then get registered in synaptic.

If you are interested it in, here's the link:
[AutoFsck]("https://wiki.ubuntu.com/AutoFsck")

---

### Post by WeEatVista on 2008-07-21
Thanks to all of you who helped. I was able to fix my problem. When the check failed, it gave me a prompt of root@ubuntu-laptop. I ran fsck manually using fsck -y. The check ran through, while ignoring all errors and blocks, and fixed all the errors. 

> An app that I like and could actually help you (in a way) is autofsck. It tailors fsck checks to your specifications. You can set it to check at a certain number of boots. There are other apps/commands that can do this, such as tune2fs, but autofsck also allows you to complete the check at shutdown rather than at boot. At least you could try to get a complete fsck when you aren't trying to use your computer.


Thanks for the direct link :) I am now fiddling around with this app, so next routine check won't interfere when I need to use my laptop.


Thanks!

We Eat Vista

---

