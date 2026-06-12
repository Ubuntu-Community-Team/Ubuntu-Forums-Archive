---
title: "HOW TO: Make static mountpoint for usb hddrive"
date: 2005-11-18
forum: Hardware &amp; Laptops
---

### Post by dlai on 2005-11-18
I wanted to make the mountpoint of one of my usb disks static, so that it wouldn't change mountpoint everytime i remounted it e.g. sda1, sdb1, sdc1 and so on. This is due to the HAL daemon and the pmount function (i think). We create the static mountpoint with udev. We have to make the file called /etc/udev/rules.d/10-local.rules. ```
sudo kwrite /etc/udev/rules.d/10-local.rules
``` then we have to open 2 terminals, one for finding the info about your usb harddisk, and the other one write: ```
sudo kwrite /etc/udev/rules.d/10-local.rules
``` In the first terminal you write: ```
udevinfo -a -p $(udevinfo -q path -n /dev/sda)
``` 

Where /dev/sda is where your disk currently mounted. You'll have alot of info displayed about your device, every time a new BUS== appears a new section is beginning. 
You have to look for the section with the BUS=="usb", there are usually quite a few, so this section also has to include the name of your manufacturer this will usually be displayed like this SYSFS{manufacturer}=="Cowon Systems_ Inc." 


The SYSFS snippets are unique information about your usb harddisk, and these we will use for linux to recognise your unique device. Now we will begin writing in your newly created 10-local.rules file, and this part i very easy, because you can actually copy-paste the info directly from the information displayed in your other terminal. 

First we have to tell linux that it is a usb device, so we copy-paste, into the first line of the file. BUS=="usb" and then we tell linux to recognise the device through one of the SYSFS== lines it could be SYSFS{serial}==yourserialhere. 

Next we write this into the file seperated by a comma and a space, so it will look like this: BUS=="usb", SYSFS{serial}=="yourserialhere", and to be sure that you can always put some of the other unique SYSFS snippets like SYSFS{idVendor}=="0e21" 

In the end we tell linux to name all the partitions of this device with what ever you want, that means, that if you have many partitions they will be named /dev/yourdrive1 ,/dev/yourdrive2, /dev/yourdrive3 and so on, this we do by adding the line NAME{all_partitions}=="yourdrive" The final 10-local.rules document will look like this ```
BUS=="usb", SYSFS{serial}=="yourserialhere", SYSFS{product}=="yourproducthere", NAME{all_partitions}=="yourdrive"
``` 

Here is an example of my config i have an iAudio M3L

```
BUS=="usb", SYSFS{serial}=="100", SYSFS{product}=="iAUDIO M3 Digital Audio Player", NAME{all_partitions}=="iaudio"
```


Now you save the document and restart your computer, and voila, your drive will mount in /dev/yourdrive,
and /media/yourdrive. Hope it helps:D

---

### Post by kiddo on 2005-11-18
Whoa thanks a bunch, I'm trying this right now~
however, if I am correct, the first command is not a directory you create but a config file no? Then you should not use mkdir, but nano or leafpad or kwrite or whatever you use as a text editor...

Edit: Okay so far I was able to go through that, up to the point where I have to specify the partitions...
[[IMG]http://img293.imageshack.us/img293/6035/screenshot5uj.th.jpg[/IMG]]("http://img293.imageshack.us/my.php?image=screenshot5uj.jpg")

I have one "physical" drive in a USB2 case, and it is separated into two partitions. They are currently correctly automounted (as shown in the system monitor), that is the 112gB partition on /media/usbdisk and the 80gB one on /media/usbdisk-1

Your concept of using dev/whatever in NAME{all_partitions} confuses me, do we really specify dev/ devices, or mountpoints? If I understand correctly, I would need to have

```
BUS=="usb",SYSFS{serial}=="00042222200000037950",SYSFS{idVendor}=="0402",NAME{all_partitions}=="backup,storage"
``` Sorry about that, please correct me. And thanks again for that how to!

---

### Post by dlai on 2005-11-19
Well I'm not quite sure I understand your question.
In this how to we specify the /dev/yourusbdrive... But that way we also determine where it should be mounted. I think that is handled by hal, and we have to edit make some .fdi files, which i looked into, but it seems a bit confusing for a newbie, like me;) . I will try and look into it, but it seems a bit strange. I don't think you can do like you suggest by make NAME{/dev/sda1, /dev/sda2} since we are naming what the partitions should be named, that would be biting one's own tail, or something like that....

---

### Post by dlai on 2005-11-19
thanks for pointing the code error with mkdir out. 

I renamed the how to.... maybe more correct, but please say so if you think there should be any corrections, or anything that should be more explicitly explained.

---

### Post by kiddo on 2005-11-19
Well actually I was expecting you to maybe give me an example of your conf, that would clear the confusion :lol: because the way you describe the syntax was a little unclear to me. You wrote:> NAME{all_partitions}=="yourdrive"

This line was unclear to me. You're kind of giving me two variables... Maybe an example would help?

---

### Post by berserker on 2005-11-19
This is what mine looks like:

```
 NAME{all_partitions}=="ipod"
