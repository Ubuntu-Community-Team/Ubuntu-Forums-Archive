---
title: "Installed Hardy Heron via Wubi and now facing minor kernel upgrade issue"
date: 2008-07-26
forum: General Help
---

### Post by hishamzz on 2008-07-26
Hey guys!

A total newbie to Ubuntu and somewhat to Linux as a whole lol. Well, the installation went fine without any glitches. The problem am facing right now is that once I select to upgrade the existing packages on the system. There is this single package namely :-

linux-image-2.6.24-19 generic

which is not being installed. It gives the following error :-

> E: /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.36_amd64.deb: unable to make backup link of `./boot/vmlinuz-2.6.24-19-generic' before installing new version

Unfortunately I am finding it a bit difficult to copy the entire list of statements which were shown whilst installation in the small terminal screen. If required please tell me so that I could atleast post a screenshot.

Any ideas on how to overcome this? Thanks!!!

Hisham

---

### Post by rats54 on 2008-07-28
Hi hishamzz,

Have you been able to resolve your problem?  I have the same problem and cannot find a resolution.  

If you stumble across an answer, please post it so I can try it.  I will do the same if I find anything.

Thanks,

---

### Post by hishamzz on 2008-07-28
Hey rats!

I have still not found a solution to my problem unfortunately. It is related to the issue specified on this page too :-

> [http://www.linuxquestions.org/questi...ubuntu-656091/](http://www.linuxquestions.org/questi...ubuntu-656091/)

Something related to the space being available on /boot bro and the only option they specify is to repartition the space which is not possible via Wubi it seems.

Zz

---

### Post by minhmeoke on 2008-07-29
Use the "df" command to find how much free space you have left. If the virtual disk is full, you may have to resize it with the lvpm utility, [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591) .

Also, what kernel are you running right now? use the "uname -a" command to find out.

---

### Post by ago on 2008-07-29
Is this an installation inside a fat32 partition?

---

### Post by markhadman on 2008-07-31
I too have this problem.

E: /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.36_i386.deb: unable to make backup link of `./boot/vmlinuz-2.6.24-19-generic' before installing new version

I'm using an 8GB wubi install on a FAT 32 partition. There is no other OS installed on this partition. WinXP and Win98 are also installed on this machine. (I'd post full partition info except there's no gparted available or any appropriate menu item - any help there appreciated)

output of df:

```

Filesystem           		1K-blocks    Used Available Use% Mounted on
/host/ubuntu/disks/root.disk	2906544    563760   2196300  21% /
varrun                  	647732        96    647636   1% /var/run
varlock                 	647732         0    647732   0% /var/lock
udev                    	647732        68    647664   1% /dev
devshm                  	647732        12    647720   1% /dev/shm
lrm                     	647732     39760    607972   7% /lib/modules/2.6.24-19-generic/volatile
/host/ubuntu/disks/usr.disk	3875344   1729412   1950620  47% /usr
gvfs-fuse-daemon       		2906544    563760   2196300  21% /home/mark/.gvfs

```

current kernel version: 2.6.24-19-generic #1 (using uname -a)




Has anybody successfully updated their kernel image with a wubi install?

---

### Post by ago on 2008-07-31
for the time being you should uncheck kernel upgrades if installed on vfat

---

### Post by markhadman on 2008-07-31
The thing that's worrying me is that I might have to reboot into Windows in order to check for sure if I'm running V-FAT. Seriously, where's the partition viewer/editor in Ubuntu-Wubi... anybody? Quickly, before I start clearing a partition for Debian!

Anyways... has this kernel update problem been noticed by anybody other than its victims? If not, where do Ubuntu bugs get reported?

---

### Post by rats54 on 2008-08-01
Hi hishamzz,

Sorry, I have been out of contact for a few days; DSL service was down. Very common problem here, especially during the rainy season.

I see we got some replies while I was away.

ago, where do I go to "... uncheck kernel upgrades ..."? Also, is this a problem that is being fixed or is this going to be a permanent temporary fix?

Thanks,
rats

---

### Post by ago on 2008-08-01
> **rats54 said:**
> 
ago, where do I go to "... uncheck kernel upgrades ..."? Also, is this a problem that is being fixed or is this going to be a permanent temporary fix?

It is an annoying issues since dpkg requires hardlinks (which are not supported by fat32) and changing a fundamental package such as dpkg in a long term release is going to be very difficult. It will certainly be fixed in 8.10. Here is an (untested) workaround though. 

