---
title: "execution from fat32 drive"
date: 2008-07-04
forum: Hardware
---

### Post by nesralretep on 2008-07-04
I am running Hardy and XP in dualboot on thinkpad t61. Everything is working beautifully except for one thing. I have a windows nfts partition, a linux ext3, a linux swap, and then a shared fat32 partition for my data.

The problem is that I cannot execute files from the fat32 partition. I have succesfully compiled e.g. c++ code on the drive, but i cannot run the compiled program. If I move the binary to my home on the linux partition, everything works fine. I have also tried to run the binary from a fat16 usb stick - also without problems. As far as I can see, the permissions are set correctly in fstab which automounts the drive on startup. 
This is done with
/dev/sda5 /media/DATA vfat users,umask=0000,auto 0 0

The permission for the program (sum) I want to run are
$ ls -l sum
-rwxrwxrwx 1 root root 10742 2008-07-04 17:26 sum

And the running of the program returns
$./sum
bash: ./sum: Permission denied

Also as root
$ sudo ./sum
sudo: unable to execute ./sum: Permission denied

Does anyone have an idea what the problem might be?

In summary, I 
1) have the right linux file permissions
2) can read, write, compile on the fat32 drive
3) can execute on ext3 and usb-stick
4) I canNOT execute on fat32

Would appreciate any kind of help or suggestions

---

### Post by nesralretep on 2008-07-04
Found the solution already

in fstab add the option exec:

/dev/sda5 /media/DATA vfat users,umask=0000,auto,exec 0 0


a good way to check the status of all partitions is with
$cat /etc/mtab

---

