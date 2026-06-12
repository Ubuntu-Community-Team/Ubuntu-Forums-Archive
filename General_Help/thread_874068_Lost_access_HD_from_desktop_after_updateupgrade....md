---
title: "Lost access HD from desktop after update/upgrade...!!"
date: 2008-07-29
forum: General Help
---

### Post by trosk on 2008-07-29
Came off vacation (2 Weeks) :), and ran a update/upgrade, after restart of PC my HD's was gone. Used to be on my desktop.

(Pc is fitted with 2 different HD's, one IDE where ubuntu is mounted, thats a 80 gb devided i 2x40, can see bouth. One sata 500 gb, devided in 3. They are gone.) !!

Have a dual sys. with win. XP pro.SP3. 
When I try to accesss my sata drive,(win) ubuntu tells me I don't have any right to do so. They have been on my desktop all the way from Hardy was ready and setup on my PC.
I'm not a linux guru, but have used ubuntu the last 3-4 years as my main OS.
This one I'm not able to solve.
Guess it's a simple issue, but right now I'm not able to figure this out.
Have searched around, without any luck.
Use to transfer a lot of files between Ubuntu and win. It was so easy, but...?????
Any help out there...  :)

---

### Post by trosk on 2008-07-29
Came off vacation (2 Weeks) :), and ran a update/upgrade, after restart of PC my HD's was gone. Used to be on my desktop.

(Pc is fitted with 2 different HD's, one IDE where ubuntu is mounted, thats a 80 gb devided i 2x40, can see bouth. One sata 500 gb, devided in 3. They are gone.) !!

Have a dual sys. with win. XP pro.SP3. 
When I try to accesss my sata drive,(win) ubuntu tells me I don't have any right to do so. They have been on my desktop all the way from Hardy was ready and setup on my PC.
I'm not a linux guru, but have used ubuntu the last 3-4 years as my main OS.
This one I'm not able to solve.
Guess it's a simple issue, but right now I'm not able to figure this out.
Have searched around, without any luck.
Use to transfer a lot of files between Ubuntu and win. It was so easy, but...?????
Any help out there...  :)

---

### Post by Potatoj316 on 2008-07-29
post the output of these commands
```
fdisk -l

cat /etc/fstab
```

also, dont post the same thing multiple times

---

### Post by Potatoj316 on 2008-07-29
post the output of these commands
```
fdisk -l

cat /etc/fstab
```

---

### Post by sdennie on 2008-07-29
Threads merged.  Please try not to double post.

---

### Post by trosk on 2008-07-29
trond@test-desktop:~$ fdisk -l
trond@test-desktop:~$ 


trond@test-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=bc5d9fae-0784-4758-bb36-a8eeba9b0c30 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=E43C9B7A3C9B4708 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=B2882E51A2DFE739 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=B8FA82B5FA826F84 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=4E7020E87020D88B /media/sda6     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=deb886e7-1ef2-427e-a8cb-e1b15beba41c none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
trond@test-desktop:~$ 

This is how it looks.....
Strange as I can see I have got 4  drives in stead of 3 as it shows in win, well never mind, dont tink thats the prob.


Sorry for multiple threads, fell free to del. I will continiue my search. ¤

---

### Post by lavinog on 2008-07-29
What drive is windows on? Can you boot to windows? can windows see the SATA drive?

Does your bios see your sata drive?

---

### Post by trosk on 2008-07-30
SATA is visible everywhere but not accessible in Ubuntu after last update. I can see the drives, but have no rights to open them. Win is on C: (Sata), and Ubuntu is on the IDE.
This setup was working 100% until last update of Ubuntu.
Everything else is working as usual.

---

### Post by lavinog on 2008-07-30
have you tried manually mounting them?

Is it possible that when you last booted to windows it hibernated instead of shutting down?  I have had a similar problem when windows hibernated.

---

### Post by vanadium on 2008-07-30
I agree with lavinog: it is well possible that one or more ntfs drives were not properly closed under Windows. In that case, the drives are not mounted.

Solution: Boot into Windows (optionally run a disk test on the drives) and shut down Windows completely.

---

### Post by Twig E. Pottox on 2008-08-02
Thanks, I had the same problem. suddenly I could not access the windows drive in a 2HDD dual boot setup. I started windows let it completely boot up and settle down then shut it down properly. after booting back up in 8.04 the windows drive is back on the desktop

---

