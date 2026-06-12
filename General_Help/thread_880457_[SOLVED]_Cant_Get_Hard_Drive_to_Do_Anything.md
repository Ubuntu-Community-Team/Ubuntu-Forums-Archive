---
title: "[SOLVED] Cant Get Hard Drive to Do Anything"
date: 2008-08-05
forum: General Help
---

### Post by yarn on 2008-08-05
hello everyone...i am very new to linux and so far love it...my problem is that i have a 200 GB hard drive that I used for windows for videos and music...I no linger have windows installed. Ubuntu recognizes the 200 GB hard drive under the computer but when I try to open it I get a error saying that it can not mount the drive. I have looked for about 3 hours now trying everything i can find. I dont need any of the items on the drive. I just need to get it to work...thank you for your help in advance.  below is what the error is.

---

### Post by lisati on 2008-08-05
You might have to do the following:

[LIST=1]
[*]Start windows
[*]Run "chkdsk" on the disk
[*]close down windows
[*]continue with Ubuntu
[/LIST]

---

### Post by jualin on 2008-08-05
Try forcing the mounting by executing the suggested command on the terminal > sudo mount -t ntfs-3g /dev/sdb1 /media/disk -o force

---

### Post by mc4man on 2008-08-05
Just install gparted (partition editor) or make a gparted boot cd and reformat and partition the drive as you want. (one partition or multiple ones)

Edit: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)

Just ck.ed gparted in hardy(from synaptic), and it works much better than in gutsy, it should be fine.
It never hurts to kept gparted and super grub cd's on hand though.

---

### Post by yarn on 2008-08-05
I have tried all of those except the gparted...ill try and let yall know..thank you for the quick feedback and your time.

---

### Post by yarn on 2008-08-06
ok...i ran gparted and linux now will open the drive but it is saying i dont have permission to put anything on it?  any ideas...thanks in advance

---

### Post by jualin on 2008-08-06
Check that you have all the permissions check under System, Administration, User and Groups, Properties. You should have check "Access external drives" and pretty much everything on that list, including Administer computer. After you log out and log in again, the changes should work.

---

### Post by mc4man on 2008-08-06
If you want the partition (drive) to mount at boot see here
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

If you just want to mount and unmount as needed from places with mouse clicks you can do this
run this to get the /dev/sdxx of the partition (probably /dev/sdb1)
```
sudo fdisk -l
```

Make sure drive isn't mounted (ie. not visible on desktop)

Change what's in red to match your partition (if not sdb1) and user name

Then simply in order
```
sudo mkdir /media/fix1
```
```
sudo mount /dev/[COLOR="Red"]sdb1[/COLOR] /media/fix1
```
```
sudo chown [COLOR="Red"]yarn:yarn[/COLOR] /media/fix1
```

now you can write to the partition. 
unmount the drive (r. click unmount) or from terminal if you want to 
```
umount /dev/[COLOR="Red"]sdb1[/COLOR] /media/fix1
``` (shouldn't need sudo, if it does add it)

and remove the dir.
```
sudo rmdir /media/fix1
```

At this point you can mount from places or places -> removable media or places -> computer  w/ mouse and unmount with a right click (_will be seen as xxxgb media_ (unless you name as below)( your ubuntu install is seen as filesystem in places -> computer)

note; If you want to name the partition then
```
 sudo e2label /dev/[COLOR="Red"]sdb1[/COLOR] NAME
``` replace NAME with name of your choice
will show up after reboot

If the drive had dir's. already on it (not your case) you'd add a -R to the chown (sudo chown -R doug:doug......)

---

### Post by yarn on 2008-08-06
MC4MAN:  I tried to do what you said and everything seemed to work going through console but after I was done it still said that I did not have permission...here is the output of console.


yarn@yarn-desktop:~$ sudo mkdir /media/fix
mkdir: cannot create directory `/media/fix': File exists
yarn@yarn-desktop:~$ sudo mount /dev/sda /media/fix
mount: /dev/sda already mounted or /media/fix busy
yarn@yarn-desktop:~$ sudo chown yarn:yarn /media/fix
yarn@yarn-desktop:~$ unmount /dev/sda /media/fix
bash: unmount: command not found
yarn@yarn-desktop:~$ 
yarn@yarn-desktop:~$ sudo rmdir /media/fix
yarn@yarn-desktop:~$ 

the reason for media.fix already being created is because I did this once already but accidentaly put my hard drive name in for dough:dough instead of my user name which is yarn...and by the way my hard drive name is sda..is this normal???  thank you for everyones help once again.

oh by the way...i did unmount the drive before i started this but it said i didnt...i right clicked on it an unmounted it and it left the desktop.

---

### Post by mc4man on 2008-08-06
@ yarn 

You were using the wrong drive (sda1, your ubuntu partition)

Whether you want to do this as I previously posted or to have the partition mounted at boot as shown in link use _/dev/sdb1_
Reboot and _don't do anything other than opening a terminal_ (that way your partition on the 2nd hdd won't be mounted)

Follow the commands in prev. post, just copy and paste, edited to reflect what i believe your username is.

---

