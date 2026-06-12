---
title: "[SOLVED] Three operating systems, two headaches."
date: 2008-11-25
forum: General Help
---

### Post by thereaper243 on 2008-11-25
Ok... I have tried to figure this out in about three different ways. I have Ubuntu 8.10 installed on one partition, nUbuntu 8.10 installed on another partition, and WinXP on a third partition. All three work. nUbuntu has its very own private GRUB setup. So does Ubuntu. Can I delete my nUbuntu /media/boot/grub folder without losing nUbuntu? It would seem that this would fix the problem but I'm so confused. Also, both GRUB on Ubuntu and on nUbuntu don't seem to notice WinXP. Please help me! *SOB*

---

### Post by thereaper243 on 2008-11-25
Please?

---

### Post by thereaper243 on 2008-11-25
Ok... I have tried to figure this out in about three different ways. I have Ubuntu 8.10 installed on one partition, nUbuntu 8.10 installed on another partition, and WinXP on a third partition. All three work. nUbuntu has its very own private GRUB setup. So does Ubuntu. Can I delete my nUbuntu /media/boot/grub folder without losing nUbuntu? It would seem that this would fix the problem but I'm so confused. Also, both GRUB on Ubuntu and on nUbuntu don't seem to notice WinXP. Please help me! *SOB*

---

### Post by thereaper243 on 2008-11-25
Bump

---

### Post by thereaper243 on 2008-11-25
Bump

---

### Post by thereaper243 on 2008-11-25
Bump

---

### Post by gTinker on 2008-11-25
[QUOTE=thereaper243]Ok... I have tried to figure this out in about three different ways.[/QUOTE]

Naturally, we have no idea of what you mean by this. You didn't state what you saw or what you tried. Or what isn't happening that you expect to happen.

[QUOTE=thereaper243]I have Ubuntu 8.10 installed on one partition, nUbuntu 8.10 installed on another partition, and WinXP on a third partition. All three work. [/QUOTE]

Good, we know they work. But, how do they work? Are you using the XP bootloader or GRUB to boot them?

[QUOTE=thereaper243]nUbuntu has its very own private GRUB setup. So does Ubuntu. Can I delete my nUbuntu /media/boot/grub folder without losing nUbuntu?[/QUOTE]

Please don't delete anything at this point. You need to be clear about what you mean by they have their "very own private GRUB setup". Do you mean that you chose to install GRUB to the partition that they are installed on? 

[QUOTE=thereaper243]It would seem that this would fix the problem but I'm so confused.[/QUOTE] 

It is confusing for us too, you didn't say what the problem is? All you've stated so far is that they all three work.

[QUOTE=thereaper243]Also, both GRUB on Ubuntu and on nUbuntu don't seem to notice WinXP. Please help me! *SOB*[/QUOTE]

I'm sure there are people here who want to help you. I imagine the lack of information in your post is part of the reason you haven't had an answer up to this point. Make it easier for them by giving more information and stating "the problem". It will be relatively easy to add a stanza to the GRUB menu.lst for the XP install, if you are booting with GRUB, once we figure out how the system is working and what it is that you are actually trying to do.

Imagine that you are trying to explain the problem and what you know about it to someone who is blind. Actually, you are, we can't see the console so the only way we can determine what is happening on it is through your description. I know it can be frustrating waiting for an answer, especially with a problem that you likely have been working on for a while but if you bump too many times, at too short an interval, you run the risk of being ignored by the most helpful posters.

---

### Post by adam_kimber on 2008-11-25
> **gTinker said:**
> I'm sure there are people here who want to help you. 

We do. We are a very helpful community and try our utmost to solve everyone's problems. Whilst the above post could be construed as harsh, they are correct. 

I read your post and was well if grub works then great! Usually fixing grub is a pain.... 

I read the part that all operating systems work. Great!

I then got to the bit about "not seeing" I assume that you require read /write access to your XP partition from Ubuntu? Theoretically it should recognise the partition and add it to your list of partitions which show up under "computer". If its there double click, enter your password (for write access) and off you go. If not then we have other things to solve. Not sure what they might be for now.....

---

### Post by natrik on 2008-11-25
> **thereaper243 said:**
> Can I delete my nUbuntu /media/boot/grub folder without losing nUbuntu? It would seem that this would fix the problem but I'm so confused. 

Deleting anything in /boot will only cause MORE TROUBLE!

