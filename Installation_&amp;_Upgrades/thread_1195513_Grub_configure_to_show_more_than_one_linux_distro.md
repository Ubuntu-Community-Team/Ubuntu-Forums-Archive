---
title: "Grub configure to show more than one linux distro"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by rcayea on 2009-06-23
Hey everyone,

Here is my issue. I have Win XP on one hard drive and Ubuntu on another hard drive. 

I installed Linux Mint on the XP hard drive.

So now I have Mint and XP on one hard drive and Ubuntu on the other. 

when I boot I get the Ubuntu screen that shows the list of kernels and this is what I want (I want to keep Ubuntu as the main setup as I fiddle with Mint).

However, Mint isn't showing up on my grub list to allow me to choose it. 

I tried adding this to my menu.1st file:
title 		Linux Mint
rootnoverify 	(hd1,0)
chainloader 	+1
boot

This is apparently wrong. I am going to post my menu.1st file, and if you could please give me some guidance. Thank you, Randy .

## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=4882cfb1-e5f7-4788-a930-d61b95cb6b55 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4882cfb1-e5f7-4788-a930-d61b95cb6b55

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

title		Ubuntu 9.04, kernel 2.6.30-020630-generic
uuid		4882cfb1-e5f7-4788-a930-d61b95cb6b55
kernel		/boot/vmlinuz-2.6.30-020630-generic root=UUID=4882cfb1-e5f7-4788-a930-d61b95cb6b55 ro quiet splash  crashkernel=384M-2G:64M@16M,2G-:128M@16M
initrd		/boot/initrd.img-2.6.30-020630-generic
quiet

title		Ubuntu 9.04, kernel 2.6.30-020630-generic (recovery mode)
uuid		4882cfb1-e5f7-4788-a930-d61b95cb6b55
kernel		/boot/vmlinuz-2.6.30-020630-generic root=UUID=4882cfb1-e5f7-4788-a930-d61b95cb6b55 ro  crashkernel=384M-2G:64M@16M,2G-:128M@16M single
initrd		/boot/initrd.img-2.6.30-020630-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		4882cfb1-e5f7-4788-a930-d61b95cb6b55
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=4882cfb1-e5f7-4788-a930-d61b95cb6b55 ro quiet splash  crashkernel=384M-2G:64M@16M,2G-:128M@16M
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		4882cfb1-e5f7-4788-a930-d61b95cb6b55
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=4882cfb1-e5f7-4788-a930-d61b95cb6b55 ro  crashkernel=384M-2G:64M@16M,2G-:128M@16M single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-12-generic
uuid		4882cfb1-e5f7-4788-a930-d61b95cb6b55
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=4882cfb1-e5f7-4788-a930-d61b95cb6b55 ro quiet splash  crashkernel=384M-2G:64M@16M,2G-:128M@16M
initrd		/boot/initrd.img-2.6.28-12-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
uuid		4882cfb1-e5f7-4788-a930-d61b95cb6b55
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=4882cfb1-e5f7-4788-a930-d61b95cb6b55 ro  crashkernel=384M-2G:64M@16M,2G-:128M@16M single
initrd		/boot/initrd.img-2.6.28-12-generic

title		Ubuntu 9.04, memtest86+
uuid		4882cfb1-e5f7-4788-a930-d61b95cb6b55
kernel		/boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows XP (loader)
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

title 		Linux Mint
rootnoverify 	(hd1,0)
chainloader 	+1
boot

---

### Post by presence1960 on 2009-06-23
you have both windows and mint as (hd1,0) so one of them is incorrect. I assume it is mint that is incorrrect since you just added mint. Windows does boot correct? so lets see what partition you have mint on. Open a terminal and run```
 sudo fdisk -l
``` BTW that is a lowercase L. Post the output back here and we'll get mint booting for you.

---

### Post by rcayea on 2009-06-23
Thanks for the help. Here is the info requested. By the way, my windows XP does boot properly.

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x259b259a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38161   306528201   83  Linux
/dev/sda2           38162       38913     6040440    5  Extended
/dev/sda5           38162       38913     6040408+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x25212520

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14817   119017521    7  HPFS/NTFS
/dev/sdb2           19317       19457     1132582+  82  Linux swap / Solaris
/dev/sdb3           14818       18806    32041642+  83  Linux
/dev/sdb4           18807       19316     4096575   83  Linux

