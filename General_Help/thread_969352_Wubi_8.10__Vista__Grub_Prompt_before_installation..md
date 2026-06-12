---
title: "Wubi 8.10 / Vista / Grub Prompt before installation. help"
date: 2008-11-03
forum: General Help
---

### Post by DeltaUK on 2008-11-03
hi
i am almost about to give up on this..
After installing wubi inside windows.. which seems to be successfull.. after reboot i choose ubuntu and instantly face the dreaded grub4dos grub> prompt.
so far trying a different version of grub4dos didnt work..
trying easybcd and adding a wubi entry to bootloader didnt work.

i am stuck, help!

(using easybcd neogrub bootloader gave file not found)

---

### Post by ago on 2008-11-03
> **DeltaUK said:**
> hi
i am almost about to give up on this..
After installing wubi inside windows.. which seems to be successfull.. after reboot i choose ubuntu and instantly face the dreaded grub4dos grub> prompt.
so far trying a different version of grub4dos didnt work..
trying easybcd and adding a wubi entry to bootloader didnt work.

i am stuck, help!

(using easybcd neogrub bootloader gave file not found)

It might be that the partition you are installing to is not visible at boot (which usually happens with encrypted drives, raids, or external devices). You can browse the devices from the grub4dos shell by using tab completion.

---

### Post by DeltaUK on 2008-11-03
i not using raid or external drives.. my laptop has 1 internal drive.. the only thing i can think that could cause a problem is that it has a recovery partition as well as the main partition.

how do i use tab completion?

---

### Post by DeltaUK on 2008-11-03
sry for double post but i rele would like to get this working as soon as possible!

can anybody chat on IM like msn to guide me? thx

---

### Post by ago on 2008-11-03
press ESC after ubuntu, then C for the grub shell.
there type