> **thereaper243 said:**
> Also, both GRUB on Ubuntu and on nUbuntu don't seem to notice WinXP. Please help me! *SOB*

Then how do you boot WinXP?   For that matter, how do you boot any of the three working OSes?   (step by step, that is)

Confused,
-- Nate

---

### Post by caljohnsmith on 2008-11-25
How about opening a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```
And please identify which is Ubuntu and nUbuntu. Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your setup is like.

---

### Post by TeXtonyx on 2008-11-25
> **thereaper243 said:**
> Ok... I have tried to figure this out in about three different ways. I have Ubuntu 8.10 installed on one partition, nUbuntu 8.10 installed on another partition, and WinXP on a third partition. All three work. nUbuntu has its very own private GRUB setup. So does Ubuntu. Can I delete my nUbuntu /media/boot/grub folder without losing nUbuntu? It would seem that this would fix the problem but I'm so confused. Also, both GRUB on Ubuntu and on nUbuntu don't seem to notice WinXP. Please help me! *SOB*

Before you delete anything, first test it. It sounds like you 
have two instances of /boot/grub/menu.lst on two different
partitions? Make each menu.lst capable of booting the other
Ubuntu partition. Starting from the assumption that you have two
partitions with Ubu* installed and not Wubi booting Ubuntu from
inside XP; examine the menu.lst and copy and paste from one
menu.lst to the other menu.lst, the content between ## ## End
Default Options ## and ### END DEBIAN AUTOMAGIC KERNELS LIST
a couple of lines after the last "quiet" shown below and save.

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=22e06212-2963-4aee-aac3-xxxxxxxxxxxx ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=22e06212-2963-4aee-aac3-xxxxxxxxxxxx ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin

quiet [<--the last "quiet"]

[copy and paste the relevant content, which I've shown you 
above, from your other menu.lst here]


### END DEBIAN AUTOMAGIC KERNELS LIST

Do the same thing, copy and paste to your other menu.lst.
You'll have the same content but not in the same order.

1st menu.lst
A (original)
B (copy from 2nd menu.lst)= original in 2nd menu.lst

2nd menu.lst 
A (original)
B (copy from 1st menu.lst)= original in 1st menu.lst

The original and the copy switch places in the order they
are seen in the menu.lst. That means you can boot both 
instances from either of the Ubuntu partitions. Your goal
is to keep the original text on top and the copy beneath it. 
Do it this way for both of your menu.lst files on each partition.

It would be helpful if you posted the result of, sudo fdisk -l

Then I wouldn't have to use words like original and copy, but
terms like sda1, sda2, and sda3. 

Now for XP. 

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Original Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1


This is what you would use to include XP into each of your
menu.lst files. That is if XP were installed to the first
partition, maybe it is, but I don't know without a sudo fisk -l

If by private install of grub, you mean you put both grub into
the /boot partition of each Ubuntu install, that is good.

It means you can boot all 3 OS from XP's boot.ini boot menu. 
[http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)   	 bootpa26.zip free
unzip and extract bootpart.exe to C:\>
run bootpart, C:\>bootpart <enter>
and it will report your two type 83 ext 3 partitions. Pretend,

-------------------------------------

Physical number of disk 0 : 40ec40eb
 0 : C:* type=7  (HPFS/NTFS), size= 140641011 KB, Lba Pos=63
 1 : C:  type=f  (Win95 XInt 13 extended), size= 15647310 KB, Lba Pos=281282085
 2 : C:  type=83   (Linux native), size= 14940418 KB, Lba Pos=281282148
 3 : C:  type=5   (Extended), size= 706860 KB, Lba Pos=311162985
 4 : C:  type=82    (Linux swap), size= 706828 KB, Lba Pos=311163048
 5 : C:  type=83   (Linux native), size= 17940418 KB, Lba 

-------------------------------------------

Since you have two type 83 partition with Ubuntu installed (I
think) you need to make two entries that automatically create
a 512 byte boot sector fragment and write the title to boot.ini

C:\> bootpart 2 UbuntuA.bin UbuntuA <enter>

C:\> bootpart 5 UbuntuB.bin UbuntuB <enter>

These were just example names, you can describe them how you want.

[http://forums.majorgeeks.com/showthread.php?t=108021](http://forums.majorgeeks.com/showthread.php?t=108021) bootpart info

Now you can boot all 3 OS from any one OS.
I don't think you can eliminate the need for grub.
But you can set the timer from 10 to 1 or even 0

Do that to the particular menu.lst that you don't want to see
load (there is even a hidden option which I don't recommend).

You can also reinstall one of the grub into the MBR but you
lose independence of booting XP that way on its own. Super
Grub Disk is a handy rescue tool to boot Ubuntu if XP fails.

Your details were a bit on the scant side so I had
to use creative interpretations to frame an answer.

EDIT: Also caljohnsmith's post came in while I was 
typing this post so use his advice first and see if
it all works out.

---

### Post by natrik on 2008-11-25
> **caljohnsmith said:**
> How about opening a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu

sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"

sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```

