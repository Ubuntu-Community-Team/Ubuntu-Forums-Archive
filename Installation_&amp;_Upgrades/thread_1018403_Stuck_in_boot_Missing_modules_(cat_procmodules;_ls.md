---
title: "Stuck in boot: Missing modules (cat /proc/modules; ls /dev) in busybox"
date: 2008-12-22
forum: Installation &amp; Upgrades
---

### Post by marisdembovskis on 2008-12-22
Starting up .....
Loading, please wait....


then ubuntu logo, seems it's loading Ubuntu. 
then it drops to non graphical place. 



Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/1d82191f-51f8-4b55-8af7-4024eb04cb39 does not exist. Dropping to shell!

BusyBox .............


(initramfs)_


BUT. there is mentioned file in /dev/disk/by-uuid/...! it exists. there are to. this mentioned is for sda1 and second one is for sda5

Interesting fact is that by insalling 8.10 it also stuck, but then get it over and install was ok. 

I think I have to replace intel ipw200 kernel (i did installed this on Debian Etch by synaptics?
but how replace kernels without getting into system?

or are there any other ideas, what to do???


thanks.

---

### Post by SaNdS1010 on 2008-12-22
I am having this exact same problem... when I type return I can load right back into Ubuntu. I still would rather fix this problem before doing any configurations.

---

### Post by SaNdS1010 on 2008-12-23
I guess these forums take awhile

---

### Post by SaNdS1010 on 2008-12-23
I guess they take a long while

---

### Post by vanderkerkoff on 2009-01-07
Has anyone worked out what is happening here?

I'm having exactly the same problem and I'd love to know how to fix it.

---

### Post by richdebc on 2009-01-07
Me too - just installed 8.10 today and the same thing is happening. Typing 'return' does load the desktop, but as well as being an annoyance I'm worried that there's a problem with the install.

Any help much appreciated!

---

### Post by vanderkerkoff on 2009-01-07
Here's a few more details about my install, if it will help resolve the problem.  I haven't installed the desktop.

I've installed Ubuntu 8.10 amd64

uname -a
Linux gitwiki 2.6.27-9-server #1 SMP Thu Nov 20 22:56:07 UTC 2008 x86_64 GNU/Linux

on my Mac OSX 10.5 that is running VMWare Fusion Version 2.0.1 (128865)

I then installed VMwareTools-7.6.3-94249.tar.gz

---

### Post by polarizeme on 2009-01-18
> **marisdembovskis said:**
> Starting up .....
Loading, please wait....


then ubuntu logo, seems it's loading Ubuntu. 
then it drops to non graphical place. 



Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/1d82191f-51f8-4b55-8af7-4024eb04cb39 does not exist. Dropping to shell!

BusyBox .............


(initramfs)_


I'm having this EXACT problem. I *just* installed Ubuntu, and am currently installing the 220 updates in hopes that this issue will be corrected.

much like another user stated, I was able to use the return command and get Ubuntu to boot, regardless.
I, too, am also afraid that, while I can get Ubuntu to boot, something is obviously wrong and I would like to correct this.

I've noticed that there hasn't been a single reply with a fix yet, but it's obvious that it's an issue for at least a small handful of people.

knowledgeable ideas, suggestions and comments are certainly welcome. ;p

cheers and thanks!
    - Tristan -

---

### Post by vanderkerkoff on 2009-01-18
Lets see if we can eliminate some possible causes ourselves.

Can everyone post up their hardware platforms and uname -a output and any other specific information to your case we can look for something that is common.

Apart from the problem :-)

---

### Post by polarizeme on 2009-01-18
clean install of Ubuntu 8.10 x86, including all 220 updates (lol)
AMD Athlon 64 3500+ 2.2GHz
Nvidia GeForce 6800gs/xt 256mb
3GB ram
internal Western Digital 250GB hdd

**uname -a:**
2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux

it should be noted that I'm also running an install of windows, which I have installed first - Ubuntu came later.

I'm all about getting to the bottom of this.
I also seem to be having the dreaded nvidia problem that a TON of people are having in 8.10, which is getting really annoying... but that's for another time. ;p

cheers!
    - Tristan -

---

### Post by vanderkerkoff on 2009-01-19
Hi Tristan

Well from your hardware configs it looks like the only thing we have in common is this section of the reply from uname -a

2.6.27-9 and we're both installing the 64 bit version

We're not even running the same versions of 8.10, I'm running the 64 bit server version and it looks like you are running the 64 bit desktop, is that right?

Is anyone on here having the same problem with the 32 bit install?

If I get some time I'll install the 32 bit server version and see if I get the same sort of error.

---

### Post by polarizeme on 2009-01-19
I'm using the 32bit version. I have a 64bit processor, but a handful of the guys I work with were all complaining about problems with the 64bit version, so I stuck with 32 for now.

this has been getting so annoying, as I bounce back and forth between OS's a lot.

*sigh*

---

### Post by laserbastu on 2009-01-19
Having the same problems here too. Saw someone recommending adding "rootdelay=130" in the kernel boot sequence in grub (press "e" on your keyboard and add it to the kernel line, then "b" to boot). 

Didn't work, tried altering the delay, didn't work.

I'm having the same troubles in Linux Mint, guess it's because it's based on Ubuntu (or is it a bug in Debian?).

It seems to be our hard drives not mounting properly (the /dev/disk/by-uuid.... thing), I have no idea how to fix this though, searched through forums the last 2 months without any luck.

Edit: I haven't had these problems in any other distro's like Fedora 10 or OpenSUSE 10 though.

---

### Post by laserbastu on 2009-01-19
Got mine to work, see how I did it here:
[http://ubuntuforums.org/showpost.php?p=6581939&postcount=322](http://ubuntuforums.org/showpost.php?p=6581939&postcount=322)

---

### Post by jcampen on 2009-03-14
I had the same problem and am still working on the fix. So far the fix Laserbastu posted hasnt worked, but will try it again

_Some steps I found to quicken the process without using grub_.

When booted up and selceted from the OS screen Ubuntu Kernel 8.10 2.6.27-11-generic it booted up and came to initramfs, so type in exit and enter, then it booted up ok.

It also booted up no problem when I selected from the OS screen Ubuntu  Kernel 8.10 2.6.24-26-generic without any errors at all.

From there you can eddit the fix from the terminal as outlined by Laserbastu.

1. Make sure Ubuntu has booted properly.
2. Start a terminal and enter:
Code:

gksu gedit /boot/grub/menu.lst

3. Scroll down and you will find a similar line to the one you edited before in the grub boot config, it will look something like this:
Code:

kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=43206294-74ef-434d-aca2-db74b4257590 ro quiet splash

4. Add all_generic_ide at the end of the line, like this (do NOT copy paste this line, your UUID number WILL be different from mine, if you copy paste you will just give yourself more problems):
Code:

kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=43206294-74ef-434d-aca2-db74b4257590 ro quiet splash all_generic_ide

5. Save the document and close gedit.

So far this didnt work for me, but will give it another try.

---

### Post by DealerMan on 2009-07-08
I'm having this issue as well, after adding a third hard drive.  I'm dual-booting Mint 7 & Mythbuntu on a WD IDE drive, with a second Seagate IDE drive for storage.  The new drive is a WD SATA drive with a Rosewill controller card.  Typing 'exit' at the initramfs prompt keeps giving me the errors.  I'll assume there's a way using the liveCD to cure my ills.  I'm open to any suggestions...

Thanks in advance for any help.

---

### Post by shivam4741 on 2009-07-11
hi everybody,
      I  updated my ubuntu 8.10 to 9.04 .after this system notification for restart. When i restarted  then grub loaded normally but login screen not appeared and i got a msg -------  
 



[B]Boot from (hdo,8) ext3    9ff4f872-f705-4134-848a-991c82189e8e
Starting up ...
Loading, please wait...
Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough ?)
   -  Check root = (did the system wait for the right device ?)
    - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/9ff4f872-f705-4134-848a-991c82189e8e does not exist . Dropping to a shell!


Busybox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
  Enter 'help' for a list of built-in commands.

(initramfs) 


[/B][I]please suggest me solution .....





[/I][COLOR=#888888]
SHIVAM DENGRE , RKGIT
B-TECH ,(CSE) FINAL yr
 Look To Your Deeds , Then To Your Plans. You Will Be Able To Justify Or Judge Yourselves
 [/COLOR]

---

### Post by LerkeR on 2009-07-15
[B][I]Pre-Note:
After looking into UUIDs a bit, it seems this is the way it [/I][I]should be done. I'm not sure why/how my UUID was altered to be incorrect, but UUIDs are the preferred method.
For more information on UUIDs and how to generate it for a partition, see:
[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)[/I][/B]
Irregardless, this method seemed to fix my issue and got the system booting again. Once you have that, you can easily generate the UUID and use it instead. Alternatively, generating the UUID through the live CD would also be an option.




I realize this is an old thread, but someone bumped this a few days ago. Perhaps he or someone else may find use in this?

I recently ran into this problem by tinkering around with boot screens, turns out it was a bad idea :P

For those running into the issue in which you are getting an error such as (from this thread):
[B]ALERT! /dev/disk/by-uuid/9ff4f872-f705-4134-848a-991c82189e8e does not exist . Dropping to a shell!

[/B]I believe (it was in my case, anyway) this is seems to be caused by your grub loader incorrectly specifying where your root partition is.

How did I fix my problem?

Load up a live CD. Check the partition editor to see what your root partition is, for me it was /dev/sda6

Mount your Ubuntu partition. Load up a terminal and cd to your partition's boot folder
(ie cd /media/disk/boot/grub) and make a backup of your grub loader file - just in case 
sudo cp menu.lst menu.lst_backup

Next, open it up in your text editor of choice with root
sudo pico menu.lst
Find your Ubuntu entry, it should look like this, as example:

title        Ubuntu, kernel 2.6.28-14-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.28-14-generic root=**UUID=9ff4f872-f705-4134-848a-991c82189e8e** ro quiet splash
initrd        /boot/initrd.img-2.6.28-14-generic
 quiet


Remember I said to find your root partition? In my case it was /dev/sda6
So now we need to specify that in the root arg

title        Ubuntu, kernel 2.6.28-14-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.28-14-generic root=**/dev/sda6** ro quiet splash
initrd        /boot/initrd.img-2.6.28-14-generic
 quiet


Save the file, reboot and hope it works.

---

### Post by DealerMan on 2009-07-15
LerkeR, thanks for replying.  Your post would surely have helped with the mess I made, but I got so frustrated I reinstalled Mint 7 (without Mythbuntu) and finally cured my system.  I will definitely keep your solution filed for future reference though, as I'm sure I'll be dual-booting again at some point.

Thanks again!

---

### Post by wolf2588 on 2009-10-14
save how??? its not clear enough for a newbie


im stuck in the save part

---

### Post by zxlstoner on 2009-10-14
I have the same problem.
I are trying to install on my external hard drive through USB connection. (Win XP on insider hard drive)
Everything is Ok when installation, except that when the install CD is ejected, the computer cannot restart itself. it keeps on spawning and seems being in a deadlock loop.
 I restarted the computer myself. 
Then I boost from USB, I cannot see the Grub menu. I chose the first to get into ubuntu. But, it's stuck always into the busybox, with some error info on PCI (no parent found for the drive.....)
What should I do to fix the problem.
Thanks!
The error info picture is attached.

---

### Post by wolf2588 on 2009-10-14
ok so u didnt specified how to get there, gksudo gedit /boot/grub/menu.lst and now i can edit it.  OK , now i need to replace some lines, i got a lot of them

title		Ubuntu 8.10, kernel 2.6.27-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=cf2c4e83-13f7-4986-9fae-90bcb3d57725 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=cf2c4e83-13f7-4986-9fae-90bcb3d57725 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.24-24-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=/dev/sda5UUID=cf2c4e83-13f7-4986-9fae-90bcb3d57725 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=cf2c4e83-13f7-4986-9fae-90bcb3d57725 ro  single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet


wich one should i replace?? my ubuntu is written on sda5


thnx!!!

---

### Post by ahmem7 on 2010-01-28
I got that same problem and had corrected very easily by following the steps on the give linke... hope it will work for you too...

[COLOR=Blue]**[http://www.ccnatoccie.com/2010/01/ubuntu-boot-error-missing-modules-cat.html]("http://khatrinetworks.blogspot.com/2010/01/ubuntu-boot-error-missing-modules-cat.html")  **[/COLOR]

---

### Post by ciric50 on 2010-02-08
So far none of these solutions has worked for me. The problem is intermittent, which makes me think it could be a relative timing issue. While I generally like what I've seen of Ubuntu so far, I've been having boot problems for more than a week. I'm about at the point where I'm going to find another distro if this particular problem can't be solved.

---

### Post by ben_l on 2010-03-17
Changing the UUID to /dev/sda5 worked for me.  It's stupid that this problem happens and that this is the fix.  This happened to me completely out of the blue, but once again the Ubuntu forums came through.

---

### Post by Melquizedeq on 2010-03-30
same here.. is something about missing partitions some grub issue..

i instaled karmic booting with a karmic live cd x64, take the whole disk sata on nvidia chipset and after finish install and reboot nathong happens but the ubuntu logo... hit any key and thebusy box shell was there with this messages...

so i install mint 8 helena x64 and no problems... maybe the mint installer has better grub config setup?

---

### Post by eclee25 on 2010-05-13
changing it to root=/dev/sda5 worked for me too on Linux Mint 8. I did not make a backup of my grub loader file because I didn't have a liveCD on me but I did right down my UUID=9c051...etc number.

Linux Mint users with this problem can see my post on the Mint forums here: [http://forums.linuxmint.com/viewtopic.php?f=46&t=47594&p=274526#p274526]("http://forums.linuxmint.com/viewtopic.php?f=46&t=47594&p=274526#p274526")  

Thanks LerkeR!

---

### Post by thatnovaguy on 2010-06-12
I just installed ubuntu 10.04 and came to this problem. I figured out that if I edited my ubuntu entry (by pressing 'e' when prompted to select a version to boot) and changing my uuid to /dev/sda5 that it would boot slowly into ubuntu without any problems. The only catch is that I would have to change it everytime I wanted to boot because where I installed 10.04 straight off the cd and didn't upgrade from a previous version, I dont have a menu.lst file. Grub pulls the entries from the grub.cfg file which I managed to edit, but it does no good. Editing grub.cfg is only a temporary fix because it is generated from the files in the etc/grub.d folder and etc/default/grub folder. I'm running a dual boot of Ubuntu 10.04 and Windows xp. ](*,)

Here's the out of my uname -a: Linux Sanctusbuntu 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux

Is there anyway I can correct the files that grub generates the grub.cfg file from?
And is there anyway that I can do the same for my recovery console?

Edit: I used sudo blkid  and compared the uuid from it to the one in grub.cfg. Turns out they are the same. I dont know why changing it to /dev/sda5 works then...
**/dev/sda5: UUID="88a4a24e-bcd5-4c7e-a6d2-2de273dec2b4" TYPE="ext4" **

menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 88a4a24e-bcd5-4c7e-a6d2-2de273dec2b4
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=**88a4a24e-bcd5-4c7e-a6d2-2de273dec2b4** ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic

](*,)](*,)

---

### Post by thatnovaguy on 2010-06-19
Bump

---

### Post by thetallestpaul on 2010-06-30
I am having the same error (as in, missing modules (cat /proc/modules; ls /dev)) but when I try to get into menu.lst it is entirely blank.

I am guessing this is entirely abnormal?

---

### Post by thatnovaguy on 2010-06-30
> **thetallestpaul said:**
> I am having the same error (as in, missing modules (cat /proc/modules; ls /dev)) but when I try to get into menu.lst it is entirely blank.

I am guessing this is entirely abnormal?

It's because you are using gub2. Grub2 doesn't use menu.lst, it generates grub.cfg from a couple different files. I personally gave up and went back to 9.10 which I know is stable.

---

### Post by TonyAdams on 2010-10-19
Hey guys. I have the same problem for my netbook, and even change UUID=blabla to /dev/sda6 doesnot work for me.

But now I've fixed this problem. Very simple, change your SATA mode from AHCI to Compatible mode in BIOS setting, then everything is OK.

---

### Post by grapse on 2010-10-26
find a solution by

[COLOR=#FF0000]sudo gedit /etc/default/grub

& edit the 

[/COLOR]# Uncomment if you don’t want GRUB to pass “root=UUID=xxx” parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

to

# Uncomment if you don’t want GRUB to pass “root=UUID=xxx” parameter to Linux
GRUB_DISABLE_LINUX_UUID=true

just delete the [COLOR=Blue]#[/COLOR] before GRUB_DISABLE_LINUX_UUID=true


save the file 
next 

[COLOR=#FF0000]sudo update-grub[/COLOR]
[COLOR=#FF0000]
[/COLOR]

---

### Post by grapse on 2010-10-26
if problem persist

**(initramfs) [COLOR=DarkRed]find[/COLOR]**

**(initramfs) [COLOR=DarkRed]return[/COLOR]**

---

### Post by Zeromaru on 2010-10-28
I am having this issue as well since updating to Maverick, however the fix mentioned here didn't work for me. My system boots just fine on an older kernel, however.

---

### Post by ricardisimo on 2011-01-11
I'm having two issues which appeared at once, and may or may not be related.

The first is the error messages at boot, same as what everyone here has described already. Sometimes the kernel will boot past the initramfs screen, sometimes not. All I can do is wait 5-10 minutes each time, sometimes varying up which kernel I boot from works, but that seems to be more coinkydink than anything, since all three standard kernels seem to boot sometimes (never recovery modes, though, as of yet).

The second issue, which I believe is related since it involves the system locating a hard drive with a uuid, is that my secondary drive - an internal sata disk for storage - has basically disappeared. "lshw" can locate it, but not "sudo blkid" nor any of the guis, such as nautilus, gparted, palimpsest, etc. Here it is:
```
*-disk:1
                description: EXT4 volume
                product: SAMSUNG HD203WI
                vendor: Linux
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/sdb
                version: 1.0
                serial: 9f997b4e-5234-4da0-a0ed-6c655babcc5f
                size: 1863GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: ansiversion=5 created=2010-07-06 13:05:31 filesystem=ext4 label=Storage lastmountpoint=/media/Storage&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;V&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;kY&#65533;P'&#65533;Dq!&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;@'&#65533;P&#65533;&#65533;&#65533;P&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;V modified=2010-12-31 19:06:50 mounted=2010-12-31 16:10:
```
So, I would imagine that a quick peek at the above should give everyone at least one idea of what the problem is, namely some kind of character encoding issue. But, really? How the hell would that happen? And how the hell would I fix it without losing all of my music and such on that drive?

Thanks in advance.

---

### Post by ricardisimo on 2011-01-14
Can no one help me out with this? What's with all of the mystery characters in this line from above?
> configuration: ansiversion=5 created=2010-07-06 13:05:31 filesystem=ext4 label=Storage lastmountpoint=/media/Storage&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;V&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;kY&#65533;P'&#65533;Dq!&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;@'&#65533;P&#65533;&#65533;&#65533;P&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;V modified=2010-12-31 19:06:50 mounted=2010-12-31 16:10:

---

### Post by ricardisimo on 2011-01-21
Hello?

---

### Post by ricardisimo on 2011-02-04
Echo??

---

### Post by ricardisimo on 2011-02-18
Here's my fstab:
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=a165b786-48a1-4d80-ac42-13f57cb918af /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a0b4e799-6d8a-4377-be28-b62396870234 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
What the hell happened to my extra drive? How did it just disappear from fstab? Commented out is one thing, but completely gone...? There's not a single reference to the /dev/sdb drive. Weird.

I'm also a bit disturbed by all of the past tense in the descriptors above. "was on /dev/sda5 during installation" and so on. What's that all about?

One more thing: Why does lshw read the "missing" drive as ext4? Since when? Shouldn't it always have been - and continue to be today - ext3? What gives?

---

### Post by matt_symes on 2011-02-18
Hi

Can you try the drive (sdb) in another computer ? 

I don't suppose you see it under

```
ls /dev/sd*
``` 

I'm not sure what to make of it :(

Does

```
cat /var/log/kern.log | grep sdb
```

return anything ?

Kind regards

---

### Post by ricardisimo on 2011-02-18
ls /dev/sdb only returns "/dev/sdb". No contents listed at all.

The other command returns a plethora of I/O errors, so many that it bumps the first half or third right off of the screen. Is there a way to run this same command, returning values only one page at a time? In the meantime, here's the tail end of what it returned:
```
Feb 17 23:00:14 ricardo-desktop kernel: [  638.115378] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:00:14 ricardo-desktop kernel: [  638.115381] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:00:14 ricardo-desktop kernel: [  638.115385] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:00:14 ricardo-desktop kernel: [  638.115407] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:00:14 ricardo-desktop kernel: [  638.115413] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
Feb 17 23:00:14 ricardo-desktop kernel: [  638.115422] end_request: I/O error, dev sdb, sector 8
Feb 17 23:00:14 ricardo-desktop kernel: [  638.115427] Buffer I/O error on device sdb, logical block 1
Feb 17 23:00:15 ricardo-desktop kernel: [  639.616865] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:00:15 ricardo-desktop kernel: [  639.616868] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:00:15 ricardo-desktop kernel: [  639.616871] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:00:15 ricardo-desktop kernel: [  639.616893] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:00:15 ricardo-desktop kernel: [  639.616899] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 78 00 00 08 00
Feb 17 23:00:15 ricardo-desktop kernel: [  639.616908] end_request: I/O error, dev sdb, sector 120
Feb 17 23:00:15 ricardo-desktop kernel: [  639.616912] Buffer I/O error on device sdb, logical block 15
Feb 17 23:00:30 ricardo-desktop kernel: [  654.632472] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:00:30 ricardo-desktop kernel: [  654.632474] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:00:30 ricardo-desktop kernel: [  654.632477] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:00:30 ricardo-desktop kernel: [  654.632493] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:00:30 ricardo-desktop kernel: [  654.632497] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 78 00 00 08 00
Feb 17 23:00:30 ricardo-desktop kernel: [  654.632504] end_request: I/O error, dev sdb, sector 120
Feb 17 23:00:30 ricardo-desktop kernel: [  654.632507] Buffer I/O error on device sdb, logical block 15
Feb 17 23:00:32 ricardo-desktop kernel: [  656.134009] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:00:32 ricardo-desktop kernel: [  656.134011] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:00:32 ricardo-desktop kernel: [  656.134015] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:00:32 ricardo-desktop kernel: [  656.134037] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:00:32 ricardo-desktop kernel: [  656.134043] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 18 00 00 08 00
Feb 17 23:00:32 ricardo-desktop kernel: [  656.134052] end_request: I/O error, dev sdb, sector 24
Feb 17 23:00:32 ricardo-desktop kernel: [  656.134056] Buffer I/O error on device sdb, logical block 3
Feb 17 23:00:47 ricardo-desktop kernel: [  671.293234] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:00:47 ricardo-desktop kernel: [  671.293237] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:00:47 ricardo-desktop kernel: [  671.293241] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:00:47 ricardo-desktop kernel: [  671.293263] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:00:47 ricardo-desktop kernel: [  671.293270] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 18 00 00 08 00
Feb 17 23:00:47 ricardo-desktop kernel: [  671.293279] end_request: I/O error, dev sdb, sector 24
Feb 17 23:00:47 ricardo-desktop kernel: [  671.293283] Buffer I/O error on device sdb, logical block 3
Feb 17 23:00:49 ricardo-desktop kernel: [  672.794652] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:00:49 ricardo-desktop kernel: [  672.794654] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:00:49 ricardo-desktop kernel: [  672.794658] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:00:49 ricardo-desktop kernel: [  672.794680] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:00:49 ricardo-desktop kernel: [  672.794686] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
Feb 17 23:00:49 ricardo-desktop kernel: [  672.794695] end_request: I/O error, dev sdb, sector 16
Feb 17 23:00:49 ricardo-desktop kernel: [  672.794700] Buffer I/O error on device sdb, logical block 2
Feb 17 23:01:05 ricardo-desktop kernel: [  688.991789] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:01:05 ricardo-desktop kernel: [  688.991792] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:01:05 ricardo-desktop kernel: [  688.991796] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:01:05 ricardo-desktop kernel: [  688.991818] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:01:05 ricardo-desktop kernel: [  688.991825] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
Feb 17 23:01:05 ricardo-desktop kernel: [  688.991834] end_request: I/O error, dev sdb, sector 128
Feb 17 23:01:05 ricardo-desktop kernel: [  688.991838] Buffer I/O error on device sdb, logical block 16
Feb 17 23:01:06 ricardo-desktop kernel: [  690.493333] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:01:06 ricardo-desktop kernel: [  690.493335] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:01:06 ricardo-desktop kernel: [  690.493339] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:01:06 ricardo-desktop kernel: [  690.493361] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:01:06 ricardo-desktop kernel: [  690.493367] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
Feb 17 23:01:06 ricardo-desktop kernel: [  690.493376] end_request: I/O error, dev sdb, sector 56
Feb 17 23:01:06 ricardo-desktop kernel: [  690.493380] Buffer I/O error on device sdb, logical block 7
Feb 17 23:01:22 ricardo-desktop kernel: [  706.348044] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:01:22 ricardo-desktop kernel: [  706.348047] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:01:22 ricardo-desktop kernel: [  706.348051] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:01:22 ricardo-desktop kernel: [  706.348073] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:01:22 ricardo-desktop kernel: [  706.348079] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
Feb 17 23:01:22 ricardo-desktop kernel: [  706.348088] end_request: I/O error, dev sdb, sector 56
Feb 17 23:01:22 ricardo-desktop kernel: [  706.348092] Buffer I/O error on device sdb, logical block 7
Feb 17 23:01:24 ricardo-desktop kernel: [  708.004147] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:01:24 ricardo-desktop kernel: [  708.004150] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:01:24 ricardo-desktop kernel: [  708.004154] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:01:24 ricardo-desktop kernel: [  708.004176] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:01:24 ricardo-desktop kernel: [  708.004182] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
Feb 17 23:01:24 ricardo-desktop kernel: [  708.004191] end_request: I/O error, dev sdb, sector 128
Feb 17 23:01:24 ricardo-desktop kernel: [  708.004195] Buffer I/O error on device sdb, logical block 16
Feb 17 23:01:40 ricardo-desktop kernel: [  724.013417] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:01:40 ricardo-desktop kernel: [  724.013420] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:01:40 ricardo-desktop kernel: [  724.013424] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:01:40 ricardo-desktop kernel: [  724.013446] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:01:40 ricardo-desktop kernel: [  724.013452] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
Feb 17 23:01:40 ricardo-desktop kernel: [  724.013462] end_request: I/O error, dev sdb, sector 128
Feb 17 23:01:40 ricardo-desktop kernel: [  724.013466] Buffer I/O error on device sdb, logical block 16
Feb 17 23:01:41 ricardo-desktop kernel: [  725.515112] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:01:41 ricardo-desktop kernel: [  725.515113] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:01:41 ricardo-desktop kernel: [  725.515116] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:01:41 ricardo-desktop kernel: [  725.515129] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:01:41 ricardo-desktop kernel: [  725.515133] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 78 00 00 08 00
Feb 17 23:01:41 ricardo-desktop kernel: [  725.515138] end_request: I/O error, dev sdb, sector 120
Feb 17 23:01:41 ricardo-desktop kernel: [  725.515141] Buffer I/O error on device sdb, logical block 15
Feb 17 23:01:57 ricardo-desktop kernel: [  740.894991] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:01:57 ricardo-desktop kernel: [  740.894994] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:01:57 ricardo-desktop kernel: [  740.895001] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:01:57 ricardo-desktop kernel: [  740.895018] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:01:57 ricardo-desktop kernel: [  740.895023] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
Feb 17 23:01:57 ricardo-desktop kernel: [  740.895030] end_request: I/O error, dev sdb, sector 16
Feb 17 23:01:57 ricardo-desktop kernel: [  740.895033] Buffer I/O error on device sdb, logical block 2
Feb 17 23:01:58 ricardo-desktop kernel: [  742.396687] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:01:58 ricardo-desktop kernel: [  742.396689] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:01:58 ricardo-desktop kernel: [  742.396693] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:01:58 ricardo-desktop kernel: [  742.396715] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:01:58 ricardo-desktop kernel: [  742.396721] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 78 00 00 08 00
Feb 17 23:01:58 ricardo-desktop kernel: [  742.396730] end_request: I/O error, dev sdb, sector 120
Feb 17 23:01:58 ricardo-desktop kernel: [  742.396734] Buffer I/O error on device sdb, logical block 15
Feb 17 23:02:13 ricardo-desktop kernel: [  757.080971] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:02:13 ricardo-desktop kernel: [  757.080974] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:02:13 ricardo-desktop kernel: [  757.080978] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:02:13 ricardo-desktop kernel: [  757.081000] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:02:13 ricardo-desktop kernel: [  757.081006] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
Feb 17 23:02:13 ricardo-desktop kernel: [  757.081015] end_request: I/O error, dev sdb, sector 132
Feb 17 23:02:13 ricardo-desktop kernel: [  757.081019] Buffer I/O error on device sdb, logical block 16
Feb 17 23:02:14 ricardo-desktop kernel: [  758.582638] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:02:14 ricardo-desktop kernel: [  758.582641] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:02:14 ricardo-desktop kernel: [  758.582645] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:02:14 ricardo-desktop kernel: [  758.582704] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:02:14 ricardo-desktop kernel: [  758.582712] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
Feb 17 23:02:14 ricardo-desktop kernel: [  758.582734] end_request: I/O error, dev sdb, sector 16
Feb 17 23:02:14 ricardo-desktop kernel: [  758.582739] Buffer I/O error on device sdb, logical block 2
Feb 17 23:02:29 ricardo-desktop kernel: [  773.211761] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:02:29 ricardo-desktop kernel: [  773.211762] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:02:29 ricardo-desktop kernel: [  773.211765] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:02:29 ricardo-desktop kernel: [  773.211778] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:02:29 ricardo-desktop kernel: [  773.211782] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
Feb 17 23:02:29 ricardo-desktop kernel: [  773.211787] end_request: I/O error, dev sdb, sector 71
Feb 17 23:02:29 ricardo-desktop kernel: [  773.211790] Buffer I/O error on device sdb, logical block 8
Feb 17 23:02:31 ricardo-desktop kernel: [  774.878903] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:02:31 ricardo-desktop kernel: [  774.878905] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:02:31 ricardo-desktop kernel: [  774.878909] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:02:31 ricardo-desktop kernel: [  774.878932] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:02:31 ricardo-desktop kernel: [  774.878938] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
Feb 17 23:02:31 ricardo-desktop kernel: [  774.878947] end_request: I/O error, dev sdb, sector 128
Feb 17 23:02:31 ricardo-desktop kernel: [  774.878951] Buffer I/O error on device sdb, logical block 16
Feb 17 23:02:45 ricardo-desktop kernel: [  789.629550] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:02:45 ricardo-desktop kernel: [  789.629553] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:02:45 ricardo-desktop kernel: [  789.629557] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:02:45 ricardo-desktop kernel: [  789.629579] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:02:45 ricardo-desktop kernel: [  789.629585] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
Feb 17 23:02:45 ricardo-desktop kernel: [  789.629594] end_request: I/O error, dev sdb, sector 71
Feb 17 23:02:45 ricardo-desktop kernel: [  789.629598] Buffer I/O error on device sdb, logical block 8
Feb 17 23:02:47 ricardo-desktop kernel: [  791.142213] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:02:47 ricardo-desktop kernel: [  791.142215] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:02:47 ricardo-desktop kernel: [  791.142219] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:02:47 ricardo-desktop kernel: [  791.142240] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:02:47 ricardo-desktop kernel: [  791.142246] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
Feb 17 23:02:47 ricardo-desktop kernel: [  791.142255] end_request: I/O error, dev sdb, sector 128
Feb 17 23:02:47 ricardo-desktop kernel: [  791.142259] Buffer I/O error on device sdb, logical block 16
Feb 17 23:03:02 ricardo-desktop kernel: [  806.080482] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:03:02 ricardo-desktop kernel: [  806.080485] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:03:02 ricardo-desktop kernel: [  806.080489] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:03:02 ricardo-desktop kernel: [  806.080511] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:03:02 ricardo-desktop kernel: [  806.080517] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
Feb 17 23:03:02 ricardo-desktop kernel: [  806.080526] end_request: I/O error, dev sdb, sector 71
Feb 17 23:03:02 ricardo-desktop kernel: [  806.080530] Buffer I/O error on device sdb, logical block 8
Feb 17 23:03:04 ricardo-desktop kernel: [  807.747674] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:03:04 ricardo-desktop kernel: [  807.747677] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:03:04 ricardo-desktop kernel: [  807.747680] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:03:04 ricardo-desktop kernel: [  807.747702] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:03:04 ricardo-desktop kernel: [  807.747707] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
Feb 17 23:03:04 ricardo-desktop kernel: [  807.747716] end_request: I/O error, dev sdb, sector 128
Feb 17 23:03:04 ricardo-desktop kernel: [  807.747720] Buffer I/O error on device sdb, logical block 16
Feb 17 23:03:18 ricardo-desktop kernel: [  821.736441] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:03:18 ricardo-desktop kernel: [  821.736444] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:03:18 ricardo-desktop kernel: [  821.736448] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:03:18 ricardo-desktop kernel: [  821.736470] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:03:18 ricardo-desktop kernel: [  821.736476] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
Feb 17 23:03:18 ricardo-desktop kernel: [  821.736486] end_request: I/O error, dev sdb, sector 71
Feb 17 23:03:18 ricardo-desktop kernel: [  821.736490] Buffer I/O error on device sdb, logical block 8
Feb 17 23:03:19 ricardo-desktop kernel: [  823.249074] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:03:19 ricardo-desktop kernel: [  823.249076] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:03:19 ricardo-desktop kernel: [  823.249080] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:03:19 ricardo-desktop kernel: [  823.249102] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:03:19 ricardo-desktop kernel: [  823.249107] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
Feb 17 23:03:19 ricardo-desktop kernel: [  823.249116] end_request: I/O error, dev sdb, sector 16
Feb 17 23:03:19 ricardo-desktop kernel: [  823.249120] Buffer I/O error on device sdb, logical block 2
Feb 17 23:03:34 ricardo-desktop kernel: [  837.867173] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:03:34 ricardo-desktop kernel: [  837.867176] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:03:34 ricardo-desktop kernel: [  837.867180] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:03:34 ricardo-desktop kernel: [  837.867202] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:03:34 ricardo-desktop kernel: [  837.867209] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
Feb 17 23:03:34 ricardo-desktop kernel: [  837.867218] end_request: I/O error, dev sdb, sector 71
Feb 17 23:03:34 ricardo-desktop kernel: [  837.867222] Buffer I/O error on device sdb, logical block 8
Feb 17 23:03:35 ricardo-desktop kernel: [  839.545454] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:03:35 ricardo-desktop kernel: [  839.545457] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:03:35 ricardo-desktop kernel: [  839.545460] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:03:35 ricardo-desktop kernel: [  839.545482] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:03:35 ricardo-desktop kernel: [  839.545487] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
Feb 17 23:03:35 ricardo-desktop kernel: [  839.545496] end_request: I/O error, dev sdb, sector 128
Feb 17 23:03:35 ricardo-desktop kernel: [  839.545500] Buffer I/O error on device sdb, logical block 16
Feb 17 23:03:43 ricardo-desktop kernel: [  847.539059] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:03:43 ricardo-desktop kernel: [  847.539062] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:03:43 ricardo-desktop kernel: [  847.539066] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:03:43 ricardo-desktop kernel: [  847.539088] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:03:43 ricardo-desktop kernel: [  847.539094] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
Feb 17 23:03:43 ricardo-desktop kernel: [  847.539103] end_request: I/O error, dev sdb, sector 71
Feb 17 23:03:43 ricardo-desktop kernel: [  847.539108] Buffer I/O error on device sdb, logical block 8
Feb 17 23:03:53 ricardo-desktop kernel: [  857.122753] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:03:53 ricardo-desktop kernel: [  857.122756] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:03:53 ricardo-desktop kernel: [  857.122760] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:03:53 ricardo-desktop kernel: [  857.122782] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:03:53 ricardo-desktop kernel: [  857.122788] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
Feb 17 23:03:53 ricardo-desktop kernel: [  857.122797] end_request: I/O error, dev sdb, sector 71
Feb 17 23:03:53 ricardo-desktop kernel: [  857.122801] Buffer I/O error on device sdb, logical block 8
Feb 17 23:04:03 ricardo-desktop kernel: [  866.717103] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:04:03 ricardo-desktop kernel: [  866.717106] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:04:03 ricardo-desktop kernel: [  866.717110] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:04:03 ricardo-desktop kernel: [  866.717132] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:04:03 ricardo-desktop kernel: [  866.717138] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
Feb 17 23:04:03 ricardo-desktop kernel: [  866.717148] end_request: I/O error, dev sdb, sector 71
Feb 17 23:04:03 ricardo-desktop kernel: [  866.717152] Buffer I/O error on device sdb, logical block 8
Feb 17 23:04:12 ricardo-desktop kernel: [  876.278312] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:04:12 ricardo-desktop kernel: [  876.278315] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:04:12 ricardo-desktop kernel: [  876.278319] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:04:12 ricardo-desktop kernel: [  876.278341] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:04:12 ricardo-desktop kernel: [  876.278347] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
Feb 17 23:04:12 ricardo-desktop kernel: [  876.278356] end_request: I/O error, dev sdb, sector 71
Feb 17 23:04:12 ricardo-desktop kernel: [  876.278360] Buffer I/O error on device sdb, logical block 8
Feb 17 23:04:22 ricardo-desktop kernel: [  886.171229] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:04:22 ricardo-desktop kernel: [  886.171232] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:04:22 ricardo-desktop kernel: [  886.171236] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:04:22 ricardo-desktop kernel: [  886.171258] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:04:22 ricardo-desktop kernel: [  886.171264] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
Feb 17 23:04:22 ricardo-desktop kernel: [  886.171273] end_request: I/O error, dev sdb, sector 71
Feb 17 23:04:22 ricardo-desktop kernel: [  886.171278] Buffer I/O error on device sdb, logical block 8
Feb 17 23:04:32 ricardo-desktop kernel: [  895.699274] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:04:32 ricardo-desktop kernel: [  895.699277] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:04:32 ricardo-desktop kernel: [  895.699281] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:04:32 ricardo-desktop kernel: [  895.699303] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:04:32 ricardo-desktop kernel: [  895.699309] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
Feb 17 23:04:32 ricardo-desktop kernel: [  895.699318] end_request: I/O error, dev sdb, sector 71
Feb 17 23:04:32 ricardo-desktop kernel: [  895.699323] Buffer I/O error on device sdb, logical block 8
Feb 17 23:04:41 ricardo-desktop kernel: [  905.437508] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:04:41 ricardo-desktop kernel: [  905.437511] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:04:41 ricardo-desktop kernel: [  905.437515] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:04:41 ricardo-desktop kernel: [  905.437537] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:04:41 ricardo-desktop kernel: [  905.437544] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
Feb 17 23:04:41 ricardo-desktop kernel: [  905.437553] end_request: I/O error, dev sdb, sector 71
Feb 17 23:04:41 ricardo-desktop kernel: [  905.437557] Buffer I/O error on device sdb, logical block 8
Feb 17 23:04:51 ricardo-desktop kernel: [  915.142464] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:04:51 ricardo-desktop kernel: [  915.142467] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:04:51 ricardo-desktop kernel: [  915.142471] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:04:51 ricardo-desktop kernel: [  915.142494] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:04:51 ricardo-desktop kernel: [  915.142500] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
Feb 17 23:04:51 ricardo-desktop kernel: [  915.142509] end_request: I/O error, dev sdb, sector 71
Feb 17 23:04:51 ricardo-desktop kernel: [  915.142513] Buffer I/O error on device sdb, logical block 8
Feb 17 23:05:00 ricardo-desktop kernel: [  924.659805] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:05:00 ricardo-desktop kernel: [  924.659808] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:05:00 ricardo-desktop kernel: [  924.659812] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:05:00 ricardo-desktop kernel: [  924.659834] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:05:00 ricardo-desktop kernel: [  924.659840] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
Feb 17 23:05:00 ricardo-desktop kernel: [  924.659850] end_request: I/O error, dev sdb, sector 71
Feb 17 23:05:00 ricardo-desktop kernel: [  924.659854] Buffer I/O error on device sdb, logical block 8
Feb 17 23:05:10 ricardo-desktop kernel: [  934.199137] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:05:10 ricardo-desktop kernel: [  934.199140] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:05:10 ricardo-desktop kernel: [  934.199144] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:05:10 ricardo-desktop kernel: [  934.199166] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:05:10 ricardo-desktop kernel: [  934.199173] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
Feb 17 23:05:10 ricardo-desktop kernel: [  934.199182] end_request: I/O error, dev sdb, sector 71
Feb 17 23:05:10 ricardo-desktop kernel: [  934.199186] Buffer I/O error on device sdb, logical block 8
Feb 17 23:05:20 ricardo-desktop kernel: [  943.937173] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:05:20 ricardo-desktop kernel: [  943.937176] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:05:20 ricardo-desktop kernel: [  943.937180] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:05:20 ricardo-desktop kernel: [  943.937202] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:05:20 ricardo-desktop kernel: [  943.937208] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
Feb 17 23:05:20 ricardo-desktop kernel: [  943.937218] end_request: I/O error, dev sdb, sector 71
Feb 17 23:05:20 ricardo-desktop kernel: [  943.937222] Buffer I/O error on device sdb, logical block 8
Feb 17 23:05:32 ricardo-desktop kernel: [  956.413383] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:05:32 ricardo-desktop kernel: [  956.413386] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:05:32 ricardo-desktop kernel: [  956.413390] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:05:32 ricardo-desktop kernel: [  956.413412] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:05:32 ricardo-desktop kernel: [  956.413418] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 01 00 00 00 08 00
Feb 17 23:05:32 ricardo-desktop kernel: [  956.413427] end_request: I/O error, dev sdb, sector 256
Feb 17 23:05:32 ricardo-desktop kernel: [  956.413431] Buffer I/O error on device sdb, logical block 32
Feb 17 23:05:42 ricardo-desktop kernel: [  966.460433] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:05:42 ricardo-desktop kernel: [  966.460436] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:05:42 ricardo-desktop kernel: [  966.460440] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:05:42 ricardo-desktop kernel: [  966.460462] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:05:42 ricardo-desktop kernel: [  966.460468] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 01 00 00 00 08 00
Feb 17 23:05:42 ricardo-desktop kernel: [  966.460477] end_request: I/O error, dev sdb, sector 256
Feb 17 23:05:42 ricardo-desktop kernel: [  966.460481] Buffer I/O error on device sdb, logical block 32
Feb 17 23:05:58 ricardo-desktop kernel: [  982.668697] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:05:58 ricardo-desktop kernel: [  982.668700] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:05:58 ricardo-desktop kernel: [  982.668704] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:05:58 ricardo-desktop kernel: [  982.668726] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:05:58 ricardo-desktop kernel: [  982.668732] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 01 00 00 00 08 00
Feb 17 23:05:58 ricardo-desktop kernel: [  982.668741] end_request: I/O error, dev sdb, sector 256
Feb 17 23:05:58 ricardo-desktop kernel: [  982.668745] Buffer I/O error on device sdb, logical block 32
Feb 17 23:06:00 ricardo-desktop kernel: [  984.170257] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:06:00 ricardo-desktop kernel: [  984.170259] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:06:00 ricardo-desktop kernel: [  984.170263] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:06:00 ricardo-desktop kernel: [  984.170285] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:06:00 ricardo-desktop kernel: [  984.170291] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 01 08 00 00 08 00
Feb 17 23:06:00 ricardo-desktop kernel: [  984.170300] end_request: I/O error, dev sdb, sector 264
Feb 17 23:06:00 ricardo-desktop kernel: [  984.170303] Buffer I/O error on device sdb, logical block 33
Feb 17 23:06:14 ricardo-desktop kernel: [  998.313562] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:06:14 ricardo-desktop kernel: [  998.313565] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:06:14 ricardo-desktop kernel: [  998.313569] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:06:14 ricardo-desktop kernel: [  998.313591] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:06:14 ricardo-desktop kernel: [  998.313597] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 01 00 00 00 08 00
Feb 17 23:06:14 ricardo-desktop kernel: [  998.313606] end_request: I/O error, dev sdb, sector 256
Feb 17 23:06:14 ricardo-desktop kernel: [  998.313610] Buffer I/O error on device sdb, logical block 32
Feb 17 23:06:16 ricardo-desktop kernel: [  999.826234] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:06:16 ricardo-desktop kernel: [  999.826237] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:06:16 ricardo-desktop kernel: [  999.826241] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:06:16 ricardo-desktop kernel: [  999.826263] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:06:16 ricardo-desktop kernel: [  999.826269] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 01 08 00 00 08 00
Feb 17 23:06:16 ricardo-desktop kernel: [  999.826278] end_request: I/O error, dev sdb, sector 264
Feb 17 23:06:16 ricardo-desktop kernel: [  999.826282] Buffer I/O error on device sdb, logical block 33
Feb 17 23:06:31 ricardo-desktop kernel: [ 1014.841867] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:06:31 ricardo-desktop kernel: [ 1014.841870] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:06:31 ricardo-desktop kernel: [ 1014.841874] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:06:31 ricardo-desktop kernel: [ 1014.841896] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:06:31 ricardo-desktop kernel: [ 1014.841902] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 01 08 00 00 08 00
Feb 17 23:06:31 ricardo-desktop kernel: [ 1014.841911] end_request: I/O error, dev sdb, sector 264
Feb 17 23:06:31 ricardo-desktop kernel: [ 1014.841916] Buffer I/O error on device sdb, logical block 33
Feb 17 23:06:32 ricardo-desktop kernel: [ 1016.343443] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:06:32 ricardo-desktop kernel: [ 1016.343446] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:06:32 ricardo-desktop kernel: [ 1016.343449] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:06:32 ricardo-desktop kernel: [ 1016.343472] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:06:32 ricardo-desktop kernel: [ 1016.343478] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 01 10 00 00 08 00
Feb 17 23:06:32 ricardo-desktop kernel: [ 1016.343487] end_request: I/O error, dev sdb, sector 272
Feb 17 23:06:32 ricardo-desktop kernel: [ 1016.343491] Buffer I/O error on device sdb, logical block 34
Feb 17 23:06:46 ricardo-desktop kernel: [ 1030.188625] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:06:46 ricardo-desktop kernel: [ 1030.188628] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:06:46 ricardo-desktop kernel: [ 1030.188632] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:06:46 ricardo-desktop kernel: [ 1030.188654] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:06:46 ricardo-desktop kernel: [ 1030.188660] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 01 08 00 00 08 00
Feb 17 23:06:46 ricardo-desktop kernel: [ 1030.188669] end_request: I/O error, dev sdb, sector 264
Feb 17 23:06:46 ricardo-desktop kernel: [ 1030.188674] Buffer I/O error on device sdb, logical block 33
Feb 17 23:06:48 ricardo-desktop kernel: [ 1031.855784] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:06:48 ricardo-desktop kernel: [ 1031.855787] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:06:48 ricardo-desktop kernel: [ 1031.855791] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:06:48 ricardo-desktop kernel: [ 1031.855813] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:06:48 ricardo-desktop kernel: [ 1031.855819] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 01 10 00 00 08 00
Feb 17 23:06:48 ricardo-desktop kernel: [ 1031.855850] end_request: I/O error, dev sdb, sector 272
Feb 17 23:06:48 ricardo-desktop kernel: [ 1031.855858] Buffer I/O error on device sdb, logical block 34
Feb 17 23:07:03 ricardo-desktop kernel: [ 1047.522559] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:07:03 ricardo-desktop kernel: [ 1047.522562] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:07:03 ricardo-desktop kernel: [ 1047.522566] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:07:03 ricardo-desktop kernel: [ 1047.522588] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:07:03 ricardo-desktop kernel: [ 1047.522594] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 01 10 00 00 08 00
Feb 17 23:07:03 ricardo-desktop kernel: [ 1047.522603] end_request: I/O error, dev sdb, sector 273
Feb 17 23:07:03 ricardo-desktop kernel: [ 1047.522607] Buffer I/O error on device sdb, logical block 34
Feb 17 23:07:05 ricardo-desktop kernel: [ 1049.024479] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:07:05 ricardo-desktop kernel: [ 1049.024482] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:07:05 ricardo-desktop kernel: [ 1049.024485] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:07:05 ricardo-desktop kernel: [ 1049.024507] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:07:05 ricardo-desktop kernel: [ 1049.024513] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 03 00 00 00 08 00
Feb 17 23:07:05 ricardo-desktop kernel: [ 1049.024522] end_request: I/O error, dev sdb, sector 768
Feb 17 23:07:05 ricardo-desktop kernel: [ 1049.024526] Buffer I/O error on device sdb, logical block 96
Feb 17 23:07:19 ricardo-desktop kernel: [ 1063.178808] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:07:19 ricardo-desktop kernel: [ 1063.178811] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:07:19 ricardo-desktop kernel: [ 1063.178815] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:07:19 ricardo-desktop kernel: [ 1063.178837] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:07:19 ricardo-desktop kernel: [ 1063.178843] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 01 10 00 00 08 00
Feb 17 23:07:19 ricardo-desktop kernel: [ 1063.178852] end_request: I/O error, dev sdb, sector 272
Feb 17 23:07:19 ricardo-desktop kernel: [ 1063.178857] Buffer I/O error on device sdb, logical block 34
Feb 17 23:07:20 ricardo-desktop kernel: [ 1064.669240] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:07:20 ricardo-desktop kernel: [ 1064.669243] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:07:20 ricardo-desktop kernel: [ 1064.669247] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:07:20 ricardo-desktop kernel: [ 1064.669269] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:07:20 ricardo-desktop kernel: [ 1064.669274] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 03 00 00 00 08 00
Feb 17 23:07:20 ricardo-desktop kernel: [ 1064.669283] end_request: I/O error, dev sdb, sector 768
Feb 17 23:07:20 ricardo-desktop kernel: [ 1064.669287] Buffer I/O error on device sdb, logical block 96
Feb 17 23:07:30 ricardo-desktop kernel: [ 1074.054197] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:07:30 ricardo-desktop kernel: [ 1074.054199] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:07:30 ricardo-desktop kernel: [ 1074.054203] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:07:30 ricardo-desktop kernel: [ 1074.054226] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:07:30 ricardo-desktop kernel: [ 1074.054232] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
Feb 17 23:07:30 ricardo-desktop kernel: [ 1074.054244] end_request: I/O error, dev sdb, sector 16
Feb 17 23:07:30 ricardo-desktop kernel: [ 1074.054248] Buffer I/O error on device sdb, logical block 2
Feb 17 23:07:39 ricardo-desktop kernel: [ 1083.074336] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:07:39 ricardo-desktop kernel: [ 1083.074339] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:07:39 ricardo-desktop kernel: [ 1083.074343] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:07:39 ricardo-desktop kernel: [ 1083.074364] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:07:39 ricardo-desktop kernel: [ 1083.074370] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
Feb 17 23:07:39 ricardo-desktop kernel: [ 1083.074380] end_request: I/O error, dev sdb, sector 16
Feb 17 23:07:39 ricardo-desktop kernel: [ 1083.074384] Buffer I/O error on device sdb, logical block 2
Feb 17 23:07:48 ricardo-desktop kernel: [ 1092.128143] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:07:48 ricardo-desktop kernel: [ 1092.128146] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:07:48 ricardo-desktop kernel: [ 1092.128150] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:07:48 ricardo-desktop kernel: [ 1092.128172] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:07:48 ricardo-desktop kernel: [ 1092.128178] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
Feb 17 23:07:48 ricardo-desktop kernel: [ 1092.128187] end_request: I/O error, dev sdb, sector 16
Feb 17 23:07:48 ricardo-desktop kernel: [ 1092.128192] Buffer I/O error on device sdb, logical block 2
Feb 17 23:07:57 ricardo-desktop kernel: [ 1101.314161] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:07:57 ricardo-desktop kernel: [ 1101.314164] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:07:57 ricardo-desktop kernel: [ 1101.314168] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:07:57 ricardo-desktop kernel: [ 1101.314190] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:07:57 ricardo-desktop kernel: [ 1101.314196] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
Feb 17 23:07:57 ricardo-desktop kernel: [ 1101.314205] end_request: I/O error, dev sdb, sector 16
Feb 17 23:07:57 ricardo-desktop kernel: [ 1101.314209] Buffer I/O error on device sdb, logical block 2
Feb 17 23:08:13 ricardo-desktop kernel: [ 1117.146794] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:08:13 ricardo-desktop kernel: [ 1117.146797] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:08:13 ricardo-desktop kernel: [ 1117.146801] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:08:13 ricardo-desktop kernel: [ 1117.146823] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:08:13 ricardo-desktop kernel: [ 1117.146829] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
Feb 17 23:08:13 ricardo-desktop kernel: [ 1117.146838] end_request: I/O error, dev sdb, sector 16
Feb 17 23:08:13 ricardo-desktop kernel: [ 1117.146843] Buffer I/O error on device sdb, logical block 2
Feb 17 23:08:15 ricardo-desktop kernel: [ 1118.802874] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:08:15 ricardo-desktop kernel: [ 1118.802877] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:08:15 ricardo-desktop kernel: [ 1118.802881] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:08:15 ricardo-desktop kernel: [ 1118.802903] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:08:15 ricardo-desktop kernel: [ 1118.802909] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
Feb 17 23:08:15 ricardo-desktop kernel: [ 1118.802918] end_request: I/O error, dev sdb, sector 128
Feb 17 23:08:15 ricardo-desktop kernel: [ 1118.802922] Buffer I/O error on device sdb, logical block 16
Feb 17 23:08:29 ricardo-desktop kernel: [ 1133.365810] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:08:29 ricardo-desktop kernel: [ 1133.365813] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:08:29 ricardo-desktop kernel: [ 1133.365817] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:08:29 ricardo-desktop kernel: [ 1133.365839] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:08:29 ricardo-desktop kernel: [ 1133.365845] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
Feb 17 23:08:29 ricardo-desktop kernel: [ 1133.365854] end_request: I/O error, dev sdb, sector 16
Feb 17 23:08:29 ricardo-desktop kernel: [ 1133.365859] Buffer I/O error on device sdb, logical block 2
Feb 17 23:08:31 ricardo-desktop kernel: [ 1135.033012] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:08:31 ricardo-desktop kernel: [ 1135.033015] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:08:31 ricardo-desktop kernel: [ 1135.033019] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:08:31 ricardo-desktop kernel: [ 1135.033041] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:08:31 ricardo-desktop kernel: [ 1135.033047] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
Feb 17 23:08:31 ricardo-desktop kernel: [ 1135.033056] end_request: I/O error, dev sdb, sector 128
Feb 17 23:08:31 ricardo-desktop kernel: [ 1135.033060] Buffer I/O error on device sdb, logical block 16
Feb 17 23:08:47 ricardo-desktop kernel: [ 1150.942801] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:08:47 ricardo-desktop kernel: [ 1150.942804] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:08:47 ricardo-desktop kernel: [ 1150.942808] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:08:47 ricardo-desktop kernel: [ 1150.942830] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:08:47 ricardo-desktop kernel: [ 1150.942836] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
Feb 17 23:08:47 ricardo-desktop kernel: [ 1150.942845] end_request: I/O error, dev sdb, sector 128
Feb 17 23:08:47 ricardo-desktop kernel: [ 1150.942849] Buffer I/O error on device sdb, logical block 16
Feb 17 23:08:48 ricardo-desktop kernel: [ 1152.444524] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:08:48 ricardo-desktop kernel: [ 1152.444527] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:08:48 ricardo-desktop kernel: [ 1152.444531] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:08:48 ricardo-desktop kernel: [ 1152.444553] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:08:48 ricardo-desktop kernel: [ 1152.444558] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
Feb 17 23:08:48 ricardo-desktop kernel: [ 1152.444567] end_request: I/O error, dev sdb, sector 16
Feb 17 23:08:48 ricardo-desktop kernel: [ 1152.444571] Buffer I/O error on device sdb, logical block 2
Feb 17 23:09:04 ricardo-desktop kernel: [ 1168.089466] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:09:04 ricardo-desktop kernel: [ 1168.089468] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:09:04 ricardo-desktop kernel: [ 1168.089472] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:09:04 ricardo-desktop kernel: [ 1168.089494] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:09:04 ricardo-desktop kernel: [ 1168.089500] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
Feb 17 23:09:04 ricardo-desktop kernel: [ 1168.089510] end_request: I/O error, dev sdb, sector 128
Feb 17 23:09:04 ricardo-desktop kernel: [ 1168.089514] Buffer I/O error on device sdb, logical block 16
Feb 17 23:09:05 ricardo-desktop kernel: [ 1169.602063] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:09:05 ricardo-desktop kernel: [ 1169.602065] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:09:05 ricardo-desktop kernel: [ 1169.602069] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:09:05 ricardo-desktop kernel: [ 1169.602091] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:09:05 ricardo-desktop kernel: [ 1169.602097] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
Feb 17 23:09:05 ricardo-desktop kernel: [ 1169.602106] end_request: I/O error, dev sdb, sector 8
Feb 17 23:09:05 ricardo-desktop kernel: [ 1169.602109] Buffer I/O error on device sdb, logical block 1
Feb 17 23:09:13 ricardo-desktop kernel: [ 1177.131965] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:09:13 ricardo-desktop kernel: [ 1177.131968] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:09:13 ricardo-desktop kernel: [ 1177.131972] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:09:13 ricardo-desktop kernel: [ 1177.131994] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:09:13 ricardo-desktop kernel: [ 1177.132001] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
Feb 17 23:09:13 ricardo-desktop kernel: [ 1177.132010] end_request: I/O error, dev sdb, sector 16
Feb 17 23:09:13 ricardo-desktop kernel: [ 1177.132014] Buffer I/O error on device sdb, logical block 2
Feb 17 23:09:29 ricardo-desktop kernel: [ 1193.538760] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:09:29 ricardo-desktop kernel: [ 1193.538763] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:09:29 ricardo-desktop kernel: [ 1193.538767] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:09:29 ricardo-desktop kernel: [ 1193.538789] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:09:29 ricardo-desktop kernel: [ 1193.538795] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
Feb 17 23:09:29 ricardo-desktop kernel: [ 1193.538805] end_request: I/O error, dev sdb, sector 16
Feb 17 23:09:29 ricardo-desktop kernel: [ 1193.538809] Buffer I/O error on device sdb, logical block 2
Feb 17 23:09:31 ricardo-desktop kernel: [ 1195.040351] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:09:31 ricardo-desktop kernel: [ 1195.040354] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:09:31 ricardo-desktop kernel: [ 1195.040358] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:09:31 ricardo-desktop kernel: [ 1195.040380] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:09:31 ricardo-desktop kernel: [ 1195.040386] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
Feb 17 23:09:31 ricardo-desktop kernel: [ 1195.040395] end_request: I/O error, dev sdb, sector 8
Feb 17 23:09:31 ricardo-desktop kernel: [ 1195.040399] Buffer I/O error on device sdb, logical block 1
Feb 17 23:09:48 ricardo-desktop kernel: [ 1212.164910] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:09:48 ricardo-desktop kernel: [ 1212.164913] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:09:48 ricardo-desktop kernel: [ 1212.164917] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:09:48 ricardo-desktop kernel: [ 1212.164939] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:09:48 ricardo-desktop kernel: [ 1212.164945] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
Feb 17 23:09:48 ricardo-desktop kernel: [ 1212.164955] end_request: I/O error, dev sdb, sector 9
Feb 17 23:09:48 ricardo-desktop kernel: [ 1212.164959] Buffer I/O error on device sdb, logical block 1
Feb 17 23:09:49 ricardo-desktop kernel: [ 1213.666142] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:09:49 ricardo-desktop kernel: [ 1213.666145] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:09:49 ricardo-desktop kernel: [ 1213.666149] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:09:49 ricardo-desktop kernel: [ 1213.666171] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:09:49 ricardo-desktop kernel: [ 1213.666176] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 10 00 00 08 00
Feb 17 23:09:49 ricardo-desktop kernel: [ 1213.666185] end_request: I/O error, dev sdb, sector 16
Feb 17 23:09:49 ricardo-desktop kernel: [ 1213.666189] Buffer I/O error on device sdb, logical block 2
Feb 17 23:10:04 ricardo-desktop kernel: [ 1227.997549] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:10:04 ricardo-desktop kernel: [ 1227.997552] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:10:04 ricardo-desktop kernel: [ 1227.997556] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:10:04 ricardo-desktop kernel: [ 1227.997578] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:10:04 ricardo-desktop kernel: [ 1227.997584] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
Feb 17 23:10:04 ricardo-desktop kernel: [ 1227.997594] end_request: I/O error, dev sdb, sector 128
Feb 17 23:10:04 ricardo-desktop kernel: [ 1227.997598] Buffer I/O error on device sdb, logical block 16
Feb 17 23:10:05 ricardo-desktop kernel: [ 1229.510084] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:10:05 ricardo-desktop kernel: [ 1229.510087] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:10:05 ricardo-desktop kernel: [ 1229.510091] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:10:05 ricardo-desktop kernel: [ 1229.510113] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:10:05 ricardo-desktop kernel: [ 1229.510119] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 08 00 00 08 00
Feb 17 23:10:05 ricardo-desktop kernel: [ 1229.510128] end_request: I/O error, dev sdb, sector 8
Feb 17 23:10:05 ricardo-desktop kernel: [ 1229.510132] Buffer I/O error on device sdb, logical block 1
Feb 17 23:10:20 ricardo-desktop kernel: [ 1244.249607] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:10:20 ricardo-desktop kernel: [ 1244.249609] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:10:20 ricardo-desktop kernel: [ 1244.249613] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:10:20 ricardo-desktop kernel: [ 1244.249636] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:10:20 ricardo-desktop kernel: [ 1244.249642] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 10 00 00 00 08 00
Feb 17 23:10:20 ricardo-desktop kernel: [ 1244.249651] end_request: I/O error, dev sdb, sector 4096
Feb 17 23:10:20 ricardo-desktop kernel: [ 1244.249655] Buffer I/O error on device sdb, logical block 512
Feb 17 23:10:22 ricardo-desktop kernel: [ 1245.916747] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:10:22 ricardo-desktop kernel: [ 1245.916750] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:10:22 ricardo-desktop kernel: [ 1245.916753] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:10:22 ricardo-desktop kernel: [ 1245.916775] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:10:22 ricardo-desktop kernel: [ 1245.916781] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 80 00 00 08 00
Feb 17 23:10:22 ricardo-desktop kernel: [ 1245.916790] end_request: I/O error, dev sdb, sector 128
Feb 17 23:10:22 ricardo-desktop kernel: [ 1245.916794] Buffer I/O error on device sdb, logical block 16
Feb 17 23:10:31 ricardo-desktop kernel: [ 1255.533357] sd 3:0:0:0: [sdb] Unhandled sense code
Feb 17 23:10:31 ricardo-desktop kernel: [ 1255.533360] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Feb 17 23:10:31 ricardo-desktop kernel: [ 1255.533364] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Feb 17 23:10:31 ricardo-desktop kernel: [ 1255.533386] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Feb 17 23:10:31 ricardo-desktop kernel: [ 1255.533392] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 10 00 00 00 08 00
Feb 17 23:10:31 ricardo-desktop kernel: [ 1255.533401] end_request: I/O error, dev sdb, sector 4096
Feb 17 23:10:31 ricardo-desktop kernel: [ 1255.533405] Buffer I/O error on device sdb, logical block 512
```
(I'm not entirely sure if I should even be posting anything this long...)

---

### Post by matt_symes on 2011-02-20
Hi
 
Are you still using Ubuntu 9.10 Karmic Koala ?
 
Kind regards

---

### Post by ricardisimo on 2011-02-25
I don't know if you were asking me, but no. I haven't used 9.10 since 10.04 came out. I finally erased everything on sdb, thinking that - and reformatting - would help. Nope. Now I have an empty storage drive that I can't access, instead of a full storage drive that I can't access. Oh, well...

---

### Post by judearasu on 2011-09-14
I too faced the same problem, later i used the live cd and booted a ubuntu without installing.Using Gparted i found my root partition and mine was /dev/sda5.

Then , i restarted my pc and made the system to boot from hard disk.Then i enter into the grub menu.
1)**Press 'e' on your keyboard to edit the boot config**

2)**Press the down arrow key to reach the 'kernel' boot parameter**
([COLOR=red]/boot/vmlinuz-2.6.31-23-generic root=UUID=4614036b0-1c9a-4311-b452-c5c0d3762690 ro quiet splash[/COLOR])

3)**Instead of UUID=4614036b0-1c9a-4311-b452-c5c0d3762690 replace it with  /dev/sda5**

4)**Now press CTRL+X to boot the grub.**

Finally my ubuntu was rescued, starts booted from the hard disk and doesn't find the boot error later

---

### Post by PayPaul on 2011-09-18
What is fstab? How do I get this same information on the drive that you got? I do have the same issue. it does seem silly that if I was able to install Ubuntu on a partition in my main drive and then run into this grub problem with the bootloader "unable to find root drive".

---

### Post by PayPaul on 2011-09-18
> **judearasu said:**
> I too faced the same problem, later i used the live cd and booted a ubuntu without installing.Using Gparted i found my root partition and mine was /dev/sda5.

Then , i restarted my pc and made the system to boot from hard disk.Then i enter into the grub menu.
1)**Press 'e' on your keyboard to edit the boot config**

