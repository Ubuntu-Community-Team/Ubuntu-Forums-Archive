---
title: "Sony Optiarc DVD ROM not detected"
date: 2015-02-16
forum: Hardware
---

### Post by alan52 on 2015-02-16
I have been trying out Ubuntu on an elderly Rock laptop that has been running Windows 8. Following a LiveCD (or USB stick) install, all my devices have been detected perfectly, including an inbuilt Bison cam that Windows refused to acknowledge and pleased with the increase in speed and responsiveness I decided to fully install the system on the hard disk, erasing Windows in the process. I am somewhat disappointed therefore to find that the internal DVD ROM is not now detected whilst all other devices are and fully functional.

I have run LiveCD sessions from both a DVD and USB stick and checked that yes, the DVD ROM is detected and plays a music CD on insertion and whilst a video DVD is detected and displayed, the LiveCD install lacks the appropriate drivers to play it, which I understand. I have also checked the various foldes and see that on the LiveCD installation the cdrom folder is populated and the dev folder contains not only a disk folder but also cdrom, cdrw, dvdrom and dvdrw files amongst others which are all missing from the hard disk install. The Disks application also correctly records the DVD ROM details on the LiveCD install but not on hard disk.

As a newcomer to the world of Linux I find this all rather baffling as I would expect the OS to either detect my hardware on both or neither type of install and wonder whether I missed something when installing to the hard disk. If anyone can give me any help on this, or at least point me in the right direction, I should be most grateful. Thank you.

---

### Post by ajgreeny on 2015-02-16
You have totally confused me about whether or not the DVD drive is detected; in one breath you say it was and then you say it is not.

Are you trying to play a commercial DVD of a movie or something similar?  That requires that you install a package, libdvdcss2, that is not available directly on the install medium so will have to get that done first and then come back again if there are still problems.

See [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) for all the info you should need.

---

### Post by alan52 on 2015-02-16
Hi ajgreeny and thanks for your quick response. Sorry to confuse you but in essence the DVD drive is _only_ detected when I use LiveCD to try but not install Ubuntu, but when I reboot into the hard disk installation the DVD ROM is absent. Hope this clarifies it.

---

### Post by ajgreeny on 2015-02-16
Let's see the output of terminal command **sudo lshw -c disk** which should normally show your CD/DVD drive listed.

---

### Post by alan52 on 2015-02-16
Output of sudo lshw -c disk

 *-disk                  
       description: ATA Disk
       product: ST910021AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 3.06
       serial: 3MH0YAT4
       size: 93GiB (100GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=512 signature=2b43baed

---

### Post by alan52 on 2015-02-17
Good morning aj. I was wondering overnight what would happen if I booted into the DVD ISO and ran the lshw command from there. This is the output I got:-

ubuntu@ubuntu:~$ sudo lshw -c disk
  *-disk                  
       description: ATA Disk
       product: ST910021AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 3.06
       serial: 3MH0YAT4
       size: 93GiB (100GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=512 signature=2b43baed
  *-cdrom
       description: DVD-RAM writer
       product: DVD RW AD-7530A
       vendor: Optiarc
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       logical name: /cdrom
       version: EX32
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /cdrom
          capabilities: partitioned partitioned:dos
          configuration: mount.fstype=iso9660 mount.options=ro,noatime signature=4a022e4f state=mounted
ubuntu@ubuntu:~$ 

It would seem therefore that the hard disk installation is at fault though I am none the wiser on how to fix it. Hope this is of some help.

Regards Alan

---

### Post by ajgreeny on 2015-02-17
Can you boot to the DVD live system again but this time take the option to "check the Install medium", or whatever the wording of that is.

I am simply wondering if the install DVD is not as good a burn as you would want, or alternatively that the .iso image file was not good, which you can check with the hashes listed at [UbuntuHashes - MD5sum]("https://help.ubuntu.com/community/UbuntuHashes")

---

### Post by alan52 on 2015-02-18
I have re-checked the original downloaded image and the checksum agrees on md5sum. I then booted into the DVD as suggested and ran an integrity check on the install disk which came back with no errors.

It seems as though I shall have to invest in an external DVD ROM as this does not to appear to be as simple a problem as I originally thought in my ignorance.

---

### Post by alan52 on 2015-02-19
Having discovered the alternate installation menu by pressing a key whilst the install DVD is booting (courtesy of the previous reply for a slightly different purpose) I decided to explore other boot options by going into F6 and was meaning to check each individually to see the effect. The first option I tried was to set ACPI off which I did and then proceeded to install, which amazingly corrected my problem and I now have full use of the internal DVD mentioned above. Both music CD's play automatically and so do video DVD's. Quite why this works is beyond my technical knowledge but I am grateful anyway.

My thanks to ajgreeny for the help and pointing me in a different direction which ultimately has proved successful (and saved me the cost of an external player).

---

