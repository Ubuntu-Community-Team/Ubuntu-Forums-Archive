---
title: "Mounting external USB HP 8200e"
date: 2005-03-15
forum: Hardware &amp; Laptops
---

### Post by endless on 2005-03-15
I have this old external HP USB CDR/RW drive and I would like to use it in Ubuntu. So I plug in the USB and the thing gets recognized correctly, because dmesg |tail gives:

usb 1-3: new full speed USB device using ohci_hcd and address 2
scsi2 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 2
usb-storage: waiting for device to settle before scanning
  Vendor: HP        Model: CD-Writer+ 8200e  Rev: 0001
  Type:   Direct-Access                      ANSI SCSI revision: 00
Attached scsi removable disk sda at scsi2, channel 0, id 0, lun 0
usb-storage: device scan complete

So I figure the device is recognized by Ubuntu. So far so good, but now when I try to mount the drive after putting a disk in and typing: (after creating /media/usb-cdrom/

sudo mount -t iso9660 /dev/sda /media/usb-cdrom/
mount: No medium found

There is nothing wrong with the CD in the drive, it's a data cd, and I can read it from the drive when I boot in my deserted win XP. Anyone have an idea what I am doing wrong, or how to solve this? Thanks in advance!

---

### Post by endless on 2005-03-15
Here is extra info from the System log.

Mar 15 21:28:15 localhost usb.agent[17464]:      usb-storage: already loaded
Mar 15 21:28:20 localhost kernel: usb-storage: waiting for device to settle before scanning
Mar 15 21:28:20 localhost kernel:   Vendor: HP        Model: CD-Writer+ 8200e  Rev: 0001
Mar 15 21:28:20 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 00
Mar 15 21:28:20 localhost kernel: Attached scsi removable disk sda at scsi2, channel 0, id 0, lun 0
Mar 15 21:28:20 localhost kernel: usb-storage: device scan complete
Mar 15 21:28:20 localhost kernel: usb 1-3: USB disconnect, address 2
Mar 15 21:28:20 localhost kernel: usb 1-1: new full speed USB device using ohci_hcd and address 3
Mar 15 21:28:20 localhost kernel: scsi3 : SCSI emulation for USB Mass Storage devices
Mar 15 21:28:20 localhost kernel: usb-storage: device found at 3
Mar 15 21:28:20 localhost kernel: usb-storage: waiting for device to settle before scanning
Mar 15 21:28:20 localhost scsi.agent[17513]:      sd_mod: loaded sucessfully
Mar 15 21:28:20 localhost udev[17524]: configured rule in '/etc/udev/rules.d/udev.rules' at line 27 applied, 'sda' becomes '%k'
Mar 15 21:28:20 localhost udev[17524]: creating device node '/dev/sda'

I was thinking... Ubuntu thinks this device is a USB Mass Storage Device, but maybe it isn't? The HP website is not really helpful in this respect, but it does mention that the OS should detect the drive as a normal cd drive without extra drivers in Windows, while there should be a driver installed to use the CD-R/RW features of the drive. So I should just be able to mount this disc? I hope someone can help!

---

### Post by lorap on 2005-03-16
all you've to do is mount this way:
/dev/sr0 instead of /dev/sda...
had the same trouble before :-)
pavel

---

### Post by lorap on 2005-03-16
remember !
this way:
sudo mount -t iso9660 /dev/sr0 /media/usb-cdrom/
:-)

p.s.:
let me know if it works.

---

### Post by endless on 2005-03-16
First of all, thank you very much for your reply. I tried your solution, but it doesn't work for me:

```
sudo mount -t iso9660  /dev/sr0 /media/usb-cdrom/
mount: special device /dev/sr0 does not exist
``` 

These are my devices starting with an "s": 
```
 sda      shm/     snd/     sndstat  stderr   stdin    stdout 
```

As you can see, there is no /dev/sr0.

It's a weird problem. Maybe someone else can help me?

---

### Post by lorap on 2005-03-16
hi again!
should i understand you being working with Hoary?
if this's the case then do what i've predicted but instead of "sr0"
you should use either "sda0" or "sda1".
let me know if it worked.
pavel

---

### Post by endless on 2005-03-16
Yes, I am working with Hoary. But as you can see from the list of entries in /dev/ starting with an 's', there are no devices named sda0 or sda1

