---
title: "Grub won't install on software raid setup"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by JohnFante on 2009-10-30
I have a Gigabyte x58 ud4p mobotherboard with two sata disks connected to the intel controller in a software raid 0 setup.

With 9.04 I used the alternate install iso that supports software raid. With 9.10 I did the same (installed on a DVD since I was out of CD's) and everything whent fine with a fresh install until the installer tryes to install grub.

It searches for another OS (I have Windows 7 installed in a dualboot also) but stops the installation of grub half way through with no errors.

The same happens when I try to install Grub manually.

Looks like som kind of grub 2 related problem. Since I afterhand installed 9.04 fine and therefrom upgraded to 9.10.

Any suggestions on how to fix it? Maby I should remove grub from the MBR before I install 9.10?

Thank you in advance.

---

### Post by ScottBatchelor on 2009-10-30
I have the same problem with a Dell 435MT with 2xSata configured as software raid 0.
Any help to get over this problem without having to reinstall 9.04 and then update to 9.10 would be much appreciated. Thanks.

---

### Post by Jezza0 on 2009-10-30
I'm having the same issue -- very annoying!  I'm sure it's possible to install GRUB from the liveCD, but I can't figure it.  fdisk -l does not list my RAID partitions, but they are visible to the installer.  Very confusing! :(

---

### Post by bamboomy on 2009-10-30
I have even a worse problem,

I installed 7, then 9.10 with raid1 (alternative cd) ,ubuntu isn't even installed on the raid so I don't see the problem there but now my setup doesn't want to boot anymore _at all_ !!!

I tried to install 9.04, (you know, to upgrade like you guys) but it doesn't boot either.

I tried to manually install grub...
```

sudo grub
root (hd0,0)
setup (hd0)
quit

```

didn't work, although grub didn't seem to complain...

```

grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.

```

didn't work either...

```

fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2027666a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1228     9858048   82  Linux swap / Solaris
/dev/sda2            1228        6412    41641984   83  Linux
/dev/sda3            6412       19458   104787968    7  HPFS/NTFS

```

anyone any idea what can be wrong?

S.

---

### Post by robrob22 on 2009-10-31
Confirmed on Nvidia mobo with sata soft raid (alternative install 9.10).
Grub2 fails to write to mbr when doing a manual install.

Installs fine on 9.10 i386 desktop without windows 7 partition.

Hope someone can post a fix.....

Rob

---

### Post by JohnFante on 2009-10-31
Well apparently the solution is simple.

With 9.10 the normal install iso supports raid out of the box.

I was intending to use the normal iso to install from a USB using this guide ([https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)) to install grub. I have used the guide before to install 9.04.

But it turns out that dmraid is allready running with the live iso. So the installer see the raid partitions etc. fine without any terminal work.

The only - minor - issue I had was that the partitions were show two times. First like normal on top and then below with a px (x beeing the partition number) at the end. And the p boot partition are also show in the grub menu under other OS but they can easily be erased.

Everything else is fine. :-) at least in my setup.

Hopes this helps.

---

### Post by Lucky. on 2009-10-31
Yep, you got it!  I was just coming here to post this:

[Ubuntu 9.10 (Karmic) Install / Boot Issues - SATA RAID](http://www.ericforyan.com/index.php?node=21)

> When I moved to Ubuntu, it wouldn't work with my fake-RAID. In order to solve installation issues on Intrepid and Jaunty, I went back to my BIOS and changed the SATA settings to "IDE" mode. Ubuntu was then able to use my two hard drives individually (or put together a software RAID).

.....


Flash-forward to Karmic Koala, and it recognized my fake-RAID just fine. It even installed on my RAID 0 without a hitch until I rebooted. I could never boot the system entirely (Got a white logo, pressed enter and was stuck at the "initramfs" prompt). 

.....

In the end, it was the simplest of things...I still had my SATA running in "IDE" mode in my BIOS. I flipped that back to "RAID", and installed again with the LiveCD. Koala saw my RAID once more, installed, and this time booted just fine. 



---

### Post by robrob22 on 2009-10-31
Found the answer why ubuntu failes to install at the grub part.
Ubunti 9.10 live cd does no come with the dmraid package.
The 9.10 installer try s to download dmraid or grub, but if you are off-line your out of luck.

At leat Im at this point.....

After reboot grub can not find /dev/mapper/nvidia.


But at least now we know why grub fails to install....

More info
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/436340](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/436340)


Rob

---

### Post by Jezza0 on 2009-11-02
:( This still does not work for me.  My BIOS settings for my fakeraid 0 are set correctly to RAID.  I've tried alt. and regular CD.  The regular CD appears to work, but on reset I still just get Windows.

I have two identical 500Gb drives in RAID0, partitioned with one 800Gb main partition (currently with fresh win7) and the rest will have Kubuntu, one day.  I can only use the liveCD manual partitioner; the installer crashes if I try to select the 2nd partition.  Again, after that all appears well, until reboot and nothing works.

This makes me very sad. :(

---

### Post by robrob22 on 2009-11-02
**UPDATE.....**


Took me all weekend to solve this but, this is how to fix
install problems on nvidia raids with Desk top and Alternative installs.

**The issues.....**

1. On 9.10 Grub is not on the LIVE CD or the Alertnative  
   CD.

2. You will have to chroot to your installed partition
   and install dmraid and grub if not installed.

3. I have found that making the first partition on your
   nvidia_something a 200 mb /boot for linux makes your life simpler.

**The solution....**
   
Here are the steps to install the Alternative 9.10 CD with
a FULL disk encryption.

1. Make the first partition on your nvidia raid a 
   200 mb /boot partition. Remember to choose to format.

2. Create a 2nd partition that is logical. Mine was a 
   logical 300 Gig logical partition.

3. Install a full disk encryption as usual to your large
   partition. Install will finish but will fail to install
   grub and give you a message. Choose the cuntinue 
   without GRUB option.

4. Reboot to the LIVE ubuntu 9.10 CD.

5. Open teminal and decypt the partion where / is.

6. Mount decrypted partion to /mnt and mount your /boot
   partition to /mnt/boot. You will also need to mount 
   --bind /dev and /proc.

7. Chroot to /mnt as usual.

8. You will find that dmraid, LVM2 and decryption debs 
   should all be set-up. The only thing missing is 
   GRUB.

9. So install GRUB with apt-get install grub.

10. Cp all of /usr/lib/grub/i386-pc/* to /boot/grub

11. Type in terminal "grub-setup". You should see grub 
    writing to /boot/grub.

12. ls /dev/mapper/ and write down the base name for your
    nvidia raid, mine was nvidia_bdbahici

13. In the terminal type "grub". Then type this in
    device (hd0) /dev/mapper/nvidia_bdbahici
    root (hd0,0)
    setup (hd0)

14. You should see grub writing to /boot and writing to
    the mbr.

15. Reboot and you should see Ubuntu asking for the 
    password to decrypt your hard drive.

---

### Post by realzippy on 2009-11-02
> **Jezza0 said:**
> :( This still does not work for me.  My BIOS settings for my fakeraid 0 are set correctly to RAID.  I've tried alt. and regular CD.  The regular CD appears to work, but on reset I still just get Windows.

I have two identical 500Gb drives in RAID0, partitioned with one 800Gb main partition (currently with fresh win7) and the rest will have Kubuntu, one day.  I can only use the liveCD manual partitioner; the installer crashes if I try to select the 2nd partition.  Again, after that all appears well, until reboot and nothing works.

This makes me very sad. :(

For softwareraid you have to **disable** your bios's raid options...set it off.

---

### Post by Jezza0 on 2009-11-03
> **realzippy said:**
> For softwareraid you have to **disable** your bios's raid options...set it off.

This isn't correct for my abit ip35 pro.  The hdd controller has to be set to sata mode, else the system is unbootable.

---

### Post by realzippy on 2009-11-04
> **Jezza0 said:**
> This isn't correct for my abit ip35 pro.  The hdd controller has to be set to sata mode, else the system is unbootable.

Yep.of course to sata.But not to raid.

---

### Post by Jezza0 on 2009-11-05
> **realzippy said:**
> Yep.of course to sata.But not to raid.

oops, not doing very well here!  My HDD controller has 3 options: IDE, AHCI, and RAID.  As I have set up my disks in a RAID0 system, any option other than RAID gives me an unbootable system.

I'm rather confused why one would specifically not select RAID on a specific RAID set-up.  What does this option do, if not facilitate RAID?

Cheers for the help guys.  One day I'll have Kubuntu 9.10 working!

---

### Post by wkulecz on 2009-11-05
> I'm rather confused why one would specifically not select RAID on a specific RAID set-up. What does this option do, if not facilitate RAID?

Like about everything in Linux there is more than one incompatable way to do things.  

The BIOS raid is so-called "fake raid" which is required to share the RAID array with windows.  The other way is software raid but only works with Linux, although its far more versatile and can be used with LVM as well.

Useful explainations, although geared to 9.04:

fakeraid (dmraid):
[http://ubuntuforums.org/showthread.php?t=721825](http://ubuntuforums.org/showthread.php?t=721825)

software raid (mdadm):
[http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)

I'm using software raid (/dev/md0) on my 6.06 server, but have come to the conclusion overall its more trouble than its worth for me.  Less hassle to use the extra drive as on on-line daily back up with rsync.

--wally.

---

### Post by realzippy on 2009-11-05
To make it clear:

To set up a softwareraid in ubuntu,you have to make the same (bios) setup
as you would when setting up a normal ubuntu installation.
Only difference is to plug 2 harddiscs instead of one...
and your abit has 6 sata channels,free choice!

---

### Post by Jezza0 on 2009-11-06
OK cheers for that, I think I understand now.  According to: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto), Ubuntu does not support fakeraid, so I guess I'm out of luck.

Thanks all.  Guess I'll try again in April.

---

### Post by realzippy on 2009-11-06
there is no need for fakeraid.Or do you want windows fakeraid on the same
harddiscs?
Linux softwareraid works fine (at last for me).Have 2 machines in raid0 setup,one of it running nearly 2 years,no problems.Only really fast...

---

### Post by Jezza0 on 2009-11-07
> **realzippy said:**
> there is no need for fakeraid.Or do you want windows fakeraid on the same
harddiscs?
Linux softwareraid works fine (at last for me).Have 2 machines in raid0 setup,one of it running nearly 2 years,no problems.Only really fast...

Yes that's right - I'm also using a Win7 install.

---

### Post by klonos on 2009-11-10
> **robrob22 said:**
> **UPDATE.....**


Took me all weekend to solve this but, this is how to fix
install problems on nvidia raids with Desk top and Alternative installs.

**The issues.....**

1. On 9.10 Grub is not on the LIVE CD or the Alertnative  
   CD.

2. You will have to chroot to your installed partition
   and install dmraid and grub if not installed.

3. I have found that making the first partition on your
   nvidia_something a 200 mb /boot for linux makes your life simpler.

**The solution....**
   
Here are the steps to install the Alternative 9.10 CD with
a FULL disk encryption.

1. Make the first partition on your nvidia raid a 
   200 mb /boot partition. Remember to choose to format.

2. Create a 2nd partition that is logical. Mine was a 
   logical 300 Gig logical partition.

3. Install a full disk encryption as usual to your large
   partition. Install will finish but will fail to install
   grub and give you a message. Choose the cuntinue 
   without GRUB option.

4. Reboot to the LIVE ubuntu 9.10 CD.

5. Open teminal and decypt the partion where / is.

6. Mount decrypted partion to /mnt and mount your /boot
   partition to /mnt/boot. You will also need to mount 
   --bind /dev and /proc.

7. Chroot to /mnt as usual.

8. You will find that dmraid, LVM2 and decryption debs 
   should all be set-up. The only thing missing is 
   GRUB.

9. So install GRUB with apt-get install grub.

10. Cp all of /usr/lib/grub/i386-pc/* to /boot/grub

11. Type in terminal "grub-setup". You should see grub 
    writing to /boot/grub.

12. ls /dev/mapper/ and write down the base name for your
    nvidia raid, mine was nvidia_bdbahici

13. In the terminal type "grub". Then type this in
    device (hd0) /dev/mapper/nvidia_bdbahici
    root (hd0,0)
    setup (hd0)

14. You should see grub writing to /boot and writing to
    the mbr.

15. Reboot and you should see Ubuntu asking for the 
    password to decrypt your hard drive.

I'm almost there... at least I got to the point where during boot instead of a blinking cursor, I get a grub> prompt. Let me say at this point that I do not use an encrypted partition like you, but I believe this has nothing to do with it.

Here's what I did as per your suggested steps above robrob22:

@ step 6:
```
ubuntu@ubuntu:~$ sudo mount /dev/mapper/isw_ddjceefghj_500G_RAID1a6 /mnt
ubuntu@ubuntu:~$ sudo mount /dev/mapper/isw_ddjceefghj_500G_RAID1a1 /mnt/boot
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
```

I got no errors in any of the above commands.

@ step 7:
```
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/#
```

This went fine as well, since I got the 'root@ubuntu:/'

@ step 8 I am not sure how to actually check what you say, but I take it is ok.

@ step 9:
```
root@ubuntu:/# apt-get install grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
grub is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

This was because it was the second time I was trying your method and I got grub installed ok during the first one.

@ step 10:
```
root@ubuntu:/# sudo cp /usr/lib/grub/**x86_64-pc**/* /boot/grub
**sudo: unable to resolve host ubuntu**
root@ubuntu:/# ls /boot/grub
e2fs_stage1_5  jfs_stage1_5    reiserfs_stage1_5  stage2	   xfs_stage1_5
fat_stage1_5   minix_stage1_5  stage1		  stage2_eltorito

```

I guess it is ok, since I was getting this 'unable to resolve host ubuntu' error each time, but files seem to be copied just fine. The only thing here is that I use a x64 version of Ubuntu, thus the 'x86_64-pc' instead of the 'i386-pc' in the path of the cp command. Anything I should check at this point?

@ step 11:
```
root@ubuntu:/# grub-setup
The program 'grub-setup' is currently not installed.  You can install it by typing:
apt-get install grub-pc
grub-setup: command not found
root@ubuntu:/# sudo grub-setup
sudo: unable to resolve host ubuntu
sudo: grub-setup: command not found
```

So I did:
```
root@ubuntu:/# sudo apt-get install grub-pc
sudo: unable to resolve host ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  desktop-base
[B]The following packages will be REMOVED:
  grub
The following NEW packages will be installed:
  grub-pc[/B]
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B/445kB of archives.
After this operation, 188kB disk space will be freed.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Can not write log, openpty() failed (/dev/pts not mounted?)
(Reading database ... 116404 files and directories currently installed.)
Removing grub ...
Processing triggers for man-db ...
**Can not write log, openpty() failed (/dev/pts not mounted?)**
Selecting previously deselected package grub-pc.
(Reading database ... 116358 files and directories currently installed.)
Unpacking grub-pc (from .../grub-pc_1.97~beta4-1ubuntu4_amd64.deb) ...
Processing triggers for man-db ...
**Can not write log, openpty() failed (/dev/pts not mounted?)**
Setting up grub-pc (1.97~beta4-1ubuntu4) ...
```

I guess this installed grub1 and removed grub2. Am I right or is it the opposite?

Also, the 'Can not write log, openpty() failed (/dev/pts not mounted?)' messages I think are safe to ignore, since the only thing happened is procedure not being able to log its progress. Or should I worry about those errors as well?

Anyways, I went on with step 11:
```
root@ubuntu:/# sudo grub-setup
sudo: unable to resolve host ubuntu
No device is specified.
Try ``grub-setup --help'' for more information.
```

At this point I got a bit confused, but I went on with step 12 anyways:
```
root@ubuntu:/# sudo ls /dev/mapper
sudo: **unable to resolve host ubuntu**
control			     isw_ddjceefghj_500G_RAID1a5
**isw_ddjceefghj_500G_RAID1a**   isw_ddjceefghj_500G_RAID1a6
isw_ddjceefghj_500G_RAID1a1
```

I know the 'sudo' is not necessary in the list command, but I wanted to show you that commands go through despite the 'unable to resolve host ubuntu' error. As you can see, my RAID isn't nvidia, but an intel one and its name is 'isw_ddjceefghj_500G_RAID1a'.

On to steps 13 and 14:
```
root@ubuntu:/# sudo grub
sudo: unable to resolve host ubuntu
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> device (hd0) /dev/mapper/isw_ddjceefghj_500G_RAID1a
device (hd0) /dev/mapper/isw_ddjceefghj_500G_RAID1a
grub> root (hd0,0)
root (hd0,0)
grub> setup (hd0)
setup (hd0)
[B] Checking if "/boot/grub/stage1" exists... [COLOR="Red"]no[/COLOR]
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes[/B]
 Running "embed /grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
**succeeded**
 Running "install /grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/grub/stage2 /grub/menu.lst"... **succeeded**
Done.
grub> quit
quit
```

What happens here?
Thing seems to be going semi-right. I get this error saying stage1 doesn't exist. Is it safe to ignore? I guess not, but how can I troubleshoot it?

Also it looks for stage1 in /boot/grub/, but other stages are under /grub/. Is this ok?

@ step 15 I shouldn't be getting the prompt for decryption, since I haven't enabled encryption in my partition, but I should be booting to ubuntu and getting the login screen. Instead I get a grub prompt:
```
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub>
```

Any thoughts? Something I am missing or doing wrong?

Thank you in advance people and sorry for this really long post, but it was necessary.

---

### Post by arkhala on 2009-11-11
To address the original topic:

If you are trying to install w/ **software** RAID and GRUB is giving you problems not wanting to install, choose "Continue without installing GRUB" - let the install finish, then when it's done, select "Go Back" instead of "Continue & Reboot." Then select to install GRUB again.... this worked for me. (though now I have [this]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/396564/") bug - seems mostly harmless, though, as everything else boots up fine)

---

### Post by ed-koala on 2009-11-11
These posts are very informative, but I don't quite understand how to do what is suggested.  Robrob22's solution assumes you know what chroot normally means, etc. I could use his solution broken down into a more friendly version for those who don't automatically know what all the commands are/do.  Steps 5-7 and 10 need specific commands listed, near as I can tell.

---

### Post by parlaan on 2009-11-12
What I find Most Odd, is the only way I could get my system to work, was to turn ON "Fakeraid" in my Bios.

Something isn't right, but I don't know what it is.

---

### Post by dargaardms on 2009-11-25
From what I have read here I think I'm on the right track but still no luck.  I'm trying to dual boot with Win XP on a fakeraid.  I noted this on the fakeraid howto

Ubiquity will fail when installing grub, and will not automatically add dmraid to the new installation. this need to be done manually. (the Installation guide for 8.10 and 9.04 contain the step required to manually install these items.

Sounds like a good place to start but I can't find anything in the installation guide about manually installing grub or dmraid,  could someone link me to the correct point in the guide.

---

### Post by dargaardms on 2009-11-26
I have figured out the fakeraid setup and thought it would be best if I shared.

I used the alt install when grub failed I continued with out boot loader
after installation completed I booted the LiveCd.

First get the device name use "ls /dev/mapper" 

then mount your root partition to /mnt
for me this was "mount /dev/mapper/nvidia_ecbcefgf5 /mnt"
if you need to mount your boot partition to /mnt/boot
next mount bind proc and dev "mount --bind /proc /mnt/proc"
now chroot to /mnt

now the fun begins, first apt-get install grub
now cp /usr/lib/grub/**x86_64-pc**/* /boot/grub
type "grub"
you want to enter the following making changes to fit your system

device (hd0) /dev/mapper/nvidia_ecbcefgf
    root (hd0,4)
    setup (hd0)

this should write changes to your disk, note the hd0,4 this is the number of your root partition grub starts at 0 to if your root part is 5 put 4 here. quit this then run update-grub this will create a menu.lst file

edit the menu file to point to the correct partitions  the device should be correct you should only have to change the partitions from hd0,0 to hd0,4  then add the chain loader for windows as usual and save and reboot, it worked for me.

Note I typed this up from memory I don't think I forgot anything but I may have give it a try.

---

### Post by dakiluxa on 2009-11-27
guys... much easier. 

1) Blindly install grub-pc
2) On the grub start screen choose the first kernel and press "e" to edit.
3) Delete the entire line which starts with "search"
4) Boot (ctrl + x)

ALSO:

disable uuid from /etc/default/grub
remove the search uuid line from grub.cfg and other files at /etc/grub.d/
run update-grub (i think)

that should solve everything

---

### Post by AlexanderDGreat on 2009-12-29
@robrob22 - seems like a lot of work and complication for a NEWBIE like me, can I just install Karmic while I'm connected to the Internet so it downloads the dmraid drivers? Or do I really need to follow the steps you mentioned? The reason I'm asking is because I don't have enough time as vacation is soon over, if something fails. Thanks.

I'm using an Adaptec 29320A Ultra320 SCSI Hardware adapter with 2 Seagate Cheetas 37gb each Raid1 setup. Grub won't install on Karmic alternate cd!

PS Pls. help!

---

### Post by gilson585 on 2010-01-23
[http://ubuntuforums.org/showthread.php?t=1360445](http://ubuntuforums.org/showthread.php?t=1360445) fakeraid how-to for 9.10 karmic very similar to robrob22

---