Ooooohhhh!  I'm gonna have to look at those on my systems.  :o) Thanks for the insight.  I saw a post of yours in a different thread.  

But what is the behavior of the first 'dd' command, if bs=_ is not specified?  Is it the same for all systems?

---

### Post by thereaper243 on 2008-11-25
Ok... I will attempt to be more clear. I have Ubuntu 8.10 installed onto an extended partition (/dev/sda1), the Ubuntu 8.10 ext3 partition is (/dev/sda5), I have a linux swap file partition at (/dev/sda6), I have nUbuntu installed on an ext3 partition (/dev/sda2), and lastly I have WinXP installed on an NTFS partition (/dev/sda3). So it looks like this:

/dev/sda1 (extended partition)
[INDENT]/dev/sda5 (ext3-Ubuntu)[/INDENT]
[INDENT]/dev/sda6 (linux swap)[/INDENT]
/dev/sda2 (ext-3-nUbuntu)
/dev/sda3 (ntfs-WinXP)

nUbuntu and Ubuntu both install GRUB when installed from a LiveCD. I installed these three operating systems in this order:
[LIST=1]
[*]Ubuntu
[*]nUbuntu
[*]WinXp
[/LIST]
I set up GRUB again by using the Ubuntu LiveCD.
```
sudo grub
```
```
find /boot/grub/stage1
```
```
root (hd0,[PARTITION #])
```
```
setup (hd0)
```
```
quit
```

Now, I have attempted to run the setup command for GRUB on both the nUbuntu partition and the Ubuntu partition. Both were set up correctly (or so says the terminal) but now when I start my computer, it automatically boots into Ubuntu without giving me any options for GRUB, and when it did give me options for GRUB at one point, WinXP was not listed in the GRUB table.

---

### Post by caljohnsmith on 2008-11-25
> **natrik said:**
> Ooooohhhh!  I'm gonna have to look at those on my systems.  :o) Thanks for the insight.  I saw a post of yours in a different thread.  

But what is the behavior of the first 'dd' command, if bs=_ is not specified?  Is it the same for all systems?
"dd" defaults to using a block size of 512 bytes, or one sector; unless you use a different dd than the one included in linux, then it should always default to 512 bytes. Basically the first dd command looks in the MBR (Master Boot Record) which is the first sector of the HDD, and then it checks if either the text string "GRUB" or "Missing operating system" exists; if the command returns "GRUB", then Grub is in the MBR, and if it instead returns "Missing operating system", then it is a Windows MBR. The second dd command (when deciphered) will tell you which partition Grub points to for its boot files. That's usually very useful info when troubleshooting Grub problems. :)

---

### Post by thereaper243 on 2008-11-25
Could someone possibly develop the two menu.lst files that I might need to fix this problem?

---

### Post by caljohnsmith on 2008-11-25
> **thereaper243 said:**
> Did anyone come up with a resolution after I posted my second comment?
OK, how about booting into Ubuntu, open a terminal (Applications > Accessories > Terminal) and do:
```
gksudo gedit /boot/grub/menu.lst
```
And then make sure the "hiddenmenu" line near the top of the file is commented, i.e. has a pound sign:
```
#hiddenmenu
```
Next, at the very end of the file add the following entries:
```
title nUbuntu Grub Menu
configfile (hd0,1)/boot/grub/menu.lst

title Windows XP
root (hd0,2)
chainloader +1
```
Reboot, and you should get the Grub menu giving you the choice of Ubuntu and also the new nUbuntu and Windows XP entries. Let me know if that works OK, and if not, please post the full output of the commands from post #10. :)

---

