---
title: "[SOLVED] I could not boot the windows vista"
date: 2009-01-07
forum: Installation &amp; Upgrades
---

### Post by halovivek on 2009-01-07
hi
i lost the windows vista. i tried with this thread .
[http://ubuntuforums.org/showthread.php?t=1033152&highlight=boot+loader](http://ubuntuforums.org/showthread.php?t=1033152&highlight=boot+loader)
but i have not downloaded the windows vista recovery disk.
by following i am posting the harddisk details
gurudheva@gurudheva-laptop:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6cabdd5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10363    83240766    7  HPFS/NTFS
/dev/sda2           10364       38913   229327875    f  W95 Ext'd (LBA)
/dev/sda5           10364       15554    41689641    7  HPFS/NTFS
/dev/sda6           15554       20726    41547776    7  HPFS/NTFS
/dev/sda7           20727       29819    73039491    7  HPFS/NTFS
/dev/sda8           29820       34373    36577760    7  HPFS/NTFS
/dev/sda9           37698       38913     9767488+  82  Linux swap / Solaris
/dev/sda10          34374       37697    26699998+  83  Linux

Partition table entries are not in disk order
gurudheva@gurudheva-laptop:~$ 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
bash: [http://home.comcast.net/~ubuntu_grub/boot_info_script.txt:](http://home.comcast.net/~ubuntu_grub/boot_info_script.txt:) No such file or directory
gurudheva@gurudheva-laptop:~$ bootrec /fixboot
bash: bootrec: command not found


could you please help me. while i select the windows vista i got this error > gurb error 1 or 2 i could not remember. please help me.

---

### Post by Tim Sharitt on 2009-01-08
Could you post the contents of /boot/grub/menu.lst

---

### Post by melojo on 2009-01-08
This will give us a clearer picture. 
copy and paste this a terminal and it will create a results.txt open it and copy and paste the output.

```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```

---

### Post by halovivek on 2009-01-08
hi 
today morning i searched the forum and found this thread.
[http://ubuntuforums.org/showthread.php?t=1033152&highlight=vista+boot+problem](http://ubuntuforums.org/showthread.php?t=1033152&highlight=vista+boot+problem)

I followed and able to go up to the ubuntu 
but i could not recover the windows booting. lot of installation of files are there in that one.
the mistake what i did was yesterday i bought 1TB hard disk and i copied all data from drives expect windows c: drive and ubuntu (since windows will not show it off) so there is no care.

Before installing ubuntu as a separate i installed ubuntu from windows and it was in E:- partition. The ubuntu which was there was done fine.

After that i thought i will have an independent ubuntu not in windows partition since if some one uses my computer they may delete the file. so I have installed the ubuntu again from booting and it went file.

This was how it was working.
[COLOR="Blue"][B]if you boot it show all four kernel as well as recover-(i used this ubuntu)
if you select the windows/other OS it will go and again it will boot the grub again and we have to select the ubuntu.
so i have choice to use both. and both went fine.
Since i was using the 1st ubuntu i have deleted the windows installed ubuntu. but the grub was still there and i use to login to windows and working fine.[/B][/COLOR]

The real tragedy came yesterday night. i have moved all the data from e:- already i have formatted the disk and i was using it for some movies and data's. to External hard disk.

once i restarted i could not get both windows or ubuntu.

[http://ubuntuforums.org/showthread.php?t=224351&highlight=vista+boot+problem](http://ubuntuforums.org/showthread.php?t=224351&highlight=vista+boot+problem)
using the above thread i have downloaded and burn the both vista recover CD as well as grub one also.

After that I load the Live CD and i followed the steps from this thread and i could able to get ubuntu back but still the windows is in vain. Tomorrow morning before 4.30( that is 3.30 GMT) i have fix it. since I use windows for the Trading of share in online. otherwise it will be very painful for me to reinstall and do the things. I even did not have the backup of vista.

please help me fast.

[B][COLOR="Blue"]Now i can able to see only ubuntu.
i can see all the four kernel and recover
i could see the windows loader but it says it got failed. 
[COLOR="Red"]i checked with the vista recovery disk, it finds the windows and tells if you have removed your music, or some thing while restarting. please contact administrator for help. nothing more[/COLOR].[/COLOR][/B]

---

### Post by melojo on 2009-01-08
Worry about getting windows back so you can use if for work.
Go to the link below and download the .iso and burn it to a cd.  You will have an option to fix windows. 

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by lgeek on 2009-01-08
if booting into windows vista is urgent then u can give it a try..
though i m not sure wether its gonna work for u or not but it definitely worked for me..
on booting go to the grub commanline by pressing c
u will have something like this:
grub>
now execute the following steps
1.rootnoverify (hda,b)
where "a" is the physical hard disk number.if u r using one hard disk it should be 0(in my case it is) or u can press tab to check.
"b" is the partition number in which vista is installed.u can press tab to check the ntfs filesystems.
2.makeactive
3.chainloader +1
4.boot
i hope u can boot into vista.give it a try.

---

### Post by halovivek on 2009-01-08
> **melojo said:**
> Worry about getting windows back so you can use if for work.
Go to the link below and download the .iso and burn it to a cd.  You will have an option to fix windows. 

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Already i have downloaded and having the copy of this one.
how to continue more?

---

### Post by halovivek on 2009-01-08
> **lgeek said:**
> if booting into windows vista is urgent then u can give it a try..
though i m not sure wether its gonna work for u or not but it definitely worked for me..
on booting go to the grub commanline by pressing c
u will have something like this:
grub>
now execute the following steps
1.rootnoverify (hda,b)
where "a" is the physical hard disk number.if u r using one hard disk it should be 0(in my case it is) or u can press tab to check.
"b" is the partition number in which vista is installed.u can press tab to check the ntfs filesystems.
2.makeactive
3.chainloader +1
4.boot
i hope u can boot into vista.give it a try.


ok i will try this and let you know

---

### Post by caljohnsmith on 2009-01-08
Halovivek, if you can run the script that melojo linked to, that would give us a much clearer picture of your setup and what your Ubuntu/Windows booting problem might be. How about trying again:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. If you don't have internet connectivity when using the Live CD, you can instead right-click [this link]("http://home.comcast.net/~ubuntu_grub/boot_info_script.txt") to the script in your web browser, choose "Save link as...", save the "boot_info_script.txt" file, transfer it to your Ubuntu desktop on the Live CD via USB stick, floppy, or however you want to do it, and then do the following in a terminal:
```
sudo bash ~/Desktop/boot_info_script.txt
```
The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by halovivek on 2009-01-08
[COLOR="Blue"]Hi 
i have solved finally. i really you all the people who helped me to do so. i got back my vista operating system as well as the ubuntu.
i have followed the [thread]("http://ubuntuforums.org/showthread.php?t=740221&highlight=vista+boot+problem") and i have solved it.
Thanks you so much all [/COLOR]

---

