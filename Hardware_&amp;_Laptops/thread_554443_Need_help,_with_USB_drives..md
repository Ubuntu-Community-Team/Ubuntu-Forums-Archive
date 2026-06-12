---
title: "Need help, with USB drives."
date: 2007-09-19
forum: Hardware &amp; Laptops
---

### Post by FarmerReg on 2007-09-19
Hello, 
         I've recently come across an irritating issue with Ubuntu and 2 of my 3 USB drives. At first I could write to them with no problems what so ever, then all of a sudden one day, when I mounted my WD HDD; every folder icon had a lock on it. I did a little digging and found that the entire drive was made read only when viewing in Linix, but on a Windows machine, I could do everything. The same with my thumb drive. On a Windows pc it says that I have 3.8 GB free and when I mount it on my Ubuntu machine, I am told that I only have 40 MB of free space.

Is there something I did wrong?? If so, could someone please take the time to explain it to me.

And is there a solution as to how I can get back to being able to write to both devices and have full access to all available space.

I'm off to work now and will check the forums from my job [hopefully] and try to respond to any questions as quickly as possible.

Thanks in advance for any and all information.






-Farmer

---

### Post by ijason on 2007-09-19
heyo.

it sounds like your problem is that ubuntu has issues with reading the NTFS file system. by issues, i mean that you have to install a program to give write access to NTFS volumes. it can _read_ them unassisted. unfortunately i can't recall the name of the program, but a search for "ntfs write permission" on here will surely find it.

i'm a bit confused though, that you say you USED to have read and write access? that sounds more like the drives are being mounted by root, so it's mounting all the volumes as being owned by root. but i'm a little to green at ubuntu to offer an expert opinion :)

you're absolutely certain that you used to have read/write to your ntfs volumes? if so i'm betting it's mounting them as the wrong user.

---

### Post by rzrgenesys187 on 2007-09-19
I have a program called ntfs configuration tool.  I forget how i got it, either from synaptic or add/remove programs

---

### Post by greenstar on 2007-09-19
I've noticed similar results with my external usb drives, and this with _ext3_ partitions. I never have issues with access to my fat32 or ntfs once I set them up, but ubuntu keeps trying to mount the ext3's as user 1001 instead of an _actual_ user. I have a user account on all boxes in question with the same name. I can't be the only one tired of having to chown and/or chmod every time I swap my drives to another box.

Sorry I can't contribute more here, but maybe this will help someone put it together.

Greenstar

---

### Post by FarmerReg on 2007-09-19
> **ijason said:**
> heyo.

it sounds like your problem is that ubuntu has issues with reading the NTFS file system. by issues, i mean that you have to install a program to give write access to NTFS volumes. it can _read_ them unassisted. unfortunately i can't recall the name of the program, but a search for "ntfs write permission" on here will surely find it.

i'm a bit confused though, that you say you USED to have read and write access? that sounds more like the drives are being mounted by root, so it's mounting all the volumes as being owned by root. but i'm a little to green at ubuntu to offer an expert opinion :)

you're absolutely certain that you used to have read/write to your ntfs volumes? if so i'm betting it's mounting them as the wrong user.

Yes I **used** to have write access. The WB Drive as well as the SanDisk thumb drives are both Fat32 devices. My 3rd USB HDD is a Seagate NTFS drive. I've tried running the NTFS Configuration tool, but I still only have read access to that drive [which is fine], but I'm mainly concerned with the other two devices as I used to have full access to them, but now I do not.

I've tried logging in as root, to try and resolve the issue, but have had no luck.

Maybe this is somehow tied to my mounting and unmounting the devices. [I have files that I take to and from work, and try to conserve space on my old 20 gig HDD; which is where I am running Ubuntu from.]



-Farmer

---

### Post by PmDematagoda on 2007-09-19
To enable write support you need to enable:-

"Write support for external NTFS volumes" in the NTFS configuration tool options.

---

### Post by FarmerReg on 2007-09-19
> **PmDematagoda said:**
> To enable write support you need to enable:-

"Write support for external NTFS volumes" in the NTFS configuration tool options.

I believe I've tried this already for the Seagate external HDD, but will give it another go when I get home.

---

### Post by mrintegrity on 2007-09-19
> **FarmerReg said:**
> I believe I've tried this already for the Seagate external HDD, but will give it another go when I get home.
I suspect that ntfs write support is already enabled but is not working or is being ignored for some reason, please post the output of this command: "mount" whilst the drives that are not working correctly are plugged in.