```

$ sudo mount -t iso9660 /dev/sda0 /media/usb-cdrom/
mount: special device /dev/sda0 does not exist
$ sudo mount -t iso9660 /dev/sda1 /media/usb-cdrom/
mount: special device /dev/sda1 does not exist
```
I don't know why I don't have the devices you are mentioning, but when dmesg says
```
 usb-storage: waiting for device to settle before scanning
  Vendor: HP        Model: CD-Writer+ 8200e  Rev: 0001
  Type:   Direct-Access                      ANSI SCSI revision: 00
Attached scsi removable disk sda at scsi2, channel 0, id 0, lun 0
usb-storage: device scan complete 
```

as I have posted before, wouldn't it make sense the device name is /dev/sda ? Maybe it is something of a driver issue? I'm sorry if I'm posing stupid questions, I'm still learning how a unix system functions.

---

### Post by lorap on 2005-03-16
hi again!
the things i've written earlier are right,but what you should do is to search for device
that works with usb devices,in warty it's sr0,in your case it could be "scd0".
check in /dev directory if such a device exist and let me know.
pavel

p.s.:
once you would find it out write this:

mount /dev/scd0 /media/usb-device -t vfat(in the hard disk case,or iso9660 in the case of cdrom) -o umask=000

the last thing grants you write privilegies.

---

### Post by endless on 2005-03-16
Thanks for your help! The problem is finding the right device, so I tried this: I also have a usb key, which gets automounted when I insert it, and I checked which devices are created after inserting it, and this comes up: a /dev/sdb and a /dev/sdb1 get created, and in mtab there is a new entry for /dev/sdb1 indicating that the usb flash device has been mounted. 

I presume through analogy I will need a /dev/sda0 or /dev/sda1 to mount my cd drive, but when I insert the cdrom, I only get a /dev/sda, but no /dev/sda1, which leaves me unable to mount this device. Any idea why there is no such device? I know what commands to use to mount it, once I know the right device, but I don't know which.

---

### Post by lorap on 2005-03-16
you know friend, i'd the same messages from ubuntu in warty when i tried to use my usb-cdr/w device!
but in my case what i've done was this:

i've not only created a folder called usb-cdrom in /media,but added this in 
/etc/fstab:

/dev/sda /media/usb-cdrom udf,iso9660,user,noauto,rw 0 0

try this please and let me know.try to mount to SDA again but add it first to FSTAB.
it didn't work in my case until i did this,but check if i've written in the right sequence the words USER,NOAUTO and so on,look as it's in the internal cdrom case,i'm not at my pc right now.
let me know.if it wouldn't work then go to the synaptic and search for USB SUPPORT.
if you find it out mark it and install.
pavel

---

### Post by endless on 2005-03-16
I have added the line to fstab, and tried mounting again, but no results: 

sudo mount -t iso9660 /dev/sda /media/usb-cdrom/
mount: No medium found

When you had this problem, did it say "No medium found", too? 

I am not sure which package you want me to install from Synaptic, can you tell me which one it is? I have hotplug installed (ofcourse) if that is what you wanted me to check.

---

### Post by lorap on 2005-03-16
i'm using WARTY so can't be sure about the right package.
yes i've gotten the same message.
did you checked how your internal cdrom is defined?
i'll stay with you till the end don't worry and i'll check up with other guys also, but what you should do that to check the sequence of definitions in fstab
i've given you the sequence as i remember it,i'm just right now at work and can't say the right sequence,but i'll get home in 2.5 hours and let you know.
try to change from sda to sda1,sdb,sdb0,sdb1,try to find in /dev if you have sr0 or sr1 once more and i'm gonna ask somebody else right now.
so remember friend,check now the sequence of the words like user,noauto and so on,don't forget about 0 0 at the end and try to play with devices
i used nano to make changes this way:

sudo nano etc/fstab

ctrl+o to save
ctrl+x to exit

p.s.:

i've usb cdr/w by benq :-)
had the same troubles :-)

go to the package manager,press SEARCH button and write in USB SUPPORT,after what choose the option DESCRITION AND NAMES then press OK.
lets see what it'd find for you out.
pavel

---

### Post by lorap on 2005-03-16
i've written a letter to one of moderators asking him to help us.
he's offline just right now but lets see what he'd propose once he gets online.
pavel

---

### Post by endless on 2005-03-16
Thanks for the trouble you're going through to help me! I doublechecked and edited fstab the way you said it:

before editing I had this line:

/dev/hda        /media/cdrom1   udf,iso9660 ro,user,noauto  		0	0

I copied it and changed it to:

/dev/sda        /media/usb-cdrom  udf,iso9660 ro,user,noauto  		0	0

No luck. Still can't mount /dev/sda...

After adding it, I can see a new device with the name of my external CD drive in Computer, but I can't mount it...

---