```

This creates "/dev/ipod" and "/media/ipod".

Hope this helps.

---

### Post by dlai on 2005-11-20
I posted my config in the end of the How to....

BTW i have a problem, when i turn on my computer, with my usbhd plugged in, it generates two icons on the desktop. I think it has something to do with hotplug, but i'm not sure. Any ideas?

---

### Post by kiddo on 2005-11-20
those icons on the desktop are normal. You get them when you mount removable media such as usb keys, cdroms, floppies, etc. But you can disable that in applications > system tools > configuration editor

go in /apps/nautilus/desktop and disable "volumes_visible"
I believe that should do the trick. You won't see your other removable media though.



Now back to the main thing: it did not work for me. I say again that I have more than one partition on the usb drive so I don't know how this is managed. My config is as follows:
[B]BUS=="usb",SYSFS{serial}=="00042222200000037950",SYSFS{idVendor}=="0402",NAME{all_partitions}=="moo,meow"

Note: there are no spaces between letters in my config file. I don't know why this forum messes it up.
[/B]

---

### Post by dlai on 2005-11-21
You hav to make sure that you have a space after your commas (at least I think this is important), in your config... and i dont know if you can name your partions with a comma like that "moo, meow" if you say NAME{all_partitions}=="meow" it will end with naming your partitions like /dev/meow1 and /dev/meow2 (I read this somewhere, so I'm not sure.)

---

### Post by kiddo on 2005-11-21
Hmm, I tried NAME{all_partitions}=="backup, storage" and I got screenshot #1
Then I tried NAME{all_partitions}=="backup" and I got screenshot #2


Having multiple partitions really is a problem it seems.

---

### Post by dlai on 2005-11-21
Can you give me your print of ```
udevinfo -a -p $(udevinfo -q path -n /dev/sda)
```

---

### Post by kiddo on 2005-11-21
There you go !

```
jeff@khloe:~$ udevinfo -a -p $(udevinfo -q path -n /dev/sda)

udevinfo starts with the device the node belongs to and then walks up the
device chain, to print for every device found, all possibly useful attributes
in the udev key format.
Only attributes within one device section may be used together in one rule,
to match the device for which the node will be created.

device '/sys/block/sda' has major:minor 8:0
  looking at class device '/sys/block/sda':
    SUBSYSTEM=="block"
    SYSFS{dev}=="8:0"
    SYSFS{range}=="16"
    SYSFS{removable}=="0"
    SYSFS{size}=="398297088"
    SYSFS{stat}=="    1612      285    13271  1611848       44       10      432      5310        0    13835  1617158"

