---
title: "USB Stick not even seen by fdisk -l"
date: 2008-09-06
forum: Hardware
---

### Post by Bridge51 on 2008-09-06
I have a big problem. I was trying to follow instructions on how to install a linux Distro on a usb stick, tried to change it a little bit so that there was an extra partition than the instructions said, and now that USB stick is not being read by my eee. The thing is, the computer can see the sda (4gb ssd), the sdb (the 16gb ssd) and my other usb stick, sdc (4gb) with no problems. It just does not see the other usb stick at all, even when i type:

sudo fdisk -l

the bad usb stick has 3 partitions on it, 2 @ ~750 meg, and a 3rd at ~14 gig. when i plug it into my windows desktop tower, it works just fine as the first 750mb partition. the partition manager in windows shows all 3 partitions, but i can't do anything to them except format the 2 smaller ones. right now i'm stuck with a 16gb usb stick that only has 750 usable, and isn't readable by my linux eeepc

I've been spinning my wheels on this since last night, please point me in the right directions

---

### Post by pytheas22 on 2008-09-06
Please remove the USB stick, plug it back in, then immediately run this command and post the output:
```

dmesg | tail
```

That should help figure out what's going on.

---

### Post by jbrown96 on 2008-09-06
It seem to be an issue with the eee. If you don't need any of the data from the drive, you can delete all the partitions in Windows (right click on My computer-->Manage-->disk management). If you do need the data, I would try a livecd on either machine (does the eee have an optical drive??) and you can copy it. 
Very strange problem.

---

### Post by Bridge51 on 2008-09-06
Here is the output of the dmesg thing

joseph@eeepc-jpn:~$ dmesg | tail
[   90.660103] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 569
[  100.962107] usb 5-2: new high speed USB device using ehci_hcd and address 4
[  101.095239] usb 5-2: configuration #1 chosen from 1 choice
[  101.097315] scsi3 : SCSI emulation for USB Mass Storage devices
[  101.098603] usb-storage: device found at 4
[  101.098618] usb-storage: waiting for device to settle before scanning
[  106.087474] usb-storage: device scan complete
[  111.687354] usb 5-2: reset high speed USB device using ehci_hcd and address 4
[  113.627295] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 574
[  120.608473] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 574
joseph@eeepc-jpn:~$


EDIT: also of note here though is that i have my other WORKING usb plugged in as well

---

### Post by Bridge51 on 2008-09-06
> **jbrown96 said:**
> It seem to be an issue with the eee. If you don't need any of the data from the drive, you can delete all the partitions in Windows (right click on My computer-->Manage-->disk management). If you do need the data, I would try a livecd on either machine (does the eee have an optical drive??) and you can copy it. 
Very strange problem.

I tried doing that, but of the three partitions, only the non-used 14 gig one even has the option to delete, and it says i can't as soon as i try to. all of the other options are greyed out as well, including the 'shrink volume'

---

### Post by pytheas22 on 2008-09-06
Thanks for the dmesg.  What happens if you unplug the stick, run this command:
```

sudo modprobe -r ehci_hcd
```

then plug the stick back in?  Does fdisk see it then?  If not, what is "dmesg | tail" after performing those steps?

---

### Post by Bridge51 on 2008-09-06
Did what you said and it didn't come up. heres the output and what i did:

joseph@eeepc-jpn:/dev$ sudo modprobe -r ehci_hcd
[sudo] password for joseph: 
joseph@eeepc-jpn:/dev$ sudo fdisk -l

Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000740f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         462     3710983+  83  Linux
/dev/sda2             463         490      224910    5  Extended
/dev/sda5             463         490      224878+  82  Linux swap / Solaris

