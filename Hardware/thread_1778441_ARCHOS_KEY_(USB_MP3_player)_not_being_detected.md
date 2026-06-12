---
title: "ARCHOS KEY (USB MP3 player) not being detected?"
date: 2011-06-09
forum: Hardware
---

### Post by itz_speld_rong on 2011-06-09
I just got a brand new MP3 player the "ARCHOS KEY" with the understanding that it is a "drag and drop" player and appears as a flash-drive. When I plugged it into the USB port, it wasn't mounted onto my desktop. So I looked around online (for I'm fairly new with Linux command line) for a solution.

 I ran across the two commands:

  	 	 	 	 	 	  sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1
 
Which seemed to get the job done. But there were some problems.

_First of_f, nothing on the KEY can be manipulated because "Permission Denied." And when right clicked and selecting the "permissions" tab, it says "The permissions of "sdb1" could not be determined." 

I don't know how to solve this issue and to put songs on my new MP3 player!

_The second problem_ is that I have to run the "sudo mount -t vfat /dev/sdb1 /media/sdb1" command every time the "mp3 stick" (if you will) is plugged into the computer. I don't understand why it isn't automatically mounted like every other USB device that is plugged in.  

I would love to get this to mount automatically and any insight would be greatly appreciated! Thank you!

---

### Post by coffeecat on 2011-06-09
Hi, a couple of questions.

Which version of Ubuntu are you using? If Natty/11.04 there's an upstream bug in the 2.6.38 kernel which prevents automounting of some Archos devices. Launchpad bug report here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/763227](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/763227)

The people contributing to that have various Archos Visions - your Archos Key is not mentioned - but I wouldn't be surprised if all Archos players are affected. It looks as though a fix has been committed by the upstream kernel developers and hopefully this will arrive in an Ubuntu kernel update soon. But if you want your Archos working now, you can install the 2.6.39 kernel from this ppa:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")

If you want to enable that ppa and don't know how, post back and I'll take you through it.

Second question: did you, by chance, install the app "usbmount" from the repositories? Or any app which purports to help with USB mounting? If so, uninstall it/them now. There are several such 3rd-party apps which cause more problems than they allegedly solve. USB automounting works out-of-the-box in Ubuntu except when there is a specific bug for a specific piece of hardware. as I have just described.

---

### Post by itz_speld_rong on 2011-06-09
> **coffeecat said:**
> Which version of Ubuntu are you using? If Natty/11.04 there's an upstream bug in the 2.6.38 kernel which prevents automounting of some Archos devices. Launchpad bug report here:
 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/763227](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/763227)

 It is 11.4 yes. It figures that I would have this problem. ](*,)

> **coffeecat said:**
> 
 
The people contributing to that have various Archos Visions - your Archos Key is not mentioned - but I wouldn't be surprised if all Archos players are affected. It looks as though a fix has been committed by the upstream kernel developers and hopefully this will arrive in an Ubuntu kernel update soon. But if you want your Archos working now, you can install the 2.6.39 kernel from this ppa:
 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")
 
If you want to enable that ppa and don't know how, post back and I'll take you through it.

I leave on vacation in under a month and this is just the occasion I purchased the MP3 player for, so there is some level of haste in solving my issue, yes.

I opened the link and haven't a clue what any of it means. I'm fairly computer savvy and I'm getting an AS in IT in just two weeks, but this is beyond my level of expertise. Your assistance is greatly appreciated!

> **coffeecat said:**
> 
Second question: did you, by chance, install the app "usbmount" from the repositories? Or any app which purports to help with USB mounting? If so, uninstall it/them now. There are several such 3rd-party apps which cause more problems than they allegedly solve. USB automounting works out-of-the-box in Ubuntu except when there is a specific bug for a specific piece of hardware. as I have just described.
 
I have _not_ installed any third-party usb mounting tools. I didn't even know they existed and didn't look for them, because as you mentioned, Ubuntu has been fastastic until this point with recognizing and mounting everything I've thrown at it.

One last question, will this kernel solution fix my issue with permissions as well? I don't see how it would, but I don't want that issue to be forgotten.

Thank you so much! :D

---

