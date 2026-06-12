---
title: "Trying to Disk Partition but.................(VISTA)"
date: 2011-10-08
forum: Hardware
---

### Post by rez001 on 2011-10-08
WINDOW VISTA 32-BIT 
    hp Pavilion Entertainment PC dv3

i am having trouble splitting my hard drive to the space that i want. (Partition so i can dual-boot Linux Ubuntu)

when i right click my C: drive to see how much space i have and used up: 
 USED:76.3 GB
 FREE SPACE: 209 GB
with total capacity 285 GB


when i go to 
start>right click computer>manage>storage>disk management

and try to shrink my volume for C: the max i can go

total size before shrink in MB: 292784
size of available shrink space in MB: 14856
total size after shrink in MB: 277928

why is that?? is there anyway i can free up more space.
i tried disk cleanup and got back 11gb but it still didnt change size of shrink space

i am going to use wubi to install linux and i feel that 14gb might not be enough if i wanna go for say a 7gb install

BTW the only to things i have in disk management is
C: NTFS HEALTHY
RECOVERY (D:) 12.17 GB HEALTHY NTFS

---

### Post by Basher101 on 2011-10-08
This is because Windows writes data all over your hard drive, even faaaaaaaaaaaaaaaaar at the end. To get your data pieces a bit more compromised and in one place you must defrag your hard drive. The maximum i can shrink is 50% from my whole drive, even after defrag (i think thats a maximum setting in windows). Thats why i did all my partitiong for my real ubuntu install witht he Live CD and Gparted. Since you only want to try it out, and you make it a WUBI install, there wont be any need to partition anything. WUBI creates a virtual partition within your windows, it installs like a **_normal_** program, only that you get a choice at boot to boot into it. Same goes for an uninstall, you can get rid of it like any other normal program with the system settings -> Software -> choosing your program -> uninstall

---

### Post by rez001 on 2011-10-08
so in other words, its safe to install linux on my C: using wubi and it wont delete my original Windows Vista OS so i can dual boot whenever?

and if i ever decide to delete it (linux) it wont affect my Hard-drive (or OS) at all?

and does installation size really matter?


sorry for all the questions im just curious and want to use linux :)

:P

---

### Post by Basher101 on 2011-10-08
> so in other words, its safe to install linux on my C: using wubi and it wont delete my original Windows Vista OS so i can dual boot whenever?
yes.
> and if i ever decide to delete it (linux) it wont affect my Hard-drive (or OS) at all?
yes.
> and does installation size really matter?
well a fresh install of Ubuntu takes up 3,6 GB (without updates and programs you install). So i would recommend giving it a minimum of 6 GB if you only want to try it or even more (depending on what you want to do with it...). Also, if you wish to install ubuntu for real, do not take hasty steps, be careful then and look up tutorials on this forum on how to do it. I did this mistake on my first install and wiped my Windows 7....

---

### Post by rez001 on 2011-10-08
from the looks of it, i will probably give it 14 gb and see where that goes

but when you say live CD... whats the difference?

i thought that Wubi and live CD both install linux on your computer plus can dual boot?

---

### Post by Basher101 on 2011-10-08
WUBI is only for the virtual partition, thus this is only an alternative, in other words "pre-mature" install. It does dualboot, but it uses the Windows Bootloader and partition. So when your Windows gets screwed, so does your WUBI install. As for the real install, you will then assign actual physical hard drive space to Ubuntu, as it needs a different Filesystem - ext4 Journaling system. After you made a real install, you will also get GRUB ([COLOR="Red"]GR[/COLOR]and [COLOR="red"]U[/COLOR]nified [COLOR="red"]B[/COLOR]ootloader)installed as your Bootloader, because Windows' Bootloader won't see your Ubuntu install. So after you have installed it and your Windows should get screwed you can revert to Ubuntu and keep working with that. Also take to note that when you reinstall Windows it will overwrite your GRUB and you will have to restore it with the Live CD (there are good guides here on the forums, and it is really easy to do). If you have any remaining questions, feel free to ask.

---

### Post by rez001 on 2011-10-08
Thank you for being so helpful..i really appreciate it. I don't like being a newbie but i guess everyone starts somewhere :) 

i do have a question(s) when you say 

As for the real install, you will then assign actual physical hard drive  space to Ubuntu, as it needs a different Filesystem - ext4 Journaling  system

do you mean the partitioning of the harddrive space?

