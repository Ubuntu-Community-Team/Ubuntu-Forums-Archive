---
title: "Help installing dual boot"
date: 2005-12-28
forum: Installation &amp; Upgrades
---

### Post by mitdxiw on 2005-12-28
Hi, I have an IBM Thinkpad laptop on Windows XP. I've tried your live CD and I really love it, and I'd like to install a dual boot of Ubuntu with my Windows XP. However, I do not want to lose any data or damage my windows xp install at all. Can I just pop in the Ubuntu CD, lower my partition size for windows and make a new partition installing ubuntu, or do i have to lose everything?

---

### Post by noeluylee on 2005-12-28
Hi, I dual boot partition my Dell Inspiron 700m with Windows Xp and Ubuntu Breezy 5.10. 

Install the windows xp first and be sure to have another free partition for ubuntu. let say if you have 60gb of hard disk, make 20gb for windows and create another empty partition (40gb) for ubuntu. you can use PartitionMagic to do the job for you. once you're ready and you have a empty partition for ubuntu, insert the ubuntu installation disk and reboot your computer. it should start on installing the ubuntu, just continue until you reach the partition part, WARNING! DO NOT USE AUTO PARTITION, use the MANUAL partition, and choose the volume that you've been created for ubutun, now you can do auto partition after choosing which volume or partition you want to assign to ubuntu, thru this your windows xp partition will not be touch. use GRUB :) just follow all instruction and you should be good...

PS -- Be sure to backup everything before doing the partition on windows, no one can tell what will happen. 

Hope this will help you.

Good luck. :)

---

### Post by mitdxiw on 2005-12-28
thats the issue though.. I already have windows xp installed from the factory and it has been used for over a year.. I want to add linux without touchign any of my windows stuff.. i have 40gb of free space on the windwos partition, is there any way i can steal form that?

---

### Post by darfel on 2005-12-28
just use a program like partition magic to create a new partition from the 40gb free space you have. Then use the new partition to install ubuntu.

---

### Post by noeluylee on 2005-12-28
Yup, just use partition magic software, its a pretty stable software. but before doing so, PLEASE BACKUP YOUR IMPORATNT DATA - no one know what will happen. In any case that its messes up your windows xp, at least you have backed up your data and you can always restor to factory default :)

Good luck.

---

### Post by DrUnKeN_TiGeR on 2006-02-26
i have successfully done this i am dual booting ubuntu and win xp i just cant find how to exit the grub boot manager so that it doesnt automatically boot into ubuntu. i want the system to automatically boot into windows. i have looked on the forum searched every possible phrase i could think of im sure it has been posted i just cant find it any help would be appriciated thanks in advance

---

### Post by GizzardBoy on 2006-02-26
I am facing similar problems on two different computers:
1) laptop with XP and FC2 booting from Symantec's bootmanager on a single 60 GB HDD.
Should be simpler, right?  I'm just replacing FC2 with UBB.  However, when I tried, neither partition would boot.  Used Symantec's tool to restore XP booting, but UBB only boots command line- go figure.  At this point, I'm for imaging the XP partitionand wiping the whole HDD and booting both from grub, but am not confident enough to proceed & risk late night computer troubleshooting on top of everything else I must do.

2) Desktop computer with 2 HDD's.  Master= 80 GB for new OS's including UBB & slave= 40 GB all OS/2. Empty partition set aside for UBB which is also listed in IBM's Boot manager.  Basically I don't want to repeat the nightmare already seen on the laptop, but would love to get UBB installed if I knew it wouldn'twipe out this computer.

I have UBB installed on a third computer that is so underpowered that I could dedicate the entire HDD for the one OS and so I know I'd like to switch, but I really need the other OS's (XP & OS/2) for at least a few months to transition.

Thanks in advance for any advice on how to proceed.  I've read multiple posts & how-to's on the subject, but they all end up with booting from grub from HDD or floppy.  If I can safely replace Symantec's & IBM's boot managers & still boot the legacy OS's then that's fine.

Many thanks,

GB

---

### Post by peppermint on 2006-02-26
[QUOTE=DrUnKeN_TiGeR]i have successfully done this i am dual booting ubuntu and win xp i just cant find how to exit the grub boot manager so that it doesnt automatically boot into ubuntu. i want the system to automatically boot into windows. i have looked on the forum searched every possible phrase i could think of im sure it has been posted i just cant find it any help would be appriciated thanks in advance[/QUOTE]

This should do it. It works on my system.

You might want to make a backup of the menu.lst file before you begin
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.bkup

```

Open the menu.lst file with a text editor.
```

sudo gedit /boot/grub/menu.lst

```

Near the bottom of the file that opens is a section that should look similar to this
```

# This entry automatically added by Debian installer for non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

Move that section so its above the line
```

### BEGIN AUTOMAGIC KERNELS LIST

```

This should make the Windows option the first in the list. This will make windows boot unless you intervene.

---

### Post by DrUnKeN_TiGeR on 2006-02-27
thanks so much

---

