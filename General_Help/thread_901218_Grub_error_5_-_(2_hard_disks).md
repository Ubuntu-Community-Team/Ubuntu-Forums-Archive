---
title: "Grub error 5 - (2 hard disks)"
date: 2008-08-26
forum: General Help
---

### Post by dhtj on 2008-08-26
Hi all!
I use ubuntu from 1 month (with wubi) but it (wubi) crashes evry week :(
Now I,m trying to instal ubuntu with GRUB.
I make evrything-mount points, drives, swap space ....
When is ready I must restart my comp, and then: :lolflag:
> GRUB loading Stage 1.5.

GRUB loading, please wait&#8230;
Error 5

My friends from bulgarian ubuntu forums says: The problem is from 2 hard disks!
I have one 30gb (master) ata maxtor drive and one 160gb (slave) ata excel store drive.


> My discs:
Hard 1 (master) - 
                   local disc C:-10gb-win-ntfs
                    Data E:-20gb-ntfs
Hard 2 (slave)  -  
                  Store D:-150gb-ntfs
                  ext3 partiton-7gb-ubuntu
                  linux swap partition-1gb
I tryed to instal ubuntu 5 times but.... :(
Sorry for my bad english :)

edit: my ubuntu is Hardy

---

### Post by Garratt on 2008-08-26
hah, yea you and everyone else....;

go here and download this:

[http://www.supergrubdisk.org/index.php]("http://www.supergrubdisk.org/index.php")

save it to a CD (it's ISO), or thumbstick (USB) ---> if you save to USB make sure that you change bios settings so USB will be the first boot.

This thing will fix whatever grub has done, you just need to read up as much as you can, and look through the super grub boot-loader forums to see problems like yours.

You will more than likely need to choose the "LIVE SWAP" option.

I'm not sure what error 5 is, but i just had error 17 unable to mount partition which was cause by grub installing on the wrong HDD and deleting the windows boot, even tho Ubuntu installed on the correct drive...

so just read up as much as you can, you may not get it straight away, it took me 2-3days to fix mine.. so good luck.

you can read these 2 extra posts for more info:

[my thread on general forums]("http://ubuntuforums.org/showthread.php?t=898326")

[eggblims post on genral]("http://ubuntuforums.org/showthread.php?t=901180")

---

### Post by Jonie on 2008-08-26
Start your computer again with ubuntu cd. Get into the rescue mode.

Start grub

At grub boot prompt type:

grub> root (hd1,1)
grub> install /grub/stage1 d (hd1) /grub/stage2 p
grub> quit

The second number (hd1, _1_ ) means that Linux is on the second primary partition on the second hdd. On the other hand, it may on extended one, i.e. fifth (hd1, 4). Check parttion layout with fdisk -l /dev/sdb if you're unsure. Remember, that grub counts from 0, not from 1.

Copy the now created mbr to usb stick or whatever you have.

First, create a copy of mbr:

dd if=/dev/sdb of=grub.mbr bs=512 count=1

Assuming that you know how to copy the file under linux, now get into windows. If you can't start windows, you have to run recovery console from the windows cd, then type fixmbr c: and quit.

Now, in Windows copy the grub.mbr file into the root of c:. Add an entry into the xp boot loader (boot.ini, which is a hidden system file):

C:\grub.mbr="Ubuntu Hardy Heron 8.04.1 LTS"

---

### Post by dhtj on 2008-08-26
Jonie you are the man !
I will try this tonight!
A rescue mode? where ?
Thank you very mutch

---

### Post by caljohnsmith on 2008-08-26
> **Jonie said:**
> Start your computer again with ubuntu cd. Get into the rescue mode.

Start grub

I think it would be helpful to let dhtj know exactly how to "start grub" first in case he doesn't know:
```
sudo grub
```
> **Jonie said:**
> 
At grub boot prompt type:

grub> root (hd1,1)
grub> install /grub/stage1 d (hd1) /grub/stage2 p
grub> quit

I think you may be remembering incorrectly, because there is no "install" command in the Grub CLI. Here is how to install Grub to the master boot record (MBR) of the same HDD that Ubuntu is on, which I think is what you mean:
```
grub> find /boot/grub/stage1 
[COLOR="Blue"][that should find your Ubuntu partition, dhtj, in the form (hdX,Y), use that:][/COLOR]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit

```
But the problem with the above commands, dhtj, is that you weren't clear about which HDD you are booting from, and which HDD has your Ubuntu. So please clarify that, and also post the output of:
```
sudo fdisk -lu
```
> **Jonie said:**
> 
Copy the now created mbr to usb stick or whatever you have.

First, create a copy of mbr:

dd if=/dev/sdb of=grub.mbr bs=512 count=1

Assuming that you know how to copy the file under linux, now get into windows. If you can't start windows, you have to run recovery console from the windows cd, then type fixmbr c: and quit.

Now, in Windows copy the grub.mbr file into the root of c:. Add an entry into the xp boot loader (boot.ini, which is a hidden system file):

C:\grub.mbr="Ubuntu Hardy Heron 8.04.1 LTS"
Although this method will work, there is no need to add complexity and do it this way; dhtj said he wanted to install Grub, and not modify his Windows XP boot loader to load Grub. But to get Grub installed to the correct HDD, dhtj, you need to first clarify what is on your HDDs and which HDD boots on startup. We should be able to work from there. :)

---

### Post by dhtj on 2008-08-26
> **caljohnsmith said:**
> 
to get Grub installed to the correct HDD, dhtj, you need to first clarify what is on your HDDs and which HDD boots on startup. We should be able to work from there. :)

My discs:
Hard 1 (master) - 
local disc C:-10gb- windows -ntfs
Data E:-20gb-ntfs
Hard 2 (slave) - 
Store D:-150gb-ntfs
ext3 partiton-7gb - ubuntu
linux swap partition-1gb

---

### Post by Jonie on 2008-08-26
> **caljohnsmith said:**
> 

I think you may be remembering incorrectly, because there is no "install" command in the Grub CLI. 



There is one:

[http://www.gnu.org/software/grub/manual/html_node/install.html#install]("http://www.gnu.org/software/grub/manual/html_node/install.html#install")

It's just to tell grub to look for stage2 on the second hdd, independently of what it "thinks" it's booting from.

> **caljohnsmith said:**
> 
Although this method will work, there is no need to add complexity and do it this way; dhtj said he wanted to install Grub, and not modify his Windows XP boot loader to load Grub.

He's got two drives for two OSes, so why not use them so? ;)

The simple method would surely work, if he were to go through bios boot menu every now and then, but we even don't know if he's got one.

---

### Post by caljohnsmith on 2008-08-26
> **Jonie said:**
> There is one:

[http://www.gnu.org/software/grub/manual/html_node/install.html#install]("http://www.gnu.org/software/grub/manual/html_node/install.html#install")

You're right, I stand corrected. :oops: When I read the entire Grub manual many moons ago, I think I didn't pay any attention to that command since "setup" has always worked for me and all other Ubuntu users I've talked to. And like it says in the manual, that's a fairly complex command and should normally be used only if "setup" doesn't work.
> **Jonie said:**
> 
It's just to tell grub to look for stage2 on the second hdd, independently of what it "thinks" it's booting from.

Fair enough, but you can accomplish exactly the same thing by first doing the "root (hdX,Y)" command before "setup", just like you did. That will make "setup" look in (hdX,Y) for all its stage files. If there is any doubt which HDD and partition contains the stage files, I think it is better to do the "find /boot/grub/stage1" command, which returns exactly the (hdX,Y) where the stage files will be (assuming they're all in the same place). :)

Jonie, I've used your method before on a single HDD that had both Windows and Ubuntu with success, but have you actually tested it in a setup using two HDDs, where you put the Grub MBR in the windows boot loader of the *other* HDD? I'm wondering if that will work, because when you created that Grub MBR, it points to a partition *on its same disk* for all its system files (stage2, etc). When you move that Grub MBR onto the other Windows HDD, it might then look on the Windows HDD for its system files instead of the other HDD. 

Dhtj, since you've clarified that Ubuntu is on your second slave HDD, and if Jonie has tested his method to work on dual HDDs, I would agree with Jonie's solution; you could just modify your Windows boot loader to load Grub. I would recommend though following my method for finding your correct Ubuntu partition, because we don't know for sure which partition has your Ubuntu; you forgot to post the output of "sudo fdisk -lu" to tell us that. And just keep in mind that Jonie's method assumes Ubuntu is on (hd1,1) which is probably correct, but it is better to make sure I think using the "find /boot/grub/stage1" command. It's up to you though. And lastly, make sure you run that "dd" command as root with sudo.

Thanks again for the correction, Jonie. :)

---

### Post by Jonie on 2008-08-26
Here you are :)

I'm only not quite sure, if setup (hd1) would not just embed sector offset to stage2 within the disk, as it's the same as root disk and for that reason I mention BIOS menu - in fact it may be as if there were commands relating to hd0, the only difference being the disk to be written. The more tricky method was to assure we are dealing with BIOS drive 0x81, just in case BIOS fools GRUB. If hd1 were to be mapped so easily to physical second disk, why doesn't it work out of the box?

Anyway, dhtj, make sure which one is the Linux partition and good luck!

---

### Post by Jonie on 2008-08-26
Here you are :)

I'm only not quite sure, if setup (hd1) would not just embed sector offset to stage2 within the disk, as it's the same as root disk and for that reason I mention BIOS menu - in fact it may be as if there were commands relating to hd0, the only difference being the disk to be written. The more tricky method was to assure we are dealing with BIOS drive 0x81, just in case BIOS fools GRUB. If hd1 were to be mapped so easily to physical second disk, why doesn't it work out of the box?

Anyway, dhtj, make sure which one is the Linux partition and good luck!

edit:
> **caljohnsmith said:**
> 
When you move that Grub MBR onto the other Windows HDD, it might then look on the Windows HDD for its system files instead of the other HDD.


That's why this mbr is carefully prepared with install command.

---

### Post by dhtj on 2008-08-26
> **caljohnsmith said:**
> you forgot to post the output of "sudo fdisk -lu" to tell us that. 
I cant post this now because my ubuntu CD is gone :lolflag: 
im kiding , one friend take it for 1 day
is this shot good?
[IMG]http://www.download.bg/upl/attachments/untitled.4100.JPG[/IMG]

---

### Post by Jonie on 2008-08-26
In this case your GRUB root is (hd1,4).

And I know why it happens. GRUB is definitely looking for stage2 on hd0, i.e. first disk. Because it's small (10 GB), GRUB looks for stage2 beyond it's capacity - that's what error 5 is (geometry error).

Apply that dirty hack from the post you thanked (substitute  hd1,1 with hd1,4). And do report your progress.

If your GRUB works (I see you can boot Windows), you may just do at grub prompt of the rescue shell:

grub> root (hd1,4)
grub> install /grub/stage1 d (hd0) /grub/stage2 p menu.lst
grub> quit

The crucial trick is the parameter d - to use drive defined in root, i.e. hd1.

Remember, menu.lst is like list, not first :)

