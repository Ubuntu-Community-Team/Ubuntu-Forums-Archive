---
title: "Trouble installing Ubuntu 9.04 on RAID 5"
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by DSL5 on 2009-07-14
Ok, so this issue had been bothering me for the last four days, and I can't find any solutions ANYWHERE!!!! I figured that this is the temple of Ubuntu knowledge, so I should start a thread here.

I recently built a Desktop PC and installed Windows 7 RC Build 7100 64bit on it. I want to dual boot this with Ubuntu 9.04 64bit.

After booting from the live CD, I noticed that Ubuntu did not recognize my three 640GB HDDs as the RAID 5 I had set up (and on which Win7 was installed). A quick look to the internet found me this article: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Relieved to find an easy guide, I followed the steps listed, but I ran into a problem at step I.ii

See, when I try to have grub find /boot/grub/stage1, it give me an error saying that the file was not found! Three days and several re-installs and internet searches later, I still can't install grub. I am positive that I am following all the instructions exactly.

My HDD is set up as such:

1. A 100MB NTFS system recovery volume (installed by Win7)
2. A 1.11TB NTFS partition that contains Windows 7
3. A 56GB Extended Partition
-------4. A 50GB ext4 partition within the extended for installing Ubuntu
-------5. A 6GB linux-swap partition within the extended for swap

Does anybody know what I might be doing wrong / how to successfully install grub on RAID 5??

---

### Post by Wratholix on 2009-07-19
im on the same boat, i will throw another attempt at this as from previous experience the  bios raid (for windows) + linux fakeraid does not mix. its just one of those things :S

ive got pretty much the same setup as you, raid 5 with WD640's :P

Ill be in touch

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
Was updated recently and will be my guide .. 


-------------
then again, why would you want to save that beta Win7 anyway, it runs well but you know you'll reinstall it soon

---

### Post by Wratholix on 2009-07-19
my raid5 setup,

```

sudo fdisk -l /dev/mapper/isw_djhjhcefcb_System

Disk /dev/mapper/isw_djhjhcefcb_System: 193.2 GB, 193273790464 bytes
255 heads, 63 sectors/track, 23497 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbe5fd94f

                            Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_djhjhcefcb_System1               1       12024    96581632    7  HPFS/NTFS
/dev/mapper/isw_djhjhcefcb_System2           12025       12039      120487+  83  Linux
/dev/mapper/isw_djhjhcefcb_System3           12040       23497    92036385    5  Extended
/dev/mapper/isw_djhjhcefcb_System5           12040       13040     8040501   82  Linux swap / Solaris
/dev/mapper/isw_djhjhcefcb_System6           13041       23497    83995821   83  Linux

```ok followed the guide, worked fine so far.. i'm going to do my first reboot now after finishing the grub installation.

i have a seperate boot partition so i mounted that before going into chroot
```

/dev/mapper/isw_djhjhcefcb_System6 on /target type ext4 (rw)
/dev on /target/dev type none (rw,bind)
proc on /target/proc type proc (rw)
sys on /target/sys type sysfs (rw)
/dev/mapper/isw_djhjhcefcb_System2 on /target/boot type ext4 (rw)

```then did run into a problem where the "find /boot/grub/stage1" didnt want to work.
```

grub> device (hd0) /dev/mapper/isw_djhjhcefcb_System
device (hd0) /dev/mapper/isw_djhjhcefcb_System
grub> find /boot/grub/stage1 
find /boot/grub/stage1 

Error 15: File not found

```i quitted grub, ran bash

ok back into grub, follow instructions and it worked.. (not sure why but incase you get the same)

