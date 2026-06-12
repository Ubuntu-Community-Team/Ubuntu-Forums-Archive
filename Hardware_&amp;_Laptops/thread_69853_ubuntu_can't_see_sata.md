---
title: "ubuntu can't see sata"
date: 2005-09-28
forum: Hardware &amp; Laptops
---

### Post by coltrane on 2005-09-28
I have an amd64 pc with 2x250gb sata II and 1x80gb IDE, with windows XP on one of the sata's and linux on the 80gb. I had a simular setup on my old pc which had all IDE's which worked fine but on the new pc, no chance. Ubuntu will install on the IDE drive but is totally blind to the sata's they are not even listed at the install, and the GRUB stage only lists the linux operating system. I assume ubuntu has no drivers for sata m/boards. Can anyone tell me how to get around this or if the latest version caters for it.
I'm no linux expert, still learning.:???:

---

### Post by floyd27 on 2005-09-28
Well im not sure but here is my impression..
The windows drive (ide or sata) have to be added to your fstab file....You can have them mount at boot its in the guide..
as for the driver question..
I have linux on a sata hdd and i didnt have to do anything special..It worked right off the bat so i know that ubuntu does have the proper drivers..

thats about all i know... :)

---

### Post by Biased turkey on 2005-09-28
I agree with Floyd27, the 2.6 Linux kernel has the proper sata drivers.
I have an AMD64 Elitegroup KN1 motherboard ( Nvidia Nforce4 chipset ) with the following configuration:
sata0 ( sda ) windows
sta1 ( sdb ) Ubuntu
hd0 ( hda ) Gentoo.
Ubuntu had no problem at all detecting both my windows and gentoo hard disks, and automtically included them in the Grub config file.

1) Check the BIOS config to be sure the sata controllers are enabled
2) try the command " sudo fdisk /dev/sda" to see if the 1st sata drive is detected . If that works, inside the fdisk program, use the "p" command to print the partitions table of that disk.

What motherboard do you have ?

---

### Post by brentoboy on 2005-09-28
I think sata is only "sort of" supported in linux.

My CD rom drive is the one on a sata connection, and ubuntu and suse were the only distros that could even launch the installer - becuase the sata driver just didnt cut it from the other distros.

I'm guessing that each sata chipset is going to get different milage from differnet distros.
Try getting live CD distros from a few alternatives, and see if any of them can see your drives.

I'd start with mepis, then knoppix and then suse. (after the ubuntu livecd of course)

if a livecd works, then try that distro's full install version. - or get a single ide drive and install to that, and use the others as data drives.

---

### Post by jhns on 2005-09-29
My problem differs a bit from yours, but maybe I should use this thread instead of a new one:
I have the 64-bit edition of Ubuntu 5.04 installed on a 30-gig IDE hard drive. I mounted my SATA hard drive (ntfs) to fstab, but I just can't browse it while logged in as a normal user. Root can browse it but cannot change the rights of it (I've tried it graphically and with "chmod"). All I get is a message saying the dirve is write protected. The situation doesn't change even if I mount it with options "gid=500,uid=500,umask=0555" or with "umask=0777".
I hope you get the picture and could help me... Thanks.

---

### Post by coltrane on 2005-09-29
Before I attempt another install, has anyone had any luck installing on an A8N-SLI Asus motherboard with Sata II drives? Thanks for the help so far. I've tried the knoppix live CD which detected the drives, with no problems. Suse and ubuntu 64bit will not see them nor will they list them at the install stage. I'm a bit woried about editing the fstab file to include the sata drives, incase something awful happens.
I've done this before but only for IDE drives. Floyd27 did you use the install cd or DVD, would this make a difference?
PS. jhns I hope I'm not insulting your intelligence, did you edit the fstab file with the 'rw' option?

---

### Post by Biased turkey on 2005-09-30
My drive is a SATA 1 so maybe that's why I don't have any problem
Do you have several drives mounted as a raid array ?

---

### Post by coltrane on 2005-10-01
I don't have my drives set as an array. I've just tried the ubuntu amd 64 DVD using the "live" option. It seems to be loading sata drivers, but when the OS has loaded, I still can't access anything for it just completly freezes.
Also the computer cannot reboot until I turn the power off then on.
I don't understand why ubuntu gives such grief yet knoppix even with an older kernel works spot on. Has anyone else had trouble installing the 64 bit version?

---

### Post by coltrane on 2005-10-02
The route of my problem turned out to be the AMD cool 'n' quiet feature of the board, when I dissabled it everything worked fine!
Linux goes bonkers with cool 'n' queit feature enabled, and will completely crash the system!

---

### Post by coltrane on 2005-10-04
Now I have the same problem as 'jhns' I can only browse the the sata drives as root. Nothing seems to be able to change it:confused: 
getting a bit fed-up with ubuntu seems to be one thing after another:mad: 
Linux for Human beings? maybe ones with a degree in computer science.:???: 
Please someone put me out of my misery.:???:

---

### Post by jaegers on 2005-10-04
Hi Guys,

@jhns: /dev/sdaX	/mnt/path	filesystem	noauto,users,ro,umask=0 1 0
should give you read-only access for all users. I prefer to test with read-only first, when it works, just edit the fstab again and make it noauto,users,rw,umask=0 1 0

@coltrane: haven't tried it with ubuntu, but sata drives work with the 2.6 kernel from Debian's 3.1 sarge network installation without me touching any setting, so an upgrade might solve your issue.

cheers - jaegers

---

### Post by coltrane on 2005-10-04
Thanks now I can read the sata drives as any user, But can't change the permisions to be able to write to the drives I entered the 'rw' in the fstab file and changed the permissons in the /dev/sdxx file, and rebooted but this makes no difference at all. It's not that I wanted to write data to the sata drives I only want to get the drive icons on the desktop but I cannot make any 'link' as it still says I have'nt permission.:???: how do I change this? 

This is one of the things that annoys me about ubuntu, I'm all for security but ubuntu does'nt even want the owner to do anything, it's more like 'linux for no human beings'.

---

