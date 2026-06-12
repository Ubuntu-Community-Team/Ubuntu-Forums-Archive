---
title: "USB Stick not mounting"
date: 2005-10-22
forum: Hardware &amp; Laptops
---

### Post by Irony on 2005-10-22
I recently got a usb memory stick and on putting it into the usb port it was immediately detected and a nautilus window opened so I copied data over to it.

The problem is that on unmounting it, removing the stick and then putting the stick back in nothing happens.

If I go to the computer an icon with usb flash memory is visible but clicking on it produces a window with;
[PHP]
Error: device /dev/sda1 is already mounted to /media/usbdisk
Error: could not execute pmount[/PHP]

A folder has been created by inserting the usb stick;

*/media/usbdisk*

But there is nothing in it. If I type;

*sudo mount -t vfat /dev/sda1 /media/usbdisk*

Nothing happens. Is this a bug? Is there a work around.

---

### Post by Irony on 2005-10-25
Haven't got anywhere with this, however loading information onto the stick from Ubuntu is much faster than doing it in Windows.

For example 50 Mb took about 10 mins in Windows whereas 150 Mb took a few seconds in Ubuntu.

The problem is the stick works first time after a boot up but doesn't work if unmounted then remounted in Ubuntu, whereas in Windows XP Home it does.

---

### Post by Irony on 2005-10-25
This is my dmesg;

