---
title: "Nvidia Nouveau Frozen on Suspend"
date: 2015-02-01
forum: Hardware
---

### Post by Gottier on 2015-02-01
Ubuntu 14.04LTS

I have tried a couple of different graphics cards, both nvidia type. The current one I am using is[SIZE=2]: "EVGA GeForce GT 730 2GB DDR3 128bit Dual DVI mHDMI Graphics Card 02G-P3-2738-KR[/SIZE]". It works fine with the Nouveau driver, except that if I use suspend, it is forever frozen. I have to force reboot. I really like to use suspend a lot, so it's kind of important that it works.

If I use one of the nvidia proprietary drivers, I have buggy behavior. When in my text editor (which is where I live) the scrolling is "sticky". I don't know how else to describe it. It's just very annoying, and driving me nuts.

I found information about what appears to be a reported bug: 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1111884](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1111884)

Does anyone know if there is a working solution for Ubuntu 14.04LTS ? This bug is old. If the solution is difficult to implement, can somebody please walk me through it?

---

### Post by Gottier on 2015-02-03
I found a few places recommending to use a special driver, so I tried it:

```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-340
```

But there were some big problems. My screen would start flashing super fast. I had to revert to Nouveau. To do that:

```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:xorg-edgers/ppa
```

Any help would be appreciated.

---

### Post by Bashing-om on 2015-02-03
Gottier; Hello;

A few thoughts to get us pointed in a direction to find a solution:
What is the hardware ?
```

lspci -vnn | grep -i VGA

```

Any residual driver components ?
```

dpkg -l | grep fglrx
dpkg -l | grep nvidia

```

Does the /etc/X11/xorg.conf file reflect the currently installed driver ?
```

cat /etc/X11/xorg.conf

```

Confirm what driver - if any - is loaded:
```

sudo lshw -C display

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Once we see these outputs, we get an idea of

[INDENT][INDENT]where we go from here
[/INDENT][/INDENT]

---

### Post by Gottier on 2015-02-06
> **Bashing-om said:**
> Gottier; Hello;

A few thoughts to get us pointed in a direction to find a solution:
What is the hardware ?
```

lspci -vnn | grep -i VGA

```

Any residual driver components ?
```

dpkg -l | grep fglrx
dpkg -l | grep nvidia

```

Does the /etc/X11/xorg.conf file reflect the currently installed driver ?
```

cat /etc/X11/xorg.conf

```

Confirm what driver - if any - is loaded:
```

sudo lshw -C display

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Once we see these outputs, we get an idea of[INDENT][INDENT]where we go from here
[/INDENT]
[/INDENT]


Thank you for your assistance. I've run the commands you specified, and put the results below:

```
gottier:~$ lspci -vnn | grep -i VGA
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:0f02] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: eVga.com. Corp. Device [3842:2738]
    Subsystem: eVga.com. Corp. Device [3842:2738]
gottier:~$ dpkg -l | grep fglrx
gottier:~$ dpkg -l | grep nvidia
rc  nvidia-331                   331.113-0ubuntu0.0.4                 amd64        NVIDIA binary driver - version 331.113
rc  nvidia-331-updates           331.113-0ubuntu0.0.4                 amd64        NVIDIA binary driver - version 331.113
rc  nvidia-340                   340.76-0ubuntu1~xedgers14.04.1       amd64        NVIDIA binary driver - version 340.76
rc  nvidia-libopencl1-331        331.113-0ubuntu0.0.4                 amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-331        331.113-0ubuntu0.0.4                 amd64        NVIDIA OpenCL ICD
rc  nvidia-opencl-icd-340        340.76-0ubuntu1~xedgers14.04.1       amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                 0.6.2                                amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings              331.20-0ubuntu8                      amd64        Tool for configuring the NVIDIA graphics driver
gottier:~$ cat /etc/X11/xorg.conf
cat: /etc/X11/xorg.conf: No such file or directory
gottier:~$ sudo lshw -C display
[sudo] password for gottier: 
  *-display               
       description: VGA compatible controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:46 memory:f6000000-f6ffffff memory:e8000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff
```

---

### Post by Bashing-om on 2015-02-06
Gottier; Well ..

That do beg the question, Nvidia drivers installed yet the system is using the open source driver.

It is past my think-a-bility time here.

I will look at this in my AM and get a start on what is going on with your system.

[INDENT][INDENT]a failure to communicate ?
[/INDENT][/INDENT]

---

### Post by Gottier on 2015-02-07
> **Bashing-om said:**
> Gottier; Well ..

That do beg the question, Nvidia drivers installed yet the system is using the open source driver.



Well, just to restate the problem:
1) Open source driver won't allow computer to suspend without freeze.
2) If Nvidia driver is used, I have super annoying issue with scrolling while using my text editor (Sublime Text 2).