2)**Press the down arrow key to reach the 'kernel' boot parameter**
([COLOR=red]/boot/vmlinuz-2.6.31-23-generic root=UUID=4614036b0-1c9a-4311-b452-c5c0d3762690 ro quiet splash[/COLOR])

3)**Instead of UUID=4614036b0-1c9a-4311-b452-c5c0d3762690 replace it with  /dev/sda5**

4)**Now press CTRL+X to boot the grub.**

Finally my ubuntu was rescued, starts booted from the hard disk and doesn't find the boot error later

Is replacing the UUID = xxxxx... with **/dev/sda5** a universal correction? Should I use **/dev/sda5** as a term or is my path going to be different?

---

### Post by PayPaul on 2011-09-18
How did you post that scrolling log in the first place? It's quite similar to what I've been looking at with a lot of *hardware error* entries.

---

### Post by millybreak on 2011-10-20
Not sure this thread is still open?
Anyway, I have this problem, too. 
The computer ran on 8.04, no other OS, and I did a clean install of 10.04.3 from CD and got stuck.
Tried everything I could find on the subject and what was mentioned here.Nothing helped.

A lot of the solutions assume you can get into your system and use a terminal and edit things. But I can't get past the [initramfs]. Can't even type in there.

Any new ideas would be welcome, because I'm getting rather desperate!:(

