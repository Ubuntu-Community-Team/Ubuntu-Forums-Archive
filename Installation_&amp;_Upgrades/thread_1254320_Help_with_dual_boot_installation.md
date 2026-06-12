---
title: "Help with dual boot installation"
date: 2009-08-31
forum: Installation &amp; Upgrades
---

### Post by TheDrunkenClam on 2009-08-31
Hi Everyone! :)

I'll start with saying i'm a complete noob Linux/Ubuntu-wise, but I have great experience in Windows :P. So when you explain this too me, please have in mind that I dont know the Ubunto-system :)

Okey to the problem :D

I would like to have a dual boot with Vista x64 and Ubuntu x64. Right now I have a Vista x64 and a Xp x32 dual boot.
I have a 250Gb harddrive with three partitions. One with Xp, one with Vista, and the last with all my files.

So whats the problem you ask? Well my XP is the primary partition, or atleast I think. That was the first I installed anyway. So is there a way to delete the XP-partition and install Ubuntu on it, without touching the vista-partition?
Or is the only solution to do a complete re-install of both vista and Ubuntu?

And another thing, I tried to do this my self, just a hour ago. And this happend:
I started the computer with Ubuntu cd in it. Everything went like a charm untill the "disk management setup"-part came up (think it was step 5 or so). It said something with "no root file" or something like that. So I thought it just couldn't format the C: drive.
So i started the computer with Gparted. And tried to format the C:
When that was ready and restarted the computer it said "bootmgr is missing" or something and i got really scared I had frakked the whole computer.
Now i have repaired the Vista part, and vista is running fine. But im too afraid to try again :P. So please help me :3


Oh and one more thing, when I tried to look up a solution here i came across the term "/".. What does that mean?

Best Regards, Tobias

---

### Post by mechdave on 2009-08-31
Tobias,
The / means root filesystem which is conceptually similar to C:\
All you have to do is to install Ubuntu on the first partition of the first hard drive (where XP used to live). Look and read [https://help.ubuntu.com/community/Installation]("https://help.ubuntu.com/community/Installation") first. The section you are interested in is Standard Installation.

Take your time, if you can take an image of Vista just in case it all goes pear shaped. Be prepared to re install on a regular basis until you get to know Ubuntu, mistakes do happen with learning a new OS. And most of all have fun :) We are here if you need more help. Also try irc.freenode.net #ubuntu for help straight away :)

---

### Post by TheDrunkenClam on 2009-08-31
Thank you for the quick reply!

Okey, i'll try again. But just one last qustion. Do I need to have a "/", "/home" and a "swap" partition? I currently have 30Gb on the "C:\", how should i divide that then?

Thanks again!

---

### Post by hal10000 on 2009-08-31
You need a root-partition ( / ) and it's a great benefit if you have a swap partition of about 1-2 GB size. You may have a /home partition where you can save all your user files and directories, but it's not mandatory.

Have fun.

---

### Post by TheDrunkenClam on 2009-08-31
> **hal10000 said:**
> You need a root-partition ( / ) and it's a great benefit if you have a swap partition of about 1-2 GB size. You may have a /home partition where you can save all your user files and directories, but it's not mandatory.

Have fun.


Oh, okey :D

Then i'll just get a "/" partition and a swap partition. I already have an partion (E) where all my current files are on :)

Thank you ^^

---

### Post by rrplay on 2009-08-31
TheDrunkenClam wrote
> Okey, i'll try again. But just one last qustion. Do I need to have a "/", "/home" and a "swap" partition? I currently have 30Gb on the "C:\", how should i divide that then?