Disk /dev/sdb: 16.1 GB, 16139354112 bytes
255 heads, 63 sectors/track, 1962 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf26d47c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1962    15759733+  83  Linux
joseph@eeepc-jpn:/dev$ dmesg | tail
[ 3113.724185] usb 4-2: configuration #1 chosen from 1 choice
[ 3113.728024] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (05e3:0505)
[ 3118.086273] usb 1-2: new full speed USB device using uhci_hcd and address 2
[ 3118.260428] usb 1-2: configuration #1 chosen from 1 choice
[ 3118.286956] scsi6 : SCSI emulation for USB Mass Storage devices
[ 3118.288745] usb-storage: device found at 2
[ 3118.288763] usb-storage: waiting for device to settle before scanning
[ 3123.279256] usb-storage: device scan complete
[ 3128.880762] usb 1-2: reset full speed USB device using uhci_hcd and address 2
[ 3143.968310] usb 1-2: device descriptor read/64, error -110
joseph@eeepc-jpn:/dev$ 


the sdb is my second hard drive, the 16 gig on the eeepc

also, thanks for continuing to help, i appreciate it

---

### Post by pytheas22 on 2008-09-06
The line from dmesg that reads:
```

device descriptor read/64, error -110
```

usually indicates some kind of problem with the hardware, like flaky connectors or electromagnetic interference (even if it works in Windows, this error can prevent Linux from mounting the device).  Generally, switching to the USB 1.1 driver (which you did using that "modprobe -r" command that I posted above) is an effective workaround, but apparently in your case it's not.

Try rebooting, then run this command again:
```

sudo modprobe -r ehci_hcd
```

and then try plugging the USB stick into all of your different USB ports.  Do you still have no luck with any of the ports, and does "dmesg" still mention the "device descriptor read/64, error -110" problem each time?

---

### Post by Bridge51 on 2008-09-06
rebooted, did the driver workaround like you said, and tried the usb in each of the ports

gives me the same 'device descriptor read/64, error -110

If it makes any difference, here are the instructions i was using the partition the drive in the first place:

[http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/](http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/)

however, i used my own logic of making a second partition just like the first, and made their 'second' partition my 3rd

I don't know what to do, it's a brand new 16 gig usb stick and i'm freakin out :-/

---

### Post by pytheas22 on 2008-09-06
I don't think that moving the partition should have hurt anything.

You may want to try wiping the drive and reformatting it as one big partition (you can use gparted: "sudo apt-get install gparted" to do so, or use Windows) just to make sure that the disk still works that way.

---

### Post by Bridge51 on 2008-09-06
I tried, it won't let me in windows disk management . and it doesn't show up in gparted

---

### Post by IntuitiveNipple on 2008-09-06
```

device descriptor read/64, error -110

```
is reported from line 2378 of drivers/usb/core/hub.c::hub_port_init()

error -110 is **ETIMEDOUT** (defined in include/asm-generic/errno.h).

That is in response to the call
```

r = usb_control_msg(udev, usb_rcvaddr0pipe(),
 USB_REQ_GET_DESCRIPTOR, USB_DIR_IN,
 USB_DT_DEVICE << 8, 0,
 buf, GET_DESCRIPTOR_BUFSIZE,
 USB_CTRL_GET_TIMEOUT
);

```
which is attempted 3 times.

The code is trying to determine the size of the descriptor message block. It appears to be trying the common 64-byte size (used by full and high speed devices, and for Windows compatibility).

Is the USB device connected directly to the PC USB ports? From what you've said I'm guessing it is, but if there's a hub between the PC and the device, try connecting directly to the device.

Usually this error is caused by a hardware fault of some kind. If it were a device on a cable the instant suggestion would be 'cable fault' but I guess the device is connected directly to the port?

What is the make and model of the device?

When the device is connected what is the output of 'lsusb'? Please capture the output and attach the resulting file "lsusb-v.log.gz" to a reply:
```
lsusb -v | gzip >lsusb-v.log.gz

```

---

### Post by Patrick_loginow on 2008-09-07
Hi,