Edit: Just realized there was one thing I hadn't done yet: install 32-bit version. And guess what: same error, same problem. Have to install with "nolapic'option in grub, by the way, Don't know what it means, but it gets my cd running.

---

### Post by TecTef on 2012-05-14
Hey millibreak!
   I don't know if you're still interested in an answer but **changing the set root = to '/dev/sda5' did indeed work for me**
This is what I did to get to that point:

1. Restart your computer

2. On loading you should see a menu that lets you boot from different ubuntu versions ** Tap the 'e' key **
<br>
[IMG]http://ubuntumanual.org/files/Grub.JPG[/IMG]


3. when you get to the new screen, scroll down to where it says set root=
  I bet 90% it will have something like this:
[IMG]http://www.intelligrape.com/blog/wp-content/uploads/2012/03/grub2.menu_.edit_.png[/IMG]

4. change everything within the set root=() parenthesis to /dev/sda5.
   so it looks like this:
   set root=(/dev/sda5).

5. Hit F10 (or CTRL-X) to boot.

6. Now it'll ask for your passphrase, make sure you type it correctly because if you do it wrong for a couple of times **it'll lock you out and reset the settings you have made, so you'll have to restart the computer and do it again.**

---

### Post by buaabella on 2012-06-15
changing root = to /dev/sdaX did not work for me....
So as the rootdelay...
I tried all the methods here!
In initramfs, I used ls /dev/disk and "No suck file "returned.
The sata disc seems to be ignored by the new kernel.
But I can boot the previous version successfully.
Help me.T.T

---

### Post by Crossle Song on 2013-03-14
same problem...

Linux 3.8.0-12-generic #21-Ubuntu SMP Thu Mar 7 19:08:49 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

---