So I have a dilema. "What negative attribute am I willing to deal with unless the problem can be fixed? "

I think ideally I would be using the open source driver, but would be able to suspend!

---

### Post by Bashing-om on 2015-02-07
Gottier; OK !

Agreed, much  preferred to use the open source driver 'nouveau' if at all possible.

Let's proceed to clean the system up and as we have the condition "using the open source driver, but would be able to suspend!"; verify the swap space is in existence to support this capability .

Cleanup; Post back:
```

sudo find / -name "NVIDIA-Linux-*"
sudo find / -name "*.run"

```
Will take a bit for the system to 'look' - ; patience .. will also get '/proc' errors. ignore these ( /proc is a virtual file system constantly changing and as such 'find' can not get a handle on it)
Make sure you don't see lines "blacklist nouveau" with this command:
```

grep -ri nouveau /etc/modprobe*

```

Depending on those outputs, we start removing the proprietary driver(s) and come up on a clean nouveau driver.
-----------------------
Take a look at 'swap' usage:
Post back:
```

free

``` to show the amount of ram and if 'swap' meets or exceeds this amount .

Just a bit of time and effort;
[INDENT][INDENT]clean up and 
[INDENT][INDENT][INDENT][INDENT]come up
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Gottier on 2015-02-08
I followed your instuctions, and ran the commands:

```
gottier:/$ sudo find / -name "NVIDIA-Linux-*"
gottier:/$ sudo find / -name "*.run"
gottier:/$ grep -ri nouveau /etc/modprobe*
gottier:/$ free
             total       used       free     shared    buffers     cached
Mem:       8104096    2438444    5665652      47776     400320     936056
-/+ buffers/cache:    1102068    7002028
Swap:      4121596          0    4121596
```

---

### Post by Bashing-om on 2015-02-08
Gottier; Ho Kay !

I think we have it isolated !
You show " Mem:       8104096 " as the amount of ram installed ....
" Swap:      4121596" ... 
When you suspend there is not enough swap space to contain what is in ram .
2 courses of action.
1) The easier - less painful - is to (RE-)install;
2) Re-partition such that the swap space is slightly larger than that of ram.

I will be more than happy to have my assessment confirmed by another.


[INDENT][INDENT]I think, I think !
[/INDENT][/INDENT]

---

### Post by Gottier on 2015-02-08
> **Bashing-om said:**
> Gottier; Ho Kay !

I think we have it isolated !
You show " Mem:       8104096 " as the amount of ram installed ....
" Swap:      4121596" ... 
When you suspend there is not enough swap space to contain what is in ram .
2 courses of action.
1) The easier - less painful - is to (RE-)install;
2) Re-partition such that the swap space is slightly larger than that of ram.

I will be more than happy to have my assessment confirmed by another.
[INDENT][INDENT]I think, I think !
[/INDENT]
[/INDENT]


Hey, at least you know what you are doing!

As a reinstall would be painful for me, I am interested to know more about re-partitioning. The hard drive is 1TB, so I have plenty of room for swap. Maybe 25GB would be totally painless.

I'd be glad to follow instructions on a re-partition if you think that will do it. What could go wrong?

Edit:
What do you think about this: [https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04) ???

---

### Post by Bashing-om on 2015-02-08
Gottier; Well ..

That tutorial is "good" in the sense that it does provide a workable solution. BUT, a swap partition is the better thing to do.

Let's look and see what making up a larger swap partition entails:
Boot up the liveDVD:
activate GParted
provide a screenshot of GParted
provide the output of terminal commands:
```

sudo fdisk -lu
sudo parted -l

```
As we will have to rob Peter to pay Paul. Let's see what we are taking from where and adding to, how.
I will save the customary admonishments 'til we know what we are going to do. (backup, backup, backup !)
-----------------------
And Hey, I may not always know what I am doing ->
But I will tell you no lies

[INDENT][INDENT]a picture, still
[INDENT][INDENT][INDENT]is worth a thousand words
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Gottier on 2015-02-09
> **Bashing-om said:**
> Gottier; Well ..

That tutorial is "good" in the sense that it does provide a workable solution. BUT, a swap partition is the better thing to do.

Let's look and see what making up a larger swap partition entails:
Boot up the liveDVD:
activate GParted
provide a screenshot of GParted
provide the output of terminal commands:
```

sudo fdisk -lu
sudo parted -l

```
As we will have to rob Peter to pay Paul. Let's see what we are taking from where and adding to, how.
I will save the customary admonishments 'til we know what we are going to do. (backup, backup, backup !)
-----------------------
And Hey, I may not always know what I am doing ->
But I will tell you no lies
[INDENT][INDENT]a picture, still[INDENT][INDENT][INDENT]is worth a thousand words
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]

OK, I booted from liveDVD, and got the screenshot from gparted, as well as the output from the terminal commands:

[IMG]http://suvovu.com/gparted-screenshot.jpg[/IMG]

Terminal output:

```
ubuntu@ubuntu:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD1002FAEX-0 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  538MB   537MB   fat32                 boot
 2      538MB   996GB   995GB   ext4
 3      996GB   1000GB  4221MB  linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           

ubuntu@ubuntu:~$ 


```

---

### Post by Bashing-om on 2015-02-09
Gottier; Hey;

Should be fairly straight forward to resize these partitions.
Repartitioning can always be hazardous to the hard drive's file system health ! Back up your data.
In this instance the chance of corruption is less as the system partition is moved to the left - header info is not touched. But, there is always that possibility of data lose - back up your data !

In Gparted turn swap off [color=green] <===[/color]
Highlight the partition - sda2 -and click on Resize/Move or in the menu, Partition > Resize/Move. Choose the new size. (You can type in the numbers or drag the color bar.)
same same for swap -sda3 - ; move the partition into the space you made when shrinking 'sda2' . A 9 Gig swap partition should be just fine. Make sure the partitions do not overlap, I like to leave a bit of cushion/head room between my partitions of 1 MB, personal preference and my peace of mind.

A most excellent tutotial.
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT][/INDENT]

---

### Post by Gottier on 2015-02-09
> **Bashing-om said:**
> Gottier; Hey;

Should be fairly straight forward to resize these partitions.
Repartitioning can always be hazardous to the hard drive's file system health ! Back up your data.
In this instance the chance of corruption is less as the system partition is moved to the left - header info is not touched. But, there is always that possibility of data lose - back up your data !

In Gparted turn swap off [COLOR=green] <===[/COLOR]
Highlight the partition - sda2 -and click on Resize/Move or in the menu, Partition > Resize/Move. Choose the new size. (You can type in the numbers or drag the color bar.)
same same for swap -sda3 - ; move the partition into the space you made when shrinking 'sda2' . A 9 Gig swap partition should be just fine. Make sure the partitions do not overlap, I like to leave a bit of cushion/head room between my partitions of 1 MB, personal preference and my peace of mind.

A most excellent tutotial.
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT]
[/INDENT]
[/INDENT]


Yes, changing the partition sizes was easy. One thing I did not know was if I should swapon after. (You said swapoff, so I did swapoff, but not swapon).

I decided to account for future RAM upgrade, so I made my swap ~ 36GB.

I left some cushion/ head room as you prefer.

Still after this the computer won't wake from suspend. It freezes at login screen.

---

### Post by Bashing-om on 2015-02-09
Gottier; shucks ...

What does swap look like ?
```

swapon -s
free

```

Did the system change the UUID and does it match what the system thinks it is ?
```

sudo blkid
cat etc/fstab

```
If no fault is found then ->
Let's see if the log files have anything to report.
```

cat ~/.xsession-errors
cat /var/log/syslog
cat /var/log/dmesg

```

We are just re-loading the system with what is in swap. 

[INDENT][INDENT]how tough can that be 
[/INDENT][/INDENT]

---

### Post by Gottier on 2015-02-09
> **Bashing-om said:**
> We are just re-loading the system with what is in swap. ... how tough can that be 

For me pretty tough! 

Here is the output for the commands:

```
gottier:~$ swapon -s
Filename                Type        Size    Used    Priority
/dev/sda3                               partition    37787644    0    -1
gottier:~$ free
             total       used       free     shared    buffers     cached
Mem:       8104096    1491208    6612888      19908      74260     626328
-/+ buffers/cache:     790620    7313476
Swap:     37787644          0   37787644
gottier:~$ sudo blkid
/dev/sda1: UUID="5A16-FE08" TYPE="vfat" 
/dev/sda2: UUID="dbfbde3c-e032-4215-97de-25e190a0b78c" TYPE="ext4" 
/dev/sda3: UUID="12317c18-022c-407a-80ab-c19b6f5c3755" TYPE="swap" 
gottier:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=dbfbde3c-e032-4215-97de-25e190a0b78c /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=5A16-FE08  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=12317c18-022c-407a-80ab-c19b6f5c3755 none            swap    sw              0       0
gottier:~$ cat ~/.xsession-errors
Script for ibus started at run_im.
```

Since the output for syslog and dmesg were large, I uploaded them to webserver:

[syslog]("http://suvovu.com/syslog")

[dmesg]("http://suvovu.com/dmesg")

---

### Post by Bashing-om on 2015-02-10
Gottier' Look'n

Upfront, this looks to be an UEFI system, I have no experience with UEFI.
However;
This looks to me to be a case of the firmware not set up to support 'resume' from suspend.
I do suggest you take a look in the EFI firmware and see what is set up.

