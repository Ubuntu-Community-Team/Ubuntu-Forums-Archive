---
title: "Seagate FreeAgent Desktop (external USB HD) not automounting"
date: 2008-02-24
forum: Hardware &amp; Laptops
---

### Post by Sciamano on 2008-02-24
Hello everybody,
I've already searched the forums for solutions to this strange behavior of my Seagate FreeAgent Desktop 500Gb external HD, but couldn't find anything.

When I plug the drive, Kubuntu correctly detects it and (apart from the "*hal-storage-removable-mount-all-options refused uid1000*" bug) it works ok until I unplug the drive.

As you probably know, this drive has a huge yellow LED on the front, and since I keep my PC in the bedroom and I never shut it down, this LED generates so much light that I can't fall asleep at night.
Therefore I "Safely Remove" the drive and unplug it at night. The following morning, when I plug the drive again, Kubuntu won't automount it anymore.

It recognizes the drive (this is the *lsusb* output:

Bus 004 Device 007: ID 0bc2:3000 Seagate RSS LLC
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 04b8:0005 Seiko Epson Corp. Stylus Printer
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 011: ID 046d:c506 Logitech, Inc. MX-700 Cordless Mouse Receiver
Bus 001 Device 001: ID 0000:0000

but no more automount. 
Of course I can mount it manually, but it would be nice to make automount work as it's supposed to).
It's not a problem related to the infamous power saving feature of the drive, since I've already disabled it in Windows.

Any help?
Thanks a lot

---

### Post by Yellow Pasque on 2008-02-24
Let's start with the obvious. Go to System, Preferences, removable Drives and Media. Is the first option checked there?

EDIT: Oops, I guess Kubuntu is different?

Ok, what does dmesg | tail -50  say when you plug in the drive?

---

### Post by Sciamano on 2008-02-24
Hi Temüjin

> **Temüjin said:**
> Let's start with the obvious. Go to System, Preferences, removable Drives and Media. Is the first option checked there?

EDIT: Oops, I guess Kubuntu is different?

No problem. Anyway it shouldn't be a configuration problem of KDE, since everything automounts correctly (USB pendrives, SD Card reader, digital cameras, MP3 players and such)

> **Temüjin said:**
> Ok, what does dmesg | tail -50  say when you plug in the drive?

Here is the output::

```
[ 4695.364508] audit(1203852027.300:7): dev=eth0 prom=0 old_prom=256 auid=4294967295
[ 4695.364512] bridge-eth0: disabled promiscuous mode
[ 4695.364589] /dev/vmnet: open called by PID 6677 (vmware-vmx)
[ 4695.364601] device eth0 entered promiscuous mode
[ 4695.364605] audit(1203852027.300:8): dev=eth0 prom=256 old_prom=0 auid=4294967295
[ 4695.364608] bridge-eth0: enabled promiscuous mode
[ 4695.364610] /dev/vmnet: port on hub 0 successfully opened
[ 4695.588575] /dev/vmmon[6677]: host clock rate change request 83 -> 19
[ 4695.774967] scsi4 : SCSI emulation for USB Mass Storage devices
[ 4695.775160] usb-storage: device found at 6
[ 4695.775163] usb-storage: waiting for device to settle before scanning
[ 4695.776010] device eth0 left promiscuous mode
[ 4695.776023] audit(1203852027.800:9): dev=eth0 prom=0 old_prom=256 auid=4294967295
[ 4695.776026] bridge-eth0: disabled promiscuous mode
[ 4696.733539] /dev/vmmon[6674]: host clock rate change request 19 -> 0
[ 4696.788311] vmmon: Had to deallocate locked 156790 pages from vm driver f5a94000
[ 4696.793727] vmmon: Had to deallocate AWE 5815 pages from vm driver f5a94000
[ 4700.766671] usb-storage: device scan complete
[ 4700.768221] scsi 4:0:0:0: Direct-Access     Seagate  FreeAgentDesktop 100F PQ: 0 ANSI: 4
[ 4700.772001] sd 4:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[ 4700.773374] sd 4:0:0:0: [sda] Write Protect is off
[ 4700.773379] sd 4:0:0:0: [sda] Mode Sense: 1c 00 00 00
[ 4700.773381] sd 4:0:0:0: [sda] Assuming drive cache: write through
[ 4700.775747] sd 4:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[ 4700.781087] sd 4:0:0:0: [sda] Write Protect is off
[ 4700.781106] sd 4:0:0:0: [sda] Mode Sense: 1c 00 00 00
[ 4700.781109] sd 4:0:0:0: [sda] Assuming drive cache: write through
[ 4700.781116]  sda: sda1
[ 4700.790974] sd 4:0:0:0: [sda] Attached SCSI disk
[ 4700.791030] sd 4:0:0:0: Attached scsi generic sg0 type 0
[ 9053.511655] usb 4-5: USB disconnect, address 6
[ 9062.009653] usb 4-5: new high speed USB device using ehci_hcd and address 7
[ 9062.158535] usb 4-5: configuration #1 chosen from 1 choice
[ 9062.162676] scsi5 : SCSI emulation for USB Mass Storage devices
[ 9062.162740] usb-storage: device found at 7
[ 9062.162742] usb-storage: waiting for device to settle before scanning
[ 9067.155109] usb-storage: device scan complete
[ 9067.157715] scsi 5:0:0:0: Direct-Access     Seagate  FreeAgentDesktop 100F PQ: 0 ANSI: 4
[ 9067.170853] sd 5:0:0:0: [sda] Spinning up disk....ready
[ 9075.782565] sd 5:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[ 9075.783930] sd 5:0:0:0: [sda] Write Protect is off
[ 9075.783934] sd 5:0:0:0: [sda] Mode Sense: 1c 00 00 00
[ 9075.783937] sd 5:0:0:0: [sda] Assuming drive cache: write through
[ 9075.786053] sd 5:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[ 9075.787423] sd 5:0:0:0: [sda] Write Protect is off
[ 9075.787427] sd 5:0:0:0: [sda] Mode Sense: 1c 00 00 00
[ 9075.787429] sd 5:0:0:0: [sda] Assuming drive cache: write through
[ 9075.787434]  sda: sda1
[ 9075.804530] sd 5:0:0:0: [sda] Attached SCSI disk
[ 9075.804588] sd 5:0:0:0: Attached scsi generic sg0 type 0

```

---

### Post by Sciamano on 2008-02-24
no one?

---

### Post by Sciamano on 2008-02-25
still no insights from anyone?

---

### Post by SneakPeak on 2008-02-26
Hi Sciamano

I know this is not the reply you are looking for but I am hoping you can help me.

You say: "apart from the "hal-storage-removable-mount-all-options refused uid1000" bug" it works fine.

From the above I assume you sorted out the bug in question. I have just purchased a drive and plugged it in and I haven't got it working.  I am still at the hal-storage-removable......problem.

Do you know how I can get it fixed?

Thanks

Sneaks

---

### Post by Sciamano on 2008-02-26
I can only tell you how to solve it if you use KDE: open D3lphin, right-click on the drive and select properties. In the last tab you should find "connect as user". Deselect it, and it works.

---

### Post by SneakPeak on 2008-02-27
Thanks Sciamano,

I am running Kubuntu but your advice worked 100% for me.  I guess Kubuntu is very similar to KDE.

I see the drive is formatted to NTFS? Should one change it to ext3 to use it for linux apps?

Thanks again.

Sneaks :)