Look at this guide as well for installing Ubuntu after windows 
[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

Note see the section on manual partitioning 12GB for /
2GB for swap and the rest available space for /home {if you want to have your user dir /home  sepaerate.

since you already mentioned > I have a 250Gb harddrive with three partitions. One with Xp, one with Vista, and the last with all my files.

you could just as easily have a / [available space ] and a 2GB swap
 
 Be sure to check out the info for the Master Boot Record and Boot Manager and rock that Ubuntu install.

---

### Post by TheDrunkenClam on 2009-08-31
> **rrplay said:**
> TheDrunkenClam wrote


Look at this guide as well for installing Ubuntu after windows 
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Note see the section on manual partitioning 12GB for /
2GB for swap and the rest available space for /home {if you want to have your user dir /home  sepaerate.

since you already mentioned 

you could just as easily have a / [available space ] and a 2GB swap
 
 Be sure to check out the info for the Master Boot Record and Boot Manager and rock that Ubuntu install.



Oh crap :(

I tried again and now vista is gone too xD. So now i want to do this the right way. 

I will install Vista first then ubuntu. But how should i setup my partitions, which ones should be primary, and wihich ones should me logical?

I wont touch my partrtion with files on it. Otherwise i want a partition with vista, one with ubuntu (and a extra for ubuntu swap).

---

### Post by hal10000 on 2009-08-31
I don't think that Vista is gone, it just might be the partition table, which is gone, but that's not as worse as you might think, we can setup the grub boot-manager to get Vista work again.

---

### Post by TheDrunkenClam on 2009-08-31
> **hal10000 said:**
> I don't think that Vista is gone, it just might be the partition table, which is gone, but that's not as worse as you might think, we can setup the grub boot-manager to get Vista work again.

We can? :D
How should i do then? :)
Should i try again to install Ubuntu?

---

### Post by hal10000 on 2009-08-31
First  need to know exactly how your harddisk(s) look like.
Open a terminal window and put in the following command: [COLOR="Red"]sudo fdisk -l[/COLOR]. You will be asked for your user password. Then post the output of the command here. (You can mark the whole output with your mouse and paste into the forum-editor with the middle mouse button).

Maybe we also need the output of this command: [COLOR="Red"]blkid[/COLOR]

Last, we also need the output of [COLOR="Red"]cat /boot/grub/menu.lst[/COLOR].

Post the outputs here and then we will see what else to do.

Good luck.

---

### Post by TheDrunkenClam on 2009-08-31
Hi!
Finally i got a cd that worked and everything :P. So ubuntu is running good.

I accedently installed it in Swedish (Im a sweed so its okey for me :P), but that means that this will be in swedish, but maybe you know what too look for anyway ^^
And if you don't just ask :)

This is what i got anyhow:



tobias@Monster:~$ sudo fdisk -1
[sudo] password for tobias: 
Sorry, try again.
[sudo] password for tobias: 
fdisk: ogiltig flagga -- 1

Användning: fdisk [-b SSZ] [-u] DISK     Ändra partitionstabell
            fdisk -l [-b SSZ] [-u] DISK  Lista partitionstabell(er)
            fdisk -s PARTITION           Visa partitionsstorlek(ar) i block
            fdisk -v                     Visa fdisks versionsnummer
DISK är någonting liknande /dev/hdb eller /dev/sda
och PARTITION är någonting liknande /dev/hda7
-u: visa början och slut i sektorer (istället för cylindrar)
-b 2048: (för vissa MO-enheter) använd 2048-bytessektorer
tobias@Monster:~$ blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="ebc006b7-2d66-4a54-b4ea-da465d166508" TYPE="swap" 
/dev/sda3: UUID="60f61771-ed14-4e85-81c1-14a1fb4949f0" TYPE="ext3" 
/dev/sda5: UUID="687CF0CB7CF094D2" LABEL="VISTA" TYPE="ntfs" 
/dev/sda6: UUID="9A6828076827E12D" TYPE="ntfs" 
tobias@Monster:~$ cat /boot/grub/menu.1st
cat: /boot/grub/menu.1st: Filen eller katalogen finns inte
tobias@Monster:~$ cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=60f61771-ed14-4e85-81c1-14a1fb4949f0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=60f61771-ed14-4e85-81c1-14a1fb4949f0

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        60f61771-ed14-4e85-81c1-14a1fb4949f0
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=60f61771-ed14-4e85-81c1-14a1fb4949f0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        60f61771-ed14-4e85-81c1-14a1fb4949f0
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=60f61771-ed14-4e85-81c1-14a1fb4949f0 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        60f61771-ed14-4e85-81c1-14a1fb4949f0
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=60f61771-ed14-4e85-81c1-14a1fb4949f0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        60f61771-ed14-4e85-81c1-14a1fb4949f0
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=60f61771-ed14-4e85-81c1-14a1fb4949f0 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        60f61771-ed14-4e85-81c1-14a1fb4949f0
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by sh1tin-a-brick on 2009-08-31
Basically I need help, and I'm not a genius with computers so nice and simple is the way to go! :lolflag:

I downloaded and installed the latest version of Wubi. It took a few hours to install and then I created my username, password etc. It then prompted me to reboot. I did so but no option to go into Ubuntu came up. I logged into Windows and rebooted again. I tried pressing F12 to get the booting options up but it didn't help. I tried accessing wubi.exe from My Computer however this just asks my if I want to uninstall Wubi. I'm stumped as I have never attempted dual booting before. Help is greatly appreciated! Oh, btw, I'm running Windows XP on a laptop.

---

### Post by hal10000 on 2009-08-31
@TheDrunkenClam

In the command [COLOR="Red"]sudo fdisk -l[/COLOR] th -l is a lower case l, not the number one.

But I guess your Vista system relies in [COLOR="Red"]/dev/sda5[/COLOR].
Now we have to change the /boot/grub/menu.lst file to get an entry for booting Vista:

First, open the file from a terminal window with the command sudo gedit /boot/grub/menu.lst

Then, go to the end of the file make the following entries (Take in mind that you need to write it exactly as stated here, including spaces etc.):

> 
#this was added manually by TheDrunkenClam
title           Windows Vista/Longhorn (loader)
root            (hd0,2)
savedefault
makeactive
chainloader     +1

In the line chainloader +1 this is a one.
Save the file, reboot and see what happens.

---

### Post by TheDrunkenClam on 2009-08-31
Okey, I did what you told me. And it added the "vista"-thing in the boot-menu (by pressing "Esc" in the start). But i cant acces Vista when i try to take that option. It sais there is some sort of error and then "press any key..." and when I do, POOF I'm back at the boot-menu :/


And if I do the comando right it shows this:


Disk /dev/sda: 250,0 GB, 250059350016 byte
255 huvuden, 63 sektorer/spår, 30401 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0xf342e91c

    Enhet Start     Början        Slut     Block    Id  System
/dev/sda1               1        1094     8787523+  82  Linux växling / Solaris
/dev/sda2            3825       30400   213471720    f  W95 Utökad (LBA)
Partition 2 slutar inte på cylindergräns.
/dev/sda3   *        1095        3824    21928725   83  Linux
/dev/sda5            3825        9350    44387563+   7  HPFS/NTFS
/dev/sda6            9351       30400   169084093+   7  HPFS/NTFS

Posterna i partitionstabellen är inte i diskordning


Is that any help?

---

### Post by rrplay on 2009-08-31
@TheDrunkenClam

You mentioned that fdisk -l shows Vista at /dev/sda5 ?

Note that for GRUB, partitions start at 0 and not 1. for example 0=Partition 1, 1=Partition 2 and so on. so you would be (hd0,4) in grub.


> #this was added manually by TheDrunkenClam
title Windows Vista/Longhorn (loader)
root (hd0,4)
savedefault
makeactive
chainloader +1 

if you want a bit more time [10 seconds] at the boot menu and do no want to press the ESC key every time do this in /grub/menu.lst

> ## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

I think that you already have mentioned that sda6 was you data on ntfs partition?

---

### Post by hal10000 on 2009-08-31
@TheDrunkenClam

OK., now that we have the partition table from the fdisk command we can see that is a little bit confusing.

I would try to change in your /boot/grub/menu.lst file the line
> root (hd0,2)
into
> root (hd0,3)
and if this doesn' do it, change to
> root (hd0,4)

---

### Post by TheDrunkenClam on 2009-09-01
Oky so i've tried to do this now and tested disk 3-5 and im only getting errors..

@ Hdd3 im getting "Error 22: No such partition"
@ Hdd 4 & 5 im getting "Error 12: Invalid device requested"


And yes, i think Vista's on /dev/sda5 :)

---

### Post by hal10000 on 2009-09-01
the last idea i have is to try it with 
> root (hd0,1)

---

### Post by TheDrunkenClam on 2009-09-01
> **hal10000 said:**
> the last idea i have is to try it with


Nope :(
Error 12. Okey, so any new ideas? Or how should i reinstall/install vista now? Do i have to install vista and then reinstall Ubuntu?

---

### Post by rrplay on 2009-09-01
@TheDrunkenClam wrote > And yes, i think Vista's on /dev/sda5

so in grub that would def be (hd0,4)

EXAMPLE
(hd0,0) = first disk, first partition
(hd0,1) = first disk, second partition   etc
This is important, Grub uses its own unique naming convention 

look here:[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

Boot into the live Ubuntu cd.
When you get to the desktop open a terminal and enter.
```
sudo grub
```
This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands
```
find /boot/grub/stage1
```
This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)
```
root (hd?,?)
```
Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Finally exit the grub shell

```
quit
```

That is it. Grub will be installed to the mbr.
When you reboot, you will have the grub menu at startup.

Read the explanation on that page.
 If you still have problems post back any errors and your /boot/grub/menu.lst in pastebin if possible.

If you just want to reinstall vista or both there are many guides available for you to follow ...Google is your friend too

---

### Post by TheDrunkenClam on 2009-09-02
Thanks rrplay for your try but this didn't work :/

First of all i only get the "hdd 0,2" and nothing else in the find-command. And when i did the guide with that partition nothing new happend on the vista part.


But could it be that vista was installed on a logical partition after xp was installed on the primary? Or should that not matter?

---

### Post by hal10000 on 2009-09-02
If vista is on /dev/sda5, then it's a logical partition. But as far as i know Vista can start from a logical partition.

---

### Post by TheDrunkenClam on 2009-09-02
Hmm okey :/
Strange. Oh well. Thanks for all the help guys! Really :)

But I think I'm gonna give up this nut and just crack it with a sledge (in other words, reinstall it :P, hehe)

---

### Post by rrplay on 2009-09-02
TheDrunkenClam wrote> 
But I think I'm gonna give up this nut and just crack it with a sledge (in other words, reinstall it

well at least you'll have  a fresh install of both and enough info in case you need to redo grub just take your time and select a good partitioning scheme   good luck

---

### Post by TheDrunkenClam on 2009-09-02
> **rrplay said:**
> TheDrunkenClam wrote

well at least you'll have  a fresh install of both and enough info in case you need to redo grub just take your time and select a good partitioning scheme   good luck


Yeah :). It's always nice to have a fresh install ^^. I just wished it was planned XD. But hey! You can&#836;'t have everything in life :P.

Thanks for all the help Everybody!
Now i will fire up that Vista disc ^^

---

### Post by TheDrunkenClam on 2009-09-02
> **hal10000 said:**
> If vista is on /dev/sda5, then it's a logical partition. But as far as i know Vista can start from a logical partition.


Okey everyone, ofcourse i can't reinstall vista now... Please help before i punch my computer XD

Okey so this is the problem: When i'm in the vista installer and select the partition i want vista on (the same i had vista on before) it sais 
"Windows is unable to find a system volume that meets its criteria for installation"

I have tried for 5 hours to get it working and I really have no idea what to do..

I will try to explain exactly how i did it too see if that helps you understand the problem.
First i booted into vista installer, then i formated the disk. When that didnt work I went into GParted and did the same thing. No better results. So i tried to boot onto vista installer, get into vistas command-thing, went into "diskpart" selected the partition i wanted vista on and tried to make it "active", but that didnt work (i tried to look that up, and apparently you cant make a logical partition active or something..) so no luck there. And the most recent thing i did was to boot into gparted and "flaged" that partition to "boot".. No luck..

So if you have any possible solution, please try too help me.

---

### Post by TheDrunkenClam on 2009-09-02
Oh great.. Now i can't even boot into Ubuntu.. When i start my computer it just sais:


"Veryfing DMI Pool Data............
Boot from CD:
GRUB Loading stage 1.5.



GRUB Loading, please wait...
Error 17"


Please, anyone that can help either with the vista problem or this new one, it would be GREATLY appreciated!

Cheers, TheDrunkenClam

---

### Post by TheDrunkenClam on 2009-09-03
Bumping.. I really need your help guys :(

---

### Post by hal10000 on 2009-09-03
If it's possible for you to save all your data-files, then it would be the best idea to backup your data and then **completly ** erase **all **your partitions.

You can then begin to install vista again, then boot your ubuntu live-cd, shrink your Vista-Partition and go on installing ubuntu.
Alternatively, if you are familiar with partitioning, before you reinstall Vista you could create new partitions (with partition manager from your ubuntu live-cd):
1.) one ntfs partition (primary) for your vista system
2.) an extended partition (the whole rest of your harddrive)
3.) a swap partition (logical), 1-2 GB
4.) an ext3 partition (logical) for your ubuntu system (~20 GB)
5.) an ntfs partition (logical) for your Vista document-files
6.) only if you like a fat32 partition (logical) for sharing files between Vista and ubuntu
7.) the remainder of your harddrive space ext3 (logical) for your /home partition

