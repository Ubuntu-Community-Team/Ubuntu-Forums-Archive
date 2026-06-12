---
title: "Mount error in Ubuntu"
date: 2009-04-30
forum: Hardware
---

### Post by ginjaninja405 on 2009-04-30
I have two drives on my computer, one with Ubuntu 9.04 installed on it, and the other with files like music and pictures. Now when in windows the drive with my files stored on it would function without any problems at all. But as soon as I boot into Ubuntu there is a mount error saying:

"$MFTMirr does not match $MFT(record3). Failed to mount '/dev/sda1': Input/output error NTFS is either inconsistent, or there is a hardware fault, or it's softRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows then reboot into Windows twice. The usage of the /f parameter is very important! If the device is SoftRAID/FakeRAID then first activate it and mount a different device under the /dev/mapper directory, (e.g. /dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation for more details."

I don't have windows anymore, and I knew there was nothing wrong with it when using Windows XP, Vista, and 7. Could somebody please enlighten my problem and help my solve it so I can access all my important files?
By the way, the hard drive I can't mount is the first one (and is NTFS), and the one with Ubuntu on it, is second (Ext3).

---

### Post by zeex on 2009-04-30
> **ginjaninja405 said:**
> I have two drives on my computer, one with Ubuntu 9.04 installed on it, and the other with files like music and pictures. Now when in windows the drive with my files stored on it would function without any problems at all. But as soon as I boot into Ubuntu there is a mount error saying:

"$MFTMirr does not match $MFT(record3). Failed to mount '/dev/sda1': Input/output error NTFS is either inconsistent, or there is a hardware fault, or it's softRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows then reboot into Windows twice. The usage of the /f parameter is very important! If the device is SoftRAID/FakeRAID then first activate it and mount a different device under the /dev/mapper directory, (e.g. /dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation for more details."

I don't have windows anymore, and I knew there was nothing wrong with it when using Windows XP, Vista, and 7. Could somebody please enlighten my problem and help my solve it so I can access all my important files?
By the way, the hard drive I can't mount is the first one (and is NTFS), and the one with Ubuntu on it, is second (Ext3).

Hi, 

I have seen this error usually when computer is switched of either in the middle of startup or shutdown. Then it doesn't mount NTFS drives in ubuntu. Going back to windows and running chkdsk <drive> /f (example chkdsk e: /f) solves all the problem. Since you don't 've windows anymore. You need to install ntfs tools in ubuntu

```
$ sudo apt-get install ntfsprogs
```

This package has a nice collection of tool for ntfs drives. To fix your problem let's say your drive is /dev/sda2 

```
$ sudo ntfsfix /dev/sda2
```

This should fix the disk. Reboot after this. 

If it still doesn't work use a Live CD like Hiren's boot CD mainly for DOS or there are a lot of other here is a [wiki list]("http://en.wikipedia.org/wiki/List_of_LiveDistros#Rescue_and_Repair_LiveDistros") of rescue n repair live CDs. Try the one you like :) Hiren's boot CD has chkdsk utility. System Rescue CD is another nice rescue CD.

---

### Post by ginjaninja405 on 2009-04-30
THANK YOU SO MUCH! :D x

---

### Post by shantiq on 2009-12-17
[COLOR=Blue][B]:):)thanx you zeex i am really grateful to you since i have all my work on my external

merry christmas 2009
[/B][/COLOR]

---

### Post by aquamammal on 2010-01-19
Thank you so much. It works like a charm.

---

### Post by groperofeuropa on 2010-05-05
zeex, this resolved the error for my external WD10EA-S drive between Ubuntu10.04 and Windows7. Its had the same problem before and I had to recover raw data when i couldnt find a solution. I lost 300G and you've prevented me losing another terabyte. 
If you would allow it, I will grow a womb to bear your child. Alternately, accept my heartfelt thanks.

---

### Post by bob_smith444 on 2010-09-24
Thanks for the information about ntfstools. I've had this problem before and I fixed it by taking the drive out of the Ubuntu machine and putting it into a Windows machine and running chkdsk /f on it. So nftstools is a time saver. My problem is that I'm using SyncBack Pro running under Win7 to backup to my 1TB drive on my Ubuntu 10.04 box. The backup process seems to be changing either $MFTMirr or $MFT so that the partition fails to mount. The drive is divided into two partitions and the second is not affected. Any suggestions on how to stop this from repeating?

---

### Post by cjames1968 on 2010-09-25
add me to the list of supplicants.  Thank you jedi master

---

### Post by karbonatok on 2010-12-23
thx, zeex

---

### Post by yabu on 2011-04-10
Thanks so much zeex, had built a local Lucid Mirror on the USB drive, computer hung while shutting down, can get back to syncing the mirror:-)

yabu@PostSFX:~$ sudo ntfsfix /dev/sdf1
[sudo] password for yabu: 
Mounting volume... FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... FAILED
Correcting differences in $MFTMirr record 0...OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
yabu@PostSFX:~$

---

### Post by DjBuRRo on 2011-05-01
Thanks zeex!! you really solved my problem.

---

### Post by bombaclaaddubplate on 2011-08-04
Thank You zeex =D> Worked for me.

---

### Post by catsandogs on 2011-12-18
Anybody know if it's possible to just erase my NTFS partition?

I have a new Toshiba Canvio plus 3.0 and all I wanna do is format it to ext2. Gparted was unable to format it, but I did manage to delete the Windows software later. Now the drive won't even mount, though it is recognized as sdb1. Even my Ubuntu machine is telling me I have to use Windoze to solve this problem, but I don't have Windoze, and anyway, all I want to do is format. Does softRAID or fakeRAID hardware make formatting impossible?

EDIT: Whatever the problem was, I fixed it by plugging into a Macbook and formatting the drive to one giant MSdos partition. Now it works perfectly on my Ubuntu box and I'm ready to format with Gparted. Ext2, I guess. Any advice?

---

### Post by monolith9000 on 2011-12-28
Thank You.

---

### Post by nimonika on 2012-06-29
Thanks a lot!! Your post saved my day....

Monika 
> **zeex said:**
> Hi, 

I have seen this error usually when computer is switched of either in the middle of startup or shutdown. Then it doesn't mount NTFS drives in ubuntu. Going back to windows and running chkdsk <drive> /f (example chkdsk e: /f) solves all the problem. Since you don't 've windows anymore. You need to install ntfs tools in ubuntu

```
$ sudo apt-get install ntfsprogs
```

This package has a nice collection of tool for ntfs drives. To fix your problem let's say your drive is /dev/sda2 

```
$ sudo ntfsfix /dev/sda2
```

This should fix the disk. Reboot after this. 

If it still doesn't work use a Live CD like Hiren's boot CD mainly for DOS or there are a lot of other here is a [wiki list]("http://en.wikipedia.org/wiki/List_of_LiveDistros#Rescue_and_Repair_LiveDistros") of rescue n repair live CDs. Try the one you like :) Hiren's boot CD has chkdsk utility. System Rescue CD is another nice rescue CD.

---

### Post by yashdv on 2012-12-30
Zeex's solution did the job.
To find your drive use "sudo fdisk -l" command.

---

### Post by coffeecat on 2012-12-30
> **yashdv said:**
> Zeex's solution did the job.

Except that with recent versions of Ubuntu, you should **not** install ntfsprogs. The ntfs-3g package, which is installed by default, includes the functionality previously provided by ntfsprogs. Indeed with 11.10 it will uninstall the ntfs-3g driver. The advice was good when posted in 2009, but time has moved on, some things have changed and this thread has been necromanced too often.

Thread closed.

---

