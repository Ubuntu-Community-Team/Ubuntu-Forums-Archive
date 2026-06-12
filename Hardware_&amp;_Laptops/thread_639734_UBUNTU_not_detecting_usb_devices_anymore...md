---
title: "UBUNTU not detecting usb devices anymore.."
date: 2007-12-13
forum: Hardware &amp; Laptops
---

### Post by Codo on 2007-12-13
I bought a external hdd afew months ago and it worked fine from the first time i plugged it in.  Then one day i plugged it in and I could not detect it for some reason.  Also i am having issues detecting other hardware devices like my ipod and micro sd card.  I imagine there is something that can be entered in the terminal to mount and or unmount something but i am unsure where to start.  Any help would be greatly appreciated,

---

### Post by badrunner on 2007-12-13
If you have them plugged in via a hub it might be that, i've had some cheap hubs that stop working after being powered for too long, and just resetting them sometimes helps. Also, it might be as simlpe as lose cables. Try them in different ports (front/back of case etc.).

---

### Post by Codo on 2007-12-13
Yeah, lose cables were my first suspicion... I use a usb mouse on a laptop running ubuntu and the mouse works for some reason.

---

### Post by indrajeet on 2007-12-13
I faced a similar issue with my keyboard once... try re-installing your x. It did it for me

---

### Post by kaervos1024 on 2007-12-13
You should plug in your device, then post the output of entering the following command in a terminal:

> dmesg | tail

Unplug it, then enter the same command again. It should give you an indication of the usb device status and perhaps recorded errors.

Let us know and we can probably help more.

---

### Post by Codo on 2007-12-14
I entered 'dmesg | tail' in the terminal and got with the external hdd turned on and plugged in and got:

'[39970.686516] sd 2:0:0:0: [sda] Write Protect is off
[39970.686525] sd 2:0:0:0: [sda] Mode Sense: 03 00 00 00
[39970.686529] sd 2:0:0:0: [sda] Assuming drive cache: write through
[39970.687686] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[39970.688767] sd 2:0:0:0: [sda] Write Protect is off
[39970.688775] sd 2:0:0:0: [sda] Mode Sense: 03 00 00 00
[39970.688779] sd 2:0:0:0: [sda] Assuming drive cache: write through
[39970.688787]  sda: sda1
[39970.697661] sd 2:0:0:0: [sda] Attached SCSI disk
[39970.697736] sd 2:0:0:0: Attached scsi generic sg0 type 0'

When i disconnect the hdd and type the same command I get 

'[39970.686525] sd 2:0:0:0: [sda] Mode Sense: 03 00 00 00
[39970.686529] sd 2:0:0:0: [sda] Assuming drive cache: write through
[39970.687686] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[39970.688767] sd 2:0:0:0: [sda] Write Protect is off
[39970.688775] sd 2:0:0:0: [sda] Mode Sense: 03 00 00 00
[39970.688779] sd 2:0:0:0: [sda] Assuming drive cache: write through
[39970.688787]  sda: sda1
[39970.697661] sd 2:0:0:0: [sda] Attached SCSI disk
[39970.697736] sd 2:0:0:0: Attached scsi generic sg0 type 0
[40182.071985] usb 3-2: USB disconnect, address 5'

---

### Post by kaervos1024 on 2007-12-14
Sorry, "tail" didn't provide enough to see the entire results of plugging in your device, but enough to tell you how to mount it manually. 

The device is sda, and assuming you want to mount the first partition on the device, and also that you have a "Public" folder in your home directory, you could manually mount the device by:

[PHP]sudo mount /dev/sda1 /home/yourusername/Public[/PHP]
(replace yourusername with your actual user name)

This is the simplest way to mount your disk. Be aware that you won't be able to write to this disk unless you are operating with root permissions. You can start an instance of nautilus from the command line operating with root permissions by:

[PHP]sudo nautilus[/PHP]

In that instance of nautilus, you'll be able to write to this directory. 

When done, to unmount the device (for safe removal) you can do:

[PHP]sudo umount /home/yourusername/Public[/PHP]

This will let you at least get access to your devices again. 

I'm not too privy to the workings of Ubuntu's auto-mounting mechanisms. Perhaps someone else can chime in. I know it has something to do with udev, which allows for specific rules for specific devices, but just check to make sure that the udev daemon is running by:

[PHP]ps -A | grep udev[/PHP]

You should see an entry for udevd.

Otherwise, there are rules in /etc/udev/rules.d/, but I can't offer too much advice on decoding them...

---

### Post by kaervos1024 on 2007-12-14
Thinking about it, I wouldn't worry about udev too much. Try installing the following packages one by one and rebooting after each to test if your automounting returns. Let us know if one of them solves the problem... would be good info for the community. This type of problem is somewhat common (it happened to me before in a feisty install):

usbmount

autofs

pmount

---