---

### Post by Sciamano on 2008-02-27
Kubuntu is Ubuntu with KDE as a desktop environment ;-)

---

### Post by FDPOD on 2008-02-28
I can't believe none of the gurus has an answer for this .....
I've got the same problem - crappy seagate HDD - power managment disabled - no automount !

---

### Post by kb8pgc on 2008-02-29
It's not the "crappy seagate HDD" Mine works fine with 7.10. No issues with the NTFS either.

---

### Post by Sciamano on 2008-02-29
Lots of people have problems with the Seagate FreeAgent Desktop drives, so I'm pretty convinced it's not a problem on the local pc. Also considering that everything else, from digital cameras to pendrives, automounts perfectly...

I temporarily "solved" by adding an entry in the fstab and then mounting the drive manually (made a couple of aliases to speed things up), but it's not what I consider an "ideal" solution.

---

### Post by Sciamano on 2008-03-09
Really, no one??

---

### Post by Sciamano on 2008-03-13
I guess I'll have to go on mounting it manually...

---

### Post by finno on 2008-03-17
I'm afraid so - I have Seagate External as well and it used to automount in dapper, but has failed to automount since in subsequent upgrades. I believe I saw in some post that it may be related to size of partition(s), but I don't want to endanger data on external by trying out gparted on it.

