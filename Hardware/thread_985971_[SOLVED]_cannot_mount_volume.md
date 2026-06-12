---
title: "[SOLVED] cannot mount volume"
date: 2008-11-18
forum: Hardware
---

### Post by ellitsas on 2008-11-18
Hello everyone! i cannot mount my ext drive. what's the command for force mount? thank u all!

---

### Post by ellitsas on 2008-11-18
sorry. forgot to mention that this is what i get when i'm trying to mount the drive: You are not privileged to mount the volume 'NieuwVolume'.

---

### Post by ellitsas on 2008-11-18
problem solved!!!!   How do i unmount it now? it won't let me unmount! Heeeeeeeeeeellp

---

### Post by boof1988 on 2008-11-18
What command did you use to mount the partition/drive?  Then we can figure out how to unmount the drive.

Which OS are you using?  Maybe we need to figure out why the drive didn't automount.

---

### Post by ellitsas on 2008-11-18
hello. these r the commands i used to mount the volume!


sudo mkdir /media/sdc1
sudo mount -t ntfs-3g /dev/sdc1 /media/sdc1 df -h

i'm using Ubuntu 8.10

---

### Post by ellitsas on 2008-11-18
and now, when i turn my system on and the ext hard drive on it doesn't mount again. i need to do force mount again!

---

### Post by ravinderreddy on 2008-11-18
> **ellitsas said:**
> and now, when i turn my system on and the ext hard drive on it doesn't mount again. i need to do force mount again!

Can you post your /etc/fstab entries. check options for the drive you want to mount on start up. one of the options should be auto.

---

### Post by ellitsas on 2008-11-18
i enter in the terminal etc/fstab and it comes back "permission denied".

---

### Post by ravinderreddy on 2008-11-18
post the result of   **less  /etc/fstab**

---

### Post by ellitsas on 2008-11-19
sorry that i didn't reply earlier. my internet connection was off for a whole day almost! so here's what comes out!



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda1
UUID=41a19cc3-2b15-4b1c-af7a-80f19a4dd92d  /              ext3         relatime,errors=remount-ro  0  1  
# /dev/sda5
UUID=89c63619-5b31-4869-be72-e79b7214acbc  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sdb1                                  /media/sdb1    ntfs         defaults                    0  0  
/dev/sdc1                                  /media/sdc1    ntfs         defaults                    0  0  
/dev/sda5                                  /media/sda5    swap         defaults                    0  0  
~
~
~
~
~
(END)

---

### Post by ravinderreddy on 2008-11-19
Can you try this..
change the line /dev/sdc1 with the below line in fstab. you should be a root to edit fstab.
/dev/sdc1 /media/sdc1 ntfs rw,auto 0 0

---

### Post by ellitsas on 2008-11-19
anyone? help? please?

---

### Post by ellitsas on 2008-11-19
how do i become root?

---

### Post by ellitsas on 2008-11-19
i'm sorry but i'm really new in this!

---

### Post by ravinderreddy on 2008-11-19
**sudo gedit /etc/fstab**

it will open in gui editor. modify fstab as i said earlier.

---

### Post by ellitsas on 2008-11-19
just did it but it still won't mount!

---

### Post by ravinderreddy on 2008-11-19
what is your external drive ..is it not /dev/sdc1. have you rebooted your system?

---

### Post by ellitsas on 2008-11-19
oki rebooted and the drive is already mounted. now, when i say "unmount" it doesn't do it!

---

### Post by ravinderreddy on 2008-11-19
what command you used to unmount?

---

### Post by ellitsas on 2008-11-19
i don't know one. i tried just with a right click on the drive!

---

### Post by ravinderreddy on 2008-11-19
ok..you should be a root to unmount the drive. if you want to allow normal user to mount/unmount then change the line /dev/sdc1..in fstab to 

/dev/sdc1 /media/sdc1 ntfs user,rw,auto 0 0

reboot and check.

---

### Post by ellitsas on 2008-11-19
it's still coming up "only root can unmount"...how do i become root?

---

### Post by ravinderreddy on 2008-11-19
have you changed your fstab as i said..?

you can unmount from terminal like..
sudo umount /dev/sdc1

---

### Post by ellitsas on 2008-11-19
i changed it to this:

/dev/sdc1      /media/sdc1    ntfs         user,rw,auto                0  0

in terminal it says command not found!

---

### Post by ravinderreddy on 2008-11-19
you have to edit /etc/fstab again

sudo gedit /etc/fstab

---

### Post by ellitsas on 2008-11-19
ok...and write what?

---

### Post by ravinderreddy on 2008-11-19
change the line starting with **/dev/sdc1**  to
/dev/sdc1 /media/sdc1 ntfs user,rw,auto 0 0

reboot and check.

---

### Post by ellitsas on 2008-11-19
i did it again and it still won't unmount!

---

### Post by ravinderreddy on 2008-11-19
in terminal type this.

sudo umount /dev/sdc1

it should unmount

---

### Post by ellitsas on 2008-11-19
ooookkkkk...i'm really sorry i was typing it wrong! everything is working now! thank u very much!

---

### Post by ravinderreddy on 2008-11-19
no problem.you are welcome.

---

### Post by ellitsas on 2008-11-19
hehee...sorry....i think my machine is crazy now i trie to mount or to unmount again and it says "command not found"

---

### Post by ravinderreddy on 2008-11-19
it seems you are doing something wrong..can you explain how exactly you are trying to mount/unmount?

---

### Post by ravinderreddy on 2008-11-19
has ext drive mounted on startup?

---

### Post by ellitsas on 2008-11-19
everything was perfect. it mounts on startup and before i mounted and unmounted from the terminal. now on the terminal it says "comand unknown" for both !

---

### Post by ellitsas on 2008-11-19
sorry again. there has to be space between mount and the /dev/sdc1 line. i was writing all together. now i got it! thanks again

---

### Post by ravinderreddy on 2008-11-19
can you post the command and it's result

---

### Post by ravinderreddy on 2008-11-19
> **ellitsas said:**
> sorry again. there has to be space between mount and the /dev/sdc1 line. i was writing all together. now i got it! thanks again

ok..no problem

---

