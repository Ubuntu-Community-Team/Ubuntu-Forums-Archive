---
title: "USB Flash Drive Not appearing"
date: 2006-06-08
forum: Hardware &amp; Laptops
---

### Post by ElderDarkReaper on 2006-06-08
Hi, 
I have a problem with accessing data off my USB Drive in Ubuntu 6.06. It is not appearing in the File manager or nor will it mount using the terminal. It has all of my data on it before i changed from 5.04 and I need it, I have hit a brick wall,](*,)  can anyone help please?

---

### Post by lkagan on 2006-06-08
Remove the usb drive.  Then type the following at a terminal:

```
sudo tail -f /var/log/messages
```

That will start showing that particular log file and will continue to watch it when new entries are appended.  Now hit enter a few times in that terminal to create some space between the last log entry and new ones that are about to appear.  Then plug in your usb drive.  You **should** see some new messages.  Copy and paste those new messages here so we can better be able to help.

Larry

---

### Post by dmspiller on 2006-06-08
Different user, same problem. Here's the info I obtained. I hope we have a common solution. TIA


Jun  8 10:01:53 localhost kernel: [4303441.734000] usb 1-1.4: new full speed USB device using uhci_hcd and address 7
Jun  8 10:01:53 localhost kernel: [4303441.780000] scsi3 : SCSI emulation for USB Mass Storage devices
Jun  8 10:01:58 localhost kernel: [4303446.783000]   Vendor: USB MASS  Model:  STORAGE DEVICE   Rev: 0.10
Jun  8 10:01:58 localhost kernel: [4303446.783000]   Type:   Direct-Access                 ANSI SCSI revision: 02
Jun  8 10:01:58 localhost kernel: [4303446.792000] SCSI device sdc: 2000880 512-byte hdwr sectors (1024 MB)
Jun  8 10:01:58 localhost kernel: [4303446.795000] sdc: Write Protect is off
Jun  8 10:01:58 localhost kernel: [4303446.808000] SCSI device sdc: 2000880 512-byte hdwr sectors (1024 MB)
Jun  8 10:01:58 localhost kernel: [4303446.811000] sdc: Write Protect is off
Jun  8 10:01:58 localhost kernel: [4303446.811000]  /dev/scsi/host3/bus0/target0/lun0: p1
Jun  8 10:01:58 localhost kernel: [4303446.819000] Attached scsi removable disk sdc at scsi3, channel 0, id 0, lun 0

---

### Post by lkagan on 2006-06-08
Okay, good.  Your machine is seeing the device.  Try mounting the device via the mount command.
```

sudo mkdir /media/usbdrive
sudo mount -t vfat /dev/sdc1 /media/usbdrive

```

Some assumptions are made.  The device probably has a FAT32 filesystem thus we use vfat for the mount argument.  Your device is registered as sdc1.  It is obviously the third physical (SCSI or SATA) disk on your system given the output you supplied from you log file,  but I'm assuming the filesystem you want is the first partition of the usb drive.  Hmm, can you even have more than 1 partition on those?  Anyway, let me know if this works for you.

Larry

---

### Post by dmspiller on 2006-06-08
Well, sort of. The drive now appears on the desktop, but I can't write to it. I get an error saying I don't have permission.
The "drive" is actually a 1G CompactFlash card w/usb adaptor.

---

### Post by lkagan on 2006-06-08
Good.  I first wanted to be sure you could mount it.  The problem you're having is that you mounted it as root so you can't write to it as a normal user.  So now add this to your /etc/fstab file (use 'sudo gedit /etc/fstab' to edit).
```

/dev/sdc1      /media/usbdrive           vfat   defaults,noauto,owner,rw,uid=larry,gid=larry   0
```

Now of course unless your name is larry, you'll want to change those values to your user and group names respectively. (they're probably both the same)

Now unmount the /media/usbdrive by typing
```
sudo umount /media/usbdrive
```
Then remount it using a shortcut (since we added the above info to the fstab file)
```
sudo mount /media/usbdrive
```

Now you should be able to write to it as your normal user.

Let me know how it goes.

Larry

---

### Post by ElderDarkReaper on 2006-06-08
I had this come up
Jun  9 09:19:13 localhost kernel: usb 1-1.2: USB disconnect, address 6