### Post by coffeecat on 2011-06-10
First thing I'll say is that when I plug my Archos in, the output of dmesg (real-time messages from the kernel) recognises something new as sdc (I already have a second drive, sdb), but with errors and then the system does not recognise the existence of sdc, and a similar mount command to yours gives me the error: "special device /dev/sdc1 does not exist". I suspect, therefore, that since you can mount your Archos from the terminal, yours is being handled differently from my Archos Vision and that the bug report I cited may not be relevant after all.

Before you do anything else, plug your Archos in, open a terminal and post the output of these two commands:

```
dmesg | tail
sudo fdisk -lu
```If you highlight the terminal output and right-click, you can copy it into the clipboard for pasting into your post.

However, installing the newer kernel will not do any damage to your system and it still might just help with this issue. The one advantage of upgrading a kernel is that you are not in fact upgrading the exising kernel; you are simply installing a newer one and the old one is still usable.

To enable the kernal-ppa repository, from a terminal:

```
sudo add-apt-repository ppa:kernel-ppa
sudo apt-get update
```If you now...

```
sudo apt-get upgrade
```... you should be offered the 2.6.39 kernel for installation. Or, instead of running apt-get upgrade, you can open Synaptic and click on the "Mark All Upgrades" button, and then "Apply". You will need to reboot after the new kernel has been installed.

If, by chance, the new kernel brings its own problems with it (unlikely), you can still boot into the 2.6.38 kernel by choosing "Previous Linux Versions" from the grub menu. If you do have problems with the 2.6.39, post back and I can tell you how to uninstall it and disable to kernel-ppa repository.

> **itz_speld_rong said:**
> I have not installed any third-party usb mounting tools.

I'm glad to hear it! :) A lot of people make that mistake.

> **itz_speld_rong said:**
> One last question, will this kernel solution fix my issue with permissions as well? I don't see how it would, but I don't want that issue to be forgotten.

That I don't know. Since your Archos Key is being handled differently from my Vision, this may be a different issue that needs investigating separately. The dmesg and fdisk commands are a start, so post those outputs. If you want to defer installing the newer kernel until we've looked at those, that's fine. Or if you want to go ahead and install the new kernel to see if it helps, that's fine too. As I said, installing the newer kernel is reversible if necessary.

---

### Post by itz_speld_rong on 2011-06-11
> **coffeecat said:**
> 
Before you do anything else, plug your Archos in, open a terminal and post the output of these two commands:

```
dmesg | tail
sudo fdisk -lu
```If you highlight the terminal output and right-click, you can copy it into the clipboard for pasting into your post.
```

dmesg | tail
[ 4061.086412] sd 6:0:0:0: [sdb] Write Protect is off
[ 4061.086418] sd 6:0:0:0: [sdb] Mode Sense: 3b 00 00 00
[ 4061.087158] sd 6:0:0:0: [sdb] No Caching mode page present
[ 4061.087164] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 4067.091910] sd 6:0:0:0: [sdb] No Caching mode page present
[ 4067.091917] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 4067.093167]  sdb: sdb1
[ 4067.096178] sd 6:0:0:0: [sdb] No Caching mode page present
[ 4067.096185] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 4067.096190] sd 6:0:0:0: [sdb] Attached SCSI removable disk
``````

sudo fdisk -lu
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001c65c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   600565759   300281856   83  Linux
/dev/sda2       600567806   625141759    12286977    5  Extended
/dev/sda5       600567808   625141759    12286976   82  Linux swap / Solaris


```

I suppose I shall take your first instructions and wait for a reply from you before moving forwards with the new kernel installation.

---

### Post by coffeecat on 2011-06-11
Interesting outputs. Your dmesg shows that the device is being assigned sdb, but there is no sdb seen by fdisk.

Compare with my dmesg when I attach my Archos Vision using the 2.6.38 kernel:

```
$ dmesg | tail
[   51.980096] usb 2-3: USB disconnect, address 2
[   51.980155] sd 6:0:0:0: [sdc] No Caching mode page present
[   51.980160] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[   51.980424] sd 6:0:0:0: [sdc] READ CAPACITY failed
[   51.980426] sd 6:0:0:0: [sdc]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[   51.980429] sd 6:0:0:0: [sdc] Sense not available.
[   51.980431] sd 6:0:0:0: [sdc] Assuming Write Enabled
[   51.980454] sd 6:0:0:0: [sdc] Incomplete mode parameter data
[   51.980456] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[   51.980458] sd 6:0:0:0: [sdc] Attached SCSI removable disk
```Mine is seen as sdc and like with yours, fdisk does not list it. My dmesg is a bit more blood-curdling than yours, but we both get the  "No Caching mode page present" message. Compare with dmesg after a healthy mount of a USB flash drive:

```
$ dmesg | tail
[22940.680883] scsi 6:0:0:0: Direct-Access     SanDisk  Cruzer Micro     8.01 PQ: 0 ANSI: 0 CCS
[22940.682415] sd 6:0:0:0: Attached scsi generic sg3 type 0
[22940.683663] sd 6:0:0:0: [sdc] 7856127 512-byte logical blocks: (4.02 GB/3.74 GiB)
[22940.684239] sd 6:0:0:0: [sdc] Write Protect is off
[22940.684250] sd 6:0:0:0: [sdc] Mode Sense: 45 00 00 08
[22940.684257] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[22940.688276] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[22940.690080]  sdc: sdc1
[22940.693265] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[22940.693279] sd 6:0:0:0: [sdc] Attached SCSI removable disk
```No "No Caching mode page present" message this time. Tbh I don't know what it means but I've seen it in posted dmesg outputs where there was failure of USB mounting. 

There are differences in the dmesg outputs between yours and mine and I get a different error  if I try to mount mine from the terminal. Nevertheless, in your situation I would try installing the 2.6.39 kernel and seeing if that helps. You won't lose anything and it's quite safe to install the newer kernel because the 2.6.38 won't be touched and will still be available if necessary. And it's an easy task to uninstall the 2.6.39 kernel and disable the ppa repository if you need to. I would suggest trying the 2.6.39 kernel and seeing if that helps. No guarantees, but I would be interested in the result.

I've described the method in my last post. If you 'sudo apt-get upgrade' at the last step it offers a kernel upgrade but doesn't specify the version. If you use Synaptic it specifically states that it will install the 2.6.39 kernel.

---

### Post by coffeecat on 2011-06-11
Just for the record: I'm now rebooted into Natty using the 2.6.39 kernel and after plugging in my Archos (which gets mounted OK), dmesg now gives me:

```
$ dmesg | tail
[   51.001160] sd 6:0:0:0: Attached scsi generic sg3 type 0
[   51.004317] sd 6:0:0:0: [sdc] 16025600 512-byte logical blocks: (8.20 GB/7.64 GiB)
[   51.004321] sd 6:0:0:0: [sdc] Assuming Write Enabled
[   51.004322] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[   51.005690] sd 6:0:0:0: [sdc] Assuming Write Enabled
[   51.005693] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[   51.006694]  sdc:
[   51.007693] sd 6:0:0:0: [sdc] Assuming Write Enabled
[   51.007696] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[   51.007699] sd 6:0:0:0: [sdc] Attached SCSI removable disk

```

---

### Post by itz_speld_rong on 2011-06-11
> **coffeecat said:**
> Just for the record: I'm now rebooted into Natty using the 2.6.39 kernel and after plugging in my Archos (which gets mounted OK), dmesg now gives me:

```
$ dmesg | tail
[   51.001160] sd 6:0:0:0: Attached scsi generic sg3 type 0
[   51.004317] sd 6:0:0:0: [sdc] 16025600 512-byte logical blocks: (8.20 GB/7.64 GiB)
[   51.004321] sd 6:0:0:0: [sdc] Assuming Write Enabled
[   51.004322] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[   51.005690] sd 6:0:0:0: [sdc] Assuming Write Enabled
[   51.005693] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[   51.006694]  sdc:
[   51.007693] sd 6:0:0:0: [sdc] Assuming Write Enabled
[   51.007696] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[   51.007699] sd 6:0:0:0: [sdc] Attached SCSI removable disk

```

I wish I could say I understand the entire output. I'm not sure why it looks so repetitive, is that listing the different interfaces?

 I guess you're saying I should install the new kernel? Haha.