and since wubi is like a pre-mature install... when i do decide to do the full installation do i just delete ubuntu on the windows side... do the partitioning and then Live CD on that particular partition and then download GRUB before or after?

---

### Post by Basher101 on 2011-10-08
> and since wubi is like a pre-mature install... when i do decide to do the full installation do i just delete ubuntu on the windows side... do the partitioning and then Live CD on that particular partition and then download GRUB before or after?
You do not need to download GRUB it gets installed together with Ubuntu. 

And you will not need to delete the WUBI install as there are ways to port it to a partition, but i do recommend for a newbie like you making a new fresh install. It wont take long to get your programs and settings in Ubuntu. Last time i wiped my whole drive (3 monts ago), it took me 50 minutes to install all updates,programs and configuring themes, settings etc in Ubuntu...in Windows it took me 3+ hours...

> do you mean the partitioning of the harddrive space?
yes you will have to partition your harddrive


edit:a small note when you decide to make a real install...when you use the partitioning tool, you will see your hard drive space in the Binary system (thus 1 GB = 1024*1024*1024 bytes). When inside the **_installer_** when you have to assign the mount points for your [COLOR="Red"]/[/COLOR] (root), it will display the partitions in the "actual" size (this 1 GB = 1000*1000*1000 bytes). this is why you will always have a little less memory on a hard drive (example: you have a 640 GB hard drive. the 640 GB are calculated in the 1000*1000*1000 bytes way. Inside Windows or Ubuntu the space gets calculated as 1024*1024*1024 bytes so in the end from those 640 GB you only have 598 GB to use).

---

### Post by rez001 on 2011-10-08
Basher101 your a lifesaver :)

i was recommended to use a 3rd party software to partition my harddrive like 

gparted disk

it gives me more freedom to partition and reduce my own windows partition. 

but i will go ahead and start the wubi installer.... excited to see Linux

and what is ext4 Journaling system?

---

### Post by Basher101 on 2011-10-08
> and what is ext4 Journaling system?
it is the filesystem Ubuntu uses (and alot of other distros too). It has some features but what i like the MOST, is that you wont ever ever EVER have to defrag it. E-V-E-R. Windows uses the NTFS ([COLOR="Red"]N[/COLOR]ew [COLOR="red"]T[/COLOR]able [COLOR="red"]F[/COLOR]ile [COLOR="Red"]S[/COLOR]ystem) filesystem as default. There are also filesystems on smaller USB sticks and SD cards, such as FAT 32 ([COLOR="red"]F[/COLOR]ile [COLOR="red"]A[/COLOR]llocation [COLOR="red"]T[/COLOR]able). The FAT 32 filesystem has a big disadvantage when used for storage media that has more space than 4 GB, because FAT 32 can only hold files that are smaller than 4 GB (so on a 4 GB stick you can still use FAT 32 without any thoughts, but on a 8 GB stick you wont be able to store files bigger than 4 GB).


You should take another look on my previous post as i edited it, if you havent noticed.

---

### Post by rez001 on 2011-10-08
so when i start to partiton does it automatically change to ext4 Journaling system or do i have to manually change it once i finish partition?

---

### Post by Basher101 on 2011-10-08
> so when i start to partiton does it automatically change to ext4 Journaling system or do i have to manually change it once i finish partition?
how can you "start" a partition? you can only start an Operating System on a partition. The easiest way to make a real install is to free up ~33% of your hard drive and then choosing the "Install Ubuntu next to Windows" option. If you want the most accurate install (with a partition of 15GB for an example) you will have to manually partition it and manually set the Mount points and the location of where the Bootloader is to be installed.

---

### Post by TLARbb on 2011-10-08
I want to jump in here because I am at the same point.  I used a drive copy/clone my existing 80GB disk on a new 160GB hard drive.  I now  have about 70+ GB in a primary partition containing my windows xp system and about an equal amount in free unpartitioned space on the hard drive.  Should I use GParted to format the free space?  How many partitions do I need and what size should they be?  
 
Does the install from the Live CD take care of this partitioning task or do I need to do it before the install?
 
It is not really my intention to hijack this thread as I felt that we both might benefit from the discussion.  If I am taking this thread in a direction the OP did not intend or does not want, I will gladly delete this post and start a new thread.
 
Ed J

---

### Post by KurtCho on 2011-10-08
after inserting the CD you can click manual configuration and choose how you want your disk. You do not need to use gparted but you can although it is not necessary however it does have some helpful tools. you can just format the free space from there

---