Jun  9 09:19:22 localhost kernel: usb 1-1.2: new full speed USB device using ohci_hcd and address 7
Jun  9 09:19:22 localhost kernel: scsi3 : SCSI emulation for USB Mass Storage devices
Jun  9 09:19:22 localhost usb.agent[18026]:      usb-storage: already loaded
Jun  9 09:19:27 localhost kernel:   Vendor: USB 2.0   Model: Flash Disk        Rev: 1100
Jun  9 09:19:27 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 00
Jun  9 09:19:27 localhost kernel: SCSI device sda: 1805416 512-byte hdwr sectors (924 MB)
Jun  9 09:19:27 localhost kernel: sda: assuming Write Enabled
Jun  9 09:19:27 localhost kernel: SCSI device sda: 1805416 512-byte hdwr sectors (924 MB)
Jun  9 09:19:27 localhost kernel: sda: assuming Write Enabled
Jun  9 09:19:27 localhost kernel:  /dev/scsi/host3/bus0/target0/lun0: unknown partition table
Jun  9 09:19:27 localhost kernel: Attached scsi removable disk sda at scsi3, channel 0, id 0, lun 0
Jun  9 09:19:27 localhost kernel: Attached scsi generic sg0 at scsi3, channel 0, id 0, lun 0,  type 0
Jun  9 09:19:27 localhost scsi.agent[18115]:      sd_mod: loaded sucessfully

---

### Post by lkagan on 2006-06-08
Excellent.  Use the exact same instructions as above but replace sdc1 with sda1.

Larry

---

### Post by ElderDarkReaper on 2006-06-08
I did try that but it said
"robert@iBook:~$ sudo mount -t vfat /dev/sda1 /media/usbdrive
mount: special device /dev/sda1 does not exist
robert@iBook:~$"

---

### Post by s6dalane on 2006-06-08
[QUOTE=ElderDarkReaper]I did try that but it said
"robert@iBook:~$ sudo mount -t vfat /dev/sda1 /media/usbdrive
mount: special device /dev/sda1 does not exist
robert@iBook:~$"[/QUOTE]
Use **sda**, it worked for me.

---

### Post by ElderDarkReaper on 2006-06-08
[QUOTE=s6dalane]Use **sda**, it worked for me.[/QUOTE]

I tried that and it came up with this:
robert@iBook:~$ sudo mount -t vfat /dev/sda /media/usbdrive
Password:
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by lkagan on 2006-06-08
Try sda2 and sda3

---

### Post by ElderDarkReaper on 2006-06-08
no joy here either. i have even tried sdb1-9 and sdc1-9

---

### Post by s6dalane on 2006-06-09
I tried your guide **lkagan**, but I still can't write as a normal user. I can moun the drive just fine and browse the files on it with Nautilus. What might be the problem?
I replaced sdc1 with sda and added my username to the line, but still nothing.
> /dev/sda      /media/usbdrive   vfat   defaults,noauto,owner,rw,uid=kaarel,gid=kaarel   0

---

### Post by dmspiller on 2006-06-09
That worked. Thanks. Now I'd like to try mounting a USB hard drive. I can send you the messages from that to decipher, too. Should I use/start another thrad so I don't go OT?

---

### Post by ifokkema on 2006-06-09
[QUOTE=ElderDarkReaper]no joy here either. i have even tried sdb1-9 and sdc1-9[/QUOTE]

If your USB drive is linked to sda, try:
```
sudo fdisk -l /dev/sda
```
This will print out the sda partition table.

---

### Post by vavoem on 2006-06-26
Sorry to bring this back up
But my camera gives back

Jun 26 17:00:48 localhost kernel: [17196830.468000] usb 4-6: new high speed USB device using ehci_hcd and address 23

end of log

---

### Post by ifokkema on 2006-06-26
[QUOTE=vavoem]Sorry to bring this back up
But my camera gives back

Jun 26 17:00:48 localhost kernel: [17196830.468000] usb 4-6: new high speed USB device using ehci_hcd and address 23

end of log[/QUOTE]

Can you see your camera in System->Administration->Device Manager?

Otherwise, it seems like there's no driver taking on your camera...
What's the output of
```
lsmod |grep usb
```

---