---

### Post by caljohnsmith on 2008-08-26
> **Jonie]grub> install /grub/stage1 d (hd0) /grub/stage2 p menu.lst[/QUOTE]
I did a little reading about the "install" command, and I think I see some serious problems with that command you gave, Jonie. Using /grub/stage1 would only be correct if the /boot/grub/ directory were being mounted on /boot in the root filesystem said:**
> And I know why it happens. GRUB is definitely looking for stage2 on hd0, i.e. first disk. Because it's small (10 GB), GRUB looks for stage2 beyond it's capacity - that's what error 5 is (geometry error).
According to the Grub manual:
> Error 5 : Partition table invalid or corrupt
This error is returned if the sanity checks on the integrity of the partition table fail. This is a bad sign. 
So it's not a geometry error. He may actually have something wrong with his slave HDD's partition table, and that may be the main thing impeding him at this point.

---

### Post by Jonie on 2008-08-27
Yep, you were right about the full path. Wrote in a hurry.

According to to the picture he posted, a Linux partition in his setup is the first logical drive of an extended partition (don't be confused with an extended fs), which is always assigned sda5, regardless whether the partitioning software assigned extended parttion as sda2 or sda4 (either is correct).

Anyway, his problem is how to load stage2. Geometry, partition table, whatever you call it, is that the physical sector to load stage 2 is non-existent and it's true cause first disk is smaller than the starting address of the Linux partition (GRUB will continue reading first disk). Even if the first disk were bigger there wouldn't be a Linux partition at given offset. The two partition tables simply don't match

Error 5 happens in mutidrive scenarios:

[http://www.linuxforums.org/forum/installation/77415-grub-error-5-dual-boot-winxp-mc-suse-10-1-a.html]("http://www.linuxforums.org/forum/installation/77415-grub-error-5-dual-boot-winxp-mc-suse-10-1-a.html")

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=758712]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=758712")

But I can agree that the first suggestion (installing grub to hd1 and using nt loader) is safer as long as windows booting is concerned. But in this case parameter d is also needed, as we'll be still mapping hd0 as booting drive in BIOS and need to do the switch somehow.

Edit:

GRUB cannot "jump" from hd0 to hd1 to find stage 2 by itself. If hd0 had ext3 filesystem with stage2 it would be no problem to boot either disk, without any hacking.

---

### Post by dhtj on 2008-08-28
Now I have only windows,
I will instal ubuntu again, and on step7 I can choose where to instal GRUB. On deafult is (hd0), I must write (hd1,4) ???

---

### Post by Jonie on 2008-08-28
Hd(1,4) is where you install Ubuntu, (hd0) is the MBR of the first hard disk to install grub, however the problem may repeat. If you're stuck again you may follow the instructions from post #3 (replacing (hd1,1) with (hd1,4). Or you may install grub straight to (hd1) from Ubuntu and use your BIOS menu each time to choose which HD to boot from. Such menu is often accessible via one of the last of function keys. With 2 disks you've got to have some way, either hacking your grub or using your BIOS to boot to redirect booting process from hd0 to hd1, as hd0 has only windows and nothing to boot linux from.

---

### Post by dhtj on 2008-08-28
I instaled grub on (hd1,4)  but windows mbr dont see it ;(
what is this trick with bios ?

---

### Post by caljohnsmith on 2008-08-28
> **dhtj said:**
> I instaled grub on (hd1,4)  but windows mbr dont see it ;(
what is this trick with bios ?
The trick that Jonie refers to is that most modern computers allow you to hit F8 or F12 (or possibly something else) on start up, and then you can choose which HDD you want to boot from. But first make sure you've got Grub installed to your Ubuntu HDD's MBR; from the Live CD just do the following:
```
sudo grub
grub> find /boot/grub/stage1
[COLOR="Blue"][should return (hd1,4), if so then proceed:][/COLOR]
grub> root (hd1,4)
grub> setup (hd1)
grub> quit

```
Let us know how it goes.

---

### Post by dhtj on 2008-08-28
i love grub :mad::mad::mad::mad:
[IMG]http://www.download.bg/upl/attachments/Screenshot.8909.png[/IMG]

---

### Post by caljohnsmith on 2008-08-28
I think you forgot the "root (hd1,4)"... :)

---

### Post by Jonie on 2008-08-28
John Smith from California ;) : I found it when exploring subject deeper:

dhtj: See the previous post and do what you're told :)

[http://en.opensuse.org/Bugs/grub]("http://en.opensuse.org/Bugs/grub")

>  File Systems or: How to proceed after stage1

Besides the message printing, stage1 contains just enough code to load the blocks for the next stage. If that fails it is usually because of one of two reasons:

   1. the stage1 running is currently "orphaned", and the further parts of the boot loader aren't any more at the physical disk location where the grub installation has recorded them, or
   2. the BIOS disk ordering is wrong, meaning stage1 is looking for the next stage on a totally wrong disk drive. 

In the former case it helps to install a generic MBR or otherwise make sure the correct stage1 gets loaded, maybe after properly (re-)installing grub to disk. In the latter case it is probably necessary to force a BIOS drive number into stage1 to continue from.

This is accomplished using the "d"-flag (just the lonely lowercase letter) in the "install" command in /etc/grub.conf. Yast will do this automatically **whenever stage1 and stage2 are on different BIOS disks. the "setup" command in /etc/grub.conf will likewise do it automatically. But there are also BIOSes that report a bogus drive number about the disk stage1 was loaded from. Without the "d"-flag, stage1 will continue loading from "that same disk" and hence fail unless "d" is specified manually**

And then:

[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/8497]("https://bugs.launchpad.net/ubuntu/+source/grub/+bug/8497")

> grub guessed BIOS disk order incorrectly

I think, that might be the case. Usually, GRUB is wise enough to handle such two disk setup without a glitch.

Personally, I've seen few Intel 9xx desktops with fixed USB flash card readers that reported them in BIOS as hd0, no matter what.

---

### Post by caljohnsmith on 2008-08-28
Jonie, if there is any ambiguity about which BIOS HDD corresponds to which Grub HDD, then I believe one simple solution is to manually tell Grub the mapping:
```
sudo grub
grub> device (hd0) /dev/sda
grub> device (hd1) /dev/sdb
```
And then you can run the root/setup commands. I don't understand yet how specifying the "d" flag with a drive like (hd0) with the "install" command will make (hd0) correspond to any different drive then what the "setup" command uses. In other words, if we first do:
```
grub> root (hd1,4)
```
Then the following two commands will both install Grub's stage1 to the MBR of (hd1), whichever BIOS drive that may be:
```
grub> setup (hd1)
grub> install /boot/grub/stage1 d (hd1) /boot/grub/stage2 p /boot/grub/menu.lst
```
The only difference between the above commands is that the "setup" command will embed the stage1.5 file into the sectors immediately after the MBR, while the "install" command doesn't (but it can be configured to do so if desired).

Thanks for posting those bugs, Jonie; that's very useful info. If you have any further insight to shed light on any of this, I'm all ears. :)

---

### Post by Jonie on 2008-08-31
I don't know what the parameter "d" really does. I'd have to recreate the situation and then install GRUB both ways, and diff produced MBRs at last. But I suspect it sets a number (0x80, 0x81 and so on if there are more disks) in the so called Boot Parameter Block in MBR. This parameter is called "Boot Drive" and tells GRUB where to look for the partition table. For a setup with master and slave disks on the same controller I see however no reason why there's got to be something messed up here. 

But, if he installed to GRUB to MBR of hd1 (slave) and I assume he did in his first attempt, as he didn't lose the ability to boot windows, then he tried to boot into Linux from BIOS boot menu. What's up then? BIOS is made to boot legacy systems as DOS, so it remapped 0x81 (slave) as 0x80 and 0x80 as 0x81, then booted. In this case the boot order in BIOS was reversed and the parameter "d" was not used by Ubuntu as GRUB was on the same disk as stage2 and it didn't have to be specified at all. So GRUB took the "Boot Drive" from BPB, which was 0x81 (that's where GRUB was to be installed) and read partition table from 0x81 (small master disk in this case of reversal).

