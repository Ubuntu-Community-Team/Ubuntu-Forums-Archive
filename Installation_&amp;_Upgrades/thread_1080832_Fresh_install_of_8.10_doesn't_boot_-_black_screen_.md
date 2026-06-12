---
title: "Fresh install of 8.10 doesn't boot - black screen + blinking cursor"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by MountainX on 2009-02-25
I don't get any error messagess - just a black screen and a blinking cursor. 

I think my system may not be finding grub... how could I verify if this is the problem?

During installation I made a boot partition on a (hd4,1) which shows up as /dev/sde1 when I boot with the live CD.

Is there something I need to do specifically to get Ubuntu to boot with this configuration? 

Maybe I'm missing the basic understanding. I assumed if I used the installer, Ubuntu would boot after it was installed. I am probably overlooking something basic, but no clue what it might be...

Thanks

**_UPDATE:_**

**[COLOR="Red"]_Will this thread help you solve your Ubuntu boot up problems?_[/COLOR]**

This thread may help you if you answer yes to all the following questions:
1. Do you have more than one hard drive in your computer?
2. Are you doing anything slightly custom with the partitions (such as creating a separate /boot parition)?
3. Is the boot process stopping at a black screen + blinking cursor before you see a Ubuntu splash screen?
4. Your video card/monitor are working correctly? (You may be able to verify this by booting from the Live CD.)

SOLUTION:
The resolution was given by caljohnsmith in two messages below:
#6 [http://ubuntuforums.org/showpost.php?p=6811432&postcount=6](http://ubuntuforums.org/showpost.php?p=6811432&postcount=6)
#8 [http://ubuntuforums.org/showpost.php?p=6811755&postcount=8](http://ubuntuforums.org/showpost.php?p=6811755&postcount=8)

---

### Post by MountainX on 2009-02-27
I think my problem may be related to the device mapping in grub

The Super Grub disk shows the following hard drive mapping:

```
GNU Grub 0.97-os.1					
					
Natural	Linux-IDE	Linux-SCSI	Grub	Hurd	Size
1	hda	sda	hd0	hd0	931 GB
2	hdb	sdb	hd1	hd1	931 GB
3	hdc	sdc	hd2	hd2	69 GB
4	hdd	sdd	hd3	hd3	69 GB
5	hde	sde	hd4	hd4	203 GB

```

The 1 TB Samsung drives are sda and sdb.

But Ubuntu sees the drives like shown below with the 1 TB Samsung drives listed as sdd and sde.

How can I fix the device mapping (preferrably from the grub command line because the computer won't boot.)

```
Disk /dev/sda: 218.9 GB, 218999291904 bytes
255 heads, 63 sectors/track, 26625 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d21dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       26625   213865281   8e  Linux LVM

Disk /dev/sdb: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa03ca03c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9039    72605736   8e  Linux LVM

Disk /dev/sdc: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000063b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9033    72557541   8e  Linux LVM

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000377d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001   8e  Linux LVM

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b7300

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1          43      345366   83  Linux
/dev/sde2              44      121601   976414635   8e  Linux LVM

Disk /dev/sdh: 1999 MB, 1999634432 bytes
16 heads, 32 sectors/track, 7628 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000
```

---

### Post by Sashin on 2009-02-27
Tried reinstalling yet?

---

### Post by MountainX on 2009-02-27
> **Sashin said:**
> Tried reinstalling yet?

about 50 times -- and that is NOT an exaggeration. I have worked on this for more than 150 hours.

---

### Post by madsporkmurderer on 2009-02-27
Your BIOS can cope with booting from drives that big can't it? I had a problem with a (rather old) computer that couln't boot from a 200GB HDD so I had to put a 30GB one in for ubuntu then once it was booted it could mount the big one no problem (automatically)

---

### Post by caljohnsmith on 2009-02-27
Can you change your BIOS to boot the sde drive on start up? If so, I think that might help fix your problem, because it looks like that is the drive that has Grub's boot files. But in order to get a clearer picture of your setup, how about downloading the **Boot Info Script** to your Ubuntu Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post.

---

### Post by MountainX on 2009-02-27
> **caljohnsmith said:**
> Can you change your BIOS to boot the sde drive on start up? 

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)


Thanks for the link to the great script. I'm attaching the results. I did change my bios settings earlier today, so the drive that was showing up as sde is sdf in the attached report.

I have changed the BIOS settings for boot drives about 20 times. So far that hasn't helped.

Here are some related posts:

Shows my HDD's the way grub sees them:
[http://ubuntuforums.org/showpost.php?p=6810691&postcount=2](http://ubuntuforums.org/showpost.php?p=6810691&postcount=2)

an attachment with more info about my disk drives:
[http://ubuntuforums.org/showpost.php?p=6806332&postcount=20](http://ubuntuforums.org/showpost.php?p=6806332&postcount=20)

---

### Post by caljohnsmith on 2009-02-27
OK, how about doing the following for the sdf drive (if the device name is different, just change that in the commands that follow, nothing else):
```
sudo grub
grub> device (hd0) /dev/[COLOR="Blue"]sdf[/COLOR]
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
Next do:
```
sudo mount /dev/sdf1 /mnt && gksudo gedit /mnt/grub/menu.lst
```
And change all the Ubuntu entries to use (hd0,0) instead of (hd1,0) similar to:
```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		[COLOR="Blue"](hd0,0)[/COLOR]
kernel		/vmlinuz-2.6.27-7-generic root=/dev/mapper/vgHD103UJ999M-lvRoot_crypt ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
```
Also change the "#groot..." line:
```
# groot=[COLOR="Blue"](hd0,0)[/COLOR]
```
Then reboot, set your BIOS to boot the sdf drive, and let me know how far you get. We can work from there.

---

### Post by MountainX on 2009-02-27
> **caljohnsmith said:**
>  let me know how far you get. We can work from there.

Thank you! I got this far...

```
grub> device (hd0) /dev/sdf
device (hd0) /dev/sdf
grub> root (hd0,0)
root (hd0,0)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/grub/stage2 /grub/menu.lst"... succeeded
Done.
grub> quit
quit
ubuntu@ubuntu:~$ 

ubuntu@ubuntu:~$ sudo mount /dev/sdf1 /mnt && gksudo gedit /mnt/grub/menu.lst
mount: unknown filesystem type 'LVM2_member'
ubuntu@ubuntu:~$ 


```

actually, I think I just need to specify that sdf1 is ext2... let me try that...

UPDATE. OK. This worked. 
```
sudo mount -t ext2 /dev/sdf1 /mnt && gksudo gedit /mnt/grub/menu.lst

```

Moving on to the next step...

---

### Post by MountainX on 2009-02-27
> **caljohnsmith said:**
>  let me know how far you get. We can work from there.

Wow. Thank you so much! That worked.


The new part of what you asked me to do was:
```
sudo grub
grub> device (hd0) /dev/sdf

```

Can you explain that? I would love to learn from this. 

I've been reading up on grub, but that command isn't something I came across in my reading.

I think I understand everything else you suggested. (I know most of what you asked me to do was undoing changes I had made to menu.lst. I guess my efforts prior to your involvement made your job harder!)

I'm going to install again from scratch now and see if I can do all this myself.

What is the easiest way to run those grub commands during installation with the alternate CD?

---

### Post by albinootje on 2009-02-27
> **MountainX said:**
> Wow. Thank you so much! That worked.

What worked exactly ? 
Can you explain for the rest of us what you did, and what is working now ? Is this thread solved now ?

And I don't know much about LVM, but I wonder whether you can have a complete system with only LVM, can the installed Grub handle that properly ?

---

### Post by MountainX on 2009-02-27
> **albinootje said:**
> What worked exactly ? 
Can you explain for the rest of us what you did, and what is working now ? Is this thread solved now ?

And I don't know much about LVM, but I wonder whether you can have a complete system with only LVM, can the installed Grub handle that properly ?

[COLOR="Red"]UPDATE: see the first message in this thread for an update about the problem this discussion addresses and the solution.[/COLOR]

I did exactly what caljohnsmith suggested in this post:
[http://ubuntuforums.org/showpost.php?p=6811755&postcount=8](http://ubuntuforums.org/showpost.php?p=6811755&postcount=8)
I went step by step. 

As far as I know, /boot can't be on LVM. (/boot certainly cannot be on crypto.)

Grub will point to "/" on LVM -- that's how my system is set up now.

---

### Post by caljohnsmith on 2009-02-27
> **MountainX said:**
> 
The new part of what you asked me to do was:
```
sudo grub
grub> device (hd0) /dev/sdf

```

Can you explain that? I would love to learn from this. 

Grub allows you to associate any of its drives (hdX) with any /dev/sdX device by using the "device" command. That can be extremely useful when you want to install Grub to the MBR of a drive that is not the drive that has Grub's boot files, because you have to use the correct (hdX) so that Grub will look on the correct drive on start up for its boot files. In your case though, since you were installing Grub to the MBR of the same drive that has Grub's boot files, it is not necessary to use that command, it was just a convenience. You could have instead used "root (hd5,0)" and "setup (hd5)" since (hd5) is by default sdf. But using the Grub "device" command makes it easier if your device name changes for some reason, because we used it to arbitrarily map whichever drive has Grub's boot files (sdf in your case) to (hd0). Then we just proceed with the rest of the Grub commands using (hd0) rather than (hd5). 
> **MountainX said:**
> 
I've been reading up on grub, but that command isn't something I came across in my reading.

You can find it in the [official Grub manual]("http://www.gnu.org/software/grub/manual/"), but unfortunately that manual is not very useful when it comes to learning how to use Grub in a practical way I think. Anyway, I'm glad you can now finally boot Ubuntu after "N" times of installing it, so cheers and hope the rest of your Ubuntu experience goes smoother. :)

---

### Post by MountainX on 2009-02-28
@caljohnsmith: thank you again!

Since my last post I have reconfigured the HDD's in my computer and reinstalled Ubuntu again.

My goals were to organize all my disks in a way to minimize problems and to learn from my experiences installing Ubuntu to date. Heree is what I did:
1. make it boot to the first HDD that my bios recognizes with the default bios settings. I assumed this would eliminate problems. The first drive is "3M", so I put /boot here. The first 2 channels are used by IDE devices (CD-ROM, etc), so I assume the SATA drives on this motherboard will always be 3M and 4M. Previously, I was trying to boot off of 4M by changing BIOS settings, but I reverted to using the defaults now.

2. I made a hardware RAID-1 array for "/" to increase reliability.

3. I put /tmp, /var and swap on a separate drive (non RAID).

4. I left /home by itself on my fastest drives -- a RAID-5 array of 4 SCSI 15k RPM Cheetahs.

After the installation finished, I tried booting the computer before making any changes just to see what would happen.

It did not boot. But it did show a message saying it was loading grub. Then it gave grub error 22. I looked that up and it relates to not finding a partition. I never got this error before, so something is different.

I ran the boot info script again, and it shows things I didn't see before. Some of the info looks confusing now.

In the live CD (gparted), I'm seeing an assignment that looks like this:
/sda - /home : 2 drives on Areca controller
/sdb - / : 4 drives on LSI controller
/sdc - to be mounted once install is finished: 1 drive on Areca
/sdd - /var, /tmp, swap -- 1 drive on Areca controller
/sde - (bios SATA drive 3M on motherboard)
  sde1 - /boot
  sde2 - to be mounted once the install is finished. 
/sdf - to be mounted once the install is finished. (bios drive 4M)

That's not what I expected. The bios is set to boot from drive 3M and the Areca and LSI controllers are lower on the boot list.

Furthermore, in the Boot Info Summary (see attached), I see grub installed on sda and sdf. What's there from sdf is old (that's from the last install and I didn't even mount that drive/partition for this install). I'm not sure when grub got written to sda, but I suspect the most recent install did that. Is that expected? I didn't see that previously.

This install seems to have worked somewhat better. The main thing I changed is that I didn't mount the custom mount points.

My plan is to follow the exact steps you recommended before, starting with this:
```
sudo grub
grub> device (hd0) /dev/sde
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```Then I'll change (hd4,0) to hd0,0) in menu.lst (root and groot lines, as before).

That should work, right?

Do you see any problems in the boot info report?

UPDATE: I made these changes and I am still seeing the GRUB loading... Error 22 message.

(Could it be trying to boot the wrong grub? There are 2 listed in the boot info report.)

---

### Post by MountainX on 2009-02-28
alright, fixed it. it was a minor mistake on my end in my BIOS settings. The same instructions caljohnsmith gave earlier in this thread (about 4 hours ago) worked perfectly (again).

My computer is booting up properly and I think I know enough to resolve this issue when it appears again.

However, I am still not sure why the Ubuntu installation is failing and requiring that I intervene by editing the grub configuration.

Next up for me is to learn how to set up LVM volumes from a running installation. (I have only done LVM setup from within the alternate CD installer so far.)

---

### Post by MountainX on 2009-02-28
P.S. I'm trying to find out how to remove those extra grub installations now that my system is booting up correctly. I see 3 grub installation on 3 different hard drives (using the fantastic boot info script). I'd like to get rid of the grubs that I don't use. Google isn't helping with a solution as of yet.

UPDATE: I found something helpful here: [http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/](http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/)

You can also use dd command from Linux itself (it removes partition table):
# dd if=/dev/null of=/dev/sdX bs=512 count=1

Just remove MBR, without the partition table:
# dd if=/dev/null of=/dev/sdX bs=446 count=1

Replace /dev/hdX with your actual device name such as /dev/hda. Use fdisk -l command to find out device name:
# fdisk -l

Anyone know if this is correct? I just want to remove grub, not the partition table. I know using dd could be dangerous if I get it wrong, so I hope someone here will confirm for me if the above commands are correct. Thanks.

EDIT: maybe extra cautions are required for using dd with RAID or SCSI storage... 
I'm just reading a good post here: [http://www.rajeevnet.com/hacks_hints/os_clone/os_cloning.html](http://www.rajeevnet.com/hacks_hints/os_clone/os_cloning.html)

This post also mentioned "BIOS scan for external SCSI controller" and reading this explains something about my problems and why a drive I set to boot first in BIOS is not being seen first by Ubuntu... still much to learn.

---

### Post by caljohnsmith on 2009-02-28
Hi Dave, I'm glad you have your setup booting again, and it sounds like you are figuring how Grub works in the process. From the results you included in post #14, I think I see the problem of why you have to mess with reinstalling Grub afterwards. When you install Ubuntu, for better or for worse Ubuntu assumes that you are booting from whichever is your sda drive on start up, so Ubuntu by default will install Grub to the MBR of sda. I do not agree with making that the default, but that is how they do it. The problem with that comes down to the fact that **Grub determines the order of drives differently on start up than when you are in Ubuntu**. On start up, Grub sees the order of drives as your BIOS boot order (so this is relevant for your menu.lst):
```

(hd0) = 1st boot drive
(hd1) = 2nd boot drive
(hd2) = 3rd boot drive
...etc.
```
But when you are in Ubuntu using Grub commands, Grub sees the order of drives as you are probably familiar with:
```

(hd0) = sda
(hd1) = sdb
(hd2) = sdc 
...etc.
```
When you installed Ubuntu /boot directory to your sde drive, which is (hd4) when you are in Ubuntu, Grub was by default installed to the MBR of your sda drive, yet Grub pointed to the (hd4) drive (the 5th boot drive) for its boot files. So unless your sde drive just happens to be exactly the 5th drive in your BIOS boot order, you will get a Grub error since Grub won't be able to find its boot files (it will look on the wrong drive). The easiest way around that is to simply install Grub to the MBR of the drive that has Grub's boot files, and boot that drive first on start up. Then Grub doesn't have to go looking on another drive for its boot files, and you don't have to worry about what order your other drives are in the BIOS boot order so that Grub can find its boot files; your drives are independent of each other this way when it comes to booting. 

So the bottom line is, when you went to install Ubuntu, you could have clicked the "Advanced" button near the end of the installation process, and there you can specify to have Grub installed to the same drive as you are installing Ubuntu to (or more specifically, the same drive that has the /boot directory). Then you shouldn't need to do any of the Grub commands afterwards that you've been doing to get Ubuntu booting properly. 

I hope my explanation didn't make things more convoluted; cheers and enjoy your new Ubuntu install. :)

---

### Post by MountainX on 2009-02-28
> **caljohnsmith said:**
> I hope my explanation didn't make things more convoluted

Your explanation is great - very helpful. I was aware that the ordering of drives could differ as you explained. I thought I had mapped that out with the help of the Super Grub disk and Live CD.

But after reading your explanation, I now have a much more clear understanding of what is going on. Thank you!

However, there are still a few things I don't understand. Am I correct that the device command generates (or modifies) the device.map file?

Second, a couple days ago I read the following [message]("http://linux.derkeiler.com/Mailing-Lists/Debian/2008-05/msg00998.html"). Do you agree that device.map should be avoided?
> Then there is a file named /boot/grub/device.map where one can define which device should have which number, but the use of this file is quite confusing and poorly documented, and it took me many tries to understand. (The GRUB manual and all sorts of search results couldn't help me clearly.) Summary:

(1) If GRUB is started from within Debian:
* If started with the command "grub", the file device.map is ignored. GRUB
assigns device names (hd0 etc.) based on *guesses* it makes.[1]
* If started with the command "grub --device-map=device.map" and the file
device.map exists, the file device.map is parsed.
* If started with the command "grub --device-map=device.map" and the file
device.map does not exist, GRUB *guesses* the device names [1] and stores
the result of the guessing in the file device.map.

(2) If GRUB is started directly from the BIOS (GRUB shell):
* The file device.map is ignored, the device names are derived from GRUB's
guessing.[1]

Note that (2) is also the situation you have when you boot your system
normally. In other words: Making changes to device.map does not influence
device numbers actually used by GRUB when booting. (That's why I don't use
that file, I personally find no use for it.)

-Moritz

Based on what you explained, I'd like to try setting up grub exactly as you explained ("install Grub to the MBR of the drive that has Grub's boot files, and boot that drive first on start up").

Do you feel like giving me some detailed steps for doing so? Can I do it from a running installation (as opposed to reinstalling with an installation CD)? Would you recommend a separate grub partition as some of the grub docs discuss? (This part of the docs seems to be dated info because it talks about old versions of Windows.)

BTW, I use the alternate installer, not the Live CD (because I set up LVM and crypto).

---

### Post by caljohnsmith on 2009-02-28
> **MountainX said:**
> 
However, there are still a few things I don't understand. Am I correct that the device command generates (or modifies) the device.map file?

Actually no, the "device" command in the Grub shell just modifies how Grub sees devices for that particular session; as soon as you quit the Grub shell, that info is lost. If you want to modify the device.map file, you usually have to do it manually.
> **MountainX said:**
> 
Second, a couple days ago I read the following [message]("http://linux.derkeiler.com/Mailing-Lists/Debian/2008-05/msg00998.html"). Do you agree that device.map should be avoided?
> Then there is a file named /boot/grub/device.map where one can define which device should have which number, but the use of this file is quite confusing and poorly documented, and it took me many tries to understand. (The GRUB manual and all sorts of search results couldn't help me clearly.) Summary:

(1) If GRUB is started from within Debian:
* If started with the command "grub", the file device.map is ignored. GRUB
assigns device names (hd0 etc.) based on *guesses* it makes.[1]
* If started with the command "grub --device-map=device.map" and the file
device.map exists, the file device.map is parsed.
* If started with the command "grub --device-map=device.map" and the file
device.map does not exist, GRUB *guesses* the device names [1] and stores
the result of the guessing in the file device.map.

(2) If GRUB is started directly from the BIOS (GRUB shell):
* The file device.map is ignored, the device names are derived from GRUB's
guessing.[1]

Note that (2) is also the situation you have when you boot your system
normally. In other words: Making changes to device.map does not influence
device numbers actually used by GRUB when booting. (That's why I don't use
that file, I personally find no use for it.)

-Moritz 
I agree with everything Moritz says except point (2); Grub does not "guess" the order of drives on start up; the drive order is always determined by the BIOS boot order.
> **MountainX said:**
> 
Based on what you explained, I'd like to try setting up grub exactly as you explained ("install Grub to the MBR of the drive that has Grub's boot files, and boot that drive first on start up").

Do you feel like giving me some detailed steps for doing so? Can I do it from a running installation (as opposed to reinstalling with an installation CD)? 
Installing Grub to the MBR of the drive that has Grub's boot files is as simple as running those Grub commands that I gave you before, and you can do that while you are booted into your Ubuntu install or from the Live CD. The main point is for whichever partition you specify with "root (hdX,Y)", then using "setup (hdX)" will ensure Grub is installed to the MBR of same drive that has Grub's boot files, because the X specifies the drive; thus if X is the same for both those commands, Grub will be installed to the same drive that has Grub's boot files. Only if you do something like "root (hd4,0)" and then "setup (hd0)" is Grub installed to a different drive than where the boot files are, because (hd4,0) would be the sde1 partition while (hd0) is the MBR of sda (assuming you didn't use the "device" command to specify otherwise). 
> **MountainX said:**
> 
Would you recommend a separate grub partition as some of the grub docs discuss? (This part of the docs seems to be dated info because it talks about old versions of Windows.)

BTW, I use the alternate installer, not the Live CD (because I set up LVM and crypto).
Only if you have multiple distros installed is it sometimes convenient to have a separate Grub partition I think, because then you can install/uninstall your distros as you please without worrying about which distro controls Grub on start up. So unless you plan on installing more distros to your setup and also foresee making lots of changes about which distros are installed, I don't think a dedicated Grub partition would make much sense in your case.

---

### Post by MountainX on 2009-02-28
Thank you! That's a great explanation -- more helpful than anything I found with weeks of googling.

I'm going to work on modifying the grub install and my BIOS boot disk order a bit more, as you described. I will report back when I either succeed or fail! :)

---

### Post by meierfra. on 2009-02-28
> I agree with everything Moritz says except point (2); the device.map file is used on start up if you have any references in your menu.lst to linux drives like hda, hdb, sda, sdb, etc. like:
Code:

title   Ubuntu 8.04, kernel 2.6.24-19-generic
root    (hd0,1)
kernel  /boot/vmlinuz-2.6.24-19-generic root=/[COLOR="Red"]dev/sda2[/COLOR] ro quiet splash
initrd  /boot/initrd.img-2.6.24-19-generic
quiet

Grub on start up will use the device.map to correlate those linux drives with the BIOS boot drives (hdX), 

Moritz got it right.   The device map is not used during start up.   "root=/dev/sda2" is an instruction for the kernel. Grub  just passes it on to the kernel without even looking at it.

---

### Post by caljohnsmith on 2009-02-28
Thanks meierfra, of course you are right. I did a few experiments some months ago that led me to believe that the device.map could be used on start up if the menu.lst had sdX/hdX references, but I see my mistake now.

---

### Post by MountainX on 2009-02-28
> **caljohnsmith said:**
> The easiest way around that is to simply install Grub to the MBR of the drive that has Grub's boot files, and boot that drive first on start up. Then Grub doesn't have to go looking on another drive for its boot files, and you don't have to worry about what order your other drives are in the BIOS boot order so that Grub can find its boot files; your drives are independent of each other this way when it comes to booting. 


Does this apply even when the drive in question is a SCSI RAID device? Initiallly I had assumed that I would have the least trouble if the /boot partition (and grub) was on a plain old single drive connected to the motherboard.

This has turned out to be a great thread -- very educational in regard to booting Ubuntu with grub.

---

### Post by caljohnsmith on 2009-02-28
> **MountainX said:**
> Does this apply even when the drive in question is a SCSI RAID device? Initiallly I had assumed that I would have the least trouble if the /boot partition (and grub) was on a plain old single drive connected to the motherboard.

Getting Grub to work with a RAID setup can be a bit of a pain, at least based on what I've seen in the forums, because I have no personal experience setting up Grub on a RAID array. Definitely having Grub on a single drive is much easier than setting up Grub to work with RAID. If you want more info on setting up Grub on a RAID array, you might find this tutorial helpful if you haven't seen it all ready:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by MountainX on 2009-03-06
I have gotten LVM and crypto set up on this system with disks sda through sdi. It is quite a complex setup. Everything works when done manually.

Now I'm adding a USB drive to help me *automatically* unlock the crypto partitions. Putting in the USB drive causes some of my drive IDs to change and that causes other disks to fail to mount.

The actual /boot partition is working great now (thanks to the help here) as I can still boot even when the drive's /dev/sdX ID changes.

**What is the best way to achieve a stable set of drive identifiers? **I have heard a lot of arguments against using UUIDs, so much that I prefer not to use that approach. (UPDATE: see comments [here]("http://www.linux.com/feature/146951"): [http://www.linux.com/feature/146951](http://www.linux.com/feature/146951))

What is the best way to go? UPDATE: I'm considering either volume labels or udev rules. I don't know if either will work with LVM + crypto and I appreciate any advice.

---

### Post by o891 on 2009-03-11
Great thread!!!!

I am currently struggling to get 8.1 server working on a HP ML110 G5 with RAID. I am pretty new to Ubuntu, but I am going to try to do as you say and will then give you an update about what happens.

Thanks for all the great advice...

---

### Post by MountainX on 2009-03-11
Good luck. Let me know if I can help.

FYI, I ended up going with UUIDs instead of labels or udev rules. I may change that in the future, but for now, I have everything working with UUID's. :)

---

### Post by o891 on 2009-03-13
So I figured it out, thanks to this thread mostly...

I booted with the U 8.10 Desktop LiveCD and in /dev/ i found a folder called cciss. Inside are the following files: c0d0, c0d0pa, c0d0p1, c0d0p2, c0d0p3 and c0d0p4.

Is seems like these are the different partitions in my RAID0 array.

Anyway I followed caljohnsmiths advice and did the following:

```

sudo grub
grub> device (hd0) /dev/c0d0
grub> root (hd0,0)
grub> setup (hd0)
grub> quit

```

Then I mounted the c0d0 drive and checked the menu.lst as cjs said, but didnt need to change anything as all the values were already set to (hd0,0).

Reboot and everything works perfectly now...

Thanks for the help!
Oliver

PS Anyone with the same problem using hardware RAID, post your problem here and maybe I can help!

---