Any other's opinions are welcome !
---------------------------
We have in 'syslog'
> 
Feb  9 08:17:21 ubuntu-h87-g43 rsyslogd-2039: Could no open output pipe '/dev/xconsole': No such file or directory [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]

Does this file exist ?
```

ls -al /dev/xconsole

```
-----------------------------------
?? scratch pads .
1. syslog
> 
Feb  9 08:17:21 ubuntu-h87-g43 kernel: [    0.150423] pci 0000:00:01.0: System wakeup disabled by ACPI

Feb  9 08:17:21 ubuntu-h87-g43 kernel: [    0.176974] PCI: Using ACPI for IRQ routing

Feb  9 08:17:21 ubuntu-h87-g43 kernel: [    0.835172] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)

Feb  9 08:17:21 ubuntu-h87-g43 kernel: [    0.835176] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT5._GTF] (Node ffff88021215feb0), AE_NOT_FOUND (20131115/psparse-536)

Feb  9 08:17:21 ubuntu-h87-g43 kernel: [    0.835960] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT5._GTF] (Node ffff88021215feb0), AE_NOT_FOUND (20131115/psparse-536

Feb  9 08:17:21 ubuntu-h87-g43 kernel: [   11.389084] ACPI Warning: 0x0000000000001828-0x000000000000182f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)

Feb  9 08:19:48 ubuntu-h87-g43 kernel: [   97.589222] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT5._GTF] (Node ffff88021215feb0), AE_NOT_FOUND (20131115/psparse-536)
Feb  9 08:19:48 ubuntu-h87-g43 kernel: [   97.589222] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
Feb  9 08:19:48 ubuntu-h87-g43 kernel: [   97.589222] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT5._GTF] (Node ffff88021215feb0), AE_NOT_FOUND (20131115/psparse-536)

--------------------------------
Feb  9 08:17:21 ubuntu-h87-g43 kernel: [    0.466877] rtc_cmos 00:06: RTC can wake from S4

??
Feb  9 08:19:48 ubuntu-h87-g43 kernel: [  102.577499] PM: resume of devices complete after 6593.226 msecs
Feb  9 08:19:48 ubuntu-h87-g43 kernel: [  102.577605] PM: Finishing wakeup.


2. dmesg:
> 
11.495589] ACPI Warning: 0x0000000000001828-0x000000000000182f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)

0.836876] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
[    0.836880] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT5._GTF] (Node ffff88021215feb0), AE_NOT_FOUND (20131115/psparse-536)

0.143503] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.143507] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)

 0.149978] pci 0000:00:01.0: System wakeup disabled by ACPI

---------------------------------------
Not related ?? But huh ? Why nouveau if Nvidia-prime is available ?
> 
Feb  9 08:17:21 ubuntu-h87-g43 kernel: [   12.854166] nouveau  [     DRM] allocated 1280x1024 fb: 0x60000, bo ffff8800dd5a6c00
 Feb  9 08:17:24 ubuntu-h87-g43 kernel: [   20.252861] init: nvidia-prime main process (967) terminated with status 127


[INDENT][INDENT][INDENT]It always amazes me, when I think I know something
[INDENT][INDENT][INDENT][INDENT]how little I do know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Gottier on 2015-02-10
Bashing-om; I know nothing, and can prove it!

/dev/xconsole doesn't exist.

I tried the nvidia proprietary drivers, but had worse problems. The proprietary drivers that can be turned on through "Additional Drivers" makes my mouse wheel hesitate to scroll, which is super annoying. I tried to install a ppa version of the latest and greatest nvidia driver, but it made stuff flash on the srcreen. I almost had a seizure. 

Here is the thing. I have another computer that has mostly the same hardware, but a different graphics card, and it does the same thing with the Nouveau driver. I think it must just be a bug in the driver, or maybe nvidia graphics cards are bad, but again I really know nothing.

---

### Post by Bashing-om on 2015-02-10
Gottier; Hey !

on the "/dev/xconsole" :
```

cat /etc/rsyslog.d/50-default.conf

```
And let's see what the file directs;

Next in this is the graphics driver:
```

lspci -vnn | grep VGA -A 12
sudo lshw -C display
dpkg -l | grep nvidia

```

On that main issue of 'suspend', await another opinion that it is firmware controlled.

[INDENT][INDENT]system administration
[INDENT][INDENT]if it ain't 1 thing, surely 2 others
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Gottier on 2015-02-10
> **Bashing-om said:**
> Gottier; Hey !

on the "/dev/xconsole" :
```

cat /etc/rsyslog.d/50-default.conf

```
And let's see what the file directs;

Next in this is the graphics driver:
```

lspci -vnn | grep VGA -A 12
sudo lshw -C display
dpkg -l | grep nvidia

```

On that main issue of 'suspend', await another opinion that it is firmware controlled.[INDENT][INDENT]system administration[INDENT][INDENT]if it ain't 1 thing, surely 2 others
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