### Post by Codo on 2007-12-14
Wow, thankyou very much :D You are very helpfull and kind.  I appreciate it alot!
Enjoy the season!

I will post my results when i get a chance here... hopefully tonight :D:guitar:

---

### Post by Codo on 2007-12-14
Greetings ,
So I entered 'sudo mount /dev/sda1 /home/yourusername/Public' in the terminal and it asked for my password and that is all.  The external hdd is still invisible.

---

### Post by Codo on 2007-12-14
ok, so i restarted my comp and turned my hdd back on after having entered 'sudo mount /dev/sda1 /home/yourusername/Public'  And I can see my hdd again!  Fecking glorious, i have been trying to get it to work for like a month now... Thanks again :D :lolflag:

---

### Post by kaervos1024 on 2007-12-15
'yourusername' was just a placeholder for your actual username... try this code verbatim:

```
sudo mkdir /media/ExtHdd0
```

```
sudo mount /dev/sda1 /media/ExtHdd0
```

This will create a new directory in the /media directory, which Ubuntu will automatically provide you links for. You should immediately see a link to ExtHdd0 appear in your "Places" menu (assuming Gnome, and not KDE). 

Then, if you run the following, you will get a root (read/write) nautilus session in your external hard drive:

```
sudo nautilus /media/ExtHdd0
```

That should cut it. Did you try to install those packages yet? I'd be curious to know if they (particularly which one) worked to fix your automounting issues.

---

### Post by Codo on 2007-12-15
Aye,  I created the new dir.  and when i run 'sudo nautilus /media/ExtHdd0' it says 'could'nt find media.  Oh wells, i can manually mount and unmount for now, but when i get another second to mess around i will.

---

### Post by ebe0 on 2007-12-17
> Thinking about it, I wouldn't worry about udev too much. Try installing the following packages one by one and rebooting after each to test if your automounting returns. Let us know if one of them solves the problem... would be good info for the community. This type of problem is somewhat common (it happened to me before in a feisty install):

usbmount

autofs

pmoun

Had a simillar problem, kinda, CD/DVD were not mounting at all. I installed these packages and now they mount !!! (automount still doesn't happen, however i'm able to mount it manually by clicking on the CD/DVD icon in Places>Computer). Thank you all.

---

### Post by lilBeat on 2007-12-17
Hi,


I have problems with my USB pen drive (My Flash from ADATA 1GB). So I followed all steps described on these 2 pages but nothing... still doesnt work.

First I did all those commands and tried to mount it as described (in my case sdb) but didnt work. First I pluged in pen drive and afterwards I took it off. So here it is.
> [ 1679.024000] sd 6:0:0:0: [sdb] Write Protect is off
[ 1679.024000] sd 6:0:0:0: [sdb] Mode Sense: 43 00 00 00
[ 1679.024000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1679.028000] sd 6:0:0:0: [sdb] 1981440 512-byte hardware sectors (1014 MB)
[ 1679.028000] sd 6:0:0:0: [sdb] Write Protect is off
[ 1679.028000] sd 6:0:0:0: [sdb] Mode Sense: 43 00 00 00
[ 1679.028000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1679.028000]  sdb: unknown partition table
[ 1679.144000] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[ 1679.144000] sd 6:0:0:0: Attached scsi generic sg2 type 0
lilbeat@ililbeat-laptop:~$ dmesg | tail
[ 1679.024000] sd 6:0:0:0: [sdb] Mode Sense: 43 00 00 00
[ 1679.024000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1679.028000] sd 6:0:0:0: [sdb] 1981440 512-byte hardware sectors (1014 MB)
[ 1679.028000] sd 6:0:0:0: [sdb] Write Protect is off
[ 1679.028000] sd 6:0:0:0: [sdb] Mode Sense: 43 00 00 00
[ 1679.028000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1679.028000]  sdb: unknown partition table
[ 1679.144000] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[ 1679.144000] sd 6:0:0:0: Attached scsi generic sg2 type 0
[ 1826.148000] usb 3-4: USB disconnect, address 6


I tried to install those 3 packages as described, with reboot after installing each. Still doesnt work

Could someone tell me what next to do? 

I really need this to work as I need to transfer work documents from home to work. I dont have dual boot.

thanks in advance.


edit:
here is what happens when try to mount now
> lilbeat@lilbeat-laptop:~$ sudo mount /dev/sdb1 /home/lilbeat/Public
mount: special device /dev/sdb1 does not exist


---