---

### Post by FarmerReg on 2007-09-19
> **mrintegrity said:**
> I suspect that ntfs write support is already enabled but is not working or is being ignored for some reason, please post the output of this command: "mount" whilst the drives that are not working correctly are plugged in.

Will do, as soon as I get home.



Now do I just go to the terminal and input the command?? 
I'm pretty sure I'll have to................... still getting the hang of Ubuntu. :D




-Farmer

---

### Post by Bablefish on 2007-09-19
I had a similiar problem with one of my drives. It began when I tried to delete some files on it on my Linux machine. I fixed it when I brought it to my Windows PC and reformated it, by the way it took 3 reformats to get the thing running normally again.

---

### Post by FarmerReg on 2007-09-19
> **mrintegrity said:**
> I suspect that ntfs write support is already enabled but is not working or is being ignored for some reason, please post the output of this command: "mount" whilst the drives that are not working correctly are plugged in.

Here are the results:

```
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb1 on /media/FASTLANE type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)
/dev/sdc1 on /media/FreeAgent Drive type ntfs (rw,nosuid,nodev,umask=222,utf8)
/dev/sda1 on /media/sda1 type vfat (rw,iocharset=utf8,umask=000)

```


[QUOTE=Babelfish]I had a similiar problem with one of my drives. It began when I tried to delete some files on it on my Linux machine. I fixed it when I brought it to my Windows PC and reformated it, by the way it took 3 reformats to get the thing running normally again.[/QUOTE]

Interesting.......................... I will connect the drives back to my windows pc and transfer the files to the 3rd drive and give it a try if all else fails.




-Farmer


P.S.
Thanks for all the help so far, I really do appreciate it guys.
You guys rock!!! :guitar:

---

### Post by FarmerReg on 2007-09-20
*bump*

---

### Post by FarmerReg on 2007-09-20
> **Bablefish said:**
> I had a similiar problem with one of my drives. It began when I tried to delete some files on it on my Linux machine. I fixed it when I brought it to my Windows PC and reformated it, by the way it took 3 reformats to get the thing running normally again.
I tried reformatting my thumb drive and it was a success on the first time out. I now have full access to all available space.

However when I tried to reformat my WD HDD, Windows only wanted to format the drive in NTFS and FAT32 wasn't even an option for me to choose. Any ideas on how to get around this??



-Farmer

---

### Post by PmDematagoda on 2007-09-21
This is very strange, but I solved a similar problem by doing this.

I couldn't read my 128Kingston pen drive after I formatted it to NTFS. I enabled the write support for external devices but had no luck. I decided to do what I'm best at, keep flipping the switches on and off until something happened. Meaning I disabled the write support, restarted Ubuntu and enabled it again after that didn't work I disabled it again, logged off and re-enabled it again. This time it worked and I don't have any further problems with my NTFS partitions. I hope it would be of help for you.

---

### Post by FarmerReg on 2007-09-23
> **PmDematagoda said:**
> This is very strange, but I solved a similar problem by doing this.

I couldn't read my 128Kingston pen drive after I formatted it to NTFS. I enabled the write support for external devices but had no luck. I decided to do what I'm best at, keep flipping the switches on and off until something happened. Meaning I disabled the write support, restarted Ubuntu and enabled it again after that didn't work I disabled it again, logged off and re-enabled it again. This time it worked and I don't have any further problems with my NTFS partitions. I hope it would be of help for you.

I will give this a go and report back my findings. Thanks for the response.




-Farmer

---

### Post by FarmerReg on 2007-09-26
> **PmDematagoda said:**
> This is very strange, but I solved a similar problem by doing this.

I couldn't read my 128Kingston pen drive after I formatted it to NTFS. I enabled the write support for external devices but had no luck. I decided to do what I'm best at, keep flipping the switches on and off until something happened. Meaning I disabled the write support, restarted Ubuntu and enabled it again after that didn't work I disabled it again, logged off and re-enabled it again. This time it worked and I don't have any further problems with my NTFS partitions. I hope it would be of help for you.

I did this but I still cannot write to the WD external drive that I reformatted to NTFS.

When I tried to mount the drives, i get an error message stating that the drives weren't shut down or disconnected properly and i need to go back to windows and shut them down properly. Tried doing that, but still no joy.

Any other suggestions??


-Farmer

---

