---
title: "Installed Ubuntu 8.10, but system wont boot to HD"
date: 2009-03-01
forum: Installation &amp; Upgrades
---

### Post by daleong on 2009-03-01
Hi all, I installed Ubuntu 8.10 from the installation CD. However, when the install is done, it reboots back to the CD. If i remove the CD and boot, the system does not find any bootable drives.

I chose the option to use the entire HD for Ubuntu during the install. There are ubuntu files on the HD. 

Any ideas? How do i make the HD bootable? Thanks in advance for the help.

---

### Post by cariboo on 2009-03-01
I sounds like grub didn't install properly. Boot from your LiveCD and once at the desktop open a Applications-->Accessories-->Terminal and type:

```
sudo grub
```

This will get you to the grub prompt, next at the prompt type:

```
find /boot/grub/stage1
```

The above command should result in something that looks like this:

```
(hd0,0)
```

Next type:

```
root (hd0,0)
```

replace the (hd0,0) with the result of the find command. Next type:

```
setup (hd0)
```

The above is the disk number without the partition number. To finish type:

```
quit
```

and reboot.

Jim

---

### Post by tommcd on 2009-03-01
Do you get the grub menu on bootup? Since you installed Ubuntu as the only operating system you may not see the grub menu when you boot. To get the grub menu, hit the **Esc** key as the system boots up. You should see a menu that looks similar, but not identical, to the picture at the top of this page:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
Select the option to boot Ubuntu and hit enter. If you get errors, report them here.

If you don't get the grub menu, then reinstall grub as Cariboo907 said.

---

### Post by daleong on 2009-03-01
Well i think the problem here is that grub is entirely missing from the install. When i go to terminal, after "sudo grub" and I type find /boot/grub/stage1, I get an "Error 15: File not found"

In the /boot directory on the drive there is no folder for grub either.

Maybe something is wrong with the Ubuntu Live CD? I did check the CD for errors and none were reported. 

Any ideas on where to go from here? Thanks for the help so far.

---

### Post by PsychJim on 2009-03-01
Hi,

I'm a relative newbie and have just installed Ubuntu 8.10 over 7.1 but it crashes just after the final boot. Freezes completely. I've tried /boot/grub/menu.lst to see if its a grub issue but receive "permission denied" message. Have done a complete MemTest with a pass - don't know enough to try something new. Any ideas, please?

---

### Post by tommcd on 2009-03-01
> **daleong said:**
> Well i think the problem here is that grub is entirely missing from the install. When i go to terminal, after "sudo grub" and I type find /boot/grub/stage1, I get an "Error 15: File not found"
In the /boot directory on the drive there is no folder for grub either.
Maybe something is wrong with the Ubuntu Live CD? I did check the CD for errors and none were reported. 


Boot from the Ubuntu live CD, open a terminal (applications > accessories > terminal) and run:
```
sudo fdisk -l
```
This will list your partitions. If you let the installer use the whole hard drive, you likely have 2 partitions: root and swap. It should look something like this:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1  *         2551        4080    12289725   83  Linux
/dev/sda2            4081        4207     1020127+  82  Linux swap

```
Assuming you get something like that, next do this:
```

sudo mount -t ext3 /dev/sda1 /mnt
ls /mnt/

```
If you get errors, try:
> 
sudo mount -t auto /dev/sda1 /mnt

This should list all the directories that Ubuntu installed to your hard drive. It should look something like this:
```

bash-3.1# ls /mnt/
bin   data  etc   lib	      media  opt   root  srv  tmp  var
boot  dev   home  lost+found  mnt    proc  sbin  sys  usr

```
Then to list what is in the boot directory, run:
```

ls /mnt/boot/

```
You should see a grub directory, along with the linux kernels, config, and system map files, etc. Then run:
```
ls /mnt/boot/grub/
```
To see what is in the /boot/grub directory. Please post the output of those commands.

I have to go out of the house right now, but I'll pick this up later. Perhaps someone else can fill in in the meantime.

---

### Post by daleong on 2009-03-01
Thanks. I ran the commands as you asked and the output of the 
"ls /mnt/boot/ are 5 files, *.generic and a memtest 86+. There is no /grub directory.

---

### Post by tommcd on 2009-03-01
> **daleong said:**
> Thanks. I ran the commands as you asked and the output of the 
"ls /mnt/boot/ are 5 files, *.generic and a memtest 86+. There is no /grub directory.

Could you post the output of those commands please after you boot the live CD:
sudo fdisk -l
sudo mount -t ext3 /dev/sda1 /mnt
ls /mnt/
ls /mnt/boot/
I would like to see just what exactly is installed on your hard drive. 
Do you get something like this when you run "sudo fdisk -l"?
```

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217        1338      979965   82  Linux swap / Solaris

