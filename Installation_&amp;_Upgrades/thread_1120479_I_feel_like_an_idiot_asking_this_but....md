---
title: "I feel like an idiot asking this but..."
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by dubstar92 on 2009-04-09
it seems like editing the device.map is the best way to solve error 17, but I can't seem to find the device map. How to I view it. :cry:


btw I'm dual booting with vista if that matters.

---

### Post by Herman on 2009-04-09
You're not an idiot, it's a good question. I think it does say somewhere in the [Gnu Grub Manual]("http://www.gnu.org/software/grub/manual/grub.html") that editing the /boot/grub/device.map file is supposed to cure GRUB Error 17, I can't seem find that exact quote right now though.
I think they were writing that about an earlier version of GRUB and the device.map seems to have been disabled since, but no-one ever thought to update the manual, (I'm only guessing, and I might be wrong).

You can view it with,
```
cat /boot/grub/device.map
```The use of the /boot/grub/device.map file is just to show you how GRUB's numbering for your hard drives compares with the Linux numbering. I don't think modern versions of GRUB refer to the device.map file at all during boot-up, so I don't think that manually editing the file will make any difference at all. 
Let me know if it does. 

Do you get GRUB Error 17 when trying to boot Ubuntu, or only when you try to boot Windows?

Do you have more that one hard disk in your computer?
Do you have IDE and SATA hard disks plugged into the same motherboard?

Solving GRUB Error 17 depends on finding out or guessing what's probably causing it.

GRUB Error 17 can be caused by a messed up file system in Ubuntu, and running a file system check should fix it if that's what the problem is, [Running a filesystem check with GParted]("http://users.bigpond.net.au/hermanzone/p10.htm#Running_a_filesystem_check_with_GParted_")** or  **[Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem").

If that's not the problem and if your computer has more than one hard disk, it could be that GRUB and the Linux kernel have a difference of opinion about which of your hard disks to number first, IDE or SATA.
You can fix most easily that by going into the [Changing the hard Disk Boot Priority]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_hard_Disk_Boot_Priority") and then [Re-install GRUB with a GRUB shell]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD").

If you want, you can update your /boot/grub/device.map with 
```
sudo grub-install --recheck /dev/sda
```Regards, Herman :)

---

### Post by king2007 on 2009-04-09
me too ! thanks for your reply herman, i need to learn more about grub.
i do have a so-called super grub disk.
having tryed to upgrade from hardy heron 8.04 yesterday which did not succeed - then having downloaded the .iso-image from the ubuntu-homepage and burnt it on a disk (with xp) i was sure to start looking at the new version called jaunty jackalope - installation went fairly well... wrong !! error 17 !!
everytime a new version is downloaded, from gutsy gibbon on ubuntu messes up the boot-record.....
i had that with hardy heron ànd with intrepid ibex.
can i not burn a disc with a standard multi-boot record ? so that whenever it is messed up i can load this from the disc ? would it not be a good idea for newbies such as me to put this in the absolute beginners forum ?

---

### Post by Herman on 2009-04-09
I'm surprised that anyone would get GRUB Error 17 anymore in Ubuntu releases later than Hardy Heron, because I think it was with Intrepid Ibex that Ubuntu advanced to using the uuid command in the menu.lst file instead of the old boot command.

Not so long ago, I think up to Hardy Heron, Ubuntu's GRUB used a 'root' command in  (hd0) numbers (GRUB notation), and a kernel option in the kernel line for specifying the root file system, (in Linux numbering), like below,
```
title    Ubuntu, kernel 2.6.20-15-generic
**root      (hd0,1)**
kernel   /boot/vmlinuz-2.6.20-15-generic **root=/dev/sda2**
initrd   /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

```In those times we used to have a little trouble with cases of GRUB Error 17 popping up here in the Ubuntu Web Forums quite regularly. Mostly it could be caused by the (hd0,1) hard disk and partition number being wrong.
That used to happen especially if a computer had IDE and SATA drives and GRUB couldn't tell which kind of drive the BIOS would count first.

The newer versions of Ubuntu, Intrepid Ibex and the soon-to-be-released Jaunty Jackalope shouldn't be able to get GRUB Error 17 thanks to the use of file system UUID numbers in the menu.lst files,
```
title    Ubuntu, kernel 2.6.20-15-generic
**uuid     fe7bf845-7ce9-4733-b6de-f70f2b62076d**
kernel   /boot/vmlinuz-2.6.20-15-generic root=**UUID=fe7bf845-7ce9-4733-b6de-f70f2b62076d** ro quiet splash
initrd   /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
```Now the hard disk and partition number can't be wrong because there is no hard disk and partition number, but instead the Universally Unique IDentifier of the file system.
So, I think if you have GRUB Error 17 in Jaunty Jackalope, probably a file system check from the Live CD will fix it. [Running a filesystem check with GParted]("http://users.bigpond.net.au/hermanzone/p10.htm#Running_a_filesystem_check_with_GParted_")** or  **[Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem").

... unless there is something new going wrong that I don't know about yet.

Regards, Herman :)