Take in mind that you have to first install Vista and then ubuntu.
When installing ubuntu, be sure to install grub into the **mbr of your harddrive**, this is /dev/sda resp. (hd0).

Your Vista boot-entry will then be automatically transfered to your grub boot menu.

---

### Post by rrplay on 2009-09-03
TheDrunkenClam --- you now have a positive and efective solution.

just follow hal 10000 prev post #29

&& let us know how this all workd out for you.

---

### Post by TheDrunkenClam on 2009-09-03
Thanks guys! :D
I will get a new harddisk tommorow (500Gb :) ) and i will do this and post back if it works :)

My thought was to back-up everything to my 500 Gb HDD, then use my 250Gb HDD to install Vista, then Ubuntu and then use the remaining space for files :D

Just some questions about your partitioning, what is the difference between 2, 5 & 7?
And do i need to have a fat32 partition to share files amongst Ubuntu & vista? :O
I thought my Ubuntu would be able to read from an ntfs partition?

---

### Post by hal10000 on 2009-09-03
ubuntu can read and (with some retrictions) write ntfs partitions, but write support is better on a fat partition.

if you have a fat32 partition you coukd easily e.g. create an Excel document with MS Excel, anf if you save it to a fat32 partition and then edit it under ubuntu with openoffice
Have fun and good luck