I see what you're saying about the fdisk output though. It doesn't show the 4G Archos being attached.

---

### Post by itz_speld_rong on 2011-06-12
Okay. I ran the commands. To the extent of my knowledge, the new kernel has been installed (though I was surprised it didn't require a reboot :P)

I just plugged it in to no avail, so I'm going to reboot anyway.



Edit: I'll just edit this post instead of making another. >_<

After the reboot, still no mount. I ran those commands again: 

```
$ dmesg | tail
[   74.578594] sd 7:0:0:0: [sdb] Write Protect is off
[   74.578598] sd 7:0:0:0: [sdb] Mode Sense: 3b 00 00 00
[   74.579331] sd 7:0:0:0: [sdb] No Caching mode page present
[   74.579335] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[   80.583228] sd 7:0:0:0: [sdb] No Caching mode page present
[   80.583235] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[   80.584465]  sdb: sdb1
[   80.587843] sd 7:0:0:0: [sdb] No Caching mode page present
[   80.587850] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[   80.587856] sd 7:0:0:0: [sdb] Attached SCSI removable disk
```And THIS looks much better: 
```
sudo fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001c65c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   600565759   300281856   83  Linux
/dev/sda2       600567806   625141759    12286977    5  Extended
/dev/sda5       600567808   625141759    12286976   82  Linux swap / Solaris

Disk /dev/sdb: 4053 MB, 4053794816 bytes
8 heads, 32 sectors/track, 30928 cylinders, total 7917568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x221e5780

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     7917567     3958768    b  W95 FAT32

```

---

### Post by coffeecat on 2011-06-12
> **itz_speld_rong said:**
> Okay. I ran the commands. To the extent of my knowledge, the new kernel has been installed (though I was surprised it didn't require a reboot :P)

You do need a reboot after installation of a new kernel and I'm surprised that you weren't prompted. Sometimes the only prompt is that the shutdown switch at top right goes red.

Let's make sure the 2.6.39 kernel has been installed properly and that you are booting into it. Firstly, your grub menu entry should say "Ubuntu, with Linux 2.6.39-0-generic". Once you've booted up, post the terminal output of:

```
uname -a
```If you are running the 2.6.39 kernel and the Archos is still not automounting I have an alternative terminal command for mounting which would be worth trying in view of the different fdisk output, but let's see whether the 2.6.39 kernel has installed first.

---

### Post by itz_speld_rong on 2011-06-12
```
$ uname -a
2.6.38-8-generic-pae #42-Ubuntu SMP Mon Apr 11 05:17:09 UTC 2011 i686 i686 i386 GNU/Linux
```From my understanding, the version of kernel I'm using is an older version that was installed April 11th, correct?

Should I try these three commands again?
 
```
sudo add-apt-repository ppa:kernel-ppa 
sudo apt-get update 
sudo apt-get upgrade
```

---

### Post by itz_speld_rong on 2011-06-12
So I scrolled up and remembered what you said about the "mark all upgrades" button in the SPM. I did that and it asked me to reboot. 

```
uname -a
Linux -laptop 2.6.39-0-generic-pae #5~20110427-Ubuntu SMP Wed Apr 27 18:53:48 UTC 2011 i686 i686 i386 GNU/Linux

```

I will give you the dmesg and fdisk report as soon as I get back. I literally have to run to get to work on time! (I'm actually enjoying all this learning!)

---

### Post by coffeecat on 2011-06-12
Yes. You're using the 2.6.38 kernel which is the default 11.04 one. I don't understand how you do not have the 2.6.39 kernel if you followed the steps I gave you before. Don't try to run the add-apt-repository command again - yet. I want to see if it ran properly the first time.

Open Synaptic. Go to Settings > Repositories > Other Software tab. Are there two lines with "deb http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu"? Are they ticked?

If yes, close the Software Sources window and click on Reload in the main Synaptic window. Now click on "Mark all Upgrades". Are 2.6.39 packages listed in the packages to be installed? If yes, click on Apply and when the update has been done, reboot.

If "deb http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu" is not listed in Software Sources, close Synaptic and do only the first two of those commands you have posted. When the second has finished, re-open Synaptic and click on "Mark all Upgrades". Hopefully now the 2.6.39 packages will be listed and you can install them. Then reboot.

---

### Post by coffeecat on 2011-06-12
> **itz_speld_rong said:**
> So I scrolled up and remembered what you said about the "mark all upgrades" button in the SPM. I did that and it asked me to reboot. 

```
uname -a
Linux -laptop 2.6.39-0-generic-pae #5~20110427-Ubuntu SMP Wed Apr 27 18:53:48 UTC 2011 i686 i686 i386 GNU/Linux

```I will give you the dmesg and fdisk report as soon as I get back. I literally have to run to get to work on time! (I'm actually enjoying all this learning!)

Right, OK, ignore my last post - we posted together. You activated the ppa repo, but forgot to install its packages. :wink: I'm waiting with bated breath to see if the -39 kernel helps!

**EDIT**: it's about 10.00pm here, so if you're running for work, you must be in a different time-zone or doing night-shift. So it seems as though I won't hear the result of plugging in the Archos until after I get up tomorrow morning in this time-zone. I think I'll keep on breathing until then. :p

---

### Post by itz_speld_rong on 2011-06-12
> **coffeecat said:**
> Right, OK, ignore my last post - we posted together. You activated the ppa repo, but forgot to install its packages. :wink: I'm waiting with bated breath to see if the -39 kernel helps!

**EDIT**: it's about 10.00pm here, so if you're running for work, you must be in a different time-zone or doing night-shift. So it seems as though I won't hear the result of plugging in the Archos until after I get up tomorrow morning in this time-zone. I think I'll keep on breathing until then. :p

Haha. I'm rocking the -5 Eastern Standard. I'm 5 hours behind you. :P

```
$ dmesg | tail
[ 1092.659430] sd 6:0:0:1: [sdc] Sense not available.
[ 1092.659438] sd 6:0:0:1: rejecting I/O to offline device
[ 1092.659444] sd 6:0:0:1: [sdc] Write Protect is off
[ 1092.659449] sd 6:0:0:1: [sdc] Mode Sense: 00 00 00 00
[ 1092.659454] sd 6:0:0:1: [sdc] Assuming drive cache: write through
[ 1092.659717] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[ 1092.661469] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1092.662707]  sdb: sdb1
[ 1092.665214] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1092.665222] sd 6:0:0:0: [sdb] Attached SCSI removable disk

``````
$ sudo fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001c65c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   600565759   300281856   83  Linux
/dev/sda2       600567806   625141759    12286977    5  Extended
/dev/sda5       600567808   625141759    12286976   82  Linux swap / Solaris

Disk /dev/sdb: 4053 MB, 4053794816 bytes
8 heads, 32 sectors/track, 30928 cylinders, total 7917568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x221e5780

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     7917567     3958768    b  W95 FAT32
```And it still didn't mount!  >_<

Thanks again for helping me!

---

### Post by coffeecat on 2011-06-13
> **itz_speld_rong said:**
> And it still didn't mount!  >_<

That's with the 2.6.39 kernel? That's disappointing. However, there is one ray of sunshine. The "No Caching mode page present" messages have gone from your dmesg output - which must be healthier. Try this from a terminal while running the 2.6.39 kernel:

```
udisks --mount /dev/sdb1
```

Don't run the 'sudo mount...' command first because that will interfere.

If that works, for interest try it also when booted into the 2.6.38 kernel (you can do this from the "Previous Linux Versions" options in the grub menu).

---

### Post by itz_speld_rong on 2011-06-13
```
$ udisks --mount /dev/sdb1
Cannot stat device file /dev/sdb1: No such file or directory

```Upon first finding out how to access the Grub Menu (I'm learning A LOT), I then selected the -28

```
udisks --mount /dev/sdb1
Mounted /org/freedesktop/UDisks/devices/sdb1 at /media/ARCHOS Key
```


Still no permissions to touch it though. I'm also not sure why this is working in the older kernel but not the new one. >_<

---

### Post by coffeecat on 2011-06-13
The grub menu must be hidden - I hadn't anticipated that. I thought it would  reveal when there is more than one kernel. I presume you're having to press the shift key at just the right moment.

This is disappointing. Boot into the -28 kernel and mount the Archos with the udisks command. Now post the output of:

```
cat /etc/mtab
```That'll show us what  permissions the Archos has been mounted with. I suspect you may need to use a root nautilus to access it, but let's have a look at that output first.

I'll let you know how to uninstall the 2.6.39 kernel in due course as it doesn't look as though it's going to be of any use to you, but let's see if we can resolve the Archos mounting issue as best we can first.

---

### Post by itz_speld_rong on 2011-06-13
```
$ cat /etc/mtab
/dev/sda1 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/eli/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=eli 0 0
/dev/sdb1 /media/ARCHOS\040Key vfat rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec 0 0

```

And yes, the "shift" key did the trick. :)

---

### Post by coffeecat on 2011-06-13
That's extraordinary:

> **itz_speld_rong said:**
> ```
/dev/sdb1 /media/ARCHOS\040Key vfat rw,nosuid,nodev,uhelper=udisks,[COLOR=Red]uid=1000,gid=1000[/COLOR],shortname=mixed,dmask=0077,utf8=1,showexec 0 0

```

Those UID and GID values should be giving you unrestricted access. This is very perplexing. When you open a nautilus browser and try to view inside the Archos filesystem, what is the exact error message?

---

### Post by itz_speld_rong on 2011-06-13
> **coffeecat said:**
> That's extraordinary:



Those UID and GID values should be giving you unrestricted access. This is very perplexing. When you open a nautilus browser and try to view inside the Archos filesystem, what is the exact error message?

Time out! I did something stupid. I right-clicked the mounted usb icon on my desktop and went to properties and looked at the "permissions" tab and then told you I still couldn't access it.

I just put a folder of songs on there and it seemed to go on flawlessly!


Question: What changed? I don't understand. I'm using the old kernel. 

Secondly: Auto-mount a possibility here? I guess I could slap that command in terminal every time I want to edit the player, but it would be a bit easier if it decided to act like everybody else and just mount!

---

### Post by itz_speld_rong on 2011-06-13
Also, if I right click it and select "Safely Remove," the I get the following message.

[IMG]http://i263.photobucket.com/albums/ii140/freakspazzatazz/ErrorMsgee.jpg[/IMG]
Sorry if it's a little small and blurry. >_<

---

### Post by coffeecat on 2011-06-13
What changed? Eerrrr... I'm getting mightily puzzled here. :-k

Whatever, if the udisks command is working with the 2.6.38 kernel, let's build on that. I don't know a way of automounting it short of adding an entry to fstab, but I'm not sure that will work. The most elegant solution I can think of is to create a custom launcher with that udisks command.

Right-click on the desktop and choose "Create Launcher". Put whatever you want in the Name and Comment fields, and for command:

```
udisks --mount /dev/sdb1
```The icon is a bit nondescript, so if you have a suitable icon, put it in a suitable place, click on the icon in the create launcher window and choose your own. Once you've created the desktop launcher, you can drag it into the -um - launcher (dock!) and then delete the desktop one if you want.

I suggest you try using both kernels again in case you missed something and the 2.6.39 would be useful. If not, I'll post details for disabling the ppa and removing the 2.6.39 kernel. I've been doing some testing on my test machine and I've found that the usually recommended ppa-purge failed to downgrade the kernel. No matter, you can do everything in Synaptic.

---

### Post by itz_speld_rong on 2011-06-13
> **coffeecat said:**
> 
I suggest you try using both kernels again in case you missed something and the 2.6.39 would be useful. If not, I'll post details for disabling the ppa and removing the 2.6.39 kernel. I've been doing some testing on my test machine and I've found that the usually recommended ppa-purge failed to downgrade the kernel. No matter, you can do everything in Synaptic.

Okay. I'll switch back to the -39 and give my little launcher a go. (I threw it up on the panel up top.)


Edit: The following was in the exact same terminal.
```
$ udisks --mount /dev/sdb1
Mounted /org/freedesktop/UDisks/devices/sdb1 at /media/ARCHOS Key
$ uname -a
Linux elis-laptop 2.6.39-0-generic-pae #5~20110427-Ubuntu SMP Wed Apr 27 18:53:48 UTC 2011 i686 i686 i386 GNU/Linux
```

Looks like I can keep my  2.6.39!

I'm going to try to grab 2 hrs of sleep... ](*,)

This entire operation has been a success. I couldn't thank you enough, not only for your time and assistance, but for the gained knowledge.

 I'll check back sometime tomorrow when my head is slightly clearer. Maybe we can work on that "Unable to stop drive" error I get when I physically remove the Archos (posted a pic of the error message in a previous post above). 

Thanks again. :D

---

### Post by itz_speld_rong on 2011-06-14
Alrighty, I just got back from a job with my new MP3 player! 

I guess that error isn't a big issue at all. It safely removes the device, it just throws the error message up when I physically pull it out of the port. I'll live with it. :D

Thank you so much coffee! I guess this thread is officially dead... :D

---

### Post by coffeecat on 2011-06-14
I'm glad things are working more-or-less, but not as well as I had hoped with the 2.6.39 kernel. Obviously the Archos Key is sufficiently differently from the Vision for that not to work in the same way.

I'm a little nervous of that unable to stop drive error you are getting and apologies for not responding to it before. If the message is not spurious and it is really not unmounting the device properly then you risk filesystem corruption every time you pull the USB plug out. This following is not as elegant as right-clicking and "safely remove", but try these from a terminal:

```
udisks --unmount /dev/sdb1
```and/or 

```
sudo umount /dev/sdb1
```Try them both. By the way, that really is u**n**mount for the usdisks command and umount (missing n) for the umount command. Just to keep you on your toes. :wink:

Also - one other thing I am slightly uneasy about. Occasionally security upgrades will come through for the 2.6.38 kernel, but I'm not sure whether this will happen for the 2.6.39 kernel. We're still on 2.6.39.0, whereas Oneiric alpha got up to 2.6.39.3 before the kernel was replaced with the newest 3.0.0 one. Perhaps the 39.3 kernel is unsuitable for Natty, but I still have a question mark in my mind about the ppa version of the 2.6.39 kernel.

For the record, therefore, this is how to uninstall the 2.6.39 kernel if you want to. An aside - I discovered why your system didn't install the 2.6.39 kernel at first. It's a strange quirk I discovered when I installed and then uninstalled the ppa kernel on my test rig. For some reason I don't understand, "apt-get upgrade" held back the ppa kernel packages whereas Synaptic installed them quite happily. Whatever, this is how to disable the kernel-ppa repository and uninstall the 2.6.39 kernel.

The terminal command "sudo ppa-purge -d natty kernel-ppa" (if you have the ppa-purge package installed) *should* do both. On my system it said it had, but the 2.6.39 kernel remained resolutely in place. Perhaps kernels are an exception. So, instead, open Synaptic, and Settings > Repositories > Other Software tab. Simply untick the two kernel-ppa lines. Now close the Software Sources window and ignore the "click on reload button" message for now. Do a search in Synaptic with the string '2.6.39' and you'll see 3 packages with a green installed box by them. Right-click on these > Mark for complete removal, and then click on the Apply button. After the system has uninstalled them the switch icon top-right should have gone red prompting a reboot, but before you do so, click on the reload button to refresh the package metadata. Now reboot and you should see only the 2.6.38 kernel in the grub menu.

---

### Post by itz_speld_rong on 2011-06-14
Both
```
udisks --unmount /dev/sdb1
sudo umount /dev/sdb1
``` 
Allowed me to eject the device without errors.

---

### Post by coffeecat on 2011-06-14
That's good. Either one is probably safer than relying on the right-click -> safely remove considering the error message you get with that. You could always make another launcher for "udisks --unmount" if you want.

Good luck with that. I have the thread subscribed so if you have any other points to raise I'll be notified if you post. :)

---

### Post by coffeecat on 2011-07-14
@itz_speld_rong, I don't know whether you're still following this thread but if you are you may want to know that the recently released update to the 2.6.38 kernel (2.6.38-10) solves the mounting problem for my Archos Vision. It is possible that it also has a fix for your Archos Key problem more satisfactory than the one we worked out.

However, if you have the PPA 2.6.39-0 kernel installed, the system will not update your 2.6.38 kernel to the -10 version automatically. If you want to try the 2.6.38-10 kernel post back and I'll give you some pointers.

---