In such situation it's better to use ntloader, install GRUB this way

```
grub> root (hd1,4)
grub> install /grub/stage1 d (hd1) /grub/stage2 p
```

and copy the MBR from hd1 to the root of drive C: by the method described earlier

or install GRUB to MBR of second hard disk which would then be called (hd0), but first do a reversed device map 

```

(hd0) /dev/sdb
(hd1) /dev/sda
```

to have the ability to use BIOS boot menu.


Of course, just to install GRUB to hd0 the default way should be just fine, too as all that seems to happen in this case just because of our friend was too scary to overwrite Windows MBR. 

A computer with ATA only disks can't rather have such buggy BIOS, some SATA or CF readers are required.

This problem with ATA and SATA I lately tested personally. Put and ATA disk to SATA and boot from CD, then ATA becomes 0x80. However if you boot from SATA and it's 0x80 and ATA is 0x81. There is no way to boot from CD and have it reversed aside from customizing the device map. I also tested that booting XP from such added disk is impossible from boot menu (BIOS order remapping) unless ATA is specified as Primary Boot Device.

To sum it up, if dhtj doesn't want to fiddle with devices and boot order and to have Windows MBR instact it's best to use ntloader and safest at that for any noob may read it.

I think a noob would be already totally confused, but anyway the discussion may be useful for someone, some day and last but not least it recorded here, on Ubuntu forums :)