---

### Post by Sciamano on 2008-03-17
That's strange though, since it worked **the first time** I plugged it into the PC.
If it worked once, I don't see why it shouldn't work anymore, also considering I have not upgraded my system since then.

---

### Post by FDPOD on 2008-03-18
And it gets even stranger....
I do not have this workaround that Sciamano has set up for himself ....

   *(which BTW I would be very interested in - Sciamano, could you please post what you did - it might help others also !?)*

..., so after I also "safely" unmounted the drive before unplugging it - to get it to reconnect I just unplugged the power supply of the Freeagent and plugged it back in. Then it would automount again when I plug the USB cable back to the computer.
If I would just plug the USB cable back in w/o the power disconnect it would not do anything.

](*,)

---

### Post by Sciamano on 2008-03-19
I've found the "workaround" online, but can't find the link anymore.
Anyway here is what I did:
[B]
STEP 1[/B]
```
sudo vol_id /dev/sd##
```
Where "##" is the partition of the FreeAgent drive (letter and number change from system to system, you just have to guess yours if you don't already know it. Mine, for example, is "d1", making the command "sudo vol_id /dev/sdd1").
This command will report a few info about your disk. Copy the UUID code of the disk/partition, it's a long series of numbers (and sometimes letters)



[B]
STEP 2[/B]
Edit /etc/fstab and add the following line:
```
UUID=longnumber /media/MOUNTPOINT FILESYSTEM user,defaults 0 0
```
where:
longnumber is the uuid code of the partition you obtained in Step 1
MOUNTPOINT is the directory where you want the disk to be mounted (create the directory if you don't already have it: "sudo mkdir /media/MOUNTPOINT")
FILESYSTEM is the filesystem present on the drive (ntfs? ext3? vfat?)
"user" should let you mount the Freeagent hard disk without root permissions (but it did not work for me, see below)




**STEP 3**
Create a script to mount/unmount your drive (change parameters where necessary). Save it (I called it 'freeagent'), make it executable and copy/move it somewhere in your path (for example /usr/local/bin)
```
#!/bin/bash
if `mount | grep -q /media/MOUNTPOINT`
then
        umount /media/MOUNTPOINT
else
        mount /media/MOUNTPOINT
fi
```

You then plug the USB drive, wait until its led stops blinking and then launch the script from a terminal (you can also create a shortcut on your desktop for ease of use, if you want).
It works this way: it checks whether the disk is mounted. If it is, it unmounts it. If it's not, it mounts it.

As I said in Step 2, all this should mount the disk without the need for root permissions, but it did not work for me. I had to edit the script and add "sudo" before 'umount' and 'mount' to make it work:

```
#!/bin/bash
if `mount | grep -q /media/MOUNTPOINT`
then
        sudo umount /media/MOUNTPOINT
else
        sudo mount /media/MOUNTPOINT
fi
```

If you are making it a desktop shortcut to be launched by clicking on it, change sudo with the "graphical" command needed by your desktop environment (for example: "gksu" if using Gnome or "kdesudo" if using KDE)

Hope this helps.

BTW: unplugging the power supply does not work for me. The disk still would not mount automatically.

---

### Post by FDPOD on 2008-03-19
Thanks Sciamano for the walk through ... =D>:-D
All sounded pretty straight forward and I set everything up as you described ...
I now also can *mount *& *umount* via terminal command - the desktop script is what I'm still struggling with :(

My ultimate goal would be (if you ever have experienced Knoppix there it is standard and I think it is a great feature to have ... + it would eliminate the need for a automount function once the connection between devices has been established once) to have a regular HD Icon on the desktop stay there and not disappear when the drive is unmounted. One can right click on the icon and choose between mount/unmount, write enabled/disabled/, other permissions, etc...

I guess none of the developers of Ubuntu has looked across the border and spotted this one apparently so far ....:cry:

=====
Funny side note though:
When I right click on the desktop icon after this change to try an unmount the drive now all of a sudden it says:

    *Cannot unmount the volume FreeAgentDrive - umount: /media/FreeAgentDrive mount disagrees with the fstab*

...same as if I use the *umount /media/FreeAgentDrive* instead of the *sudo umount /media/FreeAgentDrive*

](*,) Man, this is almost as bad as Windows ...#-o

---

### Post by leroygbiv on 2008-03-20
Hi Sciamano, 
I have the same Seagate external HDD, I run Gutsy in Gnome & came across the same problem.
I get an error stating "mount point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)". 

If you have nautilus (alt+F2 type in NAUTILUS and click ok) put computer:/// in the location bar & press enter, than right click the Icon for you drive. Under drive & volume in the properties page the mount point needs to be set to just the name of the drive & not the entire path.

EG: /media/FreeAgent needs to be changed to FreeAgent 

I found the solution from Raymurh in the following forum page:
[http://ubuntuforums.org/showthread.php?p=4551071#post45](http://ubuntuforums.org/showthread.php?p=4551071#post45)

I don't know if this works under KDE but it wouldn't harm to give it a try
Hope this helps.:)

---

### Post by Sciamano on 2008-03-24
> **FDPOD said:**
> Thanks Sciamano for the walk through ... =D>:-D
All sounded pretty straight forward and I set everything up as you described ...
I now also can *mount *& *umount* via terminal command - the desktop script is what I'm still struggling with :(

My ultimate goal would be (if you ever have experienced Knoppix there it is standard and I think it is a great feature to have ... + it would eliminate the need for a automount function once the connection between devices has been established once) to have a regular HD Icon on the desktop stay there and not disappear when the drive is unmounted. One can right click on the icon and choose between mount/unmount, write enabled/disabled/, other permissions, etc...

I guess none of the developers of Ubuntu has looked across the border and spotted this one apparently so far ....:cry:

I have no experience with Knoppix, but what you describe looks nice.
Anyway the "desktop script" is just a shortcut to the mount/unmount script.

Otherwise you can create a desktop entry: open a text editor and write:
```

[Desktop Entry]
Name=FreeAgent Drive
Exec="path to the mount/unmount script"
Type=Application
Icon="path to the desired icon"

```

Then save it as "freeagent.desktop" on the desktop (of course)

> 

=====
Funny side note though:
When I right click on the desktop icon after this change to try an unmount the drive now all of a sudden it says:

    *Cannot unmount the volume FreeAgentDrive - umount: /media/FreeAgentDrive mount disagrees with the fstab*

...same as if I use the *umount /media/FreeAgentDrive* instead of the *sudo umount /media/FreeAgentDrive*

](*,) Man, this is almost as bad as Windows ...#-o

I don't know what to say, I've never had any problem mounting/unmounting the drive via the script...

---