follow the "device"-link to the physical device:
  looking at the device chain at '/sys/devices/pci0000:00/0000:00:03.2/usb3/3-2/ 3-2:1.0/host1/target1:0:0/1:0:0:0':
    BUS=="scsi"
    ID=="1:0:0:0"
    DRIVER=="sd"
    SYSFS{device_blocked}=="0"
    SYSFS{iocounterbits}=="32"
    SYSFS{iodone_cnt}=="0x67d"
    SYSFS{ioerr_cnt}=="0x0"
    SYSFS{iorequest_cnt}=="0x67d"
    SYSFS{max_sectors}=="240"
    SYSFS{model}=="Storage Device  "
    SYSFS{queue_depth}=="1"
    SYSFS{queue_type}=="none"
    SYSFS{rev}=="0100"
    SYSFS{scsi_level}=="3"
    SYSFS{state}=="running"
    SYSFS{timeout}=="30"
    SYSFS{type}=="0"
    SYSFS{vendor}=="USB 2.0 "

  looking at the device chain at '/sys/devices/pci0000:00/0000:00:03.2/usb3/3-2/ 3-2:1.0/host1/target1:0:0':
    BUS==""
    ID=="target1:0:0"
    DRIVER=="unknown"

  looking at the device chain at '/sys/devices/pci0000:00/0000:00:03.2/usb3/3-2/ 3-2:1.0/host1':
    BUS==""
    ID=="host1"
    DRIVER=="unknown"

  looking at the device chain at '/sys/devices/pci0000:00/0000:00:03.2/usb3/3-2/ 3-2:1.0':
    BUS=="usb"
    ID=="3-2:1.0"
    DRIVER=="usb-storage"
    SYSFS{bAlternateSetting}==" 0"
    SYSFS{bInterfaceClass}=="08"
    SYSFS{bInterfaceNumber}=="00"
    SYSFS{bInterfaceProtocol}=="50"
    SYSFS{bInterfaceSubClass}=="06"
    SYSFS{bNumEndpoints}=="02"
    SYSFS{modalias}=="usb:v0402p5621d0103dc00dsc00dp00ic08isc06ip50"

  looking at the device chain at '/sys/devices/pci0000:00/0000:00:03.2/usb3/3-2' :
    BUS=="usb"
    ID=="3-2"
    DRIVER=="usb"
    SYSFS{bConfigurationValue}=="1"
    SYSFS{bDeviceClass}=="00"
    SYSFS{bDeviceProtocol}=="00"
    SYSFS{bDeviceSubClass}=="00"
    SYSFS{bMaxPower}=="  0mA"
    SYSFS{bNumConfigurations}=="1"
    SYSFS{bNumInterfaces}==" 1"
    SYSFS{bcdDevice}=="0103"
    SYSFS{bmAttributes}=="c0"
    SYSFS{configuration}==""
    SYSFS{devnum}=="4"
    SYSFS{idProduct}=="5621"
    SYSFS{idVendor}=="0402"
    SYSFS{maxchild}=="0"
    SYSFS{product}=="USB 2.0 Storage Device"
    SYSFS{serial}=="00042222200000037950"
    SYSFS{speed}=="480"
    SYSFS{version}==" 2.00"

  looking at the device chain at '/sys/devices/pci0000:00/0000:00:03.2/usb3':
    BUS=="usb"
    ID=="usb3"
    DRIVER=="usb"
    SYSFS{bConfigurationValue}=="1"
    SYSFS{bDeviceClass}=="09"
    SYSFS{bDeviceProtocol}=="01"
    SYSFS{bDeviceSubClass}=="00"
    SYSFS{bMaxPower}=="  0mA"
    SYSFS{bNumConfigurations}=="1"
    SYSFS{bNumInterfaces}==" 1"
    SYSFS{bcdDevice}=="0206"
    SYSFS{bmAttributes}=="e0"
    SYSFS{configuration}==""
    SYSFS{devnum}=="1"
    SYSFS{idProduct}=="0000"
    SYSFS{idVendor}=="0000"
    SYSFS{manufacturer}=="Linux 2.6.12-9-686 ehci_hcd"
    SYSFS{maxchild}=="6"
    SYSFS{product}=="Silicon Integrated Systems [SiS] USB 2.0 Controller"
    SYSFS{serial}=="0000:00:03.2"
    SYSFS{speed}=="480"
    SYSFS{version}==" 2.00"

  looking at the device chain at '/sys/devices/pci0000:00/0000:00:03.2':
    BUS=="pci"
    ID=="0000:00:03.2"
    DRIVER=="ehci_hcd"
    SYSFS{class}=="0x0c0320"
    SYSFS{device}=="0x7002"
    SYSFS{irq}=="23"
    SYSFS{local_cpus}=="1"
    SYSFS{modalias}=="pci:v00001039d00007002sv00001043sd00008087bc0Csc03i20"
    SYSFS{subsystem_device}=="0x8087"
    SYSFS{subsystem_vendor}=="0x1043"
    SYSFS{vendor}=="0x1039"

  looking at the device chain at '/sys/devices/pci0000:00':
    BUS==""
    ID=="pci0000:00"
    DRIVER=="unknown"