Partition table entries are not in disk order

---

### Post by presence1960 on 2009-06-23
```
title        Linux Mint
rootnoverify (hd1,2)
chainloader  +1
```

this will work as long as you installed Mint's grub to it's partition. Try it, if not we can restore Mint's GRUB to it's partition.

P.S. What happens when you try to boot Windows?

---

### Post by rcayea on 2009-06-23
I'll go try your suggestion in a second, but to answer your question, XP boots perfectly fine.

---

### Post by presence1960 on 2009-06-23
> **rcayea said:**
> I'll go try your suggestion in a second, but to answer your question, XP boots perfectly fine.

sorry I thought I saw a "not " in there referring to windows boot. My bad!

---

### Post by rcayea on 2009-06-23
not problem. you are kind enough to help so feel free to be "bad" all you want. :)

hd1,2 didn't work.

---

### Post by papenpj on 2009-06-23
I believe it should be hd1,1
since windows is hd1,0  the next logical move would be use 1.

---

### Post by presence1960 on 2009-06-23
> **papenpj said:**
> I believe it should be hd1,1
since windows is hd1,0  the next logical move would be use 1.

look at the output from his sudo fdisk -l. The second partition is swap so that is incorrect!

> Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x25212520

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 14817 119017521 7 HPFS/NTFS
/dev/sdb2 19317 19457 1132582+ 82 Linux swap / Solaris
/dev/sdb3 14818 18806 32041642+ 83 Linux
/dev/sdb4 18807 19316 4096575 83 Linux

Mint is installed on same drive as windows. Maybe it is the sdb4 partition. Try (hd1,3) in the rootnoverify line.
Is sdb3 /home & sdb4 /?

---

### Post by papenpj on 2009-06-23
> **presence1960 said:**
> look at the output from his sudo fdisk -l second partition is swap so that is incorrect!

I guess that a my bad I didn't read that far into the fdisk post after seeing 2 didn't work, I just thought it seemed weird to see 2, i guess he then should try 3 since it lists 4 paritions from fdisk

---

### Post by rcayea on 2009-06-23
I'll give that a try. 

I do have Super Grub Disk on cd if you think I should use that. 

I am not totally sure what to use with that because I just tried it where I did a manual restore and selected Mint to restore. It worked except Mint came up as my default splash screen and the first kernel to select is Mint and I want ubuntu to be the first one (you know so I can kick the comp on and then head to the fridge or something). 

So I went back with SGD and selected to fix Ubuntu thinking that might work but now I am back to the same situation.

---

### Post by papenpj on 2009-06-24
I really don't have any experience using grub to boot a from a secondary hard disk, all my systems have multiple partitions on one disk.

The only thing I might suggest is running the command to update/reinstall grub in the hopes it might detect your new operating system.

---

### Post by presence1960 on 2009-06-24
ok, you got your Ubuntu GRUB menu on bootup now? if that is correct first let us know what partition is Mint's / - sdb3 or sdb4. We can give it one more shot editing Ubuntu's GRUB. If not we'll have to pop in Mint's Live CD and restore GRUB to Mint's / (root) partition so when you select the chainload option on Ubuntu's GRUB menu Mint's GRUB will take over. Mint uses it's own specialized version of GRUB.

---

### Post by rcayea on 2009-06-24
OK. Thanks for the tips, though.

I tried hd1,3 and hd1,4 and neither worked.

I don't mind reinstalling Mint. If I was to do that, when I get the choice as to where to install the boot loader, where would you suggest I put it?

Thanks again,
Randy

---

### Post by gamblor01 on 2009-06-24
> **rcayea said:**
> not problem. you are kind enough to help so feel free to be "bad" all you want. :)

hd1,2 didn't work.

If (hd1,2) didn't work then it's probably because you didn't install a bootloader on that partition.  The whole point of chainloader +1 is that you installed grub on that partition, and instead of using grub on the Ubuntu partition to load everything up, you just hand the work off to the bootloader installed on (hd1,2) and it takes care of the details.

