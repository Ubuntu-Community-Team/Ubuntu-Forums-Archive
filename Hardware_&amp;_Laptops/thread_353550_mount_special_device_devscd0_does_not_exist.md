---
title: "mount: special device /dev/scd0 does not exist"
date: 2007-02-04
forum: Hardware &amp; Laptops
---

### Post by brettg on 2007-02-04
Hi all

On a new install of dapper or edgy i have the same problem.

#mount /media/cdrom
mount: special device /dev/scd0 does not exist

/etc/fstab says;

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0

ls -al /media says;

lrwxrwxrwx 1 root root 6 2007-02-04 13:03 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2007-02-04 13:03 cdrom0

The problem is that /dev/scd0 doesn't exist.

When I do lspci it tells me about the SATA controller;

0000:00:1d.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
0000:00:1e.0 ISA bridge: Intel Corporation 82801GHM (ICH7-M DH) LPC
Interface Bridge (rev 02) 
0000:00:1f.2 IDE Interface: Intel Corporation
82801GBM/GHM (ICH7 Family)Serial ATA Storage Controllers cc=IDE (Rev 02)

If I boot to LiveCD (which works fine) /dev/scd0 does exist

So, how do I go about creating /dev/scd0 ?

I reboot to the installed OS and did;

apt-get install makedev 

and then ran it.

It said something about devs being managed by udev so it put devices in a
hidden subdir, looking in that dir shows me that it has created scd0 now.

So I alter fstab to point /media/cdrom0 to /dev/.static/dev/scd0 instead
and try mounting, which gives me;

#mount /media/cdrom
mount: special device /dev/.static/dev/scd0 is not a valid block device

aaaargh!

This is driving me nutso

Any suggestions?

---

### Post by apjone on 2007-02-05
when you do 
```

mount /dev/cdrom [or any device]

```
you must be root ( su - or sudo ) check linux.about.com/od/commands/l/blcmdl8_MAKEDEV.htm for how to create dev's

---

### Post by brettg on 2007-02-05
The problem is something to do with grub and/or the BIOS.

If you use the kernel option acpi=off then the problem disappears.

---

### Post by apjone on 2007-02-06
cool, i will have to remember that one

---

### Post by wrightee on 2008-01-22
Is there any other way to fix this problem other than a) installing Lilo (which mounts the CD beautifully but brings its own set of 'nuances') or b) switching acpi=off which leaves us without ethernet?

I'd be really interested, though might not fully understand, to read why Lilo works for mounting the CD/DVD and Grub doesn't.

Any help would be most appreciated!

---

### Post by =JeffH on 2008-01-22
*BUMP* 

I'm having the same CD-ROM mounting problems right now and am quite curious to get more info on the issue and how to resolve it. 

thanks,

=JeffH

---

### Post by Yellow Pasque on 2008-01-22
JeffH, first thing is to get info on your drive. Run the following and post the output pertaining to your optical drive(s):
```
sudo lshw -C disk
```
The other thing to look at is your /etc/fstab file. Post that.

---

### Post by crawall on 2008-01-23
*-cdrom
       description: DVD reader
       product: DVD-ROM DV-28E-C
       vendor: TEAC
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: D.4B
       capabilities: removable audio dvd
       configuration: ansiversion=5 status=open


what can i do

---

### Post by =JeffH on 2008-01-29
Hi Temüjin, thanks for your post.

Oddly enough, I tried the cdrom-dvd unit today when I had to reboot the machine (cdrom-dvd is in modular bay and I don't usually have it installed), and it worked..  

I recall trying a couple of config things last week, from info I'd acquired from googling around, but I don't recall what it was. It didn't work last week for whatever reason. 

So, I don't know if I still need help -- I might if it decides to quit working again. 

But, that said, here's the info on the drive...

  ```
*-cdrom UNCLAIMED
       description: SCSI CD-ROM
       product: DVD+-RW SDVD8820
       vendor: PHILIPS
       physical id: 1
       bus info: scsi@1:0.0.0
       version: AD18
       capabilities: removable
       configuration: ansiversion=5
```

And here's the pertinent line in my /etc/fstab...

```

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

and here's some relevant (AFAIK) modules info..
```

> lsmod | grep cdrom
cdrom                  38944  1 sr_mod

> lsmod | grep ii
ata_piix               11780  2
libata                 74892  2 pata_pcmcia,ata_piix

> lsmod | grep gen
ppp_generic            30612  7 ppp_deflate,bsd_comp,ppp_async
slhc                    8448  1 ppp_generic
ide_generic             2432  0
generic                 6276  0

> lsmod | grep ide
video                  17540  0
ide_generic             2432  0


```

I /might/ have altered the modules that are loaded at boot, e.g. adding  ide_generic, but I don't recall exactly what it was that I (might've) tweaked. 

So I used the cd/dvd drive this morn to burn a ubuntu iso image, so I guess it's working pretty well ;)

thanks,

=JeffH

---