Thanks for posting, too. :)

---

### Post by dhtj on 2008-09-09
i instal ubuntu on first hard disk (without win) and evrything is alright
thank you very mutch:lolflag:

---

### Post by dhtj on 2008-09-14
oh i return my windows for the games:lolflag:
i want dual boot
now my partitions are
[IMG]http://www.download.bg/upl/attachments/untitled.6042.JPG[/IMG]
and i will split up C: on 3 partitions-c:, swap, ext3
but ext3 must be:  primary or extendet??

---

### Post by Jonie on 2008-09-14
> and i will split up C: on 3 partitions-c:, swap, ext3
but ext3 must be: primary or extendet?? 

For Linux it doesn't really matter. If I could give you an advice, put your ext3 on first hard disk and tailor some space on the second hard disk for swap - if you have much memory this doesn't have to be a lot, but make it at least equal the size of your RAM so you could use it for suspend to disk. Remember that 32-bit system can't use more than 4 GB (RAM + swap) total.

---

### Post by dhtj on 2008-09-15
> **Jonie said:**
> 
tailor some space on the second hard disk for swap - if you have much memory this doesn't have to be a lot, but make it at least equal the size of your RAM so you could use it for suspend to disk.  total.

i have 1gb+256mb ram
i thing 1gb swap is good???
 
