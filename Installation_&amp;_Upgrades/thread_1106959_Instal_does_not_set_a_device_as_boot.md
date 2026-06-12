---
title: "Instal does not set a device as boot?"
date: 2009-03-26
forum: Installation &amp; Upgrades
---

### Post by olddave1 on 2009-03-26
Hi,

I installed 8.10 Server amd64 on a previously used SATA drive. It used to be half a RAID 1 with Centos 4.6. I did fdisk to create one large partition and mke2fs to create a file partition on there. 

Then I booted from Ubuntu 8.10 CD and did a std install onto a 10GB partition, which it resized to. But it does not boot, fdisk -l shows none of the 4 devices as being marked for boot. /dev/sda1 is "Linux" and blocks 1-1277, /dev/sda2 is Extended and blocks 1278-24321, /dev/sda5 and has blocks 1278-23571 and /dev/sda6 is "Linux swap / Solaris" and has blocks 23572-24321

Next steps?

Thx.

David

---

### Post by dstew on 2009-03-26
Did you install a boot loader? How are you trying to boot your Ubuntu installation?

---

### Post by olddave1 on 2009-03-26
Doesn't the std install do the bootloader? I read the install docs here [https://help.ubuntu.com/8.10/serverguide/C/installing-from-cd.html](https://help.ubuntu.com/8.10/serverguide/C/installing-from-cd.html) and it does not mention having to setup a bootloader?

Thx.

David

---

### Post by olddave1 on 2009-03-26
Hi,

Now installed 4 times, using the entire disk option, I see it install the grub bootloader. But it will not boot and no device is listed as a boot device. I get isolinux:Disk error 01, AX = 0201, drive 80 when I try to boot using that optiton on the CD menu.

When I go into rescue mode and run fdisk -l I still get no devices marked as Boot. I umounted /dev/sda1 and ran e2fsck -n -f to see if there where any errors, none reported.

Can someone confirm the install 'should' instal a bootloader and mark a device as the boot device? Could this be to do with the fact it was half a RAID 1 setup previously?

Thx.

David

---

### Post by olddave1 on 2009-03-31
Hi,

Any help here? I have tried two disks. Several times for one of them. The std Guided - Entire disk results in a no SYSTEM error message on boot. 

Is there a way of cleaning everything off the disk and doing a successful fresh instal?

I have for sda fdsik -l
/dev/sda1  *   1    13       104391  fd  Linux raid autodetect
/dev/sda2     14   650      5116702+ fd  Linux raid autodetect
/dev/sda3    651  1160      4096575  fd  Linux raid autodetect
/dev/sda4   1161 24321    186040732+  5  Extended
/dev/sda5   1161 24321    186040701  fd  Linux raid autodetect

for sdb fdisk -l
/dev/sda2      1 23571    189334026  83  Linux
/dev/sda2  23572 24321      6024373   5  Extended
/dev/sda2  23572 24321      6024343  82  Linux swap/Solaris


Thx.

David

---

### Post by ronparent on 2009-03-31
Do you intend to retain rhe raid1 setup (that seem to be what the above indicates)??

If not, you probably have to disable raid in you bios prior to using the disks seperately.

---

### Post by olddave1 on 2009-03-31
Hi,

On elast attempt before I try another distro. 

I took the SATA drive I wanted to install on and put it into a Vista PC then, formatted the drive. Then I put it back in the Serve ri am trying to instal Ubuntu 8.10 Server onto. I went thru the instal for the umptenth time. It failed to bott, so I booted into Rescue mode them did 'sudo grub', 'find /boot/grub/stage1' -> '(hd0,0), then root (hd0,0)', which just echos the cmd then setup (hd0,0), which finishes successfully with 'Done.'

When I boot from the drive I get

isolinux: Disk error 01, AX = 0201, drive 80

Googled this and it send me here - [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto) which ois just wha tI did, the only thing I notice was that grub> root (hd0,0) only echo'd the comd not spit out the filesystem type as referred to here - [http://linuxmint.com/wiki/index.php/How_to_repair_your_grub](http://linuxmint.com/wiki/index.php/How_to_repair_your_grub)

So in a loop now, any next steps?

David

---

### Post by olddave1 on 2009-03-31
Hi,

RAID is disabled in bios, has been since I cut it down to a single disk. But for some reason even after the recent DOS format of the disk it still detects RAID on that single SATA disk, but if you let it try to discover the RAID it fails, and you have to start the instal again.

David

---

### Post by ronparent on 2009-03-31
I am unfamiliar with all the raid hardware/software schemes out there. And it does look like this problem has been frusterating you for a while. But it looks to me lke some hardware implementation may be subverting all your attemts to remove the raid. You might try one of the following two options:
1) plug into two sata ports that have never been used as raid.

2) Re-enable the bios raid option for your current ports, use it to clear the raid definion, and, disble it again.

I only hope that it is that simple!

---

### Post by olddave1 on 2009-03-31
Hi,

I already carried out your step 2 before.

When I am in grub (good guide here - [http://users.bigpond.net.au/hermanzone/p15.htm#cli](http://users.bigpond.net.au/hermanzone/p15.htm#cli)) and try 
grub>  configfile (hd0,1)/boot/grub/menu.lst
I get an "Error 12: Invalid device requested"

Whenever I try 
grub> kernel /vmlinuz root=/dev/sda1
I get the same error.
But if I do 
grub> find /vmlinuz
It returns (hd0,0) so can find it no problem?

David

---

### Post by olddave1 on 2009-03-31
Hi,

I cannot believe it. My mobo has 2 SATA controllers, Sil3114 is attached to one and an NVidia controller to the other. The former does not boot and the latter does. Problem solved. Although I am surprised that the Sil3114 is not working since it is so widely used. 

Thx.

David

---

### Post by ronparent on 2009-03-31
I've been using the same grub guide here.

For the heck ot it, what do you get if you, from the live cd
grub>find /boot/grub/stage1

If grub is installed properly, from what you say above, it will probably return (hd0,0)

If that is the case you
grub> root (hd0,0)     ## or whatever was retuned with the find
and
grub> setup (hd0)

Now grub should be able to find your ubuntu on the next boot to sda1.

---

### Post by ronparent on 2009-03-31
David

Our reply's crossed.  Glad to hear it. 

My guess is that both work, but since the latter was never confgured for raid, it works 'out of the box' (useful only if you should need another raid plug). 

Ron

---