OK, I will hope that somebody else has an answer, but here is the output for the commands:

```
gottier:~$ cat /etc/rsyslog.d/50-default.conf
#  Default rules for rsyslog.
#
#            For more information see rsyslog.conf(5) and /etc/rsyslog.conf

#
# First some standard log files.  Log by facility.
#
auth,authpriv.*            /var/log/auth.log
*.*;auth,authpriv.none        -/var/log/syslog
#cron.*                /var/log/cron.log
#daemon.*            -/var/log/daemon.log
kern.*                -/var/log/kern.log
#lpr.*                -/var/log/lpr.log
mail.*                -/var/log/mail.log
#user.*                -/var/log/user.log

#
# Logging for the mail system.  Split it up so that
# it is easy to write scripts to parse these files.
#
#mail.info            -/var/log/mail.info
#mail.warn            -/var/log/mail.warn
mail.err            /var/log/mail.err

#
# Logging for INN news system.
#
news.crit            /var/log/news/news.crit
news.err            /var/log/news/news.err
news.notice            -/var/log/news/news.notice

#
# Some "catch-all" log files.
#
#*.=debug;\
#    auth,authpriv.none;\
#    news.none;mail.none    -/var/log/debug
#*.=info;*.=notice;*.=warn;\
#    auth,authpriv.none;\
#    cron,daemon.none;\
#    mail,news.none        -/var/log/messages

#
# Emergencies are sent to everybody logged in.
#
*.emerg                                :omusrmsg:*

#
# I like to have messages displayed on the console, but only on a virtual
# console I usually leave idle.
#
#daemon,mail.*;\
#    news.=crit;news.=err;news.=notice;\
#    *.=debug;*.=info;\
#    *.=notice;*.=warn    /dev/tty8

# The named pipe /dev/xconsole is for the `xconsole' utility.  To use it,
# you must invoke `xconsole' with the `-file' option:
# 
#    $ xconsole -file /dev/xconsole [...]
#
# NOTE: adjust the list below, or you'll go crazy if you have a reasonably
#      busy site..
#
daemon.*;mail.*;\
    news.err;\
    *.=debug;*.=info;\
    *.=notice;*.=warn    |/dev/xconsole
gottier:~$ lspci -vnn | grep VGA -A 12
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:0f02] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: eVga.com. Corp. Device [3842:2738]
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e8000000 (64-bit, prefetchable) [size=128M]
    Memory at f0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    Expansion ROM at f7000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nouveau

01:00.1 Audio device [0403]: NVIDIA Corporation GF108 High Definition Audio Controller [10de:0bea] (rev a1)
    Subsystem: eVga.com. Corp. Device [3842:2738]
gottier:~$ sudo lshw -C display
[sudo] password for gottier: 
  *-display               
       description: VGA compatible controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:47 memory:f6000000-f6ffffff memory:e8000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff
gottier:~$ dpkg -l | grep nvidia
rc  nvidia-331                    331.113-0ubuntu0.0.4                amd64        NVIDIA binary driver - version 331.113
rc  nvidia-331-updates            331.113-0ubuntu0.0.4                amd64        NVIDIA binary driver - version 331.113
rc  nvidia-340                    340.76-0ubuntu1~xedgers14.04.1      amd64        NVIDIA binary driver - version 340.76
rc  nvidia-libopencl1-331         331.113-0ubuntu0.0.4                amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-331         331.113-0ubuntu0.0.4                amd64        NVIDIA OpenCL ICD
rc  nvidia-opencl-icd-340         340.76-0ubuntu1~xedgers14.04.1      amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                  0.6.2                               amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings               331.20-0ubuntu8                     amd64        Tool for configuring the NVIDIA graphics driver
```

---

### Post by Bashing-om on 2015-02-10
Gottier; Well !

Not sure what to recommend as you have mysql - server- installed .
Between now and then I will come up with a procedure.
> 
# NOTE: adjust the list below, or you'll go crazy if you have a reasonably
#      busy site..
#
daemon.*;mail.*;\
    news.err;\
    *.=debug;*.=info;\
    *.=notice;*.=warn    |/dev/xconsole

as "/dev/xconsole" does not exist on your system, I expect it to be save to comment that line out in the config file.

As to graphics, seems there is a conflict going on. The output indicates some components of the Nvidia driver remain.
Let's see what we can find:
```

sudo find / -name "NVIDIA-Linux-*"
sudo find / -name "*.run"
dpkg -l | grep nvidia