In Ubuntu, I would suggest you try something like this:

```

sudo mkdir /media/sdb3
sudo mount /dev/sdb3 /media/sdb3
cd /media/sdb3/boot
ls

```In the ls output do you see a directory called grub?  If not, then you didn't install a bootloader on that partition.  You can also try the following:

```

sudo grub
find /boot/grub/stage1

```My guess is that the find command will only return (hd0,0).


If it's the case that you didn't install a bootloader on the Mint partition then have no fear, we can use Ubuntu's grub to fire it up.  I just need the output of the following commands:

```

cd /media/sdb3/boot
ls
sudo vol_id /dev/sdb3

```This will tell me the name of the initrd (initial ramdisk) and vmlinuz (the compressed kernel) for Linux Mint.  The vol_is command will tell me the UUID of the Mint partition.  Armed with this info I can tell you exactly what to paste into your /boot/grub/menu.lst file in Ubuntu.  ;)  


After you have all of that output you can unmount the Mint partition:

```

sudo umount /dev/sdb3

```



NOTE:  If you ever upgrade the kernel in your Mint partition, you will need to update menu.lst in Ubuntu to point to the new initrd and vmlinuz files (but you can cross that bridge when you come to it).

---

### Post by rcayea on 2009-06-24
Mint's / is on sdb3.

---

### Post by gamblor01 on 2009-06-24
Wow a LOT happened while I was typing up that reply!  If Mint is on sdb3 then follow my commands above and post the output.  We should be able to get Ubuntu's grub configured in no time.

---

### Post by rcayea on 2009-06-24
In the ls output do you see a directory called grub?

Yes and I am going to do the other command right now.

---

### Post by rcayea on 2009-06-24
here is what i get from this command...

rcayea@randydesktop:/media/sdb3/boot$ sudo vol_id /dev/sdb3
[sudo] password for rcayea: 

ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
ID_FS_UUID=136452ec-d449-45ea-9f96-320233f99811
ID_FS_UUID_ENC=136452ec-d449-45ea-9f96-320233f99811
ID_FS_LABEL=
ID_FS_LABEL_ENC=

---

### Post by presence1960 on 2009-06-24
> **rcayea said:**
> OK. Thanks for the tips, though.

I tried hd1,3 and hd1,4 and neither worked.

I don't mind reinstalling Mint. If I was to do that, when I get the choice as to where to install the boot loader, where would you suggest I put it?

Thanks again,
Randy

Put it on the root (/) partition.

You can try reinstalling Mints GRUB by booting Mint's Live CD and doing this:
```
1. Boot your computer up with Mint CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Mint.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

```

At # 5 use Mint's (hdx,y) output only from #4. Do not use the (hdx,y) of your Ubuntu.

At #6 use the same Mint (hdx,y) to install Mint's GRUB to it's root (/) partition.

After rebooting just make sure your Ubuntu menu.lst has the right (hdx,y) in the rootnoverify line.

---

### Post by rcayea on 2009-06-24
I will now do the umount the Mint partition as instructed.

---

### Post by gamblor01 on 2009-06-24
> **rcayea said:**
> I will now do the umount the Mint partition as instructed.
Wait!  We need the output of the ls command from /media/sdb3/boot

---

### Post by rcayea on 2009-06-24
unmount command told me device was busy.

---

### Post by rcayea on 2009-06-24
ok....let me get that for you, if i can. 

I guess I am going too fast.

---

### Post by gamblor01 on 2009-06-24
> **rcayea said:**
> unmount command told me device was busy.
That's because you probably had the terminal open and were currently inside of a directory on /media/sdb3 such as /media/sdb3/boot   ;)


You can cd elsewhere such as cd ~ and then it will allow you to unmount.

---

### Post by rcayea on 2009-06-24
rcayea@randydesktop:/media/sdb3/boot$ ls

abi-2.6.27-7-generic     initrd.img-2.6.27-7-generic
boot                     memtest86+.bin
config-2.6.27-7-generic  System.map-2.6.27-7-generic
gfxmenu                  vmcoreinfo-2.6.27-7-generic
grub                     vmlinuz-2.6.27-7-generic