---

### Post by TheDrunkenClam on 2009-09-03
Oh! Cool :D

Then i will follow your advice and setup my HDD very similair to your idea!

I will have on HDD 1 (250Gb):
1) Partition for Vista - 40Gb
2) Partition for Ubuntu - 20Gb
3) Swap - 6Gb (I have 6Gb RAM :P )
4) /Home for Ubuntu - 100Gb
5) Fat32 partition for the rest, too store things that I want to us on both OS:s

And then make one big *** partition on the HDD 2 (the new 500Gb) to have all my games and programs for Vista and for back-up ^^

And as i said before, THANK YOU FOR ALL THE HELP! I really can't express my graditude :)
I will post back if this works :D. (... Or if it dont XD. But it should :)

---

### Post by hal10000 on 2009-09-03
you will not need 6 GB swap, unless your machine is used for special needs, e.g. as a webserver with heavy load or something like this.

---

### Post by TheDrunkenClam on 2009-09-03
> **hal10000 said:**
> you will not need 6 GB swap, unless your machine is used for special needs, e.g. as a webserver with heavy load or something like this.


Oh :O. Okey :)
I'll only mak it 2 then ^^. Thanks :D

---

### Post by bedes on 2009-09-03
have to tried to re-install Ubuntu yet?   Can you boot Ubuntu off the live CD?  You may have to go into the BIOS and change the boot order to the CD drive first.

Im thinking that will be the easiest solution.

I had the same error 17 issue as you and re-installing the linux side OS was the solution.

---

### Post by TheDrunkenClam on 2009-09-06
Hello everyone!

Now it all works. I have the setup I wrote about earlier and it works like a charm, plus I have my new 500Gb harddrive just waiting to be filled with files XD

Thank you very much everyone! Every little help has been great :D

Now I'm gonna install every program I've got (again) =P

Cheers! TheDrunkenClam

---