```
If you do, then /dev/sda1 is root, and /dev/sda2 is swap. To install grub to /dev/sda1 (or which ever partition is root on your system) from the live CD follow this:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)
The important part that installs grub is 
> sudo grub-install /dev/sda
But please post the output of those commands above so I can see what is on your hard drive.

---

### Post by tommcd on 2009-03-01
> **PsychJim said:**
> Hi,

I'm a relative newbie and have just installed Ubuntu 8.10 over 7.1 but it crashes just after the final boot. Freezes completely. I've tried /boot/grub/menu.lst to see if its a grub issue but receive "permission denied" message. Have done a complete MemTest with a pass - don't know enough to try something new. Any ideas, please?

PsychJim,
It may be best if you start your own thread on this. Your problem is likely different from Daleong's.
Also, I'm not sure what you mean by "it crashes just after the final boot". You do not reboot at all during the Ubuntu install. When the installer finishes you reboot into the installed system.

And welcome to the Ubuntu forums!

---

### Post by daleong on 2009-03-01
Thanks for the help tommcd. Here is the info you are looking for:

---------------------------------------
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x89848984

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4676    37559938+  83  Linux
/dev/sda2            4677        4864     1510110    5  Extended
/dev/sda5            4677        4864     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 1039 MB, 1039663104 bytes
256 heads, 32 sectors/track, 247 cylinders
Units = cylinders of 8192 * 512 = 4194304 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         248     1015280    4  FAT16 <32M
Partition 1 has different physical/logical endings:
     phys=(249, 255, 32) logical=(247, 223, 32)

ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda /mnt
mount: /dev/sda already mounted or /mnt busy

ubuntu@ubuntu:~$ ls /mnt/

ubuntu@ubuntu:~$ ls /mnt/boot/
ls: cannot access /mnt/boot/: No such file or directory

ubuntu@ubuntu:~$ sudo grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.

---

### Post by tommcd on 2009-03-01
> **daleong said:**
> 
ubuntu@ubuntu:~$ sudo fdisk -l
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4676    37559938+  83  Linux
/dev/sda2            4677        4864     1510110    5  Extended
/dev/sda5            4677        4864     1510078+  82  Linux swap / Solaris

Ubuntu is on your hard drive /dev/sda. Ubuntu's root partition is /dev/sda1.
Is /dev/sda (1st hard drive) set to boot first in your BIOS? If not, set first boot device as CDROM (so you can boot the live CD), and second boot device /dev/sda. Also, it looks like you have no boot flag set (which would be indicated by a * in the boot column of fdisk -l). If /dev/sda is set as first (or primary) hard drive then grub *should* have gone to the MBR of /dev/sda. I suppose it is possible it went to /dev/sdb.  Also, Ubuntu says /dev/sdb is only 1039MB. Is this a flash drive? If it is then unplug it, set /dev/sda to boot second after the CDROM, and try to reinstall grub.

> **daleong said:**
> 
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda /mnt
mount: /dev/sda already mounted or /mnt busy

The correct command should be:
```
sudo mount -t /dev/sda1 /mnt
```
You forgot the **1** at the end of /dev/sda1. Try it like that and post the output. Then run:
```
ls /mnt/
```
and post the output.

> **daleong said:**
> 
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
Does your BIOS see /dev/sda? Is it set to boot vefore /dev/sdb? It should be.

The idiot proof way to deal with this would be to temporarily disconnect /dev/sdb and reinstall Ubuntu to /dev/sda. But try making sure /dev/sda is set as a bootable device in the BIOS and try to reinstall grub.

---

### Post by daleong on 2009-03-02
[LIST]
/dev/sdb is a flash drive i had plugged into the system at the time so i could copy the output off the machine as you asked. I did not have it installed during the install.
[/LIST]
[list]
The HD is set to be the first bootable device in the boot order in BIOS, followed by the CD-ROM
[/LIST]

Will try to set the HD to second in the boot order and re-try the install. 

As for the output after sudo mount -t ext3 /dev/sda1 /mnt
```

ubuntu@ubuntu:~$ ls /mnt/
ls: cannot access /mnt/root: Input/output error
bin   cdrom  etc   initrd.img  lost+found  mnt  proc  sbin  sys  usr  vmlinuz
boot  dev    home  lib         media       opt  root  srv   tmp  var

```

Let me know if i missed anything, but i will retry the install and look closer at the BIOS to see if anything is awry. Thanks.

*Update*
I reinstalled the OS and saw the same results. I used fdisk to set the /dev/sda1 device as bootable. So now the system tries to boot from the HD, but it fails with an error "Error loading operating system"

I suspect everything goes back to the fact I am missing grub entirely from the /boot folder on the HD. It is probably important to note that when running the install it never looks to me like a successful install. I never see the system reach 100% install or a install complete message. It just reboots back into the Ubuntu OS from the live CD every time.

---

### Post by tommcd on 2009-03-03
> **daleong said:**
> [LIST]
As for the output after sudo mount -t ext3 /dev/sda1 /mnt
```

ubuntu@ubuntu:~$ ls /mnt/
ls: cannot access /mnt/root: Input/output error
bin   cdrom  etc   initrd.img  lost+found  mnt  proc  sbin  sys  usr  vmlinuz
boot  dev    home  lib         media       opt  root  srv   tmp  var

```

It looks like you have all the directories there. If you run:
```
ls /mnt/boot/
```
do you see a grub directory inside the boot directory? If so run:
```
ls /boot/grub/
```
to see what is there and post the output.

> **daleong said:**
> [LIST]
 It is probably important to note that when running the install it never looks to me like a successful install. I never see the system reach 100% install or a install complete message. It just reboots back into the Ubuntu OS from the live CD every time.
You should get a message that the install is finished and ask you to remove the CD and reboot to your new system. Do you get something like that?
At this point I think it would be good to try burning a new Ubuntu CD. Try using Iso Recorder or Infra Recorder (both free) and burn at the slowest possible speed. 
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Then check the CD for errors when you boot it.

Also, just out of curiosity, what are your system specs? Post the motherboard chipset, amount of RAM, and video card model if you know what they are.

---

