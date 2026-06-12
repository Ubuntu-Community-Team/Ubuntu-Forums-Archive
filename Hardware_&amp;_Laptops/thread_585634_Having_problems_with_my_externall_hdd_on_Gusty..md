---
title: "Having problems with my externall hdd on Gusty."
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by tylerdustin2008 on 2007-10-21
Hey all.

Im new to linux, but I like the look. I had Fedora 7 installed last night, it was to complicated so I have installed Gusty. And All of my media is on my external hdd. I am getting the same error on Gusty and Fedora. 

"Unable to mount drive"

Any help?

Thanks.

Tyler

---

### Post by tylerdustin2008 on 2007-10-22
Anything guys?

---

### Post by Linicks on 2007-10-22
What is it, USB drive?

I presume Ubuntu is up and running OK?

So, explain what the drive is, how you plug it in etc.

Nick

---

### Post by tylerdustin2008 on 2007-10-22
Its a 500gb Western Digital with a 3rd party enclosure. I take the USB cable and plus it into the back of my laptop, and it says "Unable to mount Volume".

---

### Post by Linicks on 2007-10-22
Ummm.  Not much to go on.

OK, try this please.

Make sure the drive is NOT attached.

In a console, run this:

 :~$ sudo tail -f /var/log/syslog > debug_drive.txt

Plug in the drive.

Let it all finish, for say 60 seconds.  Then hit Ctrl+C to exit the tail.

You will now have a file called debug_drive.txt

Attach, or paste the output of that file here.

Nick

---

### Post by tylerdustin2008 on 2007-10-22
Im doing exactly as you say,  But there is no file called debug_drive.txt anywhere.

---

### Post by Linicks on 2007-10-23
Well, the file will be created in the directory of where you run:

sudo tail -f /var/log/syslog > debug_drive.txt

OK, then, I was trying to make it easy.  Plug in the disk, then look at the last 100 lines or so of /var/log/syslog, and if you can, post them here so we can see what is going on.

Nick

---

### Post by tylerdustin2008 on 2007-10-23
Deleted...

---

### Post by Linicks on 2007-10-23
I am sorry, there is too much noise there to see what is going on.

OK. look at /var/log/syslog, and go to the end and note the time.

Plug in the drive.  Wait 60 seconds. Try to mount it. Wait 60 seconds.  Now unplugin.

Now post the last bit of /var/log/syslog from the time observed (above) to the end of the log.

It should be pretty small - maybe 50 - 100 lines at most.

Nick

---

### Post by tylerdustin2008 on 2007-10-23
Ok here you go, this is what it says.