[PHP][4295557.619000] SCSI error : <5 0 0 0> return code = 0x70000
[4295557.619000] end_request: I/O error, dev sda, sector 534882
[4295557.619000] SCSI error : <5 0 0 0> return code = 0x70000
[4295557.619000] end_request: I/O error, dev sda, sector 534883
[4295557.619000] SCSI error : <5 0 0 0> return code = 0x70000
[4295557.619000] end_request: I/O error, dev sda, sector 534884
[4295557.620000] usb 5-1: USB disconnect, address 2
[4295557.620000] SCSI error : <5 0 0 0> return code = 0x70000
[4295557.620000] end_request: I/O error, dev sda, sector 534885
[4295557.620000] SCSI error : <5 0 0 0> return code = 0x70000
[4295557.620000] end_request: I/O error, dev sda, sector 534886
[4295557.620000] SCSI error : <5 0 0 0> return code = 0x70000
[4295557.620000] end_request: I/O error, dev sda, sector 534887
[4295557.620000] SCSI error : <5 0 0 0> return code = 0x70000
[4295557.620000] end_request: I/O error, dev sda, sector 534888
[4295557.620000] SCSI error : <5 0 0 0> return code = 0x70000
[4295557.620000] end_request: I/O error, dev sda, sector 534889
[4295557.621000] SCSI error : <5 0 0 0> return code = 0x70000
[4295557.621000] end_request: I/O error, dev sda, sector 534890
[4296243.376000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on is a0060/serio0).
[4296243.376000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296243.439000] atkbd.c: Unknown key released (translated set 2, code 0xaa on i sa0060/serio0).
[4296243.439000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.[/PHP]

---

### Post by Samuel on 2005-10-25
```
sudo /etc/init.d/hotplug restart
``` 
usually fixes this for me

---

### Post by Irony on 2005-10-25
Unfortunately that didn't work.

I've installed *usbmount* via synaptic so I'll see if that works on booting up tomorrow.

---

### Post by BatsotO on 2005-10-25
Can you try with another usb stick, coz maybe the problem was with the usb.

---

### Post by Irony on 2005-10-26
The problem seems to have been solved though I'm not sure that it has anything to do with installing *usbmount*.

Instead of unmounting the memory stick I just pull it out. The desktop icon disappears. Then on pushing the stick back in it mounts, the icon appears on the desktop and it is useable.

Maybe I'll uninstall *usbmount* and see if pulling and pushing the stick in works with out clicking unmount.

---

### Post by WayneSchuller on 2005-10-28
Remove any entries you have from your /etc/fstab for the removable devices (let the hotplug system create them magically)

and then follow my instructions at:
[http://www.ubuntuforums.org/showthread.php?p=449299#post449299](http://www.ubuntuforums.org/showthread.php?p=449299#post449299)

---

### Post by Irony on 2005-10-28
Thanks WayneSchuller I'll have a look into that.

Like many others I have noticed that hotplug doesn't okay on boot-up. My cd-roms both mount properly on inserting a disc (icon appears on desktop) - they work fine.

I thought my usb stick was working after installing *usbmount* but in fact it still works first time, but not properly if I pull it out then put it back in. The stick shows on the desktop second time round as on the first time but doesn't accept data properly second time round, presumably due to the improper dismounting of just pulling it out. Of course if I dismount it, it then won't remount.

Here's my fstab file, it doesn't have removable devices unless you count cd-roms and floppies as removable.

[PHP]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  vfat    rw,user,noauto  0       0
/dev/hda1       /mnt/XPa  ntfs    nls=utf8,umask=0222 0       0
/dev/hda3       /mnt/XPb  ntfs    nls=utf8,umask=0222 0       0
/dev/hdb1       /mnt/2nd  vfat    defaults,umask=000  0       0
/dev/hda4       /mnt/Ubb      ext3    defaults        0       0[/PHP]

---

### Post by jamieson on 2005-10-30
When I insert my CompactFlash card into the PCMCIA slot (using adapter) breezy shows an icon on the desktop for a second, then it's gone.  Very strange, it worked the first time I tried it, though.  Tried rebooting, restarting hotplug, etc.  Tried manually mounting it... nope.  Tried different CF cards, same problem.  I get the following kernel messages:

ct 30 09:13:51 localhost kernel: [ 3494.105914] Probing IDE interface ide2...
Oct 30 09:13:51 localhost kernel: [ 3494.369704] hde: SanDisk SDCFB-128, CFA DIS K drive
Oct 30 09:13:52 localhost kernel: [ 3494.981257] ide2 at 0x100-0x107,0x10e on ir q 5
Oct 30 09:13:52 localhost kernel: [ 3494.984925] hde: max request size: 128KiB
Oct 30 09:13:52 localhost kernel: [ 3494.984940] hde: 250880 sectors (128 MB) w/ 1KiB Cache, CHS=980/8/32
Oct 30 09:13:52 localhost kernel: [ 3494.984952] hde: cache flushes not supporte d
Oct 30 09:13:52 localhost kernel: [ 3494.988778]  /dev/ide/host2/bus0/target0/lu n0: p1
Oct 30 09:13:52 localhost kernel: [ 3494.996084] ide-cs: hde: Vcc = 3.3, Vpp = 0 .0
Oct 30 09:13:52 localhost kernel: [ 3495.124780]  /dev/ide/host2/bus0/target0/lu n0: p1
Oct 30 09:13:52 localhost kernel: [ 3495.140882]  /dev/ide/host2/bus0/target0/lu n0: p1
Oct 30 09:13:52 localhost kernel: [ 3495.401266]  /dev/ide/host2/bus0/target0/lu n0: p1
Oct 30 09:13:53 localhost kernel: [ 3495.630785]  /dev/ide/host2/bus0/target0/lu n0: p1
Oct 30 09:13:53 localhost kernel: [ 3495.666776] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

---

### Post by PaganHippie on 2005-10-30
Are you using any USB hubs?  If so, try physically removing the hub(s), reboot the computer, & try hotplugging again.

I was having a similar problem, Ubuntu was seeing neither my USB thumb-drive nor my iPod Shuffle. Both lsusb and usbview would hang, producing no output. I removed the hub, and now everything works as it should. It seems that the (cheap) hub I was using was somehow pulling the entire USB subsystem down in Ubuntu.

Go figure....  :???:

---

### Post by metoo on 2005-10-30
You might have fallen into the cache pit!

When you copied data with lightning speed with ubuntu, the feedback you saw was only the copy process from the desktop program to the PC cache.
The actual writing of the data will take as long as with windows, which apparently does not cache the data and gives therefore the user a better feedback of the copy process.
You will notice, that the led on the stick will still blink and you can not manually unmount the stick, even if your desktop program already signals the end of a successful copy process - because the underlying system is still copying data...

So by pulling out the stick after this bleeding fast copy process the first time, you probably have corrupted the file system of the stick.
Not a big deal, if you can live with the data loss on it.
Simply re-format the stick in windows or ubuntu.
If more is corrupted, you can first re-create the partition with cfdisk. (cfdisk /dev/sda)
To format the partition of the stick with a Fat 32 file system try something like
mkfs.vfat -F 32 /dev/sda1
if /dev/sda1 is indeed you memory stick. Better be sure about it!
May be you should check with cfdisk first, sometimes sticks have multiple partitions (e.g 1 for booting or hidden partitions). You can still make one big partition then, but you might lose some (windows) functionality.

---

### Post by mephtny on 2006-02-09
Hi,

I have the same problem like jamieson with my PCMCIA Card Reader. When I put an SD-Card into the reader the volume gets mounted and for a second an icon appears on the desktop before it is unmounted.

I think the gnome-volume-manager does this. Heres some output:

```

manager.c/1619: New Device: /org/freedesktop/Hal/devices/pcmcia__1__1
manager.c/1619: New Device: /org/freedesktop/Hal/devices/computer_ide_2_0
manager.c/1619: New Device: /org/freedesktop/Hal/devices/storage_model_5in1_Adapter
manager.c/1642: not a mountable volume: /org/freedesktop/Hal/devices/storage_model_5in1_Adapter
manager.c/1686: Changed: /dev/hde
manager.c/1619: New Device: /org/freedesktop/Hal/devices/volume_uuid_3827_126C
manager.c/1686: Changed: /dev/hde1
manager.c/1258: mounting /org/freedesktop/Hal/devices/volume_uuid_3827_126C...
manager.c/696: executing command: /usr/bin/pmount-hal /org/freedesktop/Hal/devices/volume_uuid_3827_126C
manager.c/1878: Mounted: /org/freedesktop/Hal/devices/volume_uuid_3827_126C
manager.c/1896: Unmounted: /org/freedesktop/Hal/devices/volume_uuid_3827_126C

```

My kernel log shows nearly the same as posted by jamieson above.

Has there been any progress in that? Is there a solution or what else might be the problem?

---

### Post by mephtny on 2006-02-09
There seems to be a workaround for the last one.

[http://bugzilla.ubuntu.com/show_bug.cgi?id=17607](http://bugzilla.ubuntu.com/show_bug.cgi?id=17607)

replace your /etc/dev.d/blocks/hal-umount.dev with the one attached to the bug report. (and keep a copy of the original to be sure) 
works fine for me.

---

### Post by beetroot on 2006-02-09
Sorry for my english.

Do you check permission user hal   (hardware abstract layer).
He do automount.

check 
$groups hal

you check user hal to automaticly mounting CD,USB, etc.

$ groups hal
hal : hal cdrom floppy plugdev


you check - information in english
[http://ubuntuforums.org/archive/index.php/t-95310.html](http://ubuntuforums.org/archive/index.php/t-95310.html)

mayby it resolve problem.

In my system after this automont returns.

---

