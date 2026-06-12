---
title: "LiveCD problems on Lenovo Thinkpad R61"
date: 2007-06-15
forum: Hardware &amp; Laptops
---

### Post by WebDrake on 2007-06-15
Hello all,

I'm writing this from my new Lenovo ThinkPad R61, currently running Windows Vista Business.  It's a lovely little machine apart from one thing---it seems to be allergic to Linux in all its forms.

The latest distributions---(K)ubuntu Feisty and Fedora 7---suffer from the problem described at length in the following threads:
[http://ubuntuforums.org/showthread.php?t=415009](http://ubuntuforums.org/showthread.php?t=415009)
[http://ubuntuforums.org/showthread.php?t=421588](http://ubuntuforums.org/showthread.php?t=421588)

However, the workarounds do not work, resulting in an error described shortly.  Earlier distros such as Edgy and Dapper do not have the tty problem described above but still suffer the latter.

In either case---an earlier distro or the use of the workaround---when booting from the LiveCD, I wind up in a situation with error messages such as the following occurring repeatedly:

[number.number] Buffer I/O error on device hda, logical block 107426
[number.number] Buffer I/O error on device hda, logical block 107427
[number.number] Buffer I/O error on device hda, logical block 107428
[number.number] Buffer I/O error on device hda, logical block 107429
   etc. etc.
[number.number] VFS: brebe: trying to free free buffer
[number.number] SQUASHFS error: sb_bread failed reading block 0x33944
[number.number] SQUASHFS error: Unable to read fragment cache block [ce48b44]
[number.number] SQUASHFS error: Unable to read page, block ce48b44, size 858
[number.number] Buffer I/O error on device hda, logical block 107426
  etc. etc.

Evidently there is some issue with the hard disk---perhaps because it is a SATA drive?---which all the distros are having problems with.

Does anyone have any advice what to do here?

Many thanks,

     -- Joe

---

### Post by WebDrake on 2007-06-15
To add to the above, I tried booting with a Sabayon Linux 3.3 livecd, and noted the following at boot:

[     6.499000]  parkbd:  no such parport
[     7.412000]  specify port
Activating mdev
Activating Device-Mapper RAID(s)
No RAID disks
Loading unionfs module
Mounting ramdisk to /memory for unionfs support
Attempting to mount media:- /dev/sda
Attempting to mount media:- /dev/sda1
Attempting to mount media:- /dev/sda2
No bootable medium found.  Waiting for new devices
Attempting to mount media:- /dev/sda
Attempting to mount media:- /dev/sda1
Attempting to mount media:- /dev/sda2
umount: Couldn't umount /newroot: Invalid argument
!! Could not find CD to boot, something else needed!
Determining root device...
The root block device is unspecified or not detected
Please specify a device to boot, or "shell" for a shell...
(boot) ::

... the last line being a command prompt.

---

### Post by racer7890 on 2007-06-21
Try booting with the all-generic-ide boot option. Probably would cause a performance penalty but may work for you.

Let us know what happens as I am interested in this notebook as well.

---

### Post by Tobba25 on 2007-07-01
So what is going on with this laptop? I was JUST about to order one tonight, but as I am going to run Ubuntu on it, I decided to do a search on it. Just to check for any puck-ups with regards to Ubuntu.

Cannot find much about it, other than this post? Is R61 cool with the latest Ubuntu?

---

### Post by WebDrake on 2007-07-03
> **Tobba25 said:**
> So what is going on with this laptop? I was JUST about to order one tonight, but as I am going to run Ubuntu on it, I decided to do a search on it. Just to check for any puck-ups with regards to Ubuntu.

Cannot find much about it, other than this post? Is R61 cool with the latest Ubuntu?

I really should have provided an update here.

I suspect that the problem I experienced was to do with difficulties reading burned CDs.  I was able to install using a cover disk from a magazine but had to follow the process described here: [http://ubuntuforums.org/showthread.php?t=421588](http://ubuntuforums.org/showthread.php?t=421588)

I do have some current problems which I have not been able to solve:

    -- no sound (the soundcard is Intel High-Definition Audio)
    -- the screen does not turn off during a blank-screen screensaver
    -- occasionally the system hangs during boot

I don't think any of these problems are insoluble and to be honest I have not made a great effort, as right now having a working machine (emphasis on "working" ;) ) is *far* more important than any of the above.  But this may be a consideration for you.

---

### Post by ciphermonk on 2007-07-03
All of those problems have work arounds/have been solved...

[http://forums.fedoraforum.org/showthread.php?t=159516](http://forums.fedoraforum.org/showthread.php?t=159516)

---

### Post by Tobba25 on 2007-07-03
> **ciphermonk said:**
> All of those problems have work arounds/have been solved...

[http://forums.fedoraforum.org/showthread.php?t=159516](http://forums.fedoraforum.org/showthread.php?t=159516)

On that forum they discuss the T61... Makes no difference?

Anywho, I am not familiar with the body of the Ubuntu organisation. I'd like to know if I can rest assured that somewhere down the road, the R61 will be fully supported. I dont mind having some initial problems, but future prefection would be great... :-)

Please don hesitate to reply, as I am VERY eager to order this thing. My 4 year old PowerBook has done its cause.

---

### Post by ciphermonk on 2007-07-03
Yes... the same instructions should work on the R61. It's pretty much the same machine with the exception of the R61 being a bit thicker and something about the plastics being different. Same machine if you ask me. Same specs. Same chipset. Same processor.

---

### Post by Tobba25 on 2007-07-03
Probably hard to answer, but can I buy the computer with good expectations of Ubuntu working well in the future? Or does this computer contain rare non-mainstream hardware?

---

### Post by WebDrake on 2007-07-04
> **ciphermonk said:**
> All of those problems have work arounds/have been solved...

[http://forums.fedoraforum.org/showthread.php?t=159516](http://forums.fedoraforum.org/showthread.php?t=159516)

Your post on the Fedora forums doesn't refer to the screensaver/power management issue I have observed.  Does your video solution make the screen turn off as set?

---

### Post by bob_dvd on 2007-07-06
Yesterday I installed Ubuntu 7.0x Fiesty Fawn for the first time on my Lenovo R61 and it went without too much trouble. It had a problem with registering the SATA hard disk, but using modprobe piix I managed to get it to register the hard disk for install. Then I had to mount the hard disk and add piix to the modules that are autoloaded. 

I used a guide for the T61 and it was close enough to manage the install. The variations are really only about the wireless and graphics drivers. But my Intel ABG wireless card was recognised (although Ubuntu complained about the drivers a bit) and everything seems ok. I fixed the custom keys, although I have not had backlight adjustment working fully yet.

I then installed VMWare Player and had that running Vista in a VM off the native physical drive. That sucked and I am going to try installing XP instead of Windows because this is a work laptop.

Bob

---

### Post by Tobba25 on 2007-07-07
> **ciphermonk said:**
> All of those problems have work arounds/have been solved...

[http://forums.fedoraforum.org/showthread.php?t=159516](http://forums.fedoraforum.org/showthread.php?t=159516)

Hello

Is that not for Fedora then?

And I don't get it all to work. There is some difference in file endings (bz gz2 or something)... And I cant get the following code to work:

cp ../patch_analog.c alsa-driver-1.0.14/alsa-kernel/pci/hda/

---