### Post by ebe0 on 2007-12-17
Have a look at this post -- [http://ubuntuforums.org/showthread.php?t=342887]("http://ubuntuforums.org/showthread.php?t=342887")
They seem to be having a similar problem  > mount: special device /dev/sdb1 does not exist  and have solved it

---

### Post by kaervos1024 on 2007-12-17
I don't think the guys in that thread referenced by ebe0 have the same problem as you. From what I can tell you should just repartition your flash drive. The problem is highlighted by this line in your dmesg:

> [ 1679.028000] sdb: unknown partition table

Due to the unknown partition table, udev does not link sdb1 (which would typically point to your first partition on the device), which results in the:

> mount: special device /dev/sdb1 does not exist

You could try using the acpi=off kernel option, but I don't think this will help your particular situation. I would copy all the data off your USB drive, and then repartition it with GParted. If you have Fuse (previously known as ntfs-3g) installed, you should be able to make the partition(s) NTFS format and get windows / linux interoperability.

If you are feeling like getting your hands dirty, you can use fdisk to delete the partition table and create a new one, and then mkfs.ntfs (mkntfs) to format it w/ NTFS.

Edit: Oh, and definitely DONT go installing LiLo instead of GRUB. Severe headaches will likely ensue, and it doesn't pertain at all to the issue at hand.

---

### Post by lilBeat on 2007-12-17
While waiting for reply I put data on a windows OS computer. Afterwards, I formated flash pen drive on that windows OS computer even twice so it can be red. It was FAT filesystem (FAT32 if I recall well) as windows OS through it format command from right click menu when selected USB pen drive offers just that option. Nothing worked. :( [IMG]http://img504.imageshack.us/img504/305/screenshotcomputerfilebgn7.png[/IMG]

ebe0
I red thread you proposed, but didn't find solution to the problem. I might understand that the actual problem is in ACPI and compiling etc. sounds to &#8220;heavy&#8221; for me. Nevertheless, thanks you for posting link to that thread as I learned a bit.

kaervos1024
Seems like you know a lot about this problems. Guess you are developer of Ubuntu. I want to thank you b/c I followed your instructions and solved my problem. Though, not following ad literam your &#8220;tutorial&#8221;. 

Here is what I have done:
I didn't try acpi=off option. 
I tried > gparted command in my console. Got the message I don't have it so I installed it with > sudo apt-get install gparted. Then I started gparted from console in GUI mode. Choosed my sdb drive, which is USB pen drive and deleted it. Then choosed New to make  a new partiotion on it and automatically it is offered to make it ext3. But there are other options, so I choosed NTFS this time. Formated it. Gparted crashed but after starting it again and selecting sdb I saw it did a job. There is NTFS on my flash pen drive. USB pen drive is mounted automaticly now and icon is shown on my desktop when inserted in USB port. I copied a file to see if it works and it is OK. File can be deleted also. [IMG]http://img504.imageshack.us/img504/5003/screenshotdevsdbgpartedkx2.png[/IMG]
[IMG]http://img520.imageshack.us/img520/2339/screenshotcomputerfilebii0.png[/IMG]
[IMG]http://img520.imageshack.us/img520/1396/screenshotdiskfilebrowscs1.png[/IMG]
 
I don't have that windows OS computer at the moment to try USB pen drive on it but I guess it should work. I will post tomorrow after I check it.

I never got to the Fuse and fdisk part. And of course, to the lilo part.

---

### Post by kaervos1024 on 2007-12-18
Glad to hear you had success lilBeat. I would avoid using FAT16 or FAT32 formats at all costs unless you have a absolute need for backwards compatibility with like Win9x or something. Your NTFS formatted USB flash drive should now work fine w/ both Windows and Linux. 

Apparently GParted doesn't need Fuse to create NTFS  partitions, or you already had it installed. Yeah, using fdisk isn't even done that much anymore since GParted is so powerful and easy to use these days. Its just an exercise in nostalgia for me... plus I like to see people do things the hard way first so they know the real nuts and bolts of things. =)

Either way, I'm happy to be of service.

Enjoy the season, mates!

---

### Post by lilBeat on 2007-12-19
Hi,

My apologies for not keeping my promise, but just now I found some time to post. I've been busy with work and some other duties.

@kaervos1024
I didn't know until now it is possible to have NTFS on flash pen drive. Actually never bothered to think about it. Now, I guess it can be anything (any file system). I used Windows until few weeks ago both on my personal computer and, of course, computer at work, and Windows OS makes FAT32 on flash as you probably know. That's why I never bothered as it just worked. Now, I'll just keep it NTFS.


There are few things I would like to mention for anybody who would have similar problem:
I put files from Windows OS computer to flash pen drive, unplugged it and it didn't get mounted. Where did I make mistake? Even though if you do this and plug pen drive into another Windows OS computer, pen drive will work on that computer. In order to get it work on Linux computer, you should “Safely remove” flash pen drive from Windows OS computer.


@kaervos1024
This might be the problem I had, actually. Now, when thinking backwards. Maybe this “safely remove thing” should be written in some tutorial like “first thing to do” before deleting, formatting etc.

So, I understand you troubled for years to learn things you know and do them in hard way. But I must be sincere and say I am really glad Linux got to the point where it is now -- easier to use. Anyway, new users will still need you and people alike when problems occur. So, feel blessed.

Enjoy holidays!

---