and why you say
tailor some space on the [COLOR="Red"]second hard disk[/COLOR] for swap ? 
why not on first?

edit: aaa i know (?) my second hard is faster than first (7200rpm)

---

### Post by caljohnsmith on 2008-09-15
> **dhtj said:**
> i have 1gb+256mb ram
i thing 1gb swap is good???
 
and why you say
tailor some space on the [COLOR="Red"]second hard disk[/COLOR] for swap ? 
why not on first?

edit: aaa i know (?) my second hard is faster than first (7200rpm)
Maybe Jonie will explain why he recommends putting the swap file on the other HDD :), but offhand I don't see any advantage to doing that, only disadvantages. In case you want my opinion, I would do like you had planned and keep the swap partition on the same HDD as your main Ubuntu install.

---

### Post by Jonie on 2008-09-15
Back to the blackboard... dhtj got it ;) - just for performance reasons. :))) 

Ubuntu with 1 GB of RAM and it's default vm.swappiness=60 will mostly ignore it... but if you follow what kernel developers say, you'd be better off with a lot of swapping and big buffers, the "Vistish" way.

----
[SIZE="1"]**Of course it all is just a speculation, people usually tend to swap to where they find to be the most convenient, an area under the carpet is an ubiquitous example.**[/SIZE]

---

### Post by dhtj on 2008-09-18
i'm ready
i had a little problem : unable to resolve host dhtj-ubuntu but i  find a theme here for this:lolflag:
thank you very mutch
the moderators can lock the theme:)

---