### Post by sasquatch on 2006-06-26
Yet another user, trying to automount a USB hard drive. Here's what I get from /var/log/messages when I turn the drive on:

un 26 08:32:30 localhost kernel: [17181100.464000] usb 4-1.3: new high speed USB device  using ehci_hcd and address 6
Jun 26 08:32:31 localhost kernel: [17181100.572000] scsi2 : SCSI emulation for USB Mass Storage devices
Jun 26 08:32:41 localhost kernel: [17181111.152000]  2:0:0:0: scsi: Device offlined - no t ready after error recovery
Jun 26 08:32:41 localhost kernel: [17181111.152000] usb 4-1.3: USB disconnect, address 6

What does it mean?

-dave


[QUOTE=lkagan]Remove the usb drive.  Then type the following at a terminal:

```
sudo tail -f /var/log/messages
```

That will start showing that particular log file and will continue to watch it when new entries are appended.  Now hit enter a few times in that terminal to create some space between the last log entry and new ones that are about to appear.  Then plug in your usb drive.  You **should** see some new messages.  Copy and paste those new messages here so we can better be able to help.

Larry[/QUOTE]

---

### Post by akechi on 2006-06-26
Hi, Im also having issues with my USB flash drive not appearing. 

I typed this this into terminal:
```
sudo tail -f /var/log/messages
```
and this was my output:  
```

Jun 26 11:31:18 localhost kernel: [35265.748769] usb 3-1: new high speed USB device using ehci_hcd and address 2
Jun 26 11:31:19 localhost kernel: [35266.748429] ehci_hcd 0000:00:13.2: Unlink after no-IRQ?  Controller is probably using the wrong IRQ.
Jun 26 11:31:30 localhost kernel: [35277.401011] usb 3-1: new high speed USB device using ehci_hcd and address 3
Jun 26 11:31:41 localhost kernel: [35289.053260] usb 3-1: new high speed USB device using ehci_hcd and address 4
Jun 26 11:31:52 localhost kernel: [35299.585703] usb 3-1: new high speed USB device using ehci_hcd and address 5

```
Im pretty sure that this is an error and something is wrong, especially the part about controller is probably using wrong IRQ.

If anyone has any ideas please let me know, i really do need my flash drive.

Thanks.

---

### Post by vavoem on 2006-06-26
[QUOTE=ifokkema]Can you see your camera in System->Administration->Device Manager?

Otherwise, it seems like there's no driver taking on your camera...
What's the output of
```
lsmod |grep usb
```[/QUOTE]
usbcore               130692  3 ehci_hcd,uhci_hcd

BTW
i Have 
uname -r 

kernel image 2.6.15-25-386 



I have a laptop on wich it works flawlessly

It has 

lsmod |grep usb
uhci_hcd installed only

It has 2.6.15-25-386 kernel

Hope it is of some help

---

### Post by ifokkema on 2006-06-26
[QUOTE=sasquatch]Yet another user, trying to automount a USB hard drive. Here's what I get from /var/log/messages when I turn the drive on:

un 26 08:32:30 localhost kernel: [17181100.464000] usb 4-1.3: new high speed USB device  using ehci_hcd and address 6
Jun 26 08:32:31 localhost kernel: [17181100.572000] scsi2 : SCSI emulation for USB Mass Storage devices
Jun 26 08:32:41 localhost kernel: [17181111.152000]  2:0:0:0: scsi: Device offlined - no t ready after error recovery
Jun 26 08:32:41 localhost kernel: [17181111.152000] usb 4-1.3: USB disconnect, address 6[/QUOTE]
It's getting busy here...
This means the driver that handles your device threw an error, possibly because of an hard ware problem, or a driver problem. Does the device work on a different OS?

---

### Post by sasquatch on 2006-06-26
Yes, it works on Windoze XP. It also worked on Ubuntu, as of last Friday. This particular error is new as of this morning.

History: last week I bought the drive enclosure, formatted the drive FAT32 using WinXP, booted Dapper, plugged the drive into the USB port and it automounted under /media/usbdrive. This morning I get the errors noted below.

I'll double-check it still works under Windoze......

UPDATE:

Whoops, false alarm... apparently the drive went belly-up over the weekend. :( 
Thanks for the help anyway, I learned a lot of good stuff.

[QUOTE=ifokkema]It's getting busy here...
This means the driver that handles your device threw an error, possibly because of an hard ware problem, or a driver problem. Does the device work on a different OS?[/QUOTE]

---

### Post by ifokkema on 2006-06-26
[QUOTE=vavoem]usbcore               130692  3 ehci_hcd,uhci_hcd[/QUOTE]
Did you see your drive in System->Administration->Device Manager?

And about lsmod, sorry, I should have been more specific. My list looks like this BEFORE I attach any drive:
```
  18:49:12 ifokkema@elim:~$ lsmod |grep usb
usbhid                 30688  0
usbcore               104316  4 usbhid,ehci_hcd,uhci_hcd
```
And AFTER attaching my Sony Camera:
```
  18:49:16 ifokkema@elim:~$ lsmod |grep usb
usb_storage            64704  0
scsi_mod              124872  1 usb_storage
usbhid                 30688  0
usbcore               104316  5 usb_storage,usbhid,ehci_hcd,uhci_hcd
ide_core              125268  6 usb_storage,ide_floppy,ide_cd,ide_disk,ide_generic,via82cxxx
```

See the difference? My kern.log had this to say:
```
Jun 26 18:50:09 localhost kernel: [4295803.282000] usb 3-1: new full speed USB device using uhci_hcd and address 2
Jun 26 18:50:09 localhost kernel: [4295803.524000] SCSI subsystem initialized
Jun 26 18:50:09 localhost kernel: [4295803.530000] Initializing USB Mass Storage driver...
Jun 26 18:50:09 localhost kernel: [4295803.534000] scsi0 : SCSI emulation for USB Mass Storage devices
Jun 26 18:50:09 localhost kernel: [4295803.536000] usb-storage: device found at 2
Jun 26 18:50:09 localhost kernel: [4295803.536000] usb-storage: waiting for device to settle before scanning
Jun 26 18:50:09 localhost kernel: [4295803.536000] usbcore: registered new driver usb-storage
Jun 26 18:50:09 localhost kernel: [4295803.536000] USB Mass Storage support registered.
Jun 26 18:50:14 localhost kernel: [4295808.539000]   Vendor: Sony      Model: Sony DSC          Rev: 4.50
Jun 26 18:50:14 localhost kernel: [4295808.539000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Jun 26 18:50:14 localhost kernel: [4295808.545000] usb-storage: device scan complete
Jun 26 18:50:14 localhost kernel: [4295808.659000] SCSI device sda: 466944 512-byte hdwr sectors (239 MB)
Jun 26 18:50:14 localhost kernel: [4295808.659000] sda: assuming Write Enabled
Jun 26 18:50:14 localhost kernel: [4295808.659000] sda: assuming drive cache: write through
Jun 26 18:50:14 localhost kernel: [4295808.668000] SCSI device sda: 466944 512-byte hdwr sectors (239 MB)
Jun 26 18:50:14 localhost kernel: [4295808.668000] sda: assuming Write Enabled
Jun 26 18:50:14 localhost kernel: [4295808.668000] sda: assuming drive cache: write through
Jun 26 18:50:14 localhost kernel: [4295808.668000]  /dev/scsi/host0/bus0/target0/lun0: p1
Jun 26 18:50:14 localhost kernel: [4295808.680000] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
```

So, if you miss drivers after attaching your drive, you could try and add them manually, see what happens.
```
sudo modprobe usb_storage
```

---

### Post by vavoem on 2006-06-28
[QUOTE=ifokkema]Did you see your drive in System->Administration->Device Manager?

And about lsmod, sorry, I should have been more specific. My list looks like this BEFORE I attach any drive:
```
  18:49:12 ifokkema@elim:~$ lsmod |grep usb
usbhid                 30688  0
usbcore               104316  4 usbhid,ehci_hcd,uhci_hcd
```
And AFTER attaching my Sony Camera:
```
  18:49:16 ifokkema@elim:~$ lsmod |grep usb
usb_storage            64704  0
scsi_mod              124872  1 usb_storage
usbhid                 30688  0
usbcore               104316  5 usb_storage,usbhid,ehci_hcd,uhci_hcd
ide_core              125268  6 usb_storage,ide_floppy,ide_cd,ide_disk,ide_generic,via82cxxx
```

See the difference? My kern.log had this to say:
```
Jun 26 18:50:09 localhost kernel: [4295803.282000] usb 3-1: new full speed USB device using uhci_hcd and address 2
Jun 26 18:50:09 localhost kernel: [4295803.524000] SCSI subsystem initialized
Jun 26 18:50:09 localhost kernel: [4295803.530000] Initializing USB Mass Storage driver...
Jun 26 18:50:09 localhost kernel: [4295803.534000] scsi0 : SCSI emulation for USB Mass Storage devices
Jun 26 18:50:09 localhost kernel: [4295803.536000] usb-storage: device found at 2
Jun 26 18:50:09 localhost kernel: [4295803.536000] usb-storage: waiting for device to settle before scanning
Jun 26 18:50:09 localhost kernel: [4295803.536000] usbcore: registered new driver usb-storage
Jun 26 18:50:09 localhost kernel: [4295803.536000] USB Mass Storage support registered.
Jun 26 18:50:14 localhost kernel: [4295808.539000]   Vendor: Sony      Model: Sony DSC          Rev: 4.50
Jun 26 18:50:14 localhost kernel: [4295808.539000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Jun 26 18:50:14 localhost kernel: [4295808.545000] usb-storage: device scan complete
Jun 26 18:50:14 localhost kernel: [4295808.659000] SCSI device sda: 466944 512-byte hdwr sectors (239 MB)
Jun 26 18:50:14 localhost kernel: [4295808.659000] sda: assuming Write Enabled
Jun 26 18:50:14 localhost kernel: [4295808.659000] sda: assuming drive cache: write through
Jun 26 18:50:14 localhost kernel: [4295808.668000] SCSI device sda: 466944 512-byte hdwr sectors (239 MB)
Jun 26 18:50:14 localhost kernel: [4295808.668000] sda: assuming Write Enabled
Jun 26 18:50:14 localhost kernel: [4295808.668000] sda: assuming drive cache: write through
Jun 26 18:50:14 localhost kernel: [4295808.668000]  /dev/scsi/host0/bus0/target0/lun0: p1
Jun 26 18:50:14 localhost kernel: [4295808.680000] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
```

So, if you miss drivers after attaching your drive, you could try and add them manually, see what happens.
```
sudo modprobe usb_storage
```[/QUOTE]

I cannot find system administration devices.

Some additional info while in ptp mode an icon appears on my desktop when clicked it opens a screen system://camera with the device listed
when i doubleclick the device system://camera/camera with device listed and so on and so on.

sudo tail -f /var/log/messages only sees something is connected but is not doing anything with it.

You have loaded a driver ide_core but  when i insmod ide_core it cannot be found.
Any idea where to find it.

However i don't think that is the problem because on my laptop those drivers are not loaded and it works like a charm there

---

### Post by vavoem on 2006-06-28
Forget everything i solved it.

I installed a program called digikam :cool: 
Put my camera in ptp mode and let the program solve the connection.

It works jippy though it would be nicer if i could use it as a mass storage device if anyone still has some idea's i will be forever gratefull.

p.s. finally getting full resolution of my wedding pictures

---

### Post by pvdg on 2006-07-07
> **lkagan said:**
> Remove the usb drive.  Then type the following at a terminal:

```
sudo tail -f /var/log/messages
```

That will start showing that particular log file and will continue to watch it when new entries are appended.  Now hit enter a few times in that terminal to create some space between the last log entry and new ones that are about to appear.  Then plug in your usb drive.  You **should** see some new messages.  Copy and paste those new messages here so we can better be able to help.

Larry

I have a similar problem: upgraded from Breezy (where all usb drives were recognized and automounted) to Dapper and nothing apparently happens when I plug in the usb drive. There is no reference to it in fstab (cdrom and floppy are there) and following Ikagan's advice gives:

> Jul  8 01:34:01 localhost kernel: [4305784.706000] usb 5-7: new high speed USB device using ehci_hcd and address 6

and nothing more. Any help welcome.

[COLOR="Red"]EDIT:Problem solved!:) [/COLOR]
Apparently, it was a kernel version problem (probably caused by my messing around with linux-image packages in Breezy). I uninstalled linux-image-2.6.15.25-686 which was causing Kernel Panic anyway and installed linux-image-2.6.15-23-386 (as a dependency of nvidia-glx, which I reinstalled). On reboot, the usbdisk problem was solved, along with the sound problems I was also experiencing. Hope this will be useful to someone.

