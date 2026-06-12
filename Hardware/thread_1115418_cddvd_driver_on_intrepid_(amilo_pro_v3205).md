---
title: "cd/dvd driver on intrepid (amilo pro v3205)"
date: 2009-04-03
forum: Hardware
---

### Post by splashhtc on 2009-04-03
hello all...

i have a Fujitsu Siemens...Amilo pro v3205...2.0 GHz.

i have absolutely no problems with Ubuntu regarding hardware detection (for the past 4 yrs) etc....except one...

my CD/DVD drive.,. it only detects and mounts the cds...dvd are as if they weren't there...cant detect dvds or burn them ofcourse...

ive been on the irc channels searching for help and here ofcourse and i googled it..and still no results...

the following is a copy paste from my v3205 manual...so people would stop telling me i dont have dvd or burner :-k:? on my laptop...(which i used to use on windoze..)



Fixed drives
DVD+/- RW Dual layer (+R) Multiformat DVD writer with
double layer support
:lolflag:



hope someone can help me out here plz...cuz i have loads of work stuff on dvds , and im fed up of needing to use a windoze to open the dvds

thanks all...

---

### Post by oobe-feisty on 2009-04-03
you could try adding this line to your /boot/grub/menu.lst file all-generic-ide=1

e.g  /boot/vmlinuz-2.6.27-11-generic root=UUID=d42a5628-b05e-4b0e-9a86-6d95ec98ed9c ro quiet splash all-generic-ide=1 

you could also try acpi=off aswell.


also post back with "sudo lshw | grep cdrom" if the above wont work

also i had a problem where my dvd-rw drive could not read disks at all it started off just a little flaky and got worse and worse until it was unusable i upgraded the firmware from a cd forum and it worked fine after that

---

### Post by splashhtc on 2009-04-04
*-cdrom        
                logical name: /dev/cdrom
        *-cdrom
             logical name: /dev/cdrom1
             logical name: /dev/cdrom2
                logical name: /dev/cdrom1

---

### Post by splashhtc on 2009-04-04
see..the thing is it does read 2 cd devices.....thats whats making me mad...!

---

### Post by oobe-feisty on 2009-04-04
> **splashhtc said:**
> see..the thing is it does read 2 cd devices.....thats whats making me mad...!

sorry i typed the wrong things mine came out the same as yours using the last lshw i posted this is what might shed some light 

sudo lshw -class disk


this is the relavent output on my machine 

*-cdrom                        
       description: DVD-RAM writer
       product: DVD A  DH20A4P    
       vendor: ATAPI              
       physical id: 0.1.0         
       bus info: scsi@3:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 9P59
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc


did you try either of those grub options i showed you

---

### Post by splashhtc on 2009-04-04
i opened the file in the boot/grub...but i wanted to ask u where would i add the line? or is that irrelevent..

anyway ..


-cdrom                 
       description: DVD writer
       product: DVD-RW GWA-4082N
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: CW02
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=nodisc

-cdrom
       description: SCSI CD-ROM
       product: Mass Storage
       vendor: HUAWEI
       physical id: 0
       bus info: scsi@9:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrom2
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: 2.31
       capabilities: removable audio
       configuration: ansiversion=2 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
          capabilities: partitioned partitioned:mac



as u see i do have a dvd reader/writer...:p

---

### Post by splashhtc on 2009-04-04
plz ommit the second part of my previous post...

the following is the correct one.,..( I REMOVED THE HUWAUEI USB MODEM AND RAN THE LSHW COMMAND)

cdrom
description: DVD writer
product: DVD-RW GWA-4082N
vendor: HL-DT-ST
physical id: 0.0.0
bus info: scsi@4:0.0.0
logical name: /dev/cdrom
logical name: /dev/cdrw
logical name: /dev/dvd
logical name: /dev/dvdrw
logical name: /dev/scd0
logical name: /dev/sr0
version: CW02
capabilities: removable audio cd-r cd-rw dvd dvd-r
configuration: ansiversion=5 status=nodisc



i wonder why that usb shows up on the system as a cd:S

---

### Post by oobe-feisty on 2009-04-05
here is an example for grub 

title           Kubuntu 8.04.1, kernel 2.6.26.5-version1
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.26.5-version1 root=UUID=e8abcd62-fdb1-4b0e-bc78-97a05b9d2dcc ro quiet splash all_generic_ide=1 
initrd          /boot/initrd.img-2.6.26.5-version1
quiet
savedefault

this is from an old install backup basically you can add all_generic_ide=1 right after ro or after the other options it doesent matter

---

