---
title: "Windows wont boot after insalling ubuntu on seperate hard drive"
date: 2014-08-21
forum: Hardware
---

### Post by matt_schuster on 2014-08-21
I installed ubuntu on a DIFFERENT hard drive in my desktop pc And now my windows wont boot with error 0xc000000f
I accidently used my windows hard drive as a "Swap" option during install... DID I LOSE ALL MY FILES ON MY WINDOWS HARD DRIVE???

I AM FREAKING OUT RIGHT NOW

---

### Post by matt_schuster on 2014-08-22
Ok can Someone please help I booted into windows install usb and it cant find a windows install. I dont care about the windows install or my programs. I only need my music, pictures and movies back please help.

btw the files are still on the disk because i havent overwrited ANYTHING yet on the hdd knowing i have a chance of recovering the files.

Im not a noob at computers either I just completely f****** up and or wasn't paying attention

---

### Post by anchitsingh9 on 2014-08-22
Have you tried 'testdisk' to recover files. If no, install it using software-center or terminal : 'sudo apt-get install testdisk'.
Read the instructions on its wiki. Also read about 'photorec' (program gets installed with testdisk), it might be a better way.
Although if your swap was encrypted, it might be really difficult or impossible to recover data from that sectors.

---

### Post by yancek on 2014-08-22
You should be able to check to see if you still have any windows partition by booting the Ubuntu installation medium.  After getting to the Desktop with the install icon, click on the Ubuntu logo in the upper left and in the Search box type:  terminal

That should open a terminal where you can type:  sudo fdisk -l(Lower Case Letter L in the command)  Look at the column on the far right of the output labelled System to see if any partitions are ntfs.   Post the info here.

---

### Post by matt_schuster on 2014-08-22
My windows is completely gone, my windows installer could not find any windows operating system on the drive So thats gone. Im gonna try to use test disk. How do i make ubuntu STOP USING my other hdd as a swap and how do i know if my swap is encrypted

---

### Post by weatherman2 on 2014-08-22
Boot the live USB or live disc you used to install.  Then mount your install drive's / partition - say it's on /dev/sdb1.  In a terminal type:

sudo mount /dev/sdb1 /mnt

(replace "sdb1" with the real partition of your Ubuntu OS partition.  I don't mean the swap partition.)

Now edit the fstab file

sudo gedit /mnt/etc/fstab

and in that file, find the line mentioning "SWAP" and comment it out - put a single "#" at the beginning of the line.  That will tell the booted OS not to use a swap at all anymore.  (which is fine for some use especially if you have a lot of RAM).

---

### Post by anchitsingh9 on 2014-08-22
If you encrypted your /home while installing ubuntu, swap would be encrypted too. Open gparted(install it if you haven't), if it shows your swap's file system as 'unknown', then its encrypted.
Try 'sudo swapoff -a' to turn swap off. You may have to edit /etc/fstab to permanently avoid swap partition to mount.
Anyway, first post the info whether your swap is encrypted or not..?

---

### Post by matt_schuster on 2014-08-22
[http://i1307.photobucket.com/albums/s598/Doomkiller98/Screenshotfrom2014-08-22123709_zps4697c08a.png](http://i1307.photobucket.com/albums/s598/Doomkiller98/Screenshotfrom2014-08-22123709_zps4697c08a.png)

heres a screenshot of gparted, is my swap encrypted? Gonna try to do what weatherman said in a little while i have an errand to go run I'll be back later, Thanks so much for your help guys..

---

### Post by matt_schuster on 2014-08-22
Before i leave im gonna ask the question of.. can test disk put all the files still on my hard drive onto the ubuntu hdd? if u get what im saying...

---

### Post by anchitsingh9 on 2014-08-22
Maybe, depends on how much data you have to recover.
Eg: If your data to be recovered is 10GB, but your Ubuntu HDD(I am assuming /home folder) is <=10GB, then it could be difficult, especially when using 'photorec'.
It would be better if you have an external drive, otherwise if space on your Ubuntu HDD is enough, it would work too.

Also your swap isn't encrypted.

---

### Post by oldfred on 2014-08-22
Often the Ubuntu live installer mounts and uses swap, so booting Ubuntu may be overwriting your data in your Windows partition.
Often better to use a gparted liveCD as it does not automatically mount swap. Then you may be able to recover your entire Windows if swap had not overwritten any data.

Testdisk's deeper search should find files as long as not too much is overwritten.

But some suggest Windows tools as they may work better. So try testdisk and photorec as free choices, but you may get more data with NTFS tools.

 NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam.

---

### Post by matt_schuster on 2014-08-22
YES I was hoping for that. Ok so Now what do i have to do to get my data off my hdd (and yes my ubuntu disk has plenty of space 600gb)

---

### Post by yancek on 2014-08-22
Step by Step instructions at the cgsecurity site below, the people who wrote testdisk.  As you can see, it's not something you are going to accomplish with a few mouse clicks but if the data is important, read carefully.

[URL="http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step"]http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step

[/URL]If you reinstall, I would suggest you use the manual (Something Else) option as you will see what is happening.  Maybe read a tutorial or two on install Ubuntu, the current version.  The link below leads to a very detailed tutorial with a lot of useful information.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by matt_schuster on 2014-08-22
Ok success, i booted into the live cd and got linux to not use my hdd as swap anymore (THANK GOD) Now Its time to get my data back.

EDIT: nvm its still using it as swap im just gonna have to keep manually disabling it. ( going into disks and pressing deactivate the swap space)
:/

EDIT AGAIN: ok got the swap to stop happening automatically on boot.

---

### Post by matt_schuster on 2014-08-22
Ok i have an idea, My mom has a beast laptop with external sata connection, If i take the hard drive out of my desktop, hook it up to her WINDOWS pc And use recuva Do i have a better chance of recovery? Im struggling to use testdisk

---

### Post by Mark Phelps on 2014-08-23
Don't know how you intend to connect the drive to your mom's PC, but I've had major problems getting Windows data recovery apps to see drives connected through external (USB) connectors, regardless of the app being used. I've generally had to resort to connecting the drive internally to my desktop to do data recovery.

If Recuva doesn't see the drive, or doesn't find anything, consider trying RecoverMyFiles -- it's free to install and try out.

---

### Post by matt_schuster on 2014-08-24
My Moms laptop has a external sata port :) gonna try later today

---