rcayea@randydesktop:/media/sdb3/boot$ sudo vol_id /dev/sdb3
[sudo] password for rcayea: 
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
ID_FS_UUID=136452ec-d449-45ea-9f96-320233f99811
ID_FS_UUID_ENC=136452ec-d449-45ea-9f96-320233f99811
ID_FS_LABEL=
ID_FS_LABEL_ENC=


I will wait for a reply so that I don't mess anything up...thanks.

---

### Post by rcayea on 2009-06-24
Presence1960, I will gladly give this a try if I have to reboot, but I want to see what I can do without rebooting, first. I do appreciate the attention to my little problem. 

> **presence1960 said:**
> Put it on the root (/) partition.

You can try reinstalling Mints GRUB by booting Mint's Live CD and doing this:
```
1. Boot your computer up with Mint CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Mint.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

```

At # 5 use Mint's (hdx,y) output only from #4. Do not use the (hdx,y) of your Ubuntu.

At #6 use the same Mint (hdx,y) to install Mint's GRUB to it's root (/) partition.

After rebooting just make sure your Ubuntu menu.lst has the right (hdx,y) in the rootnoverify line.

---

### Post by gamblor01 on 2009-06-24
yikes!  Next time wrap output from the terminal in code tags.  It's just easier to read.  In any case, you should be able to add this to your menu.lst file on Ubuntu and it *should* work.  Run:

```

gksudo gedit /boot/grub/menu.lst

```and paste the following lines at the very end of the file:

```

# Mint
title       Linux Mint
uuid        136452ec-d449-45ea-9f96-320233f99811
kernel      /boot/vmlinuz-2.6.27-7-generic    root=UUID=136452ec-d449-45ea-9f96-320233f99811 ro quiet splash
initrd      /boot/initrd.img-2.6.27-7-generic
quiet

```Now save the file, reboot, and see if it works.

---

### Post by rcayea on 2009-06-24
Sorry about that. I am obviously fairly new to the linux world.

OK, going to reboot and I'll report back...

thanks,
Randy

---

### Post by gamblor01 on 2009-06-24
> **presence1960 said:**
> Put it on the root (/) partition.

You can try reinstalling Mints GRUB by booting Mint's Live CD and doing this:
```
1. Boot your computer up with Mint CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Mint.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

```At # 5 use Mint's (hdx,y) output only from #4. Do not use the (hdx,y) of your Ubuntu.

At #6 use the same Mint (hdx,y) to install Mint's GRUB to it's root (/) partition.

After rebooting just make sure your Ubuntu menu.lst has the right (hdx,y) in the rootnoverify line.

Yeah that would work too...he would have to use the command "setup (hd1,2)" since Mint is on /dev/sdb3.  This would allow him to chainload.  Either way should work.  :)

---

### Post by gamblor01 on 2009-06-24
> **rcayea said:**
> Sorry about that. I am obviously fairly new to the linux world.


No problem -- we all start somewhere.  The best way to learn is to dive right in though.  Keep partitioning your drive, installing more distros, and configuring grub and you will find that you become a master in no time (at least...with this particular aspect of Linux).

I hope it boots!

---

### Post by rcayea on 2009-06-24
I received this message upon selecting Mint:

Error 15: File not found.

---

### Post by rcayea on 2009-06-24
Hey fellows, Thanks for the help. I am out of steam for tonight so I am going to go to bed. I will keep trying tomorrow and if I have any other questions I will post here. If you can help out that would be cool, if not, you have certainly done your good deed for the day by helping so much already. 

Thanks again,
Randy

---

### Post by presence1960 on 2009-06-24
Mint uses it's own specialized version of GRUB. The problem would seem to be that Mint's GRUB is not installed to Mint's root partition. So even though you added the Mint entry with UUID in Ubuntu's menu.lst it isn't pointing to Mint's GRUB.

You want to restore Mint's GRUB to Mint's root partition for 2 reasons : 1. so it will boot Mint and 2. so you can chainload Mint off Ubuntu's GRUB menu. This way when Mint upgrades it's kernels you won't have to update that in Ubuntu's menu.lst because it is chainloaded. When you select Mint in Ubuntu's GRUB menu it passes off to Mints GRUB which is auto updated with new kernels when installed. No editing necessary. When Mint upgrades it's kernels it will not update Ubuntu's menu.lst to reflect the new kernels. if you chainload there will be no editing necessary.

