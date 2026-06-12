---
title: "USB drives no longer mount and log output"
date: 2008-11-12
forum: General Help
---

### Post by jrz on 2008-11-12
I frequently transfer files to USB drives or memory sticks, and experience problems often. Currently I cannot mount any USB drives, and searching for a fix I ran across some posts requesting the output of "dmesg | tail -50" and "tail -f /var/log/messages" and ran both commands. The output I received appears to show a problem but I am unaware of how it might be solved. Does anyone understand what it is saying and what needs to be done to fix the problem? I shortened the output of each command to 15 lines and display them here:
(My internal drive is hda, and the external drives mount as sda, sdb, or sdc, depending on how many are connected) Also, the file outputs displayed continue repeating as shown, both with or without a USB drive connected.

dmesg |tail -15
[260722.148444] sdb: Write Protect is off
[260722.148448] sdb: Mode Sense: 00 00 00 00
[260722.148450] sdb: assuming drive cache: write through
[260722.705914] sda : READ CAPACITY failed.
[260722.705918] sda : status=0, message=00, host=7, driver=00 
[260722.705928] sda : sense not available. 
[260722.706623] sda: Write Protect is off
[260722.706627] sda: Mode Sense: 00 00 00 00
[260722.706630] sda: assuming drive cache: write through
[260722.707302] sda : READ CAPACITY failed.
[260722.707303] sda : status=0, message=00, host=7, driver=00 
[260722.707307] sda : sense not available. 
[260722.707896] sda: Write Protect is off
[260722.707900] sda: Mode Sense: 00 00 00 00
[260722.707902] sda: assuming drive cache: write through

tail -f /var/log/messages
Nov 12 13:36:12 amd kernel: [260800.750024] sda : sense not available. 
Nov 12 13:36:12 amd kernel: [260800.750607] sda: Write Protect is off
Nov 12 13:36:13 amd kernel: [260801.890990] sdb : READ CAPACITY failed.
Nov 12 13:36:13 amd kernel: [260801.890993] sdb : status=0, message=00, host=7, driver=00 
Nov 12 13:36:13 amd kernel: [260801.891007] sdb : sense not available. 
Nov 12 13:36:13 amd kernel: [260801.899492] sdb: Write Protect is off
Nov 12 13:36:13 amd kernel: [260801.977249] sdb : READ CAPACITY failed.
Nov 12 13:36:13 amd kernel: [260801.977253] sdb : status=0, message=00, host=7, driver=00 
Nov 12 13:36:13 amd kernel: [260801.977262] sdb : sense not available. 
Nov 12 13:36:13 amd kernel: [260801.978173] sdb: Write Protect is off
Nov 12 13:36:14 amd kernel: [260802.757633] sda : READ CAPACITY failed.
Nov 12 13:36:14 amd kernel: [260802.757637] sda : status=0, message=00, host=7, driver=00

---

### Post by Crafty Kisses on 2008-11-12
See if you can mount it from a terminal.
```
sudo mkdir /media/thumbdrive
sudo mount -t ntfs-3g /dev/sdc1 /media/thumbdrive
```
I'm just assuming your USB drive is **/dev/sdc1** so you'll have to substitute your own information obviously.

---

### Post by jrz on 2008-11-12
I'm not sure whatit should mount as now, and /dev has entries for sda, sdb, and sdc currently. Also the thumbdrives are all formatted as fat, and only the hard drives are formatted as ntfs.
The messages I posted keep rolling out when I tail /var/log/messages and are showing both sda and sdb, although no drives are inserted in the USB slots. It appears that a process has never been killed after a previous insertion.


PS output:
107       4662     1  0 Nov09 ?        00:00:22 /usr/sbin/hald
root      4663  4662  0 Nov09 ?        00:00:00 hald-runner
107       4669  4663  0 Nov09 ?        00:00:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
107       4677  4663  0 Nov09 ?        00:00:00 hald-addon-keyboard: listening on /dev/input/event1
107       4687  4663  0 Nov09 ?        00:00:00 hald-addon-keyboard: listening on /dev/input/event4
107       4690  4663  0 Nov09 ?        00:00:00 hald-addon-keyboard: listening on /dev/input/event5
107       4693  4663  0 Nov09 ?        00:00:00 hald-addon-keyboard: listening on /dev/input/event6
107       4735  4663  0 Nov09 ?        00:00:20 hald-addon-storage: polling /dev/hdc
107      10516  4663  0 Nov09 ?        00:00:21 hald-addon-storage: polling /dev/sda
root     10557     7  0 Nov09 ?        00:00:00 [scsi_eh_8]
root     10559     7  0 Nov09 ?        00:00:15 [usb-storage]
107      10600  4663  0 Nov09 ?        00:00:22 hald-addon-storage: polling /dev/sdb
root     11136     7  0 Nov09 ?        00:00:00 [scsi_eh_13]

---

### Post by Crafty Kisses on 2008-11-12
If the process is still running, I'm not sure what it would be called, there could be another terminal session running somewhere I'm not sure. Post the results of this command:
```
top
```
That will give you a list of running processes. Close all terminals and what not, once you've done that see if there is anything running that shouldn't be like terminal (if you closed all of them, of course) then kill the process you want, you can do that by doing the following:
```
kill *process ID*
```
Then once you've killed the process that's running, try remounting it, and I guess if it's FAT32, it would be something like this then:
```
sudo mount -t fat32-3g /dev/sdc1 /media/thumbdrive
```
Try that and see if that works.

---

### Post by jrz on 2008-11-12
The 'top' command doesn't seem to display the offending processes.
I can resolve the problem temporarily by rebooting, and for a while the drives will mount and dismount properly, but at some point the problem reappears. I'd like to find the source of the problem and eliminate it, rather than find a way to work around it.
I'm uncertain if sda, sdb, and sdc should remain in /dev after the external drives are unmounted. The /media directory cleans up properly each time a drive is mounted and unmounted, but at some point external drives cease to mount.

---

### Post by jrz on 2008-11-12
If you missed my edit in the earlier response, it looks like the offending process which continues to run is /usr/sbin/hald

---

### Post by Crafty Kisses on 2008-11-12
Try the following command to kill the HAL daemon:
```
sudo killall hald
```

---

### Post by jrz on 2008-11-12
I did that, and that stops the messages from rolling out of /var/log/messages.
Inserting a USB device still does not do anything, and the hald process does not re-iniate after being killed when a device is plugged in. I assume this is the process which populates /media/.hal-mtab and /dev/sd[a|b|c]1.

---

### Post by jrz on 2008-11-12
I just rebooted, and checking I find that /dev cleared the entries for sda, sdb, and sdc. Inserting a memory stick I see /dev/sda and /dev/sda1 appear as well as an entry in /media/.hal-mtab and an entry in /media containing the name assigned to the memory stick, and an icon on the desktop. The device works properly, and I can read from and write to it.
Clicking on eject, the icon disappears, the device name file in /media disappears, and /media/.hal-mtab becomes a 0 byte file. In /dev the entry for sda1 disappears, and the entry sda remains until I unplug the device from the usb slot and at that time it also disappears. 

/usr/bin/hald remains loaded, but shows sleeping.

I repeated this several times with no problems encountered. Now I have to find out what it is that has to be done to create the problem anew.

This problem is keeping me from moving from 7.04 to 8.10 as I need to move all my personal files to an external drive before starting. I was hoping 8.10 might resolve the problem, but can't get to the point where I can install it.

---