### Post by thereaper243 on 2008-11-26
> **caljohnsmith said:**
> OK, how about booting into Ubuntu, open a terminal (Applications > Accessories > Terminal) and do:
```
gksudo gedit /boot/grub/menu.lst
```
And then make sure the "hiddenmenu" line near the top of the file is commented, i.e. has a pound sign:
```
#hiddenmenu
```
Next, at the very end of the file add the following entries:
```
title nUbuntu Grub Menu
configfile (hd0,1)/boot/grub/menu.lst

title Windows XP
root (hd0,2)
chainloader +1
```
Reboot, and you should get the Grub menu giving you the choice of Ubuntu and also the new nUbuntu and Windows XP entries. Let me know if that works OK, and if not, please post the full output of the commands from post #10. :)

Ok, so I have done as Caljohnsmith said. Unfortunately, I didn't get any new results. That being said, I figure that now would be a good time to cut to the chase. The following is the [COLOR="Red"]**UBUNTU**[/COLOR] copy of **[COLOR="Red"]menu.lst:[/COLOR]**

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		0

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=416f2dee-f158-4cdc-92d4-a7ec74d926e2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=416f2dee-f158-4cdc-92d4-a7ec74d926e2

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
# defoptions=quiet splash vga=792

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		416f2dee-f158-4cdc-92d4-a7ec74d926e2
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=416f2dee-f158-4cdc-92d4-a7ec74d926e2 ro quiet splash vga=792 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		416f2dee-f158-4cdc-92d4-a7ec74d926e2
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=416f2dee-f158-4cdc-92d4-a7ec74d926e2 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		416f2dee-f158-4cdc-92d4-a7ec74d926e2
kernel		/boot/memtest86+.bin
quiet

title nUbuntu Grub Menu
configfile (hd0,1)/boot/grub/menu.lst

title Windows XP
root (hd0,2)
chainloader +1
### END DEBIAN AUTOMAGIC KERNELS LIST
```


This is my **[COLOR="Red"]NUBUNTU[/COLOR]** GRUB [COLOR="Red"]**menu.lst**[/COLOR] file:

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
# kopt=root=UUID=66dae6a4-e37d-4ec0-a50d-8319dd5d440f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=66dae6a4-e37d-4ec0-a50d-8319dd5d440f

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		66dae6a4-e37d-4ec0-a50d-8319dd5d440f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=66dae6a4-e37d-4ec0-a50d-8319dd5d440f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		66dae6a4-e37d-4ec0-a50d-8319dd5d440f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=66dae6a4-e37d-4ec0-a50d-8319dd5d440f ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		66dae6a4-e37d-4ec0-a50d-8319dd5d440f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=416f2dee-f158-4cdc-92d4-a7ec74d926e2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=416f2dee-f158-4cdc-92d4-a7ec74d926e2 ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.10, memtest86+ (on /dev/sda5)
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot

title nUbuntu Grub Menu
configfile (hd0,1)/boot/grub/menu.lst

title Windows XP
root (hd0,2)
chainloader +1
```

I have no idea why neither of these items are taking charge of startup. I also have no idea why I can't select any of my OS's. Thnx for all the responses so far!!! I love the Ubuntu community!

-TheReaper-

---

### Post by caljohnsmith on 2008-11-26
OK, I believe I see your problem; you have the "timeout" line in your Ubuntu menu.lst set at 0 seconds, so that's why you don't see the Grub menu on start up. How about when you automatically boot into Ubuntu, pull up the menu.lst again:
```
gksudo gedit /boot/grub/menu.lst
```
And change the "timeout" line to:
```
timeout 10
```
Reboot, and I think you should be all set, but let me know if you run into problems.

---

### Post by thereaper243 on 2008-11-27
> **caljohnsmith said:**
> OK, I believe I see your problem; you have the "timeout" line in your Ubuntu menu.lst set at 0 seconds, so that's why you don't see the Grub menu on start up. How about when you automatically boot into Ubuntu, pull up the menu.lst again:
```
gksudo gedit /boot/grub/menu.lst
```
And change the "timeout" line to:
```
timeout 10
```
Reboot, and I think you should be all set, but let me know if you run into problems.

Firstly I want to thank everyone who helped out with my mess. You guys have secured my Ubuntu destiny. This community is amazing and you should all be very proud of yourselves. I have never found a more dedicated virtual community. I play old war boardgames and those guys aren't even that dedicated, despite the fact that they have held on to their gaming way of life since the late seventies! Again, thanks so much for your help.

The Reaper243
PS-Caljohnsmith... could you PM me about how to add another GRUB entry for an installation of Mac OS X? (Thanks in advance!)

---