1) create a /boot.win directory
2) change /etc/fstab so that /host/ubuntu/disks/boot is mounted to /boot.win
3) unmount /boot, and remount /boot.win
4) copy the files from /boot.win/* to /boot
5) after every kernel/boot upgrade repeat #4

The commands to do the above:

sudo mkdir /boot.win
sudo sed -i 's:/boot:/boot.win:' /boot/grub/menu.lst
sudo umount /boot
sudo mount /boot.win
sudo cp -a /boot.win/* /boot/

#Now try to upgrade:

sudo apt-get upgrade

#Then sync /boot with /boot.win:

sudo rsync -a /boot/* /boot.win/

---

### Post by kyawkyaw83 on 2008-08-02
> **ago said:**
> Is this an installation inside a fat32 partition?


yes.this is an installation inside a fat32 partition.how will i solve this problem?


thanks.

---

### Post by minhmeoke on 2008-08-02
Kernel upgrade with Wubi running on NTFS should be possible. On the other hand, FAT32 does not support hard-links, and has 4GB file limit size (this is the largest virtual disk that you can have), so it will break.


@kyawkyaw83: Ago's instructions should fix the problem, but be aware that it is untested. If you have any important data on the wubi install, then you should back it up first using explore2fs [http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs) .

@rats54: Disable kernel updates by opening synaptic, selecting linux-generic, then in the menu: Package > Lock Version.

@markhadman: You can list the filesystems of all partitions in the terminal with "sudo fdisk -l", or for a graphical solution, mount the partition (just click on it in the Places menu), then check System > Administration > System Monitor > File Systems.

---

### Post by rats54 on 2008-08-02
ago, thank you for the instructions.  Using Putty I cut and pasted your instructions step by step into the terminal of the affected wubi Ubuntu computer.

"Everything went fine until I rebooted the computer. At the start of the reboot I got the following error message

"File type is fat, partition type 0xb kernel /boot.win/vmlinuz-2.6.24-19-generic root=UUID=488C-DB09 loop=/ubuntu/disks/root.disks ro single

"ERROR 15: File not found

"Press any key to continue ... "

Pressing any key took me to the menu:

"Ubuntu 8.04.1 kernel 2.6.24-19 generic
"Ubuntu 8.04.1 kernel 2.6.24-19 generic (recovery mode)
"Ubuntu 8.04.1 memtest86+
"Other operating systems:
"Microsoft Windows XP Home Edition"

Selecting either of the Ubuntu choices took me back to the Error Message.  In other words I could not boot into Ubuntu.

I restored the drive/partition image I made before following your instructions and Ubuntu boot as always.

For me the Untested Work Around did not work.

Thanks.

---

### Post by ago on 2008-08-02
> **rats54 said:**
> 

"File type is fat, partition type 0xb kernel /boot.win/vmlinuz-2.6.24-19-generic root=UUID=488C-DB09 loop=/ubuntu/disks/root.disks ro single



menu.lst should look like this:

root ()/ubuntu/disks
kernel /boot/vmlinuz...

hence replace /boot.win with /boot in menu.lst

---

### Post by rats54 on 2008-08-03
Thanks ago,

But I have already wasted enough time on this and I have restored from the partition image and everything else is working, so I will just wait until 8.10 is released.

This is just one more example, in a long list of examples, of why Linux of any flavor will never be a challenge to Windows or Apple.

Thanks again,

rats

---

### Post by baldydlab on 2008-08-11
Hi rats54

> **rats54 said:**
> 
But I have already wasted enough time on this and I have restored from the partition image and everything else is working, so I will just wait until 8.10 is released.

I have tested ago's workaround on a FAT32 Partition of an old 98SE Box. It worked like a charm. Kernel Update took me no longer than 2-3 minutes. 

> **rats54 said:**
> This is just one more example, in a long list of examples, of why Linux of any flavor will never be a challenge to Windows or Apple.

It's not really a Linux problem but acutally a partition type issue, which you would not have encountered if you had installed (K)ubuntu on a dedicated Ext2/3 Partition.

Kind regards
baldydlab

---

### Post by spike.robinson on 2008-08-12
> **ago said:**
>  Here is an (untested) workaround though. 
...
2) change **/etc/fstab** so that /host/ubuntu/disks/boot is mounted to /boot.win
...
The commands to do the above:
...
sudo sed -i 's:/boot:/boot.win:' **/boot/grub/menu.lst**


Sorry, but I'm not clear if we should be modifying /etc/fstab, or /boot/grub/menu.lst?  That might be where rats54 went astray. Could you please clarify?

Thanks!

(PS Also isn't the sed command going to replace **both** instances of the string '/boot' with '/boot.win' - not intended?)

---

### Post by rats54 on 2008-08-25
I have found a work around solution for this problem that is quick and easy to apply and best of all IT WORKS!  I found it at [http://fosswire.com/2008/08/20/exclude-packages-from-being-installed-and-upgraded-in-debianubuntu/]("http://fosswire.com/2008/08/20/exclude-packages-from-being-installed-and-upgraded-in-debianubuntu/").

It simply requires installing wajig.  This is a Deb app and can be downloaded and installed by either

[INDENT][/INDENT]sudo apt-get install wajig

or by using Synaptic.

After wajig is installed open a terminal and type:

[INDENT][/INDENT]sudo wajig hold linux-image-2.6.24-19-generic

The linux image will be put on hold and will not update or attempt to update.  It does not require any other action on your part and Update Manager will get and install all other available update without a problem.

When you are ready to remove the hold on the linux-image just open a terminal and type:

[INDENT][/INDENT]sudo wajig unhold linux-image-2.6.24-19-generic

I hope this helps.

---