---

### Post by raymondh on 2009-06-24
> **presence1960 said:**
> The problem would seem to be that Mint's GRUB is not installed to Mint's root partition.

I think you're right.  Just following this thread.  Good learnings here.

---

### Post by gamblor01 on 2009-06-24
> **rcayea said:**
> I received this message upon selecting Mint:

Error 15: File not found.
If that is the case then it's not finding either the initrd file or the vmlinuz file for some strange reason.  I looked through all of your output again and again and I don't understand what the problem is.  Going to bed sounds good though!  Here's some stuff for you to try tomorrow:

1) Remember I said before to try this:

```

sudo grub
find /boot/grub/stage1

```What is the output of that?


2) If you do have a grub directory on sdb3 then let's see what is in there. You can mount the partition again and list the files:

```

sudo mount /dev/sdb3 /media/sdb3
cd /media/sdb3/boot/grub
ls

```What is the output?


3) If you truly have grub installed already on /dev/sdb3, then the old chainloader line you had should work.  After looking at it again, I wonder if maybe we need to make it active?  I don't really think so but what if you put this into menu.lst

```

title           Linux Mint
root            (hd1,2)
makeactive
chainloader     +1

```


I would wait on #3 until we can verify that you really do have grub installed on sdb3 though (which means we need the output of #1 and #2 above).

---

### Post by presence1960 on 2009-06-24
Let's get a better look at your setup & boot info. Download to your desktop the boot Info Script from here: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)  Then open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on your desktop. Paste the entire contents of this file back here. After pasting here, highlight all text and click # on the toolbar to place code tags around the text.

This will show us all configuration and boot info about your machine, including where GRUB is installed and where it looks for menu.lst.

Have a good sleep and we'll hopefully have this going tomorrow.

---

### Post by gamblor01 on 2009-06-24
> **presence1960 said:**
> Mint uses it's own specialized version of GRUB.
Ahhh...that explains a lot.  I assumed it was the same as Ubuntu since, well, they are pretty much based off of the same code.

I agree though -- chainloading is definitely easier.  ;)

Let's see what we can do tomorrow.

---

### Post by papenpj on 2009-06-24
gamblor01, 
im with you on thinking that it would have been the same grub. 

But I guess I agree with the chainloading idea to avoid needing to constantly update ubuntu's grub. Ill definately keep that idea in mind if I decide to try another distro on my laptop.

---

### Post by presence1960 on 2009-06-24
> **gamblor01 said:**
> Ahhh...that explains a lot.  I assumed it was the same as Ubuntu since, well, they are pretty much based off of the same code.

I agree though -- chainloading is definitely easier.  ;)

Let's see what we can do tomorrow.

From Mint's GRUB wiki:

Mint's Grub

Mint has a special version of Grub called gfxgrub. This enables the nice Grub splash and has been used since Celena.
Some hardware "does not like" this version of grub, notably Mac(book).

"not liking" is not the problem here.

---

### Post by gamblor01 on 2009-06-24
> **presence1960 said:**
> 
Mint has a special version of Grub called gfxgrub. This enables the nice Grub splash and has been used since Celena.
Some hardware "does not like" this version of grub, notably Mac(book).

Good to know.  This still should be an easy fix though:

1) Edit your menu.lst file in Ubuntu (you can use: gksudo gedit /boot/grub/menu.lst) and delete the lines I told you put in there about the UUID and initrd and so on:

```

# Mint
title       Linux Mint
uuid        136452ec-d449-45ea-9f96-320233f99811
kernel      /boot/vmlinuz-2.6.27-7-generic    root=UUID=136452ec-d449-45ea-9f96-320233f99811 ro quiet splash
initrd      /boot/initrd.img-2.6.27-7-generic
quiet
```Replace them with this again:

```

title    Linux Mint
rootnoverify (hd1,2)
chainloader +1

```2) Put in the Mint cd and reboot into a live session

3) Open a terminal and type:

```

sudo grub
root (hd1,2)
setup (hd1,2)
quit

```4) Reboot, remove the live CD, and select the "Linux Mint" option in grub.  It should boot.


If that doesn't work I will be really surprised.  We can try the grub-install command if that's the case though.  Perhaps we just need to lay down the files for grub again?  Let's see what happens with the steps above first.

---

### Post by presence1960 on 2009-06-24
+1

That is what I have been suggesting all along. I know that works because I tribooted Ubuntu/Mint/XP for about 8 months.

---

### Post by rcayea on 2009-06-24
I tried the Mint live CD fix grub. I think the results from this tells all... 

grub> root (hd1,2)

Error 22: No such partition


I am now going to do the "sudo bash ~/Desktop/boot_info_script*.sh" command and I will post the results.

---

### Post by rcayea on 2009-06-24
Here is the information from the RESULTS.txt file:


```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda1 and 
                       looks at sector 296804513 on boot drive #2 for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #3 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 6 Felicia
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x259b259a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   613,056,464   613,056,402  83 Linux
/dev/sda2         613,056,465   625,137,344    12,080,880   5 Extended
/dev/sda5         613,056,528   625,137,344    12,080,817  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x25212520

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   238,035,104   238,035,042   7 HPFS/NTFS
/dev/sdb2         310,311,540   312,576,704     2,265,165  82 Linux swap / Solaris
/dev/sdb3         238,035,105   302,118,389    64,083,285  83 Linux
/dev/sdb4         302,118,390   310,311,539     8,193,150  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="4882cfb1-e5f7-4788-a930-d61b95cb6b55" TYPE="ext3" 
/dev/sda5: UUID="e331abd7-60b4-49f5-b96f-8bd0207d058e" TYPE="swap" 
/dev/sdb1: UUID="F094489894486368" LABEL="Windows XP" TYPE="ntfs" 
/dev/sdb2: UUID="e7a8f774-38fe-4e0b-a899-3716bb682d1a" TYPE="swap" 
/dev/sdb3: UUID="136452ec-d449-45ea-9f96-320233f99811" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb4: UUID="805920b0-6fd7-45eb-85a0-1eee2695f2c4" SEC_TYPE="ext2" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/rcayea/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=rcayea)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=rcayea)


=========================== sda1/boot/grub/menu.lst: ===========================

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=4882cfb1-e5f7-4788-a930-d61b95cb6b55 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4882cfb1-e5f7-4788-a930-d61b95cb6b55

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

title		Ubuntu 9.04, kernel 2.6.30-020630-generic
uuid		4882cfb1-e5f7-4788-a930-d61b95cb6b55
kernel		/boot/vmlinuz-2.6.30-020630-generic root=UUID=4882cfb1-e5f7-4788-a930-d61b95cb6b55 ro quiet splash  crashkernel=384M-2G:64M@16M,2G-:128M@16M
initrd		/boot/initrd.img-2.6.30-020630-generic
quiet

title		Ubuntu 9.04, kernel 2.6.30-020630-generic (recovery mode)
uuid		4882cfb1-e5f7-4788-a930-d61b95cb6b55
kernel		/boot/vmlinuz-2.6.30-020630-generic root=UUID=4882cfb1-e5f7-4788-a930-d61b95cb6b55 ro  crashkernel=384M-2G:64M@16M,2G-:128M@16M single
initrd		/boot/initrd.img-2.6.30-020630-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		4882cfb1-e5f7-4788-a930-d61b95cb6b55
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=4882cfb1-e5f7-4788-a930-d61b95cb6b55 ro quiet splash  crashkernel=384M-2G:64M@16M,2G-:128M@16M
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		4882cfb1-e5f7-4788-a930-d61b95cb6b55
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=4882cfb1-e5f7-4788-a930-d61b95cb6b55 ro  crashkernel=384M-2G:64M@16M,2G-:128M@16M single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-12-generic
uuid		4882cfb1-e5f7-4788-a930-d61b95cb6b55
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=4882cfb1-e5f7-4788-a930-d61b95cb6b55 ro quiet splash  crashkernel=384M-2G:64M@16M,2G-:128M@16M
initrd		/boot/initrd.img-2.6.28-12-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
uuid		4882cfb1-e5f7-4788-a930-d61b95cb6b55
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=4882cfb1-e5f7-4788-a930-d61b95cb6b55 ro  crashkernel=384M-2G:64M@16M,2G-:128M@16M single
initrd		/boot/initrd.img-2.6.28-12-generic

title		Ubuntu 9.04, memtest86+
uuid		4882cfb1-e5f7-4788-a930-d61b95cb6b55
kernel		/boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows XP (loader)
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

title 		Linux Mint
rootnoverify 	(hd1,2)
chainloader 	+1
boot

# Mint
title        Linux Mint
uuid        136452ec-d449-45ea-9f96-320233f99811
kernel        /boot/vmlinuz-2.6.27-7-generic    root=UUID=136452ec-d449-45ea-9f96-320233f99811 ro quiet splash
initrd        /boot/    initrd.img-2.6.27-7-generic
quiet

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=4882cfb1-e5f7-4788-a930-d61b95cb6b55 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e331abd7-60b4-49f5-b96f-8bd0207d058e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   6.0GB: boot/grub/menu.lst
   6.0GB: boot/grub/stage2
   6.0GB: boot/initrd.img-2.6.28-12-generic
   5.9GB: boot/initrd.img-2.6.28-13-generic
   5.9GB: boot/initrd.img-2.6.30-020630-generic
   6.1GB: boot/vmlinuz-2.6.28-12-generic
   5.9GB: boot/vmlinuz-2.6.28-13-generic
   6.0GB: boot/vmlinuz-2.6.30-020630-generic
   5.9GB: initrd.img
   5.9GB: initrd.img.old
   6.0GB: vmlinuz
   5.9GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sdb3/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## Graphical boot menu location
gfxmenu=/boot/gfxmenu/default.message

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

# Pretty colours
color cyan/blue white/blue

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/sdb3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,2)

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
##      altoptions=(single-user) single
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

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Linux Mint Universal Edition, kernel 2.6.27-7-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sdb3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Linux Mint Universal Edition, kernel 2.6.27-7-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sdb3 ro single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Linux Mint Universal Edition, kernel Last successful boot
root		(hd1,2)
kernel		/boot/last-good-boot/vmlinuz root=/dev/sdb3 ro quiet splash  last-good-boot
quiet

title		Linux Mint Universal Edition, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.30-020630-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.30-020630-generic root=UUID=4882cfb1-e5f7-4788-a930-d61b95cb6b55 ro quiet splash crashkernel=384M-2G:64M@16M,2G-:128M@16M 
initrd		/boot/initrd.img-2.6.30-020630-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.30-020630-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.30-020630-generic root=UUID=4882cfb1-e5f7-4788-a930-d61b95cb6b55 ro crashkernel=384M-2G:64M@16M,2G-:128M@16M single 
initrd		/boot/initrd.img-2.6.30-020630-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=4882cfb1-e5f7-4788-a930-d61b95cb6b55 ro quiet splash crashkernel=384M-2G:64M@16M,2G-:128M@16M 
initrd		/boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=4882cfb1-e5f7-4788-a930-d61b95cb6b55 ro crashkernel=384M-2G:64M@16M,2G-:128M@16M single 
initrd		/boot/initrd.img-2.6.28-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-12-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=4882cfb1-e5f7-4788-a930-d61b95cb6b55 ro quiet splash crashkernel=384M-2G:64M@16M,2G-:128M@16M 
initrd		/boot/initrd.img-2.6.28-12-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=4882cfb1-e5f7-4788-a930-d61b95cb6b55 ro crashkernel=384M-2G:64M@16M,2G-:128M@16M single 
initrd		/boot/initrd.img-2.6.28-12-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb3
UUID=136452ec-d449-45ea-9f96-320233f99811 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb4
UUID=805920b0-6fd7-45eb-85a0-1eee2695f2c4 /home           ext3    relatime        0       2
# /dev/sda5
UUID=e331abd7-60b4-49f5-b96f-8bd0207d058e none            swap    sw              0       0
# /dev/sdb2
UUID=e7a8f774-38fe-4e0b-a899-3716bb682d1a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb3: Location of files loaded by Grub: ===================


 151.9GB: boot/grub/menu.lst
 151.9GB: boot/grub/stage2
 152.0GB: boot/initrd.img-2.6.27-7-generic
 151.9GB: boot/vmlinuz-2.6.27-7-generic
 152.0GB: initrd.img
 151.9GB: vmlinuz
```