---

### Post by dubstar92 on 2009-04-09
Ok, I'm going to run a system file check.

Just for some more info, I only have one hardrive. Also, I found device.map, and only (hd0)/dev/sda is showing up. So I assume boot order isn't a problem. Also I get error 17 only when booting up ubuntu, vista is working fine.

---

### Post by king2007 on 2009-04-09
Sorry Herman ! i am having Error 15 in stead of error 17 
now i can only boot with the sgd in the dvd-drive so i am trying to solve that ...

---

### Post by cariboo on 2009-04-09
I've had goog luck using [thread=224351]this[/thread] howto for fixing various grub errors. I still get a grub error 17 on a new installation. I have Ubuntu on a PATA which always is detected as /dev/sdb as I use an internal SATA drive for file storage and it is detected as /dev/sda, the switch to uuid doesn't help on a fresh install in my situation. Using the howto I linked to repairs the problem.

Jim

---

### Post by dubstar92 on 2009-04-09
well doing a sysetm file check didn't work. I'm thinking about uninstalling ubuntu then re-installing. The only problem is I don't have my vista cd... is there any way to get rid of ubuntu without having it?

---

### Post by dubstar92 on 2009-04-09
Cariboo, thank you so much. That got it to work. :D

---

### Post by Herman on 2009-04-09
Hello dubstar92,
I'm glad you got it fixed, and thanks cariboo907 for posting the solution too.
Can you tell me which version of Ubuntu you are using please, dubstar92?

I know so far that you have a computer with only one hard disk, and you had GRUB Error 17 and a file system check didn't fix it.
I assume that re-installing GRUB to MBR was what fixed it for you.

I am wondering if you are using a pre-release version if Jaunty Jackalope?
In that case it could be a bug that the developers will probably solve by the time Jaunty is released. We could check and see if a bug report already exists.
Otherwise it could be just a random fault caused by a speck of dust or a tiny scratch on a CD, a small power fluctuation at a critical moment of some other such unlikely or unusual conditions.

If you could provide a little but more information please, it might turn out to be helpful to others.

Did you use the standard ext3 file system or the new ext4fs?
Which CD did you install from, Jaunty Jackalope Alpah6?

The reason I'm asking is because I guess they're making some changes to GRUB to get it to be compatible with the new ext4 file system which is a new option in Jaunty Jackalope.

Thanks, 
Regards, Herman :)

---

### Post by dubstar92 on 2009-04-09
Well, I just downloaded the latest version off the ubuntu site, ubuntu 8.10, here is the link: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download). I used an ext3 file system. I just burned the image to a DVD and installed.

edit: I can't connect to the internet when in ubuntu, it works fine fine when I'm in vista, but my wireless network isn't showing up on the network manager. Any solutions for that?

---

### Post by Herman on 2009-04-09
ubuntu 8.10 eh?, okay, that's Intrepid Ibex.
Any bugs in Intrepid would have been sorted out by now, so this is likely just a freak, random occurence, but I'll make a note of it. Thank you for your information. 
> edit: I can't connect to the internet when in ubuntu, it works fine fine when I'm in vista, but my wireless network isn't showing up on the network manager. Any solutions for that?
Probably run,```
sudo lshw -C network
```To get find out what kind of wireless card you have and do a forum search for existing threads concerning your make and model of wireless cards that have already been solved, and even threads that have not yet been marked solved.
Take a look in 'Applications'-->'Add/Remove' and see if there are any special programs there you can install for your wireless card.
Also, go to the [Networking & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336") section of Ubuntu Web Forums and take a look around there.
If you can't find an answer, start a new thread and the experts there will probably be able to help you.

---

### Post by Herman on 2009-04-09
king2007,
If you're still there thank you for your patience.

According to the [Gnu Grub Manual]("http://www.gnu.org/software/grub/manual/grub.html"), GRUB Error 15 means, 
> 15 : File not found
This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK.So, you need to check your /boot/grub/menu.lst file and make sure the path and names for your kernel and initrd.img files are exactly correct.

Otherwise, if you are getting GRUB Error 15 when using Super Grub Disk, it could be that you are attempting to boot by using an option in Super Grub that uses the 'configfile' command. In that case, Super Grub Disk's GRUB will attempt to boot Ubuntu using Ubuntu's menu.lst file, which contains the uuid command, and as far as I know, Super Grub Disk isn't able to use that command yet, so you get Grub Error 15 from that.

If you find an option in Super Grub Disk that will boot Ubuntu directly, Super Grub Disk should instead be able to boot Ubuntu by the symlinks (shortcuts) to the kernel and initrd.img which are located in the root directory.

When you have Ubuntu up and running, you should check to make your /boot/grub/menu.lst file has the right path and name for your kernel and initrd.img file. ```
ls /boot/grub/
``````
gksudo gedit /boot/grub/menu.lst
```

---

### Post by HMCafe on 2009-04-09
Hello, Herman. I sent you a friend request.

---

