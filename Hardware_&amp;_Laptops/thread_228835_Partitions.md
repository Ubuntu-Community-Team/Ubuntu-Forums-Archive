---
title: "Partitions"
date: 2006-08-03
forum: Hardware &amp; Laptops
---

### Post by Jerim on 2006-08-03
When I installed Ubuntu I installed it on a 20gig partition on my 40gig harddrive. I had windows on the other partition. However, since Ubuntu has turned out so great, I plan on using it exclusively. I want to format the other 20gig and have it automatically recognized by Ubuntu.

How do I accomplish this? In Windows, you just format the partition and the OS will find it as a seperate partition. You then have to directly reference the partition when saving files or installing programs. I understand Linux works on directories and doesn't have drive letters. So where exactly will the additional 20gig go? Does it just get added to the free space or is there something I have to do to access it?:confused:

---

### Post by ahaslam on 2006-08-03
You can use Gparted to format the partition from within Ubuntu. It should be recognised automatically, though you may not be able to write to it without root permissions. To be able to write to it normally you may have to change the permissions & maybe add a line for it in /etc/fstab, where you can also select a place for the partition to be mounted. 

If you want to utilise the extra space solely for Ubuntu, why not delete the Windows partition and the resize your Ubuntu one, taking up the whole drive. You will need the live cd version of Gparted to do that and it may involve a reinstallation of grub (unless Ubuntu was on the 1st partition).

I know that's not exactly a definitive answer, but it gives you another option and other things to look into.

Good look,

Tony.

---

### Post by Jerim on 2006-08-07
I have decided to erase the Windows partition and repartition it for exclusive Ubunut use. When I go to format the partition it will ask for a format type, correct? Such as ext3. Do I want to make it the same as my exisiting partition.

---

### Post by ahaslam on 2006-08-07
You can create any filesystem you wish, I recommend either ext3 or reiserfs, though they don't have to match.

Tony.

---

### Post by Andcor on 2006-08-08
ext3 certainly is a great fs. I'll recoment that.
Once you have formatted your partition you have to choose where to put it, the way you do this is, that you make a directory where you find that you could use a little more space, and then edit the /etc/fstab file to include the line:
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/DISC       /mount          ext3    defaults,errors=remount-ro 0       1

```

Where you have to replace DISC with the name of the partition you have just formatted (such as hda2 or hdb1), replace the /mount with the path to the dir you have created for the disk and ext3 with the fs format you have choosen.

After that you only have to either reboot or run the command 
```
mount /path/to/created/dir
```

---

### Post by Titus A Duxass on 2006-08-08
First off are you doing a complete new installation (it sounds like you are)?

If yes, then follow the steps during the installation process, I would go with reiserfs.

If you are removing the windows partition and are not reinstalling ubuntu do as suggested by Andcor.

---

### Post by hayalci on 2006-08-08
You can use the Disk admin program which can be found on the system menu. You can specify the access path that the partition will be mounted to. Do not forget to first disable the partition. You can see the screenshot of disks-admin: 


[[IMG]http://img150.imageshack.us/img150/4578/ekrangoruntusuzp8.th.png[/IMG]](http://img150.imageshack.us/my.php?image=ekrangoruntusuzp8.png)

---