I have been pulling my hair out all weekend with this exact problem :( 
Are you by chance using a A-Data 16GB USB key? I'm beginning to suspect that it has something to do with the key itself (Although it did work fine before I executed the format step from the same instruction set that you were following). 

Thank you,
Patrick

---

### Post by Patrick_loginow on 2008-09-07
I have uploaded the result of lsusb -v. It took a few times to get this because lsusb would freeze up sometimes depending on which of the 2 usb ports I put the key in had to move it around a few times to get it to not freeze.

Thanks,
Patrick

---

### Post by Patrick_loginow on 2008-09-07
Just a side note - thinking it might be a problem with the laptop I was using I tried this on my IBM T60 (with 3 usb ports) as well as on my wife's Dells Inspiron 5100 (with 2 usb ports) - same results both times (plugged directly into the ports - no hubs or cables or anything). 

also (another side note) when I ran the lsusb -v it wrote out the following errors to the terminal session:

"can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1) "


Thanks,
Patrick

---

### Post by kool_kat_os on 2008-09-07
did you "sudo" the command?

```
sudo lsusb -v
```

---

### Post by Patrick_loginow on 2008-09-08
Hi,

Thanks I will give that a try when I get home this evening (don't have the key with me at the moment) - I figured that since lsusb let me execute without sudo, then the verbose mode would let me execute as well but maybe not?

will keep you posted...

Thanks,
Patrick

---

### Post by IntuitiveNipple on 2008-09-08
If you see the same issue on other PCs then it looks as if the device is faulty. Despite the marketing blurb I've had several flash-memory devices go bad without much use.

---

### Post by Patrick_loginow on 2008-09-08
A friend of mine found me this thread on a different forum. 
[http://www.houseofhelp.com/forums/showthread.php?t=71249](http://www.houseofhelp.com/forums/showthread.php?t=71249)

It seems from reading this thread that the linux kernel does not like certain usb memory keys (that is just my interpretation after reading that - I have very limited knowledge of hardware stuff).

Some people had success using a windows tool called "hddtools" to reformat the entire stick as FAT32. I will try that later this evening and let you know how it goes.

Has anyone else on this forum had success with this approach?


Thanks,
Patrick

---

### Post by Bridge51 on 2008-09-08
> **Patrick_loginow said:**
> A friend of mine found me this thread on a different forum. 
[http://www.houseofhelp.com/forums/showthread.php?t=71249](http://www.houseofhelp.com/forums/showthread.php?t=71249)

It seems from reading this thread that the linux kernel does not like certain usb memory keys (that is just my interpretation after reading that - I have very limited knowledge of hardware stuff).

Some people had success using a windows tool called "hddtools" to reformat the entire stick as FAT32. I will try that later this evening and let you know how it goes.

Has anyone else on this forum had success with this approach?


Thanks,
Patrick

Anyone ever heard of this before? I looked it up, i think it's actually a music player of some sort?

Thing is, it says it needs to be put in my root directory... i got suspicious and canceled. any thoughts?

---

### Post by IntuitiveNipple on 2008-09-08
> **Patrick_loginow said:**
> A friend of mine found me this thread on a different forum. 
[http://www.houseofhelp.com/forums/showthread.php?t=71249](http://www.houseofhelp.com/forums/showthread.php?t=71249)

Reading that thread something occurs to me. I wonder if the firmware of the stick *expects* it to be formatted with FAT32/NTFS - it would explain all the scenarios described including the FAT32 + NTFS one. I'm wondering if it is keyed to the fact that they both encode a BIOS Parameter Block whereas ext3 etc, don't.

Can you get it reformatted on a Windows system and then take a backup of the first few sectors from Linux before doing anything with it, then compress them, and attach the compressed file to a reply here:
```

# set DEV to the device letter the device is given
DEV=d
dd if=/dev/sd${DEV} bs=512 count=100 of=sectors00-63.bin
gzip sectors00-63.bin

```
The compressed file will be sectors00-63.bin.gz.

---

### Post by IntuitiveNipple on 2008-09-08
I forgot the important bit! What is the make and model of the device?

---

### Post by Bridge51 on 2008-09-08
it is a 16 gig corsair voyager (rubber outside)

could you be a little more specific about those last instructions? pronouns mess me up :-p (it, mostly)

should i just type those commands at the command prompt?

---

### Post by Patrick_loginow on 2008-09-08
Hi, 

Well it worked....kinda.

So here is what I did,

1. Went to HDDGuru.com and downloaded something called "Hard Disk Low Level Format Tool 2.36 Build 1181" (AKA Spyware installation executable - just kidding - but seriously I don't vouch for these guys, it just seemed to work).
2. Installed the thing
3. Inserted the USB key and ran the tool and performed a "Low Level Format" - took about 10-15min
4. From the windows control panel went to Administrative Tools->Computer Management->Disk Management and reformted the usb as FAT32 - it churned away for a bit and then at the end it opened a window to the usb volume
5. Booted in the ubuntu live disk
6. Plugged in the usb key (oh ya forgot to say unplug the key before rebooting in step 5).
7. Now the key looked like a file system and was mounted and all that ****- which is cool
..THUS ENDS the happy part of this story.


So now I decided to try the steps again for creating a live USB key. Got to the same step as before and it did the same as before. So I guess I will have to perform another "Low level format" on the key again. :(

So let me axe you guys this?

In the forums it says that Hardy makes Live USBs redundant and that you should just install to the USB key itself. If that is the case then am I wasting my time trying to repartition with ext2 and all that - should I just run a "low level format", make it FAT32 and then install hardy right onto the thing?

Thanks,
Patrick

---

### Post by Bridge51 on 2008-09-09
Pat, I don't know why it worked or how, but that program worked.

I ran it on my usb stick, used disk management in windows to format it correctly, and it worked

Of note though: I was able to fix the '3 partition' problem before i ran this program. I was trying all of this on my home vista computer, and it didn't work. ran dism management on my xp work computer, and i was able to completely erase the hardrive, partitions and all, then reformat it, THEN run Pat's program. either way, this worked and i have a working 16 gig usb stick again :-)

Thank you so much to everyone in this post!

---

### Post by Patrick_loginow on 2008-09-09
Hi,

A question - were you able to use your 16gig key now as a liveUSB key with Hardy? If so I was wondering how you got that working?

Thanks,
Patrick

---

### Post by yani1shu on 2008-09-14
So i'm having a similar problem and hope someone here can help me. First off i don't have easy access to a M$ box so anything involving Windows isn't really an option. Here's what happens. I have two external USB hard drives,one 500Gb and a 1Tb. Both drives work fine when they are connected to my computer individually, meaning only one is plugged in at a time. So i have my 500Gb drive plugged in, heres the fdisk:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16561655

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23944   192330148+  83  Linux
/dev/sda2           23945       24321     3028252+   5  Extended
/dev/sda5           23945       24321     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d399bc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60800   488375968+   7  HPFS/NTFS



but as soon as i plug in the 1Tb drive, my 500 disappears and all that shows up is the 1Tb as /dev/sdc1. I can't find /dev/sdb1 at all. Of course, then when i unplug the 1Tb plug the 500 back in i get an able to mount error because the $logfile got corrupted so i have to delete the logfile on the500 before i can mount it. It's very frustrating, especially because i'm trying to copy files from the 500 to the 1Tb and can't connect them both to my machine. 

I can't connect the 1Tb right now to show the dmesg or fdisk with it attached, but if anyone has any ideas i would be able todo some testing tomorrow. I appreciate an suggestions.Copying the files over my network is taking forever.

---

### Post by marioitalo on 2008-10-01
I found a solution to that problem (apparently this is about the time needed to the device wake-up):
At /etc/modprobe.d/options I added the line:
options scsi_mod inq_timeout=20
Then I tried to unload and load the module(scsi_mod), but didn't work, because this option was in initrd file. So I reinstalled the package linux-image-* what forced the system to make a new initrd file and use the new configuration (of course there is a better way to do that but I didn't want to search how to), then, after a reboot, voilá, the pen drive was back to life.
I hope this help someone.

---

