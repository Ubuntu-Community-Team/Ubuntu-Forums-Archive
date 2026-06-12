---
title: "Want to delete Win7 from Ubuntu+XP+Win7 triple boot"
date: 2009-07-28
forum: Installation &amp; Upgrades
---

### Post by cosmicappuccino on 2009-07-28
At the moment I have Ubuntu, XP, and Windows 7 Beta on different partitions in my computer. I want to get rid of Windows 7 now (it expires soon).

I don't know what is the best way to do this - the Microsoft page doesn't include instructions for my situation. I don't need any of the files in my Win7 partition; I've hardly used it.

At the moment, I get the Ubuntu boot screen upon starting the computer up, where I get the options of booting Ubuntu, XP, or Win7. Ubuntu boots fine. If I choose XP, the computer fails to boot. If I choose Win7, I get the Win7 boot screen - here, I can choose from XP and Win7, both of which boot correctly.

I'd like to be able to boot XP and Ubuntu from the initial Ubuntu boot screen. Any advice, please?

Thank you for reading this. :)

---

### Post by coffeecat on 2009-07-28
It sounds as though the Win7 bootloader is configured so that you have the choice of XP or W7, but that the XP entry in grub is faulty. Do you get a grub error when you choose XP from the grub menu?

If it wasn't for this problem, all you would have to do is to edit your grub's menu.lst to remove the W7 entry. You could then re-use the W7 C: partition however you want. You don't have to uninstall W7 - you could either reformat the partition or simply delete all the files on it and use it for data storage. Its NTFS filesystem is read/writeable in Ubuntu and XP will simply see it as E:, F:, G: or whatever.

But of course, if you remove the W7 files, you wan't be able to boot XP, so let's see if we can get XP booting from grub first.

Post the following:

The contents of /boot/grub/menu.lst

And the terminal output of:

```
sudo fdisk -l
```

---

### Post by cosmicappuccino on 2009-07-28
Thanks for the reply, coffeecat! :)

In response to your questions:

1. When I choose XP from the ubuntu boot menu, I get hp pc system recovery.

2. This is my menu.lst:

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
# kopt=root=UUID=d9450401-fd27-49b8-a2ff-826d8f00a72b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=d9450401-fd27-49b8-a2ff-826d8f00a72b ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=d9450401-fd27-49b8-a2ff-826d8f00a72b ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

3. This is the terminal output from *sudo fdisk -l*:

```

Disk /dev/sda: 80.0 GB, 80060424192 bytes
240 heads, 63 sectors/track, 10341 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x4fa9eb4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         732     5533888+   b  W95 FAT32
/dev/sda2             733        2899    16382520    7  HPFS/NTFS
/dev/sda3            2900        4966    15626520    7  HPFS/NTFS
/dev/sda4            4967        8971    30277800    5  Extended
/dev/sda5            4967        6904    14651248+  83  Linux
/dev/sda6            6905        8842    14651248+  83  Linux
/dev/sda7            8843        8971      975208+  82  Linux swap / Solaris

```

Hope this is enlightening... :confused:

Thanks again

---

### Post by dutchman72 on 2009-07-28
Your menu.lst is pointing to the wrong partition for your XP.

Since you mentioned that the Win 7 choice from grub works (hd0,1) then you will need to change the XP line to point to hd0,2. Since the default setup thought the HP recovery partition was being used as XP instead. This has happened to me before as well, and I learned to wipe that portion of the disk out just to stop headaches later (plus I never want to recover my Windows...ever).

---

### Post by coffeecat on 2009-07-28
I'd agree with dutchman72, except that there's something that's a bit odd. So, before you edit menu.lst, a few thoughts.

In your grub menu, the entry titled "Windows NT/2000/XP" points to (hd0,0) which is grubspeak for sda1, and that's why you get the HP PC recovery when you choose the NT/XP entry. So far, so good.

The Vista entry points to (hd0,1) which is grubspeak for sda2, and I presume that's how you get to Windows 7. Am I correct?

The third partition - sda3, which would be (hd0,2) in grub - presumably contains your XP partition and dutchman72 is correct in saying you need a grub entry pointing to (hd0,3) for this.

HOWEVER, I find it strange that HP should set up the system with the recovery partition on sda1 and XP on sda3. What would sda2 have been originally? How did W7 get there? Curious.

Whatever, I suggest you edit menu.lst as follows. Open a terminal, and...

```
gksudo gedit /boot/grub/menu.lst
```And edit the two Windows stanzas so you get three, as follows:

```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        HP recovery partition
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista/Windows 7
root        (hd0,1)
savedefault
makeactive
chainloader    +1

title        Windows XP
root        (hd0,2)
savedefault
makeactive
chainloader    +1
```Save the file and then boot up each entry and see what you get. Then you can be sure that sda3 really is the XP partition, and you can then delete the W7 entry if you want. Personally, I wouldn't advise removing the recovery partition entry. You might just want it in the future, but that's up to you.