### Post by lorap on 2005-03-16
:-)
we'll solve this trouble!
if i remember well now your fstab looks as it should to.the first stair we've walked up!now try to change only devices from sda1 to sda0,scd0 to scd1,but remeber the power on cd should be on,moreover it would be good to have a cd with data inside.
when there's no cd inside it popups the message your device's empty.
pavel

---

### Post by endless on 2005-03-16
You mean I should change it in fstab?

When I run the mount command with those four names I get:

$ sudo mount -t iso9660 /dev/sda0 /media/usb-cdrom/
mount: special device /dev/sda0 does not exist
$ sudo mount -t iso9660 /dev/sda1 /media/usb-cdrom/
mount: special device /dev/sda1 does not exist
$ sudo mount -t iso9660 /dev/scd0 /media/usb-cdrom/
mount: special device /dev/scd0 does not exist
$ sudo mount -t iso9660 /dev/scd1 /media/usb-cdrom/
mount: special device /dev/scd1 does not exist

Power is on, and this drive can read the CD inside when I'm in windows. (and it's a data cd). Thanks again for your help. The problem still is that there is no new drive entry in /dev/ like sda1 or something like it...

---

### Post by lorap on 2005-03-16
we'll solve it.
it took me 2 weeks to solve my problem so don't worry friend! we do have a time!
you've done everything properly except this:

sudo mount /dev/sr0 /media/usb-cdrom -t iso9660 -o umask=000

always add this it'd grant you read rights.
i go home now and get there in 40 minutes,we'll solve it.
and we've a guy i've sent a private message to,he's a moderator here,i'm gonna ask someone else,don't worry friend,somehow we'll do it.
pavel

---

### Post by endless on 2005-03-16
Yes, but for now none of these devices exist. I tried the command I forgot, and there you go:

sudo mount /dev/sr0 /media/usb-cdrom -t iso9660 -o umask=000
mount: special device /dev/sr0 does not exist

Are you sure this is not a more difficult issue, concerning drivers for this particular drive (HP 8200e). I am aware this drive is an old sod, but hey, there is no reason this shouldn't work, is there?

---

### Post by lorap on 2005-03-16
now i'm at home beside my pc.
to get device needed open /dev directory and look at the files being present there.
now turn of the power and watch what device's gone or if the power was off then what device's appeared!we're almost done!do it friend!my usb cd isn't new one also.
once you catch the device appears/disappears you got the right driver!
let me know please and don't worry,it took me almost 2 weeks to get my cd working.
my device's sr0.once i turn on the power on the cd it goes but when i turn it on it comes back.
you can install "usbview" utility.go to Computer--------->System Configuration---->Synaptic Package Manager.after you get inside press Search button and write in USBVIEW.once the synaptic finds it out for you mark it and press Apply button.after the process of installation close the synaptic and run this utility.it'll show you up all usb devices connected even when the power's off.
friend don't worry,sometimes it takes its time:-)
waiting for the news from you.
pavel

---

### Post by endless on 2005-03-16
Well, when I plug and unplug the drive, the only difference it makes is one entry in /dev/, and that is /dev/sda, which sometimes gets the name /dev/sdb too. I installed the  usbview package I get info about my cd drive, but nothing really helpful (about the same things device manager could tell me). The only thing I really need to know is how to make ubuntu create a device named /dev/sda0 or /dev/sda1, which I can use to mount my drive.

I am downloading kernel 6.10-5 in synaptic, and I'm hoping this will solve the issue. I will keep you informed!!

---

### Post by endless on 2005-03-17
The new kernel didn't solve much. Just as there is a hdc (internal hard disk) with various partitions hdc1, hdc5, ..., the sda is created upon insertion of the drive, but the 'partitions' are not recoginized: there is no sda0 or sda1 or anything like that.

Maybe I just should give up?

---

### Post by lorap on 2005-03-17
you shouldn't give up friend.
why should you?
on my oppinion you'd to install version that works i mean warty cause hoary isn't completed one destribution.be you using warty this problem was for sure solved a long time ago.but probably we do something wrong,i'll write now to the community so they'd help us.
don't give up!
we just begun working.
pavel
holly land

---

### Post by endless on 2005-03-17
I will boot the Warty live cd and I will try if it recognizes this drive. I'll keep you informed. Thanks again for all your help!

---

### Post by lorap on 2005-03-17
the problem's hoary isn't a released version that means there's a possibility something wouldn't work.
if you decided install warty i'm sure this will solve this problem.
but anyway keep me in touch,i'll watch for your messages.
but if you wait some time i'll find the solution.
it took me 2 weeks to have my trouble resolved so yours one would take some time.
leave your email so i'd inform you about the things i've found.
pavel

---