kernel (hd[HIT TAB HERE]

it will show a possible list of values, select one, and type the tab key again. See if you can navigate to c:\ubuntu\install\.

Of course there is no C: that is windows stuff, grub uses (hdX,Y) where X is the drive number starting at 0 and Y is the partition number. So partition 2 on drive 1 is (hd0,1)

---

### Post by DeltaUK on 2008-11-03
I was unable to press esc b4 the grub prompt came up.. so i tried insert to see what was happening.

warning: MBR cylinders (24322) is not equal to the bios one (16383)

warning: MBR sectors (390732930) is greater than the bios one (390721968). Some bioses can hang when tryint to access sectors exceeding bios limit.
LBA, C/H/S = 24322/255/63, Sector Count / size = 390732930

Starting cmain() ... Open / Default .. failure

---

### Post by ago on 2008-11-04
Is it a cmain failure? Can you type commands? If so follow the above instruction.

---

### Post by DeltaUK on 2008-11-04
i can type in the grub prompt.. 

i get a choice of hd0,0 and hd0,1

it says they are both ntfs and 0,1 is active

cant do anything other than that.

---

### Post by mutlus on 2008-11-05
I had the same problem in fact. First time i couldn't do it but after i've done things below, it worked. I don't know these were the problems but give it a try;

1-While installing Wubi, close your antivirus and firewall (and security programs all)
2-After install, directly restart your computer, don't wait for anything!!!

First time i installed, hadn't done these but at second time i've done these and worked.  Give a shot...

---

### Post by DeltaUK on 2008-11-05
> **mutlus said:**
> I had the same problem in fact. First time i couldn't do it but after i've done things below, it worked. I don't know these were the problems but give it a try;

1-While installing Wubi, close your antivirus and firewall (and security programs all)
2-After install, directly restart your computer, don't wait for anything!!!

First time i installed, hadn't done these but at second time i've done these and worked.  Give a shot...

thats what im doing =[

---

### Post by gibbon1993 on 2008-11-05
I'm having the same problem here!

I downloaded Ubuntu 8.04 months ago and have upgraded and used 8.10 a handful of times except now when I boot I just get a grub> prompt.

The startup text is the same "Starting cmain() ... Open / Default .. failure" and when I use tab I get a choice between 0,0 and 0,1, both shown in the format:
Partition num: x, Filesystem type is ntfs, partition type 0x7

Please help this is really bugging me!

---

### Post by gibbon1993 on 2008-11-05
Sorry for double post just getting a bit frustrated with it.
I found my way to the ubuntu file on C:\ and it can't find the boot directory, and install only contains '.fuse_hidden000...' Found wubildr.mbr in C:\ so attempted to boot it. It just stays on boot and nothing happens. Any help?

---

### Post by DeltaUK on 2008-11-06
im gettin really impatient and frustrated with this! any help?

---

### Post by DeltaUK on 2008-11-09
/me jumps off a cliff

---

### Post by DeltaUK on 2008-11-10
/me dies

---

### Post by gibbon1993 on 2008-11-10
I know this isn't any help but I just reinstalled Ubuntu, I think it may have something to do with me starting to mess about with lvpm, the program moving wubi to a normal seperate partition.

Hope you fix it eventually

---

### Post by gibbon1993 on 2008-11-10
I know this isn't any help but I just reinstalled Ubuntu in the end aftering exhausting everything.

I think it may have something to do with me starting to mess about with lvpm, the program moving wubi to a normal partition, just before this happened.

I didn't have anything particularly important on ubuntu and I needed it on a seperate partition anyway.

Hope you fix it eventually and don't have to resort to a reinstall

---

### Post by DeltaUK on 2008-11-10
> **gibbon1993 said:**
> I know this isn't any help but I just reinstalled Ubuntu in the end aftering exhausting everything.

I think it may have something to do with me starting to mess about with lvpm, the program moving wubi to a normal partition, just before this happened.

I didn't have anything particularly important on ubuntu and I needed it on a seperate partition anyway.

Hope you fix it eventually and don't have to resort to a reinstall

I cant even get to the ubuntu install after first reboot... i have tried many reinstalls and tried 32 and 64bit.

---

### Post by ago on 2008-11-10
> **DeltaUK said:**
> i can type in the grub prompt.. 

i get a choice of hd0,0 and hd0,1

it says they are both ntfs and 0,1 is active

cant do anything other than that.

can't you browse them as explained above?

---

### Post by Lordnet on 2008-11-11
i have the same problem

But my 2 drives are using windows Dynamic disk Storage 
[http://support.microsoft.com/kb/314343](http://support.microsoft.com/kb/314343)
(The drives G and S are striped volumes, a.k.a. Windows' Software RAID-0)
it doesn't work in G (striped volume) and F (single volume)

[[IMG]http://img142.imageshack.us/img142/359/diskmanagerib1.th.jpg[/IMG]](http://img142.imageshack.us/my.php?image=diskmanagerib1.jpg)[[IMG]http://img142.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)


[[IMG]http://img135.imageshack.us/img135/9605/dsc06162hc7.th.jpg[/IMG]](http://img135.imageshack.us/my.php?image=dsc06162hc7.jpg)[[IMG]http://img135.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

[[IMG]http://img232.imageshack.us/img232/2753/dsc06166ul6.th.jpg[/IMG]](http://img232.imageshack.us/my.php?image=dsc06166ul6.jpg)[[IMG]http://img232.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by DeltaUK on 2008-11-11
> **ago said:**
> can't you browse them as explained above?

I dont know how, i didnt understand your post.

[[IMG]http://img84.imageshack.us/img84/7712/44371918yt4.th.jpg[/IMG]](http://img84.imageshack.us/my.php?image=44371918yt4.jpg)[[IMG]http://img84.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by ago on 2008-11-11
kernel (hd0,1)/ubuntu/disks[hit tab here]

---

### Post by DeltaUK on 2008-11-11
kernel (hd0,1)/ubuntu/disks[tab]

Error 16: Inconsistent File Structure

i also tried:

kernel (hd0,0)/ubuntu/disks[tab]

Error 15: File not found

---

### Post by SkepticUK on 2008-11-15
Hi ago

I can navigate to 

kernel (hd0,2)/ubuntu/disk/boot

tab gives several options, what am I looking for?

---

### Post by DeltaUK on 2008-11-18
help?

---

### Post by DeltaUK on 2008-11-29
please?

---

### Post by ago on 2008-12-01
> **DeltaUK said:**
> i can type in the grub prompt.. 

i get a choice of hd0,0 and hd0,1

it says they are both ntfs and 0,1 is active

cant do anything other than that.

Choose one of the two and keep expanding with tab completion

---

### Post by Jammanuser on 2008-12-03
> **gibbon1993 said:**
> Sorry for double post just getting a bit frustrated with it.
I found my way to the ubuntu file on C:\ and it can't find the boot directory, and install only contains '.fuse_hidden000...' Found wubildr.mbr in C:\ so attempted to boot it. It just stays on boot and nothing happens. Any help?

Hi, DeltaUK! i just popped in to say that the file ".fuse_hidden000..." is actually the ISO...wubi apparently renames it after installation! i found this out in my own problem trying to create a Ubuntu Desktop CD from the ISO that i already had instead of downloading it! i renamed mine to "ubuntu-8.10-desktop-i386.iso" and then burned it to a CD...and i had my Ubuntu Desktop CD!

Hope this 2 cents helps! ):P

-jammanuser

;)

---

### Post by DeltaUK on 2008-12-03
kernel (hd0,1)/

tab here i get Error 16: Inconsistent File Structure

---

### Post by ago on 2008-12-06
> **DeltaUK said:**
> kernel (hd0,1)/

tab here i get Error 16: Inconsistent File Structure

Then see the sticky post on grub, and do a follow up on the grub4dos forum

---