---

### Post by rcayea on 2009-06-24
I am thrilled thatI learned about the "#" code posting format. I have also learned a lot of other things. 

I am heading out to do errands and will check back in, in a few hours. 

Thanks again,
Randy

---

### Post by presence1960 on 2009-06-24
I think I know what the issue is. look in your BIOS and see if your sdb disk is set as first boot. if it is just change those commands to (hd0,2) Sometimes GRUB and BIOS read disk order differently. I don't know why that is but they do. So boot up the Mint CD and try (hd0,2) if your sdb is set to boot first. Mine is like that check this out : 

```
raz@raz-desktop:~$ sudo fdisk -l
[sudo] password for raz: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000d179

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        4569    36596736    7  HPFS/NTFS
/dev/sda3            4570       29879   203302575   83  Linux
/dev/sda4           29880       30401     4192965   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7a57e45

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14519   116623836   83  Linux
/dev/sdb2           14520       16477    15727635   83  Linux
/dev/sdb3           16478       18389    15358140   83  Linux
/dev/sdb4           18390       19458     8579072    f  W95 Ext'd (LBA)
/dev/sdb5           18390       19458     8578048    7  HPFS/NTFS

```

according to fdisk my windows is on sda. sda1 is win7 boot partition, sdb2 is win 7, sda3 is /home. sdb1 is storage, sdb2 is Jaunty, sdb3 is Hardy. so by this my windows entry should be (hd0,0) since win 7 boots off that boot partition... But check out my menu.lst entry for windows:
```

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-12-generic
uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-12-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro  single
initrd		/boot/initrd.img-2.6.28-12-generic

#title		Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro quiet splash 
#initrd		/boot/initrd.img-2.6.28-11-generic
#quiet

#title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro  single
#initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows 7 RC
rootnoverify	(hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader	+1

title           Hardy 8.04
rootnoverify    (hd0,2)
chainloader     +1
```

