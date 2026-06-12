---
title: "[SOLVED] grub - Format of install_device not recognized"
date: 2008-09-27
forum: General Help
---

### Post by zzzzz1 on 2008-09-27
Hi Guys,

Have trouble setting up grub and would appreciate some help.

i tried: sudo grub-install --root-directory=/mnt/root/ dev/sda4

and get: Probing devices to guess BIOS drives. This may take a long time.
Format of install_device not recognized.

below is the complete output including the mnt commands and fdisk -l

thanks a lot in advance


[PHP]...

[/PHP].

---

### Post by zzzzz1 on 2008-09-27
I tried again after a reboot and this time get a different error:

---

### Post by zzzzz1 on 2008-09-27
id be grateful for any suggestion....

---

### Post by zzzzz1 on 2008-09-27
i have now my other drives connected

i get the following output , but still grub error 22 @ reboot


[PHP]root@ubuntu:~# sudo grub-install --root-directory=/mnt/root /dev/sdc4
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /mnt/root/boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/mnt/root/boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /mnt/root/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc[/PHP]

---

### Post by semitone36 on 2008-09-27
Grub error 22 usually means that one of your partitions was deleted.  What was your original problem with Grub?

---

### Post by zzzzz1 on 2008-09-27
well, i tried to change the grub theme and screwed this up
I was than able to get grub back on sda2 or 3 (cant remember)
where i had an old hardy alpha install but grub would list only all those old kernels + some kernels from an old gutsy install on another drive
so i deleted the hardy alpha partition 
I though I could just reinstall grub on sda4 (now sdc4 with my other 2 drives connected) which is now my main OS , but I seem to miss something out.

---

### Post by semitone36 on 2008-09-27
This is a bit above my level, Ive never experimented with using multiple drives before.  Might I suggest moving this thread to the installation and upgrades forum? you might get more help there.

---

### Post by zzzzz1 on 2008-09-28
should I try sudo grub-install --root-directory=/mnt/root /dev/sdc on a different partition?

---

### Post by caljohnsmith on 2008-09-28
When you use the grub-install command like so:
```
sudo grub-install --root-directory=/mnt/root/ dev/sda4
```
You are telling Grub to install to the boot sector of partition sda4, and then point Grub to whatever is mounted on /mnt/root for Grub's system files. I assume though that you are trying to install Grub to the MBR (master boot record). If you all ready have Grub installed in partition sda4, and want to install Grub to the MBR, you can just do this:
```
sudo grub
grub> root (hd0,3)
grub> setup (hd0)
```
But do you have more than one HDD? It doesn't seem like you posted the full output of "sudo fdisk -l", based on other evidence you gave. If you do have more than one HDD, please post the full output of:
```
sudo fdisk -l
```

---

### Post by zzzzz1 on 2008-09-28
in case it helps to shed some light on the issue I have, ive been following this thread:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by unutbu on 2008-09-28
zzzzz1, let's try the following:

First, follow the instructions here: [http://ubuntuforums.org/showpost.php?p=1308395&postcount=1](http://ubuntuforums.org/showpost.php?p=1308395&postcount=1)
Copy the terminal output to a file so you can post it here if necessary.

This may be enough to solve your problem, but if it does not work,
post the output here and then do the following:

Reboot from the LiveCD. 
Run

```
sudo mount -t reiserfs /dev/sda4 /mnt
ls -l /mnt
ls -l /mnt/boot
ls -l /mnt/boot/grub

```
Please post this output as well

---

### Post by zzzzz1 on 2008-09-28
here is my fdisk -l output ( in the first post only one drive was connected, ive got 4 in total, right now 3 are connected )

[PHP]...
[/PHP]

---

### Post by caljohnsmith on 2008-09-28
OK, so which HDD are you booting off of on start up?

---

### Post by zzzzz1 on 2008-09-28
[PHP]...
[/PHP]

---

### Post by zzzzz1 on 2008-09-28
ok 

just rebooted and now i am @         [PHP] [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub>[/PHP]

the output:

[PHP]find /boot/grub/stage1

(hd0,3)
(hd1,1)
[/PHP]

dont get this as I have 3 drives connected 

[PHP]root (hd0,3)
setup (hd0)

checking if ....
checking if....

etc etc [/PHP]

and in the midle of the screen it says.
[PHP]
Bootsector Write!!
VIRUS: Continue (Y/N)?[/PHP]

i press Y

it says

[PHP] running "install /boot/grub/stage1 (hd0) (hd0)1+19 p (hd0,3)/boot/grub/stage2/boot/grub/menu.lst" ... succeeded
Done.[/PHP]

when i reboot iam @ the same screen again (top of this reply)

---

### Post by zzzzz1 on 2008-09-28
ive tried the other partions,
the only other one it will lett me do it is (hd1,1)
but the result is exactly the same

---

### Post by caljohnsmith on 2008-09-28
Since you ran those Grub commands using (hd0,3), that could only work for your sdc drive, so sdc must be first in the boot order I think. Have you checked your BIOS to make sure? 

I suspect that since sdc is a 320 GB drive, and your Linux partition sdc4 starts at ~190 GB, it may be out of range of your BIOS since many BIOSes can't "see" past 137 GB. I would shrink your first NTFS partition from its beginning by about ~10 MB, and create a small ~10 MB ext3 partition at the beginning of your HDD that you can use as a dedicated Grub partition. If you can create that partition, I can lead you through how to install Grub to that partition.

---

### Post by zzzzz1 on 2008-09-28
thats probably the issue then
cause i have about 70 GB unpartitioned space , then 120 GB ntfs and then as 3 partition reiserfs
so will create this ext3 now as you advised 
thx a lot

---

### Post by zzzzz1 on 2008-09-28
according to gparted my sdc looks now like this:

```
/dev/sdc1  ext3              68.42  GiB
/dev/sdc2  ntfs              112.30 GiB
/dev/sdc4  reiserfs    set   48.64  GiB
unallocated                  62.98  GiB
/dev/sdc3  extended           5.76  GiB
/dev/sdc5  linux-swap         5.76  GiB
```

looks like quit a mess to me....

pls advise how to proceed

---

### Post by caljohnsmith on 2008-09-28
> **zzzzz1 said:**
> according to gparted my sdc looks now like this:

```
/dev/sdc1  ext3              68.42  GiB
/dev/sdc2  ntfs              112.30 GiB
/dev/sdc4  reiserfs    set   48.64  GiB
unallocated                  62.98  GiB
/dev/sdc3  extended           5.76  GiB
/dev/sdc5  linux-swap         5.76  GiB
```

looks like quit a mess to me....

pls advise how to proceed
Now that I look more carefully at your HDD numbers, instead of making a dedicated Grub partition, I would just move your entire sdc4 partition to sdc1. You can do that with gparted if you like. That's just an idea, but if you still want to go with the Grub partition idea, all you need to do is just copy all your Grub files from sdc4 over into /boot/grub/ on sdc1, and then run the "root" and "setup" commands in Grub's CLI to make the Grub MBR point to sdc1 instead of sdc4 (do this from the Live CD):
```
sudo grub
grub> root (hd2,0)
grub> setup (hd2)
```
Let me know how it goes, or I can provide more specifics if you like. But first let me know what you want to do.

---

### Post by zzzzz1 on 2008-09-28
resize/move in gparted confusses me and am a bit scared of screwing it completely 

it gives me

```
Free space preceding
New Size
Free Space following
```

and am simply not sure what to do there.

---

### Post by zzzzz1 on 2008-09-28
"all you need to do is just copy all your Grub files from sdc4 over into /boot/grub/ on sdc1"

how can I do this ?

drag and drop gives me:
> 
the folder "boot" can not be copied because you do not have the permissions to create it in the destination.

---

### Post by caljohnsmith on 2008-09-28
Are you sure you don't want to give gparted a try? I think you first need to delete the empty ext3 sdc1 partition to make it unallocated space again, then select your sdc4 partition, right-click and "copy", then select the unallocated space and do "paste". If you are sure it looks right, then just click the "apply" button.

---

### Post by zzzzz1 on 2008-09-28
when ext3 still existed i could select copy on sdc4
now that i have deleted the ext3 partition i can not select copy any longer at sdc4

you recon i partition again with ext3 or reiserfs and than copy and paste ?

---

### Post by caljohnsmith on 2008-09-28
Hang on, I think I may have found your original problem: your menu.lst in sdc4 is only 32 bytes, so it is probably empty. Go ahead and quit gparted, and please post the output of the following from your Live CD:
```
sudo mount -t reiserfs /dev/sdc4 /mnt
cat /mnt/boot/grub/menu.lst
cat /mnt/boot/grub/menu.lst_backup
```

---

### Post by zzzzz1 on 2008-09-28
[PHP]...[/PHP]


the reason it says message.suse it that I tried to change the optic of grub following this thread [http://ubuntuforums.org/showthread.php?t=208855](http://ubuntuforums.org/showthread.php?t=208855)
and obviously screwed it up big time

---

### Post by caljohnsmith on 2008-09-28
OK, while you have your sdc4 mounted on /mnt, do the following:
```
sudo cp /mnt/boot/grub/menu.lst_backup /mnt/boot/grub/menu.lst
```
It looks like we will need to clean up your menu.lst, but first do the above, reboot, and tell me what happens. I'm guessing that you will get the Grub menu this time, but some of the entries are not going to work.

---

### Post by zzzzz1 on 2008-09-28
thx so much

got it back and you where right, it needs a clean up
all those development branch kernels from the old alpha install are in there aswell

when I try xp i get:
> 
BootSector Write !!
Virus: Continue (Y/N)?

shall I continue ?

---

### Post by caljohnsmith on 2008-09-28
Yes, I should have caught your menu.lst problem sooner, because if your Grub files were beyond a BIOS 137 GB limitation, then you should have gotten a Grub error 18 or similar, but instead you were getting dropped into the Grub command line. Well at least we finally found the root cause of your problem. :)

Try this from the Live CD, as it may save us a lot of time changing your menu.lst manually (make sure sdc4 is mounted on /mnt):
```
sudo mount -o bind /dev /mnt/dev
sudo mount -t proc none /mnt/proc
sudo chroot /mnt
update-grub
cat /boot/grub/menu.lst
ls -l /boot
exit
```
Please post the output of everything above.

---

### Post by zzzzz1 on 2008-09-28
i did this from my Hardy installation not the live CD 


[PHP]...
[/PHP]

just edited the output as I forgot  sudo mount -t reiserfs /dev/sdc4 /mnt

---

### Post by caljohnsmith on 2008-09-28
OK, I forgot that you can boot into Hardy now and don't have to use the Live CD, so just run the following:
```
sudo update-grub
cat /boot/grub/menu.lst
```

---

### Post by zzzzz1 on 2008-09-28
nothing has changed

and when i try booting xp i still get

> BootSector Write !!
Virus: Continue (Y/N)? 

shall I continue?

Edit: actualy something has changed, a bootsplash which i installed long time ago which did not work, comes now up just FYI

---

### Post by caljohnsmith on 2008-09-28
No I wouldn't continue at this point, because I think I know what the problem is. In Hardy, open your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And delete the "makeactive" line in your Windows entry so that it looks like:
```
title        Microsoft Windows XP Professional
root        (hd0,1)
savedefault
chainloader    +1 
```
Save, reboot, and see if you have the same problem.

---

### Post by zzzzz1 on 2008-09-28
windows could not start because the following fie is missing or corrupt:

<windows root>/ system32/hal.dll

pls reinstall a copy of the above fie

---

### Post by caljohnsmith on 2008-09-28
> **zzzzz1 said:**
> windows could not start because the following fie is missing or corrupt:

<windows root>/ system32/hal.dll

pls reinstall a copy of the above fie
Hmmm... well it looks like you now have a Windows problem rather than a Grub problem, so at least your Windows menu.lst entry seems to be OK. While you are in Hardy, try the following:
```
sudo mkdir /mnt/sdc2
sudo mount /dev/sdc2 /mnt/sdc2
```
If that doesn't return any errors, proceed with:
```
ls -l /mnt/sdc2
```
If that works, please post the output. Also, boot your Windows Install CD, choose "r" at the first menu to get the "recovery console", and then run:
```
chkdsk /r
```
Let me know if it finds errors.

---

### Post by zzzzz1 on 2008-09-28
above entry's worked flawless (will post the output later)

but I dont get an option to  press r anywhere

only Enter , C or D

when the Setup is still loading it offers F2 for automated system recovery (shall I try this?)

---

### Post by caljohnsmith on 2008-09-28
> **zzzzz1 said:**
> above entry's worked flawless (will post the output later)

but I dont get an option to  press r anywhere

only Enter , C or D

when the Setup is still loading it offers F2 for automated system recovery (shall I try this?)
I wouldn't do the automated system recovery yet, because that might be the equivalent of a "Windows Repair" which will reinstall all your Windows system files and knock you back to Service Pack 1. But you get the above options from your Windows Install CD? Maybe because you have Windows Professional and not Home edition like I do it is different. 

The bottom line is when you boot your Windows Install CD, you need to get to the command line or recovery console to run that chkdsk command. If you can post more info, I might be able to guide you through it.

---

### Post by zzzzz1 on 2008-09-28
I think the reason it doesent offer me R is that it doese not recognize
my Windows installation.

I may add that i had also another old windows install on another drive.
This one was assigned as c: and the new one as I:
now in the setup the old partition is showing as D: and the new one (which i want to recover ) as c:

not sure what else i could provide

---

### Post by caljohnsmith on 2008-09-28
OK, before going further with the Windows Install CD, boot back into Ubuntu, mount your Windows partition, and post the contents of your Windows "boot.ini" file:
```
sudo mount /dev/sdc2 /mnt/sdc2
cat /mnt/sdc2/boot.ini

```
I've heard that sometimes a hal.dll error can be because the boot.ini is pointing to the wrong disk/partition, so we should at least check your boot.ini to make sure it is correct.

---

### Post by zzzzz1 on 2008-09-28
I dont know whats going on.

I havend done anything but now grub is gone again
and i get straight :
[PHP]
windows could not start because the following fie is missing or corrupt:

<windows root>/ system32/hal.dll

pls reinstall a copy of the above fie[/PHP]

am gone boot from Live CD now and send you the output of above commands

---

### Post by caljohnsmith on 2008-09-28
Did you do the F2 "automated system recovery" you mentioned before? That might have reinstalled the Windows MBR. While you are in the Live CD, do the following to reinstall Grub to the MBR:
```
sudo grub
grub> root (hd2,3)
grub> setup (hd2)
grub> quit

```
Then to print the Windows boot.ini file:
```

sudo mkdir /mnt/sdc2
sudo mount /dev/sdc2 /mnt/sdc2
cat /mnt/sdc2/boot.ini
```

---

### Post by zzzzz1 on 2008-09-28
not sure why but the partition order has changed



```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        8931       23590   117756450    7  HPFS/NTFS
/dev/sdc2           23591       29939    50998342+  83  Linux
/dev/sdc3           38162       38913     6040440    5  Extended
/dev/sdc5           38162       38913     6040408+  82  Linux swap / Solaris
```



[PHP]root@ubuntu:~# sudo mount /dev/sdc2 /mnt/sdc2
mount: mount point /mnt/sdc2 does not exist[/PHP]

I did not do the auto recovery, the only thing i did was connect the 4 HD with the old windows installation to see what the setup shows (now disconnected again)

[PHP]
grub> find /boot/grub/stage1
 (hd0,1)
 (hd2,1)[/PHP]

---

### Post by caljohnsmith on 2008-09-28
That is really crazy that your partition order seems to be different now, compared to your post #12. That's definitely not a good sign. But anyway, try the following from the Live CD and post the results:
```
sudo grub
grub> root (hd2,1)
grub> setup (hd2)
grub> quit
sudo mkdir /mnt/sdc1
sudo mount /dev/sdc1 /mnt/sdc1
cat /mnt/sdc1/boot.ini
```

---

### Post by zzzzz1 on 2008-09-28
[PHP]root@ubuntu:~# sudo mkdir /mnt/sdc1
root@ubuntu:~# cat /mnt/sdc1/boot.ini
cat: /mnt/sdc1/boot.ini: No such file or directory
root@ubuntu:~# 
[/PHP]

grub setup runs fine without errors (hd2,1) but ive done it already before
and i got my kernels showing as Debian now  instead Ubuntu and when i selected it I got error 22, same with xp now, error 22

---

### Post by caljohnsmith on 2008-09-28
If you are getting a different Grub menu on start up, it sounds like you might be booting from your sda drive. Be sure not to connect/disconnect any drives at this point so we can have consistency about troubleshooting this. Can you go into BIOS and make sure you are booting your sdc drive?

Also, please read the commands carefully, because in your last post it looks like you forgot to run the "mount" command that I gave in my previous post. Try again:
```
sudo mkdir /mnt/sdc1
sudo mount /dev/sdc1 /mnt/sdc1
cat /mnt/sdc1/boot.ini
```

---

### Post by zzzzz1 on 2008-09-28
sry, your right , I forgot to mount

root@ubuntu:~# sudo mount /dev/sdc1 /mnt/sdc1

[PHP]root@ubuntu:~# 
root@ubuntu:~# cat /mnt/sdc1/boot.ini
[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
root@ubuntu:~# 
[/PHP]
i definitely have sdc selected in the BIOS

---

### Post by unutbu on 2008-09-28
Hi zzzzz1, I just want to mention that when you change  the drives plugged into your machine, the (hdX,Y) numbers for the drives may change. Also, if you use the BIOS to select which drive to boot, the (hdX,Y) numbers may change. 

So the easiest way to make things work is to plug everything in, and fix the BIOS boot order and never change it. 

If you'd like a system with more flexibility, it would  help us if you post your 
```

sudo fdisk -l
```
with all four drives (post #12 is gone!), identify which partition has an OS on it, and describe what scenarios/combinations of drives plugged in you plan to use.

---

### Post by zzzzz1 on 2008-09-28
@ unutbu

not sure if i should do this now as caljohnsmith ask me not to change anything @ this point to have some consistency

the 4 drive just contains an old windows xp where i have some Games installed which i play sometimes from my new xp install 

so iam realy just dualbooting from sdc  Ubuntu/XP

the rest is storgae and some old OS on /dev/sda2 which i dont use anymore

[PHP]...
[/PHP]

---

### Post by caljohnsmith on 2008-09-28
Unutbu has a good point about including all your HDDs, but since we are just trying to get your sdc HDD to work (and Grub is installed to its MBR, not another drive), let's wait on connecting that last old Windows XP drive at this point. Once we are sure sdc is booting OK and able to boot into Windows or Ubuntu on that drive, then we can deal with your old Windows HDD. It will also make it difficult to use your Windows Install CD to repair Windows on sdc1 if you have your other HDD connected, because the Windows CD will probably also detect your old Windows on the other HDD.

Well you definitely have a problem in your boot.ini file since your Windows went from sdc2 to sdc1. I've attached a new boot.ini.gz file to this post that points to sdc1 as the new Windows partition, so download it to your Ubuntu desktop on the Live CD, and do the following:
```
cd ~/Desktop
gunzip boot.ini.gz
sudo mkdir /mnt/sdc1
sudo mount /dev/sdc1 /mnt/sdc1
cp /mnt/sdc1/boot.ini /mnt/sdc1/boot.ini.backup
sudo mv boot.ini /mnt/sdc1/.
```
Also, what exactly happens on start up now? Are you getting the Grub menu but with Debian entries like you mentioned before?

Please also post:
```
sudo mkdir /mnt/sdc2
sudo mount /dev/sdc2 /mnt/sdc2
cat /mnt/sdc2/boot/grub/menu.lst
```

---

### Post by zzzzz1 on 2008-09-28
[PHP]...
[/PHP]

gone reboot now ....

---

### Post by zzzzz1 on 2008-09-28
Still get  the Kernels showing as Debian GNU/Linux
when i select them:

```
error 22 : No such partition
```

---

### Post by caljohnsmith on 2008-09-28
OK, while you are in the Live CD:
```
sudo mkdir /mnt/sdc2
sudo mount /dev/sdc2 /mnt/sdc2
gksudo gedit /mnt/sdc2/boot/grub/menu.lst
```
That will pull up your current menu.lst, so just select all of it, delete it, and replace it with:
```
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
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=b80b309f-114b-4d67-a02e-96d62beffabc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## ## End Default Options ##

title        Ubuntu 8.04, kernel 2.6.24-19-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=b80b309f-114b-4d67-a02e-96d62beffabc ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
boot

title        Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=b80b309f-114b-4d67-a02e-96d62beffabc ro single
initrd        /boot/initrd.img-2.6.24-19-generic
boot

title        Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=b80b309f-114b-4d67-a02e-96d62beffabc ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
boot

title        Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=b80b309f-114b-4d67-a02e-96d62beffabc ro single
initrd        /boot/initrd.img-2.6.24-16-generic
boot

title        Ubuntu 8.04, kernel memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
chainloader    +1  
```
Let me know what errors you get on start up when trying both Ubuntu and Windows.

---

### Post by zzzzz1 on 2008-09-28
John Smith for President ! :)

thanks sooooo much!

both booting now.

:D :D :D

---

### Post by caljohnsmith on 2008-09-28
> **zzzzz1 said:**
> John Smith for President ! :)

thanks sooooo much!

both booting now.

:D :D :D
That's great news, and you're certainly welcome. I'm glad the only thing wrong with your Windows turned out to be the boot.ini file. Anyway, cheers and have fun! :)

---