---

### Post by cosmicappuccino on 2009-07-29
Thanks, both of you.

I followed coffeecat's instructions, and HP Recovery and Windows 7 both boot fine. However, when I choose the XP option, I get a black screen saying "Starting up..." on the first line, and with a string of nonsensical characters on the second line, and nothing else. I waited a while and nothing else seems to happen.

Any ideas? Thanks...

---

### Post by cosmicappuccino on 2009-07-29
Here's some possibly useful info:

Using a partition manager, I get the list of partitions (in order) to be:

1. HP Recovery
2. HP Pavilion (XP)
3. Windows7
4. Other (Ubuntu)
5. Other (Ubuntu)
6. Unallocated

Also, the contents of XP's boot.ini file are:

> 
;
;Warning: Boot.ini is used on Windows XP and earlier operating systems
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional"/FASTDETECT


---

### Post by coffeecat on 2009-07-29
Hmmm.. Well, if XP still boots up fine from the W7 bootloader, then the XP partition must be OK. XP has to be on sda3 from what you've told us, therefore the grub stanza *should* work, and you are not getting a grub error. I'm really out of sensible ideas, but I do have two suggestions.

- Try changing the XP menu.lst stanza to...

```
title        Windows XP
rootnoverify   (hd0,2)
savedefault
makeactive
chainloader    +1
```

- And/or try running a chkdsk of the XP C: partition from Windows 7.

Although, to be honest, these are both shots in the dark.

---

### Post by coffeecat on 2009-07-29
> **cosmicappuccino said:**
> Here's some possibly useful info:

Using a partition manager, I get the list of partitions (in order) to be:

1. HP Recovery
2. HP Pavilion (XP)
3. Windows7
4. Other (Ubuntu)
5. Other (Ubuntu)
6. Unallocated

...

So the partition manager is telling us that XP is on the second partition and W7 on the third, whereas when grub boots into the second partition, you get Windows7. :confused:

I'm confused. :(

---

### Post by cosmicappuccino on 2009-07-29
I've solved it!!! :D

In case it is useful for anyone (it's probably pretty much the same if the problem is Vista rather than Windows 7), here's what I did:

[I](The steps previously mentioned in this thread aren't necessary.)

1. Boot into Windows 7. Open a command prompt with admin privileges (right-click Command Prompt and choose "Run as administrator").

2. (This step removes the ability to boot into Windows 7! So be careful.) Type in: ```
bcdedit /delete {current} /f /cleanup
``` ...and hit enter. It will say the task was successfully completed, or something like that. 

3. Restart computer. (Be aware you won't be able to access Windows 7 again, after restarting.) Choosing the Windows option on the Ubuntu boot screen will now automatically take you into XP.

4. Using XP or Ubuntu, whichever you prefer, you can now get rid of the Windows 7 partition.[/I]

Coffeecat, to clear your confusion (and thanks for sticking with me!): here's my understanding of what happened. When Windows 7 was installed, it created some files in the XP partition that would make bootmgr manage the booting of both Windows partitions, rather than ntldr which used to manage XP booting. So, although Windows 7 was on the third partition, it had to be booted via the second partition. Since the bootmgr came with Windows 7, I thought it was like a "part" of Windows 7, which must have increased everyone's confusion. But anyway, it turned out the booting is managed from C: so just deleting the Windows 7 option and partition will result in making XP the default option. :)

---

### Post by coffeecat on 2009-07-29
> **cosmicappuccino said:**
> Coffeecat, to clear your confusion (and thanks for sticking with me!): here's my understanding of what happened. When Windows 7 was installed, it created some files in the XP partition that would make bootmgr manage the booting of both Windows partitions, rather than ntldr which used to manage XP booting. So, although Windows 7 was on the third partition, it had to be booted via the second partition. Since the bootmgr came with Windows 7, I thought it was like a "part" of Windows 7, which must have increased everyone's confusion. But anyway, it turned out the booting is managed from C: so just deleting the Windows 7 option and partition will result in making XP the default option. :)

Thanks for the explanation - that one's new to me. I'd read that the old XP/Vista NTLDR had been replaced by bootmgr, but I didn't know any of the details. It also explains how Windows 7 seemed to be on sda2 when HP must have stuck XP there.

> bcedit /delete {current} /f /cleanupAnd the Windows fan crowd makes fun of Linux for its "obscure" terminal commands!

---

### Post by cosmicappuccino on 2009-07-29
> **coffeecat said:**
> And the Windows fan crowd makes fun of Linux for its "obscure" terminal commands!

Haha ;)

---