```

---

### Post by dlai on 2005-11-22
Now I'm only guessing, because your print looks a little wierd, and we have to do some trial and error...

```
BUS=="scsi", SYSFS{model}=="Storage Device  ", SYSFS{vendor}=="USB 2.0 ", NAME{all_partitions}=="storage"
BUS=="usb", SYSFS{serial}=="00042222200000037950", SYSFS{idVendor}=="0402", NAME{all_partitions}=="backup"
```

copy paste to your 10-local.rules ... THIS IS JUST AN IDEA!!! So if you don't want to do it, then don't. I don't know anything about the consequenses.

---

### Post by dlai on 2005-11-24
Well I kinda got to thinking about your problem this morning...
And I forgot to mention that you might have to see if you can find any differencies between ```
udevinfo -a -p $(udevinfo -q path -n /dev/sda1)
``` and
```
udevinfo -a -p $(udevinfo -q path -n /dev/sda2)
```

Then maybe you could configure for each partition since every partition has a unique serial...

---

### Post by kiddo on 2005-11-26
Sorry for the delayed reply. Here is the diff between the two drives (I output the commands you just gave me to two text files, and used diff), I am not really sure if it can be used to identify them properly. What do you think?

```
@@ -5,13 +5,13 @@
 Only attributes within one device section may be used together in one rule,
 to match the device for which the node will be created.
 
-device '/sys/block/sda/sda1' has major:minor 8:1
-  looking at class device '/sys/block/sda/sda1':
+device '/sys/block/sda/sda2' has major:minor 8:2
+  looking at class device '/sys/block/sda/sda2':
     SUBSYSTEM=="block"
-    SYSFS{dev}=="8:1"
-    SYSFS{size}=="234452547"
-    SYSFS{start}=="63"
-    SYSFS{stat}=="    1096     7445       46      368"
+    SYSFS{dev}=="8:2"
+    SYSFS{size}=="163830870"
+    SYSFS{start}=="234452610"
+    SYSFS{stat}=="     730     5258        7       56"
 
 follow the "device"-link to the physical device:
   looking at the device chain at '/sys/devices/pci0000:00/0000:00:03.2/usb3/3-2/3-2:1.0/host1/target1:0:0/1:0:0:0':
@@ -20,9 +20,9 @@
     DRIVER=="sd"
     SYSFS{device_blocked}=="0"
     SYSFS{iocounterbits}=="32"
[B]-    SYSFS{iodone_cnt}=="0x64c"
+    SYSFS{iodone_cnt}=="0x655"[/B]
     SYSFS{ioerr_cnt}=="0x0"
[B]-    SYSFS{iorequest_cnt}=="0x64c"
+    SYSFS{iorequest_cnt}=="0x655"[/B]
     SYSFS{max_sectors}=="240"
     SYSFS{model}=="Storage Device  "
     SYSFS{queue_depth}=="1"