Oct 23 15:39:29 tyler-laptop kernel: [  348.860000] usb 4-3: new high speed USB device using ehci_hcd and address 2
Oct 23 15:39:29 tyler-laptop NetworkManager: <debug> [1193168369.636352] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4fc_c15_WDC_WD5000_____WD_WMANU1405928').
Oct 23 15:39:29 tyler-laptop kernel: [  348.992000] usb 4-3: configuration #1 chosen from 1 choice
Oct 23 15:39:29 tyler-laptop kernel: [  349.104000] usbcore: registered new interface driver libusual
Oct 23 15:39:29 tyler-laptop NetworkManager: <debug> [ 1193168369.761521] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4fc_c15_WDC_WD5000_____WD_WMANU1405928_if0').
Oct 23 15:39:29 tyler-laptop kernel: [  349.156000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Oct 23 15:39:29 tyler-laptop kernel: [  349.156000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Oct 23 15:39:29 tyler-laptop kernel: [  349.160000] Initializing USB Mass Storage driver...
Oct 23 15:39:29 tyler-laptop kernel: [  349.160000] scsi2 : SCSI emulation for USB Mass Storage devices
Oct 23 15:39:29 tyler-laptop kernel: [  349.160000] usb-storage: device found at 2
Oct 23 15:39:29 tyler-laptop kernel: [  349.160000] usb-storage: waiting for device to settle before scanning
Oct 23 15:39:29 tyler-laptop kernel: [  349.164000] usbcore: registered new interface driver usb-storage
Oct 23 15:39:29 tyler-laptop kernel: [  349.164000] USB Mass Storage support registered.
Oct 23 15:39:29 tyler-laptop NetworkManager: <debug> [1193168369.824528] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4fc_c15_WDC_WD5000_____WD_WMANU1405928_usbraw').
Oct 23 15:39:34 tyler-laptop kernel: [  354.160000] usb-storage: device scan complete
Oct 23 15:39:34 tyler-laptop kernel: [  354.164000] scsi 2:0:0:0: Direct-Access     WDC WD50 00YS-01MPB0           PQ: 0 ANSI: 2
Oct 23 15:39:34 tyler-laptop kernel: [  354.180000] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Oct 23 15:39:34 tyler-laptop kernel: [  354.180000] sd 2:0:0:0: [sdb] Write Protect is off
Oct 23 15:39:34 tyler-laptop kernel: [  354.180000] sd 2:0:0:0: [sdb] Mode Sense: 38 00 00 00
Oct 23 15:39:34 tyler-laptop kernel: [  354.180000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Oct 23 15:39:34 tyler-laptop kernel: [  354.184000] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Oct 23 15:39:34 tyler-laptop kernel: [  354.184000] sd 2:0:0:0: [sdb] Write Protect is off
Oct 23 15:39:34 tyler-laptop kernel: [  354.184000] sd 2:0:0:0: [sdb] Mode Sense: 38 00 00 00
Oct 23 15:39:34 tyler-laptop kernel: [  354.184000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
Oct 23 15:39:34 tyler-laptop kernel: [  354.184000]  sdb: sdb1
Oct 23 15:39:34 tyler-laptop kernel: [  354.192000] sd 2:0:0:0: [sdb] Attached SCSI disk
Oct 23 15:39:34 tyler-laptop kernel: [  354.192000] sd 2:0:0:0: Attached scsi generic sg2 type 0
Oct 23 15:39:36 tyler-laptop NetworkManager: <debug> [1193168376.581285] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4fc_c15_WDC_WD5000_____WD_WMANU1405928_if0_scsi_host').
Oct 23 15:39:36 tyler-laptop NetworkManager: <debug> [1193168376.584146] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4fc_c15_WDC_WD5000_____WD_WMANU1405928_if0_scsi_host_scsi_device_lun0').
Oct 23 15:39:36 tyler-laptop NetworkManager: <debug> [1193168376.623740] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4fc_c15_WDC_WD5000_____WD_WMANU1405928_if0_scsi_host_scsi_device_lun0_scsi_generic').
Oct 23 15:39:36 tyler-laptop NetworkManager: <debug> [1193168376.854150] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_WDC_WD50_00YS_01MPB0_WDC_WD5000_WD_WMANU1405928_0_0').
Oct 23 15:39:36 tyler-laptop NetworkManager: <debug> [1193168376.944338] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_E8806E28806DFD86').
Oct 23 15:41:04 tyler-laptop NetworkManager: <debug> [ 1193168464.500399] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4fc_c15_WDC_WD5000_____WD_WMANU1405928_if0_scsi_host_scsi_device_lun0_scsi_generic').
Oct 23 15:41:04 tyler-laptop NetworkManager: <debug> [ 1193168464.524794] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_E8806E28806DFD86').
Oct 23 15:41:04 tyler-laptop NetworkManager: <debug> [1193168464.562934 ] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4fc_c15_WDC_WD5000_____WD_WMANU1405928_if0_scsi_host_scsi_device_lun0').
Oct 23 15:41:04 tyler-laptop NetworkManager: <debug> [ 1193168464.565862] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4fc_c15_WDC_WD5000_____WD_WMANU1405928_if0_scsi_host').
Oct 23 15:41:04 tyler-laptop NetworkManager: <debug> [ 1193168464.574362] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4fc_c15_WDC_WD5000_____WD_WMANU1405928_usbraw').
Oct 23 15:41:04 tyler-laptop NetworkManager: <debug> [ 1193168464.577287] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_WDC_WD50_00YS_01MPB0_WDC_WD5000_WD_WMANU1405928_0_0').
Oct 23 15:41:04 tyler-laptop NetworkManager: <debug> [ 1193168464.579186] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4fc_c15_WDC_WD5000_____WD_WMANU1405928_if0').
Oct 23 15:41:04 tyler-laptop NetworkManager: <debug> [ 1193168464.581334] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4fc_c15_WDC_WD5000_____WD_WMANU1405928').
Oct 23 15:41:04 tyler-laptop kernel: [  443.844000] usb 4-3: USB disconnect, address 2

---

### Post by Linicks on 2007-10-23
OK, it looks good?

Try this.

In your home directory:

```
mkdir extdrive
```

That will create a directory called 'extdrive'

Now plug the drive in.  Wait 60 seconds.  Issue this:

```
sudo mount /dev/sdb1 /home/<yourusername>/extdrive
```

That should mount it to the directory we just created (<yourusername> needs to be what your home directory is called (tyler or whatever).

Now try:

```
ls /home/<yourusername>/extdrive
```

Nick

---

### Post by tylerdustin2008 on 2007-10-23
Sorry for being an idiot, but how do i make this "mkdir extdrive"?

Tyler

---

### Post by tylerdustin2008 on 2007-10-23
I think i did everything correctly.

tyler@tyler-laptop:~$ mkdir extdrive
tyler@tyler-laptop:~$ sudo mount /dev/sdb1 /home/tyler/extdrive
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /home/tyler/extdrive -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /home/tyler/extdrive ntfs-3g defaults,force 0 0
tyler@tyler-laptop:~$ sudo mount /dev/sdb1 /home/<tyler>/extdrive
bash: tyler: No such file or directory
tyler@tyler-laptop:~$

---

### Post by Linicks on 2007-10-23
OK, so it is a NTFS filesytem.

Also, the <tyler> was an example.  I don't know what your home directory is called.

type:

```
echo $HOME
```


The output will show you your home directory.  You need to 'mkdir extdrive' in you home directory, then mount the disk as explained.

mount -t ntfs-3g /dev/sdb1 /home/tyler/extdrive -o force
The ABOVE line needs the /home/tyler/ bit changing to whatever was produced above by the echo $HOME command.

This is so easy, but so hard to explain remotely.
 
Nick

---

### Post by tylerdustin2008 on 2007-10-23
I do that last command and it says this.

> tyler@tyler-laptop:~$ mount -t ntfs-3g /dev/sdb1 /home/tyler/extdrive -o force
mount: only root can do that


And type in su root. Then my password. and it says.

> su: Authentication failure
Sorry.

I have only entered one password on this entire computer......

There is no way to take remote access is there?

---

### Post by Linicks on 2007-10-23
> **tylerdustin2008 said:**
> There is no way to take remote access is there?
There is, but you DO NOT want to start doing that with anybody.  So don't.

```
sudo mount -t ntfs-3g /dev/sdb1 /home/tyler/extdrive -o force
```

Nick

---

### Post by tylerdustin2008 on 2007-10-23
Thanks Nick! You got it working for me.

Have a great day.

---

### Post by Linicks on 2007-10-24
OK, but now remember that you are mounting a NTFS fs.  The reason it wasn't mounted auto looks like Ubuntu does that as a precaution, as writing to NTFS paritions can be hazardous (to say the least) from Linux.

Nick

---