---

### Post by stopsatgreen on 2006-07-07
Hi,

Same problem here:

```
Jul  8 02:55:18 peter-desktop kernel: [17181979.628000] usb 1-6: new high speed USB device using ehci_hcd and address 22
Jul  8 02:55:18 peter-desktop kernel: [17181980.172000] usb 1-6: new high speed USB device using ehci_hcd and address 23
Jul  8 02:55:19 peter-desktop kernel: [17181980.716000] usb 1-6: new high speed USB device using ehci_hcd and address 24
Jul  8 02:55:19 peter-desktop kernel: [17181981.236000] usb 1-6: new high speed USB device using ehci_hcd and address 25
```

```
usbcore               130692  3 ohci_hcd,ehci_hcd
```

Flash drive works fine, but not found here.

---

### Post by pvdg on 2006-07-08
I have no idea whether this will help you (I am just a newbie), but I suggest you read the EDIT in my previous post.

---

### Post by jamaas on 2006-07-29
Any chance someone could point me in the right direction.  I've read and tried but still no luck.

My messages are as such
usb 5-2.2.4: new full speed USB device using ehci_hcd and address 14Jul 29 09:00:14 localhost kernel: [17218797.636000] usb 5-2.2.4: not running at top speed; connect to a high speed hub
Jul 29 09:00:14 localhost kernel: [17218797.656000] scsi5 : SCSI emulation for USB Mass Storage devices
Jul 29 09:00:19 localhost kernel: [17218802.660000]   Vendor: USB2.0    Model: SMARTMEDIA        Rev:
Jul 29 09:00:19 localhost kernel: [17218802.660000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Jul 29 09:00:19 localhost kernel: [17218802.664000] sd 5:0:0:0: Attached scsi removable disk sda
Jul 29 09:00:19 localhost kernel: [17218802.664000] sd 5:0:0:0: Attached scsi generic sg1 type 0
Jul 29 09:00:19 localhost kernel: [17218802.668000]   Vendor: USB2.0    Model: CompactFlashCard  Rev:
Jul 29 09:00:19 localhost kernel: [17218802.668000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Jul 29 09:00:19 localhost kernel: [17218802.672000] sd 5:0:0:1: Attached scsi removable disk sdb
Jul 29 09:00:19 localhost kernel: [17218802.672000] sd 5:0:0:1: Attached scsi generic sg2 type 0
Jul 29 09:00:19 localhost kernel: [17218802.768000]   Vendor: USB2.0    Model:  SD/MMC     card  Rev:
Jul 29 09:00:19 localhost kernel: [17218802.768000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Jul 29 09:00:19 localhost kernel: [17218802.772000] SCSI device sdc: 1996800 1024-byte hdwr sectors (2045 MB)
Jul 29 09:00:19 localhost kernel: [17218802.776000] sdc: Write Protect is off
Jul 29 09:00:19 localhost kernel: [17218802.788000] SCSI device sdc: 1996800 1024-byte hdwr sectors (2045 MB)
Jul 29 09:00:19 localhost kernel: [17218802.788000] sdc: Write Protect is off
Jul 29 09:00:49 localhost kernel: [17218802.788000]  sdc:<6>usb 5-2.2.4: reset full speed USB device using ehci_hcd and address 14
Jul 29 09:01:19 localhost kernel: [17218863.132000] usb 5-2.2.4: reset full speed USB device using ehci_hcd and address 14
Jul 29 09:01:50 localhost kernel: [17218893.384000] usb 5-2.2.4: reset full speed USB device using ehci_hcd and address 14
Jul 29 09:02:20 localhost kernel: [17218923.704000] usb 5-2.2.4: reset full speed USB device using ehci_hcd and address 14
Jul 29 09:02:50 localhost kernel: [17218953.992000] usb 5-2.2.4: reset full speed USB device using ehci_hcd and address 14
Jul 29 09:02:51 localhost kernel: [17218954.224000] sd 5:0:0:2: SCSI error: return code = 0x50000
Jul 29 09:02:51 localhost kernel: [17218954.224000] end_request: I/O error, dev sdc, sector 0
Jul 29 09:03:21 localhost kernel: [17218984.360000] usb 5-2.2.4: reset full speed USB device using ehci_hcd and address 14
Jul 29 09:03:51 localhost kernel: [17219014.640000] usb 5-2.2.4: reset full speed USB device using ehci_hcd and address 14
Jul 29 09:04:21 localhost kernel: [17219045.004000] usb 5-2.2.4: reset full speed USB device using ehci_hcd and address 14
Jul 29 09:04:52 localhost kernel: [17219075.292000] usb 5-2.2.4: reset full speed USB device using ehci_hcd and address 14
Jul 29 09:05:22 localhost kernel: [17219105.640000] usb 5-2.2.4: reset full speed USB device using ehci_hcd and address 14
Jul 29 09:05:22 localhost kernel: [17219105.852000] sd 5:0:0:2: SCSI error: return code = 0x50000
Jul 29 09:05:22 localhost kernel: [17219105.852000] end_request: I/O error, dev sdc, sector 0
Jul 29 09:05:22 localhost kernel: [17219105.852000]  unable to read partition table
Jul 29 09:05:22 localhost kernel: [17219105.852000] sd 5:0:0:2: Attached scsi removable disk sdc
Jul 29 09:05:22 localhost kernel: [17219105.852000] sd 5:0:0:2: Attached scsi generic sg3 type 0
Jul 29 09:05:22 localhost kernel: [17219105.860000]   Vendor: USB2.0    Model: MemoryStick Card  Rev:
Jul 29 09:05:22 localhost kernel: [17219105.860000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Jul 29 09:05:22 localhost kernel: [17219105.868000] sd 5:0:0:3: Attached scsi removable disk sdd
Jul 29 09:05:22 localhost kernel: [17219105.868000] sd 5:0:0:3: Attached scsi generic sg4 type 0





> **lkagan said:**
> Remove the usb drive.  Then type the following at a terminal:

```
sudo tail -f /var/log/messages
```

That will start showing that particular log file and will continue to watch it when new entries are appended.  Now hit enter a few times in that terminal to create some space between the last log entry and new ones that are about to appear.  Then plug in your usb drive.  You **should** see some new messages.  Copy and paste those new messages here so we can better be able to help.

Larry

---

### Post by ifokkema on 2006-07-29
Judging from your kernel logs.... it attaches sda, sdb AND sdc for the same drive. Then it keeps resetting sdc.
- What kind of drive are you connecting?
- Does it work on a different OS?
- What's the output of
```
sudo fdisk -l /dev/sd?
```

---

### Post by jamaas on 2006-07-29
Thanks,

Brief synopsis,

Bought new phone, nokia n80, comes with 128 mb mini sd card

bought generic 2 Gig card off ebay

original card from nokia mounts just fine in my little usb-attached card reader as you can see below

When I (unmount) eject at sd from my reader and replace it with the new 2 gig one, which works ok in the phone, and formatted just fine in the phone, then terminal just locks up.  Is this something in the card formatting or something?

Thanks Jim

===========================

Disk /dev/sdc: 125 MB, 125960192 bytes
8 heads, 32 sectors/track, 961 cylinders
Units = cylinders of 256 * 512 = 131072 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         961      122959+   6  FAT16

now I unmount this sd card, replace with new one and everything just hangs!?

jamaas@Bossy-Lite:~$ sudo fdisk -l /dev/sd?





> **ifokkema said:**
> Judging from your kernel logs.... it attaches sda, sdb AND sdc for the same drive. Then it keeps resetting sdc.
- What kind of drive are you connecting?
- Does it work on a different OS?
- What's the output of
```
sudo fdisk -l /dev/sd?
```

---

### Post by ifokkema on 2006-07-29
> **jamaas said:**
> Bought new phone, nokia n80, comes with 128 mb mini sd card

bought generic 2 Gig card off ebay

original card from nokia mounts just fine in my little usb-attached card reader as you can see below

When I (unmount) eject at sd from my reader and replace it with the new 2 gig one, which works ok in the phone, and formatted just fine in the phone, then terminal just locks up.  Is this something in the card formatting or something?
So the terminal locks up? Does your entire PC freeze, or just the terminal?
A FAT16 partition can only have 2 Gb, and FAT16 is far from effecient on disks that size. Possibly the Nokia phone has formatted the drive in a non-fat16 filesystem, but that still shouldn't lock your PC up. Apart from directly in the Nokia, does this card (with the card reader) work on, say, Windows?

---

### Post by jamaas on 2006-07-29
To the best of my knowledge ... no!  I'v just gone and got lspci and it is seen 

lsusb
Bus 005 Device 010: ID 0421:0446 Nokia Mobile Phones
Bus 005 Device 008: ID 0402:5635 ALi Corp.
Bus 005 Device 006: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard ReceiverBus 005 Device 005: ID 413c:9001 Dell Computer Corp.
Bus 005 Device 004: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 005 Device 002: ID 413c:a005 Dell Computer Corp.
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 002 Device 001: ID 0000:0000


> **ifokkema said:**
> Apart from directly in the Nokia, does this card (with the card reader) work on, say, Windows?


Thanks

Jim

---

### Post by gstrock on 2006-07-29
My Lexar JumpDrive automounts, but I can't copy anything to the drive because root owns everything.

I don't think mucking around in /etc/fstab is a viable solution.  This particular usb drive mounts as /media/FlashLinux for me.

Does that mean I have to have a line in fstab just for "FlashLinux"?  what about the next usb device I want to mount that is called something else?

isn't there some way to set a configuration option that all usb devices get mounted with write privleges for all users?

---

### Post by gstrock on 2006-07-29
I found this:

[I]pmount can only be executed by members of
this group (it is root:plugdev 750), hal runs in this group to be able
to detect file systems (but it does not run in 'disk'), and udev
assigns the 'plugdev' group to removable devices (static drives remain
in group 'disk').[/I]

[http://lists.debian.org/debian-devel/2004/11/msg00201.html]("http://lists.debian.org/debian-devel/2004/11/msg00201.html")

so how do we change root:plugdev to 777 or 770

---

### Post by ifokkema on 2006-07-29
> **jamaas said:**
> lsusb
Bus 005 Device 010: ID 0421:0446 Nokia Mobile Phones
Bus 005 Device 008: ID 0402:5635 ALi Corp.
Bus 005 Device 006: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard ReceiverBus 005 Device 005: ID 413c:9001 Dell Computer Corp.
Bus 005 Device 004: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 005 Device 002: ID 413c:a005 Dell Computer Corp.
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 002 Device 001: ID 0000:0000
Isn't that the phone in stead of the card reader? I'm not sure if a card reader should show up in lsusb. But if a card is inserted, that one should show up on lsusb.

If the other card works, it shows all of your drivers are loaded correctly and your system is configured correctly. If then the 2 Gb card is inserted, and your system freezes, it must be something specific with this card. If you can't test this card on Windows, I think it'll be a hard problem to figure out...

> **gstrock said:**
> I found this:
[I]pmount can only be executed by members of
this group (it is root:plugdev 750), hal runs in this group to be able
to detect file systems (but it does not run in 'disk'), and udev
assigns the 'plugdev' group to removable devices (static drives remain
in group 'disk').[/I]

[http://lists.debian.org/debian-devel/2004/11/msg00201.html]("http://lists.debian.org/debian-devel/2004/11/msg00201.html")

so how do we change root:plugdev to 777 or 770
Check if you are in the correct group ID's. When logged in as your user, run:
```
groups
```
It should mention the plugdev group. If not:
```
sudo adduser <your_username> plugdev
```
Log out, log in, and try again.

---

### Post by gstrock on 2006-07-30
another area that looks interesting:
/etc/udev/rules.d/40-permissions.rules

BUS=="usb",                             GROUP="plugdev"
# USB devices (usbfs replacement)
SUBSYSTEM=="usb_device",                MODE="0664"

---

### Post by Dakkar on 2006-08-06
I have this same problem, I have a palmZire 72, and Card Export Program to use it has a SD Card Reader, when I use it with a 512, 128, 64 MB card it works fine, but when I plug a 2Gb card it won't appear has a flash usb disk  and the palm program says this error message: A Sector that was accesed is bad.

My card works perfect on windows, and I readed someplace something about a bug that makes usb driver read more sectors than the total available on card, could this be the problem?

---

