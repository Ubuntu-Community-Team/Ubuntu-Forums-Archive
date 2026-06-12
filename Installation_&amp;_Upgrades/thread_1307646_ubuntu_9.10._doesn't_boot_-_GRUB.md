---
title: "ubuntu 9.10. doesn't boot - GRUB"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by Matej R on 2009-10-31
HI!

I need help. I've installed the 9.10. on my computer from a CD. The installation went fine, but when I had to restart the computer - it didn't boot. It stops with the word "GRUB". I have no other OS on my computer.

what do I have to do to make it work?

Thanks for answering!

---

### Post by Sealbhach on 2009-10-31
Hi, first thing to try is to boot up from your Live CD and reinstall Grub. The procedure for Grub2 can be found here:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

It looks a little more complicated but it's not too bad.

Give it a try and see how you do.

.

---

### Post by Matej R on 2009-10-31
I've done it to the letter but te response was that - command not found. When the comupeter was restarted the same problem reemerged. have I done it wrong?

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe142e142

   Device Boot      Start         End      Blocks   Id  System
 /dev/sda1   *           1       23947   192354246   83  Linux
/dev/sda2           23948       24321     3004155    5  Extended
/dev/sda5           23948       24321     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
 255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfacbfacb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         370     2971993+  82  Linux swap / Solaris
 /dev/sdb2             371       19457   153316327+   5  Extended
/dev/sdb5   *         371        2922    20498908+  83  Linux
/dev/sdb6            2923       19457   132817356   83  Linux
ubuntu@ubuntu:~$ sudo mount /dev/sdb5 /mnt
 mount: /dev/sdb5 already mounted or /mnt busy
mount: according to mtab, /dev/sdb5 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev/ /mnt/dev
ubuntu@ubuntu:~$ sudo chroot /mnt
bash: groups: command not found
 root@ubuntu:/# sudo grub-install /dev/sdb
bash: sudo: command not found
root@ubuntu:/# sudo grub-install --recheck /dev/sdb
bash: sudo: command not found
root@ubuntu:/# exit
ubuntu@ubuntu:~$ sudo umount /mnt/dev
 ubuntu@ubuntu:~$ sudo umount /mnt
umount: /mnt: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
ubuntu@ubuntu:~$ reboot

---

### Post by Sealbhach on 2009-10-31
You've got this problem I've seen before:

```
ubuntu@ubuntu:~$ sudo chroot /mnt
bash: groups: command not found
 root@ubuntu:/# sudo grub-install /dev/sdb
bash: sudo: command not found
```

Somebody else last night had this as well: [http://ubuntuforums.org/showthread.php?t=1306476](http://ubuntuforums.org/showthread.php?t=1306476)

I don't know what the solution is but you could PM him and see if he got anywhere.

.

---

### Post by ssican on 2009-10-31
Grub 2 Basics :

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by phekdra on 2009-10-31
> **Matej R said:**
> HI!

I need help. I've installed the 9.10. on my computer from a CD. The installation went fine, but when I had to restart the computer - it didn't boot. It stops with the word "GRUB". I have no other OS on my computer.

what do I have to do to make it work?

Thanks for answering!

I wonder if this is the same problem I've been having when AHCI mode is set to enabled in the BIOS. I disabled it and it boots, but I really would like a proper solution rather than a workaround, other than going back to grub1 of course. :confused:

Andrew

---

### Post by Matej R on 2009-10-31
It sucks. I've tried everything and it still doesn't work. When I'm uninstalling and then installing GRUB it doesn't find the /boot device (Not found or not a block device), or when I'm reinstalling it doesn't recognise the command.

My computer is unusable at the moment, but surprisingly my net book works perfectly whit netbook remix 9.10.

Thanks anyway!

---

### Post by ibuclaw on 2009-11-01
> **Matej R said:**
> It sucks. I've tried everything and it still doesn't work. When I'm uninstalling and then installing GRUB it doesn't find the /boot device (Not found or not a block device), or when I'm reinstalling it doesn't recognise the command.

My computer is unusable at the moment, but surprisingly my net book works perfectly whit netbook remix 9.10.

Thanks anyway!

Try switching the order of the boot devices in BIOS. (switch around the two hard drives).

That resolved someone else's issue, as linked earlier in this thread.

Regards
Iain

---