```

root@ubuntu:/# grub --no-curses

grub> device (hd0) /dev/mapper/isw_djhjhcefcb_System
device (hd0) /dev/mapper/isw_djhjhcefcb_System
grub> find /grub/stage1
find /grub/stage1
 (hd0,1)
grub> root (hd0,1)
root (hd0,1)
grub> setup (hd0)  
setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /grub/stage1 (hd0) (hd0)1+17 p (hd0,1)/grub/stage2 /grub/menu.lst"... succeeded
Done.
grub> quit
quit

root@ubuntu:/# update-grub 
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... Generating /boot/grub/default file and setting the default boot entry to 0
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
Found kernel: /memtest86+.bin
Found kernel: /vmlinuz-2.6.28-11-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

```edit the menu
```

root@ubuntu:/# vi /boot/grub/menu.lst 

(pasting the changes i made)
timeout        5
...

# groot=(hd0,1)
...

title        Ubuntu 9.04, 2.6.28-11-generic
root        (hd0,1)

title        Windows
rootnoverify    (hd0,0)   # use the correct partition for Windows, of course
makeactive
chainloader +1

title        Ubuntu 9.04, 2.6.28-11-generic (recovery)
root        (hd0,1)

title        Ubuntu 9.04, memtest86+
root        (hd0,1)

```then continue the instructions
```

root@ubuntu:/# update-grub 
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.28-11-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done


root@ubuntu:/# echo dm-raid4-5 >> /etc/initramfs-tools/modules

root@ubuntu:/# update-initramfs -u
update-initramfs: Generating /boot/initrd.img-2.6.28-11-generic


root@ubuntu:/# vi /etc/modules
root@ubuntu:/# cat /etc/modules 
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
dm-raid4-5

```


OK im going for the reboot :P

---

### Post by Wratholix on 2009-07-19
disco!

both vista-x64 & Ubuntu 9.04 x64 boot perfectly :)

thx for the hard work on making this possible, i've been waiting for this for a long time!
i previously thought mdadm was ahead of mdraid but this kind intel fakeraid seems only possible using mdraid. 

btw i did make a backup of my 'System' raid5 volume before attempting this procedure.

Ubuntu is lekka ek se!

```

Linux dish-desktop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux

/proc/cpuinfo
model name    : Intel(R) Core(TM)2 Quad  CPU   Q9300  @ 2.50GHz

dmraid -s -s isw_djhjhcefcb_System
*** Group superset isw_djhjhcefcb
--> Active Subset
name   : isw_djhjhcefcb_System
size   : 377487872
stride : 128
type   : raid5_la
status : ok
subsets: 0
devs   : 3
spares : 0

```Now off to installing drivers etc.. more fun :)   hope this post has shed some light for some users. I used the regular cd installation (first boot the live cd)

---

### Post by DSL5 on 2009-07-19
I'm sorry, but I don't quite understand what you did that got it to work. Would you mind going through, step by step, what you did?

---

### Post by Wratholix on 2009-07-20
> **DSL5 said:**
> I'm sorry, but I don't quite understand what you did that got it to work. Would you mind going through, step by step, what you did?

My hdd setup is as follows
On my Intel (bios) config i have a raid5 Volume called "System" (200Gig) having 4 partitions.

1 - (primary) Vista64    (90Gig)
2 - (primary) Linux Boot (150mb)
3 - extended
5 - (logical) Linux Swap (8Gig)
6 - (logical) Linux ext4 (84Gig)



how clued up are you on Linux buddy? what can i explain further for you?