```

---

### Post by dlai on 2005-11-28
Maybe you can try and make it depend on the SYSFS{size}
... Else I'm really getting nowhere. This SYSFS{dev} looks interesting too... just  try all the diff's out...and post the outcome, please.

---

### Post by kiddo on 2005-11-29
Hey... I finally had the courage to try it out and.. it worked! I'm suprised :)

Here is the content of my /etc/udev/rules.d/10-local.rules:
```
BUS=="usb", SYSFS{dev}=="8:1", SYSFS{size}=="234452547", NAME{all_partitions}=="backup"
BUS=="usb", SYSFS{dev}=="8:2", SYSFS{size}=="163830870", NAME{all_partitions}=="storage"
```

I don't know if using dev or size simply would work. It is likely, but I just wanted to go with a "two factor authentification" to be sure. So far, over ~10-15 iterations, I have not seen the partitions switch places yet. Great ! We could write a wiki page out of this. Needs further testing though.

---

### Post by dlai on 2005-11-30
Cool... I'm glad it finally worked, in the end it's all about trial and error;)

---

### Post by kiddo on 2005-12-01
I am very sorry to announce this, but actually it did not work 100%, I did some more tests this morning, and on the first try they were mounted incorrectly. I have noticed something though:

/dev/backup and /dev/storage are created and always properly attached to the right partition. What is bogus, however, is the mount points, /media/usbdisk and /media/usbdisk-1 which are not attached to the same devices.

Any clue? I feel we were pretty close :???:

---

### Post by dlai on 2005-12-03
Hmm... I'm not sure what your problem is... is it that your /dev/backup and /dev/storage mounts at /media/usbdisk-1 and /media/usbdisk respectively? Ohh I think I understand, /media/usbdisk and /media/usbdisk-1 are changing between the partitions.

I'm still having some problems too, especially the fact that KDE wants to put two icons for each device, if i pluck them in before startup... really strange. i would reallt like it to mount automatically when i startup, but i don't know how, any ideas?

---

### Post by kiddo on 2005-12-03
Just thought of something.. that scares me greatly: the solution might be editing our FSTAB @_@ that way maybe we could tell "it" to use the same mountpoints for those devices...? Any idea how to do that or if it would work?

---

### Post by dlai on 2005-12-03
well I tried something like. And a guy in another thread said that you could do something like writing the volume id instead of the /dev/yourdrive, i tried it, and HAL or udev seems to override fstab.

---

### Post by relarson on 2005-12-18
The easiest way to do this, if your filesystem is ext* is to set the volume label using tune2fs -L "the_name_you_want" /dev/<device name>  

so for me:

tune2fs -L "fire-2" /dev/sda2

means that when I plug in my firewire drive, the partition on /dev/sda2 is mounted as /media/fire-2.

If you are not using a filesystem that supports labels you will have to do as previous posters have described, editing the fdi/policy/10osvendor/10-storage-policy.fdi


for my vfat partition I did the following:
in the section like this:
  <!-- Normal volumes; use volume label, uuid or drive_type -->
    <match key="block.is_volume" bool="true">
      <match key="volume.fsusage" string="filesystem">
        <!-- skip for drives with the no partitions hint (they are handled above) -->
        <match key="@block.storage_device:storage.no_partitions_hint" bool="true">
          <merge key="volume.policy.desired_mount_point" type="copy_property">@block.storage_device:storage.policy.desired_mount_point</merge>
        </match>
        <match key="@block.storage_device:storage.no_partitions_hint" bool="false">

..... Added section below.....

         <!-- for my vfat firewire drive set it to fire-1 -->
          <match key="volume.uuid" string="42AC-D677">
                <merge key="volume.policy.desired_mount_point" type="string">fire-1</merge>
                <match  key="volume.label" empty="true">
                        <!-- for my vfat firewire drive set its desktop (volume name) to fire-1 also -->
                        <merge key="volume.label" type="string">fire-1</merge>
                </match>
          </match>
.... end added section ....

To find what the UUID of your drive is go to System menu-> Administration->Device Manager (Hal)
then select your volume and look at the advanced tab for the volume.uuid, probably at the end of the list.

Hope that helps someone!
-Rich

---

### Post by kiddo on 2005-12-18
I don't use vfat anymore, too much hassle ;) but I use ReiserFS everywhere, does tune2fs work well with that? Basically, the only thing I would have to do would be 

 tune2fs -L "the-drive-label" /dev/sda1

I assume all the rest below was for vfat?

---

### Post by kiddo on 2006-01-06
Hey dlai, are you still alive? I think an interesting solution was given to me, I'll have to do further testing but it seems to work nicely.

[http://bugzilla.ubuntu.com/show_bug.cgi?id=20733](http://bugzilla.ubuntu.com/show_bug.cgi?id=20733)

---

### Post by dlai on 2006-01-06
still alive yes, this seems to be the easiest solution, i've heard so from other sources too... but my only problem seems to be that, there is no possibility to label my fat32 mp3-player, at least i think so...:confused:

---

### Post by Blutack on 2007-02-23
Guys and gals, I found a rather nice solution :-)


[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

Hope it helps and keep on greppin'!

---

### Post by kiddo on 2007-02-23
I added my ReiserFS trick there :) thanks for the link

---

### Post by dgray_from_dc on 2007-11-11
I tried this solution on gutsy gibbon using IDE drives with USB-to-IDE cables attatched.  No joy.  

The output from
```
udevinfo -a -p $(udevinfo -q path -n /dev/sda1)
```
yielded different output.

```

Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/block/sdb':
    KERNEL=="sdb"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{capability}=="12"
    ATTR{stat}=="      50       77      536      456        0        0        0        0        0      356      456"
    ATTR{size}=="488397168"
    ATTR{removable}=="0"
    ATTR{range}=="16"
    ATTR{dev}=="8:16"

  looking at parent device '/devices/pci0000:00/0000:00:1e.0/0000:01:04.2/usb4/4-4/4-4.3/4-4.3:1.0/host3/target3:0:0/3:0:0:0':
    KERNELS=="3:0:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS=="sd"
    ATTRS{modalias}=="scsi:t-0x00"
    ATTRS{ioerr_cnt}=="0x0"
    ATTRS{iodone_cnt}=="0x39"
    ATTRS{iorequest_cnt}=="0x39"
    ATTRS{iocounterbits}=="32"
    ATTRS{timeout}=="30"
    ATTRS{state}=="running"
    ATTRS{rev}=="3.AA"
    ATTRS{model}=="STM3250820A     "
    ATTRS{vendor}=="MAXTOR  "
    ATTRS{scsi_level}=="3"
    ATTRS{type}=="0"
    ATTRS{queue_type}=="none"
    ATTRS{queue_depth}=="1"
    ATTRS{device_blocked}=="0"
    ATTRS{max_sectors}=="240"

  looking at parent device '/devices/pci0000:00/0000:00:1e.0/0000:01:04.2/usb4/4-4/4-4.3/4-4.3:1.0/host3/target3:0:0':
    KERNELS=="target3:0:0"
    SUBSYSTEMS==""
    DRIVERS==""
    ATTRS{uevent}==""

  looking at parent device '/devices/pci0000:00/0000:00:1e.0/0000:01:04.2/usb4/4-4/4-4.3/4-4.3:1.0/host3':
    KERNELS=="host3"
    SUBSYSTEMS==""
    DRIVERS==""
    ATTRS{uevent}==""

  looking at parent device '/devices/pci0000:00/0000:00:1e.0/0000:01:04.2/usb4/4-4/4-4.3/4-4.3:1.0':
    KERNELS=="4-4.3:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb-storage"
    ATTRS{modalias}=="usb:v0409p006Ad0000dc00dsc00dp00ic08isc06ip50"
    ATTRS{bInterfaceProtocol}=="50"
    ATTRS{bInterfaceSubClass}=="06"
    ATTRS{bInterfaceClass}=="08"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bInterfaceNumber}=="00"

  looking at parent device '/devices/pci0000:00/0000:00:1e.0/0000:01:04.2/usb4/4-4/4-4.3':
    KERNELS=="4-4.3"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{product}=="BackUP-Q EasyGO"
    ATTRS{manufacturer}=="BackUP-Q"
    ATTRS{quirks}=="0x0"
    ATTRS{maxchild}=="0"
    ATTRS{version}==" 2.00"
    ATTRS{devnum}=="4"
    ATTRS{busnum}=="4"
    ATTRS{speed}=="480"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bcdDevice}=="0000"
    ATTRS{idProduct}=="006a"
    ATTRS{idVendor}=="0409"
    ATTRS{bMaxPower}=="  2mA"
    ATTRS{bmAttributes}=="c0"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{configuration}==""
    ATTRS{dev}=="189:387"

  looking at parent device '/devices/pci0000:00/0000:00:1e.0/0000:01:04.2/usb4/4-4':
    KERNELS=="4-4"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{quirks}=="0x0"
    ATTRS{maxchild}=="4"
    ATTRS{version}==" 2.00"
    ATTRS{devnum}=="2"
    ATTRS{busnum}=="4"
    ATTRS{speed}=="480"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bDeviceProtocol}=="02"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bcdDevice}=="0008"
    ATTRS{idProduct}=="6560"
    ATTRS{idVendor}=="04b4"
    ATTRS{bMaxPower}=="100mA"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{configuration}==""
    ATTRS{dev}=="189:385"

  looking at parent device '/devices/pci0000:00/0000:00:1e.0/0000:01:04.2/usb4':
    KERNELS=="usb4"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{serial}=="0000:01:04.2"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{manufacturer}=="Linux 2.6.22-14-generic ehci_hcd"
    ATTRS{quirks}=="0x0"
    ATTRS{maxchild}=="4"
    ATTRS{version}==" 2.00"
    ATTRS{devnum}=="1"
    ATTRS{busnum}=="4"
    ATTRS{speed}=="480"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bcdDevice}=="0206"
    ATTRS{idProduct}=="0000"
    ATTRS{idVendor}=="0000"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{configuration}==""
    ATTRS{dev}=="189:384"

  looking at parent device '/devices/pci0000:00/0000:00:1e.0/0000:01:04.2':
    KERNELS=="0000:01:04.2"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{msi_bus}==""
    ATTRS{broken_parity_status}=="0"
    ATTRS{modalias}=="pci:v00001106d00003104sv00001106sd00003104bc0Csc03i20"
    ATTRS{local_cpus}=="ff"
    ATTRS{irq}=="11"
    ATTRS{class}=="0x0c0320"
    ATTRS{subsystem_device}=="0x3104"
    ATTRS{subsystem_vendor}=="0x1106"
    ATTRS{device}=="0x3104"
    ATTRS{vendor}=="0x1106"

  looking at parent device '/devices/pci0000:00/0000:00:1e.0':
    KERNELS=="0000:00:1e.0"
    SUBSYSTEMS=="pci"
    DRIVERS==""
    ATTRS{msi_bus}=="1"
    ATTRS{broken_parity_status}=="0"
    ATTRS{modalias}=="pci:v00008086d00002418sv00000000sd00000000bc06sc04i00"
    ATTRS{local_cpus}=="ff"
    ATTRS{irq}=="0"
    ATTRS{class}=="0x060400"
    ATTRS{subsystem_device}=="0x0000"
    ATTRS{subsystem_vendor}=="0x0000"
    ATTRS{device}=="0x2418"
    ATTRS{vendor}=="0x8086"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""
    ATTRS{uevent}==""