Why is it (hd1,0)? because in BIOS my boot order has sdb disk booting before sda.

So take a look in your BIOS and see what you have.

---

### Post by presence1960 on 2009-06-24
I just looked at your boot info output and your Mint partition indeed has menu.lst installed to that partition but not GRUB. I looked at your Mint menu.lst also. If indeed your sdb is set to boot first in BIOS you will have to change the (hd1,2) in Mint's menu.lst to (hd0,2) as well as the chainload option in Ubuntu's menu.lst. Also boot the Mint CD and install GRUB to partition (hd0,2) It looks as though everything else is installed on both Ubuntu & Mint!

---

### Post by gamblor01 on 2009-06-24
> **presence1960 said:**
> look in your BIOS and see if your sdb disk is set as first boot. if it is just change those commands to (hd0,2) Sometimes GRUB and BIOS read disk order differently.
Yeah there should be an option in BIOS to see what order the hard drives are mapped to.  As presence1960 mentioned, you should probably have a look at that.

You can also try these commands in a grub command prompt (use "sudo grub" to get there) to see what information grub obtained from BIOS:

```

geometry (hd0)
geometry (hd1)

```

---

### Post by rcayea on 2009-06-24
hey fellas,

I greatly appreciate your help. As stated, I have learned a lot in this process, but for now, I am going to use the Super Grub Disk and I guess for now I will live with Mint's grub screen and it being the first kernel choice. 

Thanks again and I am sending your way a virtual cold one!

Randy

---

### Post by gamblor01 on 2009-06-25
> **rcayea said:**
> 
I guess for now I will live with Mint's grub screen and it being the first kernel choice.

You can change the order of the entries in the menu.lst file and it should change the order that they are presented to you.  Also, you can set the default entry at the top of menu.lst:

```

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

```

---

### Post by rcayea on 2009-06-25
Thanks for the tip. I will give that a try tomorrow. 

Randy

---