Easiest is to boot the live ubuntu installation and start at:
open browser [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
its easy to find, just google FakeRaid

Scroll down to the "Ubuntu 9.04 (Jaunty Jackalope)" installation

Open terminal (Applications -> Terminal)
Open text editor

copy & paste one by one:
```

sudo modprobe dm-raid4-5
sudo apt-get install -y dmraid
sudo dmraid -ay
ls -l /dev/mapper/

```copy the output from ls -l /dev/mapper into your text editor for later

yours will look something like:
> 
brw-rw---- 1 root disk 252,  2 2009-07-21 08:49 [COLOR=Blue]isw_djhjhcefcb_Name[/COLOR]
brw-rw---- 1 root disk 252,  3 2009-07-21 00:49 isw_djhjhcefcb_Name1
brw-rw---- 1 root disk 252,  4 2009-07-21 08:49 isw_djhjhcefcb_Name2
brw-rw---- 1 root disk 252,  5 2009-07-21 00:49[COLOR=Red] isw_djhjhcefcb_Name4[/COLOR]
brw-rw---- 1 root disk 252,  5 2009-07-21 00:49 [COLOR=Magenta]isw_djhjhcefcb_Name5[/COLOR]
**note**: the blue/red/pink will be different on your system and are just examples in this post.. 

```

sudo cfdisk /dev/mapper[COLOR=Blue]/isw_djhjhcefcb_Name[/COLOR]

```You'll see isw_djhjhcefcb_Name1 is marked with "boot"
using the arrow keys, select it and choose the "boot" option and the "boot" text should be gone now, continue to move down to [COLOR=Red]isw_djhjhcefcb_Name4[/COLOR] and choose the "boot" option again and it should show here now.

**Select write and then quit**


Now launch the "Install" on the desktop
choose 'manual" for the partition configuration make
> /dev/mapper[COLOR=Red]/isw_djhjhcefcb_Name4[/COLOR]   your   "/"  mountpoint
/dev/mappe[COLOR=Magenta]r/[/COLOR][COLOR=Magenta]isw_djhjhcefcb_Name5[/COLOR]   your   "swap"
On the last step before installing, click the Advanced options and uncheck the install boot loader option (grub).

now continue the installation as usual and wait for it to finish and ask if you want to reboot. 
Choose to continue **without** reboot.

Go to your terminal again, step by step

```

sudo mount /dev/mapper/[COLOR=Red]isw_djhjhcefcb_Name4[/COLOR] /target/sudo mount --bind /dev /target/dev/ 
sudo mount -t proc proc /target/proc/ 
sudo mount -t sysfs sys /target/sys/ 
sudo cp /etc/resolv.conf /target/etc/resolv.conf  
sudo chroot /target/ 
apt-get update  
apt-get install -y dmraid 
apt-get install -y grub 
mkdir /boot/grub 
cp /usr/lib/grub/x86_64-pc/* /boot/grub/ 

```now to configure your boot, get inside "grub>"
```

grub --no-curses
device (hd0) /dev/mapper/[COLOR=Blue]isw_djhjhcefcb_Name[/COLOR] 
find /boot/grub/stage1 

```
I got an error 15 here because im using a seperate boot partition, the find command changes to "[COLOR=Teal]find /grub/stage1[/COLOR]"


if all goes well, it will show something like:   [COLOR=DarkOrchid]hd(0,3)[/COLOR]
again this will vary but i think it should show this for you.

continue in "grub>" and do as follows
```

root [COLOR=DarkOrchid]hd(0,3)[/COLOR] 
setup (hd0)
quit
update-grub

```say **Y**es to creating a menu.lst 

```

nano /boot/grub/menu.lst

```scroll down to "**timeout**"
- change value to **5**

scroll down to "**groot**"   (dont remove the # infront of the line)
- change value to [B][COLOR=DarkOrchid](hd0,3)
[/COLOR][/B][COLOR=Black]
scroll down to
> 
title        Ubuntu 9.04, kernel 2.6.28-11-generic
root        (hd0,1)
kernel        /vmlinuz-2.6.28-11-generic root=/dev/mapper/[COLOR=Red]isw_djhjhcefcb_Name4[/COLOR] ro quiet splash
initrd        /initrd.img-2.6.28-11-generic[/COLOR][COLOR=Black]

[/COLOR]this is the boot menu and has 3 options by default,  the priority is top to bottom so if you want windows to boot by default paste the below above it, else put it below the first option.

> 
title                 Windows7
rootnoverify (hd0,0)
makeactive
chainloader +1
now save & exit nano

```

echo dm-raid4-5 >> /etc/initramfs-tools/modules
update-initramfs -u
echo dm-raid4-5 >> /etc/modules

```now if everything went well, you are ok now and you can close everything and reboot


i probably wrote too much but i hope its useful to anyone with the same issues..
 if not explain clearly where you are stuck..
good luck with your install :P

---

### Post by DSL5 on 2009-07-20
> **Wratholix said:**
> (if you get an error code 15 not found here, type "quit" and then "bash"  and do the grub config again

That's what I didn't get, but I understand now.

Also, is having a separate boot partition necessary? I would prefer to have the /boot within my ext4 ubuntu partition if possible.

---

### Post by Wratholix on 2009-07-20
> **DSL5 said:**
> That's what I didn't get, but I understand now.

Also, is having a separate boot partition necessary? I would prefer to have the /boot within my ext4 ubuntu partition if possible.


its not necessary, but it must be a primary partition, not in the extended as a logical partition.. hence i made a 150mb boot partition in front of my extended partition.

if you repartition then you'll probably need to reboot before continuing the installation..

please, post some info so we can see what you got

---

### Post by DSL5 on 2009-07-20
I will try again when I get home and post how it goes.

---

### Post by DSL5 on 2009-07-20
eh.....still didn't work

I tried typing quit then bash like you suggested, but I still get the "Error 15: File not found" error when I try find /boot/grub/stage1

This is my ls -l /dev/mapper output:

```

crw-rw---- 1 root root  10, 61 2009-07-20 20:53 control
brw-rw---- 1 root disk 252,  0 2009-07-21 00:55 isw_ccajfhgiae_Volume0
brw-rw---- 1 root disk 252,  1 2009-07-21 00:55 isw_ccajfhgiae_Volume01
brw-rw---- 1 root disk 252,  2 2009-07-21 00:55 isw_ccajfhgiae_Volume02
brw-rw---- 1 root disk 252,  3 2009-07-21 00:55 isw_ccajfhgiae_Volume03
brw-rw---- 1 root disk 252,  4 2009-07-21 00:55 isw_ccajfhgiae_Volume05
```

The first volume is "System Reserved Space"
The second is Windows 7
The third is ext4 for Ubuntu
The last is an extended partition containing the swap

---

### Post by Wratholix on 2009-07-24
> **DSL5 said:**
> eh.....still didn't work

I tried typing quit then bash like you suggested, but I still get the "Error 15: File not found" error when I try find /boot/grub/stage1

This is my ls -l /dev/mapper output:

```

crw-rw---- 1 root root  10, 61 2009-07-20 20:53 control
brw-rw---- 1 root disk 252,  0 2009-07-21 00:55 isw_ccajfhgiae_Volume0
brw-rw---- 1 root disk 252,  1 2009-07-21 00:55 isw_ccajfhgiae_Volume01
brw-rw---- 1 root disk 252,  2 2009-07-21 00:55 isw_ccajfhgiae_Volume02
brw-rw---- 1 root disk 252,  3 2009-07-21 00:55 isw_ccajfhgiae_Volume03
brw-rw---- 1 root disk 252,  4 2009-07-21 00:55 isw_ccajfhgiae_Volume05
```The first volume is "System Reserved Space"
The second is Windows 7
The third is ext4 for Ubuntu
The last is an extended partition containing the swap

sorry for the late reply, its been really busy for me the last few days.

i remember why i got the error,  because i was using the wrong command for find since i got a separate boot partition.
i choose a separate boot partition when the main ubuntu partition gets errors due to a power failure or lockups etc the boot partition wouldnt be affected since its inactive.
This would allow you to at least boot the kernel without falling back to starting off the cd.


You can try do "find /grub/stage1" or perhaps you made a mistake on the hd(??) command.
Play with it.. you're on the last piece of the puzzle :)

Here is some more info [http://ubuntuforums.org/showthread.php?t=297261](http://ubuntuforums.org/showthread.php?t=297261)


** edit again **
Would run the command as follows:
```
device (hd0) /dev/mapper/isw_ccajfhgiae_Volume0 
find /boot/grub/stage1
```Your result  would be:
[COLOR=Red](hd0,4)[/COLOR]

The find command is just a 'easy' way of finding the right partition. You can try skip it if it doesnt work, just make sure all the required files are in /boot and continue the grub installation.

---

### Post by david2b on 2009-08-25
Thanks Wratholix, you're my man !!!
I even had wanted to install Fedora 11 to have it work !

---

