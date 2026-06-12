---
title: "new to ubuntu installing second hard drive"
date: 2014-05-17
forum: Hardware
---

### Post by costello1201 on 2014-05-17
Hello this is my first time using ubuntu or any linux distro.  have ubuntu installed on my 128ssd.  just installed a second hard drive ( a 500gb) and would like to use that one for just storage.  the drive appears on my unity bar, but i can not save anything to it.  i can open it but it is empty.  i already have it formatted and when i right click on it it does give me the option to unmount.  any help would be greatly appreciated.  hoping this is an easy fix.  as i am new to ubuntu could you please explain it as easily as you can.  thank you.

---

### Post by oldfred on 2014-05-18
Did you partition it, not just format it? We often see issues where someone just partitions a drive not a partition then has major issues.

Did you label partition? I like to do that but not required. But sometimes I have confused myself as I have labelled a partition Data but mounted it as data which are two different things.

You have to create a mount, give yourself ownership & permissions.
Best to give yourself a permanent mount by adding it to fstab to auto mount on reboot. Otherwise you have to click on it each time after you boot and it will auto mount under the UUID, label or size in /media.

       Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)

   [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Good specific instructions for mounting in this thread:
      
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Edit template for your UUID, desired mount and name of mount.
Some mount in /media, others use /mnt.

If mounted to /mnt/data for example, then give yourself ownership & permissions. Change to your Mount.
Only for Linux formatted partitions. NTFS can only be set by fstab.
      
 sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data

Note that $USER is just you, you can use your name instead.
echo $USER

---