```

I tried picking it apart and using variables along the same line as you described, but found no serial numbers in my output.  I also have two of the same model drives that I want to use simultaneously.

Any suggestions?

---

### Post by crash_x on 2007-11-11
I'm having the same issue, but using feisty.

Here is what I have in my 10-local.rules file:

```
SUBSYSTEMS=="scsi", ATTRS{vendor}=="WDC WD50", ATTRS{model}=="00AAKS-00TMA0   ", NAME{all_partitions}=="asp_media"
```

And here is the output of udevinfo -a -p $(udevinfo -q path -n /dev/sdb1)

```
Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/block/sdb/sdb1':
    KERNEL=="sdb1"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{stat}=="     579      796        0        0"
    ATTR{size}=="976768002"
    ATTR{start}=="63"
    ATTR{dev}=="8:17"

  looking at parent device '/block/sdb':
    KERNELS=="sdb"
    SUBSYSTEMS=="block"
    DRIVERS==""
    ATTRS{stat}=="      90      559     1356     7056        0        0        0        0        0     6940     7056"
    ATTRS{size}=="976773168"
    ATTRS{removable}=="0"
    ATTRS{range}=="16"
    ATTRS{dev}=="8:16"

  looking at parent device '/devices/pci0000:00/0000:00:10.3/usb4/4-5/4-5:1.0/host1/target1:0:0/1:0:0:0':
    KERNELS=="1:0:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS=="sd"
    ATTRS{ioerr_cnt}=="0x0"
    ATTRS{iodone_cnt}=="0x61"
    ATTRS{iorequest_cnt}=="0x61"
    ATTRS{iocounterbits}=="32"
    ATTRS{timeout}=="30"
    ATTRS{state}=="running"
    ATTRS{rev}=="    "
    ATTRS{model}=="00AAKS-00TMA0   "
    ATTRS{vendor}=="WDC WD50"
    ATTRS{scsi_level}=="3"
    ATTRS{type}=="0"
    ATTRS{queue_type}=="none"
    ATTRS{queue_depth}=="1"
    ATTRS{device_blocked}=="0"
    ATTRS{max_sectors}=="240"

  looking at parent device '/devices/pci0000:00/0000:00:10.3/usb4/4-5/4-5:1.0/host1/target1:0:0':
    KERNELS=="target1:0:0"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:10.3/usb4/4-5/4-5:1.0/host1':
    KERNELS=="host1"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:10.3/usb4/4-5/4-5:1.0':
    KERNELS=="4-5:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb-storage"
    ATTRS{interface}=="MSC Bulk-Only Transfer"
    ATTRS{modalias}=="usb:v152Dp2339d0100dc00dsc00dp00ic08isc06ip50"
    ATTRS{bInterfaceProtocol}=="50"
    ATTRS{bInterfaceSubClass}=="06"
    ATTRS{bInterfaceClass}=="08"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bInterfaceNumber}=="00"

  looking at parent device '/devices/pci0000:00/0000:00:10.3/usb4/4-5':
    KERNELS=="4-5"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{serial}=="DCA0661214FF"
    ATTRS{product}=="USB to ATA/ATAPI Bridge"
    ATTRS{manufacturer}=="JMicron"
    ATTRS{maxchild}=="0"
    ATTRS{version}==" 2.00"
    ATTRS{devnum}=="3"
    ATTRS{speed}=="480"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bcdDevice}=="0100"
    ATTRS{idProduct}=="2339"
    ATTRS{idVendor}=="152d"
    ATTRS{bMaxPower}=="  2mA"
    ATTRS{bmAttributes}=="c0"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{configuration}=="USB Mass Storage"

  looking at parent device '/devices/pci0000:00/0000:00:10.3/usb4':
    KERNELS=="usb4"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{serial}=="0000:00:10.3"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{manufacturer}=="Linux 2.6.20-16-generic ehci_hcd"
    ATTRS{maxchild}=="6"
    ATTRS{version}==" 2.00"
    ATTRS{devnum}=="1"
    ATTRS{speed}=="480"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bcdDevice}=="0206"
    ATTRS{idProduct}=="0000"
    ATTRS{idVendor}=="0000"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{configuration}==""

  looking at parent device '/devices/pci0000:00/0000:00:10.3':
    KERNELS=="0000:00:10.3"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{msi_bus}==""
    ATTRS{broken_parity_status}=="0"
    ATTRS{modalias}=="pci:v00001106d00003104sv00001458sd00005004bc0Csc03i20"
    ATTRS{local_cpus}=="ff"
    ATTRS{irq}=="17"
    ATTRS{class}=="0x0c0320"
    ATTRS{subsystem_device}=="0x5004"
    ATTRS{subsystem_vendor}=="0x1458"
    ATTRS{device}=="0x3104"
    ATTRS{vendor}=="0x1106"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```

Any help is appreicated!!

---

### Post by crash_x on 2007-11-12
Fixed! See here: [http://ubuntuforums.org/showthread.php?t=168221&page=4](http://ubuntuforums.org/showthread.php?t=168221&page=4) and scroll down a bit

---

