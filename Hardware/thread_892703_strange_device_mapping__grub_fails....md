---
title: "strange device mapping / grub fails..."
date: 2008-08-17
forum: Hardware
---

### Post by ironfist1916 on 2008-08-17
Hi everyone

I got a problem while installing ubuntu server 8.04, which led me later to a very strange issue, maybe someone could give a hint...

the situation:
I have a small server which serves mainly as a jukebox. The design goal was to keep it very silent and with a low load.
The hardware is a via hush pc which is entirely passively cooled. to minimize the last moving part (the harddisc), I decided to put the actual system on a usb stick

I was running fedora core 2 with this setup for several years now and it worked as wanted... (and still runs ok)
=> / is on the usb stick, which comes as first scsi hard drive
=> the other partitions are on the (first and only IDE) disc

the motivation to upgrade:
FC2 is very old now and I hoped to get better power-saving options with a newer distro...

I first tried fc9, but it had some issues with my hardware and it was generally just an overkill...
(I did install FC9 on a 2nd USB Stick and it worked generally without issues...!)

goal:
- install ubuntu 8.04 server on a 2nd usb stick

the installation first ran smooth - i could locate the usb-stick and ubuntu installed on a new 12GB partition on the stick.

the problems:
- grub was set up by the installer, but after the reboot grub hung:
  "loading stage 1.5"
  (after a very long time)
  "Error 5"

trying to fix it:
- I tried several things to get it running (with super grub, live cds, etc.) - no luck! :-(
- the result was always the same: partition not found or corrupt...

now the really strange stuff:
- booted the old Fedora Core 2
- now look at this mount or df respectively:

# mount
**/dev/sda1 on / type ext3 (rw)**
none on /proc type proc (rw)
none on /sys type sysfs (rw)
none on /dev/pts type devpts (rw,gid=5,mode=620)
usbdevfs on /proc/bus/usb type usbdevfs (rw)
/dev/hda1 on /boot type ext3 (rw)
none on /dev/shm type tmpfs (rw)
/dev/hda8 on /home type ext3 (rw)
/dev/hda9 on /tmp type ext3 (rw)
/dev/hda5 on /usr type ext3 (rw)
/dev/hda3 on /var2 type ext3 (rw)
/dev/hda10 on /var/ext1 type ext3 (rw)
sunrpc on /var2/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
[B]/dev/sda1 on /mnt/ubuntu type ext3 (rw)
[/B]
# df -h
Filesystem            Size  Used Avail Use% Mounted on
**/dev/sda1             981M  951M     0 100% /**
/dev/hda1              99M   15M   80M  16% /boot
none                  221M     0  221M   0% /dev/shm
/dev/hda8             487M  8.4M  453M   2% /home
/dev/hda9             244M  4.1M  227M   2% /tmp
/dev/hda5             3.9G  2.6G  1.2G  70% /usr
/dev/hda3             3.9G  819M  2.9G  22% /var2
/dev/hda10            257G  192G   52G  79% /var/ext1
**/dev/sda1              12G  729M   11G   7% /mnt/ubuntu**

Note: /dev/sda1 is mounted 2 times!
- once as the fc2-/ and once it is the partition ubuntu is installed on...
- i checked the files: / and /mnt/ubuntu ARE two different partitions, with their different files on, but they claim to be on the same device!! What the heck???

it is possible that i messed with the partition tables somewhere, but i can't really imagine what happened...

any clue anyone?

thx anyway ;-)

---

### Post by caljohnsmith on 2008-08-17
From the Grub online manual:
> **Error 5** : Partition table invalid or corrupt
This error is returned if the sanity checks on the integrity of the partition table fail. This is a bad sign. 
And the fact you have /dev/sda1 mounted twice... Yes, I would guess you somehow have a corrupt partition table, but that is only a guess based on what you have said so far. "testdisk" is a great utility that can help you rewrite your drive's partition table. I would check it out. Here's a [how-to guide]("http://www.users.bigpond.net.au/hermanzone/p21.html") for using testdisk for partition recovery that might help you.

---

### Post by ironfist1916 on 2008-08-18
Hi caljohnsmith

Yepp, I already got that one 'bout 'Error 5' and the partition tables.

But I'm not quite sure this fits.

See, those two partitions are on two physically different disks (!)

/dev/sda1 aka / is on one 1GB memory stick (and healthy - it's my active root of the system (FC2) that still runs like a charm...;-)

/dev/sda1 aka /mnt/ubuntu is on a second 2GB memory stick (and is also readable, writable and 'usable' - only while booting i can't access it.

and more then everything i just distrust this very situation... ;-)

---