```

And awaiting others to have a looksee, see if they also agree there is something not set in the firmware to control 'suspend'.

[INDENT][INDENT]but hey, making progress !
[/INDENT][/INDENT]

---

### Post by Gottier on 2015-02-11
> **Bashing-om said:**
> Gottier; Well !

Not sure what to recommend as you have mysql - server- installed .
Between now and then I will come up with a procedure.

as "/dev/xconsole" does not exist on your system, I expect it to be save to comment that line out in the config file.

As to graphics, seems there is a conflict going on. The output indicates some components of the Nvidia driver remain.
Let's see what we can find:
```

sudo find / -name "NVIDIA-Linux-*"
sudo find / -name "*.run"
dpkg -l | grep nvidia

```

And awaiting others to have a looksee, see if they also agree there is something not set in the firmware to control 'suspend'.[INDENT][INDENT]but hey, making progress !
[/INDENT]
[/INDENT]


I'm not sure what you are telling me to do in the section above the commands. This is just a dev machine, so I am the only site visitor. Typical LAMP stack for local development.

Output of commands:

```
gottier:~$ sudo find / -name "NVIDIA-Linux-*"
[sudo] password for gottier: 
gottier:~$ sudo find / -name "*.run"
gottier:~$ dpkg -l | grep nvidia
rc  nvidia-331                    331.113-0ubuntu0.0.4                 amd64        NVIDIA binary driver - version 331.113
rc  nvidia-331-updates            331.113-0ubuntu0.0.4                 amd64        NVIDIA binary driver - version 331.113
rc  nvidia-340                    340.76-0ubuntu1~xedgers14.04.1       amd64        NVIDIA binary driver - version 340.76
rc  nvidia-libopencl1-331         331.113-0ubuntu0.0.4                 amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-331         331.113-0ubuntu0.0.4                 amd64        NVIDIA OpenCL ICD
rc  nvidia-opencl-icd-340         340.76-0ubuntu1~xedgers14.04.1       amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                  0.6.2                                amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings               331.20-0ubuntu8                      amd64        Tool for configuring the NVIDIA graphics driver
```

---

### Post by Bashing-om on 2015-02-11
Gottier; Morning:

OK, ' /etc/rsyslog.d/50-default.conf ' I do recommned to follow the advise in the file and comment out the line ' *.=notice;*.=warn |/dev/xconsole ' .
Always make a backup of any file one edits, just because never can tell .
```

sudo cp /etc/rsyslog.d/50-default.conf /etc/rsyslog.d/50-default.conf-original

```
Now edit the file in your favorite text editor ( gedit );
```

gksudo gedit /etc/rsyslog.d/50-default.conf

```
notate in the file when and why you are making the edit. I also maintain a "change log" file of all changes I make to my system.
a '#' character denotes a comment line, and the system will not parse the line.
so the edit is something similar to this:
```

#11feb15 comment out /dev/xconsole - file does not exist on  my system.
daemon.*;mail.*;\
	news.err;\
	*.=debug;*.=info;\
#	*.=notice;*.=warn	|/dev/xconsole

```
That should take care that minor error .
--------------------------------------

Looking at the driver situation:
Let's do:
```

sudo service lightdm stop
sudo apt-get remove --purge nvidia*

```
And, because Nvidia may not play nice with the operating system:
```

sudo rm /etc/X11/xorg.conf
sudo apt-get update
sudo apt-get  install --reinstall ubuntu-desktop

```

Next is to insure the open source driver is properly installed:
```

# I expect no return, just checking !
sudo grep 'blacklist.*nouveau' /etc/modprobe.d/*
sudo apt-get install --reinstall xserver-xorg-video-nouveau
sudo apt-get upgrade

```

Reboot to see the effect . I do feel the more comfortable to reboot rather than just re-starting the desktop to insure all memory is cleared.

And check once more:
```

dpkg -l | grep nvidia*

``` to see if we have any stray config files still present.

[INDENT][INDENT]little things mean a lot[/INDENT][/INDENT]

---

### Post by Gottier on 2015-02-12
> **Bashing-om said:**
> Gottier; Morning:

OK, ' /etc/rsyslog.d/50-default.conf ' I do recommned to follow the advise in the file and comment out the line ' *.=notice;*.=warn |/dev/xconsole ' .
Always make a backup of any file one edits, just because never can tell .
```

sudo cp /etc/rsyslog.d/50-default.conf /etc/rsyslog.d/50-default.conf-original

```
Now edit the file in your favorite text editor ( gedit );
```

gksudo gedit /etc/rsyslog.d/50-default.conf

```
notate in the file when and why you are making the edit. I also maintain a "change log" file of all changes I make to my system.
a '#' character denotes a comment line, and the system will not parse the line.
so the edit is something similar to this:
```

#11feb15 comment out /dev/xconsole - file does not exist on  my system.
daemon.*;mail.*;\
    news.err;\
    *.=debug;*.=info;\
#    *.=notice;*.=warn    |/dev/xconsole

```
That should take care that minor error .
--------------------------------------

Looking at the driver situation:
Let's do:
```

sudo service lightdm stop
sudo apt-get remove --purge nvidia*

```
And, because Nvidia may not play nice with the operating system:
```

sudo rm /etc/X11/xorg.conf
sudo apt-get update
sudo apt-get  install --reinstall ubuntu-desktop

```

Next is to insure the open source driver is properly installed:
```

# I expect no return, just checking !
sudo grep 'blacklist.*nouveau' /etc/modprobe.d/*
sudo apt-get install --reinstall xserver-xorg-video-nouveau
sudo apt-get upgrade

```

Reboot to see the effect . I do feel the more comfortable to reboot rather than just re-starting the desktop to insure all memory is cleared.

And check once more:
```

dpkg -l | grep nvidia*

``` to see if we have any stray config files still present.
[INDENT][INDENT]little things mean a lot[/INDENT]
[/INDENT]


OK, so I did all of this. After reboot no nvidia present. Still frozon on wake from suspend.

Side note; A little scary after stopping lightdm and screen goes black. Used Ctrl-Alt-F1 to get a terminal and complete the rest of the commands. Then sudo shutdown -h now.

---

### Post by Bashing-om on 2015-02-12
Gottier; Yeah;

Sorry, I did not see that tree ( ctl+alt+F1)in the forest prior to stopping the display. Glad ya worked over my oversight.

What do we look like now ?
Please post back the output of:
```

dpkg -l | grep nvidia
sudo lshw -C display

```
See if there are any old config files about.

Then refocus our attention on the ACPI errors/suspend issue.

[INDENT][INDENT]in that process of learning
[/INDENT][/INDENT]

---

### Post by mc4man on 2015-02-12
Re: scroll issues with nvidia driver
Not sure if you have any intention of using the nvidia drivers but if so it may be worth checking the 'performance' setting. Many nvidia cards will be defaulted to an adaptive mode.
If that's the case for you then you could try setting it to max performance (full clock speeds) & see if that improves scrolling. 
(- noveau doesn't support adaptive so it runs the card at full speed all the time.

---

### Post by Gottier on 2015-02-13
> **Bashing-om said:**
> Gottier; Yeah;

Sorry, I did not see that tree ( ctl+alt+F1)in the forest prior to stopping the display. Glad ya worked over my oversight.

What do we look like now ?
Please post back the output of:
```

dpkg -l | grep nvidia
sudo lshw -C display

```
See if there are any old config files about.

Then refocus our attention on the ACPI errors/suspend issue.
[INDENT][INDENT]in that process of learning
[/INDENT]
[/INDENT]


I appreciate your time. I have confidence that you know almost everything, and compared to me that is a lot.

Here is the output of the commands:

```
gottier:~$ dpkg -l | grep nvidia
gottier:~$ sudo lshw -C display
[sudo] password for gottier: 
  *-display               
       description: VGA compatible controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:46 memory:f6000000-f6ffffff memory:e8000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff


```

---

### Post by Gottier on 2015-02-13
> **mc4man said:**
> Re: scroll issues with nvidia driver
Not sure if you have any intention of using the nvidia drivers but if so it may be worth checking the 'performance' setting. Many nvidia cards will be defaulted to an adaptive mode.
If that's the case for you then you could try setting it to max performance (full clock speeds) & see if that improves scrolling. 
(- noveau doesn't support adaptive so it runs the card at full speed all the time.

I don't think I have ever seen a settings area. Can you tell me how to find it?

---

### Post by Bashing-om on 2015-02-13
Gottier; Hey, hey ;

Looks good to me ... I expect now we are down to the "failure to resume" from suspend .
All else is good, yes ?
If you are stable on the open source , nouveau, driver, will put the proprietary driver, Nvidia, in our back pocket, for the time you want to investigate performance (nvidia drivers but if so it may be worth checking the 'performance' setting.(mc4man)

As I do not have access to a UEFI machine, I know little about this firmware interface. The going is going to be slow now.

Knowledge: The more I think I know the more I realize how little I do know - a constant process of learning.

[INDENT][INDENT]we will finger out sumpthin
[/INDENT][/INDENT]

---

### Post by mc4man on 2015-02-13
> **Gottier said:**
> I don't think I have ever seen a settings area. Can you tell me how to find it?

Well it's nvidia-settings ( the nvidia-settings package should be installed when installing any nvidia driver package

---

### Post by Gottier on 2015-02-14
> **Bashing-om said:**
> Gottier; Hey, hey ;

Looks good to me ... I expect now we are down to the "failure to resume" from suspend .
All else is good, yes ?
If you are stable on the open source , nouveau, driver, will put the proprietary driver, Nvidia, in our back pocket, for the time you want to investigate performance (nvidia drivers but if so it may be worth checking the 'performance' setting.(mc4man)

As I do not have access to a UEFI machine, I know little about this firmware interface. The going is going to be slow now.

Knowledge: The more I think I know the more I realize how little I do know - a constant process of learning.
[INDENT][INDENT]we will finger out sumpthin
[/INDENT]
[/INDENT]


Yes, everything is good and stable. I have no other problems that I know of.

---

### Post by Bashing-om on 2015-02-14
Gottier; Well, Let's

See what we can find out. as a place to start, UEFI conflicts ?
```

lsmod | grep rtc_efi
lsmod | grep efivars

```

Got to start somewhere,
[INDENT][INDENT]here's a start
[/INDENT][/INDENT]

---

### Post by Gottier on 2015-02-14
> **Bashing-om said:**
> Gottier; Well, Let's

See what we can find out. as a place to start, UEFI conflicts ?
```

lsmod | grep rtc_efi
lsmod | grep efivars

```

Got to start somewhere,[INDENT][INDENT]here's a start
[/INDENT]
[/INDENT]


Those commands had no output:

```
gottier:~$ lsmod | grep rtc_efi
gottier:~$ lsmod | grep efivars
gottier:~$
```

---

### Post by Bashing-om on 2015-02-15
Gottier; Well, 

That I take as good; I had seen where patches were to be submitted, I recon that little matter has been taken care of.

OK, so what is set for "Devices Power On" ?
post back:
```

cat /proc/acpi/wakeup
grep -i rtc /var/log/kern.log
sudo grep -i rtc /var/log/dmesg

```
See what we can find for errors, hints.
I remind you that I do not have the UEFI experience, but am more than happy to explore this issue with you.

[INDENT][INDENT]here is no end to learning
[/INDENT][/INDENT]

---

### Post by Gottier on 2015-02-17
Bashing-om,

Sorry it took so long to get back. I was too busy the last couple days.

Today there were some updates for Ubuntu, and some mentioned Nouveau and X, but after installing I tried to see if maybe it was fixed; no luck.

Here is the output of those commands:

```
gottier:~$ cat /proc/acpi/wakeup
Device    S-state      Status   Sysfs node
RP01      S4    *disabled  pci:0000:00:1c.0
PXSX      S4    *disabled
RP02      S4    *disabled  pci:0000:00:1c.1
PXSX      S4    *enabled   pci:0000:03:00.0
RP04      S4    *disabled  pci:0000:00:1c.3
PXSX      S4    *disabled  pci:0000:04:00.0
GLAN      S4    *disabled
EHC1      S4    *enabled   pci:0000:00:1d.0
EHC2      S4    *enabled   pci:0000:00:1a.0
XHC      S4    *enabled   pci:0000:00:14.0
HDEF      S4    *disabled  pci:0000:00:1b.0
PEG0      S4    *disabled  pci:0000:00:01.0
PEGP      S4    *disabled  pci:0000:01:00.0
PEG1      S4    *disabled
PEG2      S4    *disabled
PWRB      S3    *enabled 
gottier:~$ grep -i rtc /var/log/kern.log
gottier:~$ sudo grep -i rtc /var/log/dmesg
[sudo] password for gottier: 
[    0.119620] RTC time:  2:12:54, date: 02/18/15
[    0.466510] rtc_cmos 00:06: RTC can wake from S4
[    0.466679] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.466704] rtc_cmos 00:06: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.476608] rtc_cmos 00:06: setting system clock to 2015-02-18 02:12:55 UTC (1424225575)
```

---

### Post by Bashing-om on 2015-02-18
Gottier; Humm ...

I still think we are back to looking at what is set in the firmware for the "power state" :
see:
[https://msdn.microsoft.com/en-us/library/windows/hardware/ff564575(v=vs.85).aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/ff564575(v=vs.85).aspx)
for an explanation.
On my system the 'wakeup' result :
```

sysop@1404mini:~$ cat /proc/acpi/wakeup
Device  S-state   Status   Sysfs node
HUB0      S5    *disabled  pci:0000:00:06.0
XVR0      S5    *disabled  pci:0000:00:0f.0
XVR1      S5    *disabled  pci:0000:00:0e.0
XVR2      S5    *disabled  pci:0000:00:0d.0
XVR3      S5    *disabled  pci:0000:00:0c.0
XVR4      S5    *disabled
XVR5      S5    *disabled  pci:0000:00:0a.0
USB0      S3    *enabled   pci:0000:00:02.0
USB2      S3    *enabled   pci:0000:00:02.1
AZAD      S5    *disabled  pci:0000:00:06.1
MMAC      S5    *enabled   pci:0000:00:08.0
MAC1      S5    *enabled   pci:0000:00:09.0
sysop@1404mini:~$

```

seems to confirm that assumption. Please look once more .

[INDENT][INDENT][INDENT]I have been known to be in error
[INDENT][INDENT][INDENT]I try real hard, not to let that happen
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

