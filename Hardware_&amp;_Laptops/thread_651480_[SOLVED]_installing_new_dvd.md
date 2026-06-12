---
title: "[SOLVED] installing new dvd"
date: 2007-12-27
forum: Hardware &amp; Laptops
---

### Post by gishaust on 2007-12-27
hi everyone

I installed a dvd rw last night and the computer is not seeing it. I thnk it should be auto recognise but it is not there. I have the cdrom and dvd drive naster and slave on the same ide cable. I tried to place this is fstab

/dev/hda     /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb      /media/cdrom0   udf,iso9660 user,noauto     0       0 

I got it off another thread but when i try to open the drives i get

mount: special device /dev/hda does not exist
mount: special device /dev/hda does not exist


on both the cd drive and the dvd /rw

I really need to be pointed in the right direction

gishaust

---

### Post by Yellow Pasque on 2007-12-27
ok, let's do a:
```
lshw -C disk
```
to see what's what. Your CD drives will prbably be /dev/cdrom<_>, not /dev/hd<_>

Also, is there a reason you're trying to mount them to the same directory? What happens if you put a disc in each drive? :o

---

### Post by gishaust on 2007-12-27
thankyou for the reply

  *-cdrom
       description: SCSI CD-ROM
       product: ROM-DRIVE-52MAX
       vendor: ATAPI-CD
       physical id: 1
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 52AR
       capabilities: removable audio
       configuration: ansiversion=5
     *-disc
          physical id: 0
          logical name: /dev/cdrom

that is the only media device and it is an old one.To answer your question no there is no reason except that I don't know what  I am doing. I haven't at any time created a folder that is the what is in fstab. So I am guessing that is the next thing i will be asked to do. But  i have not found any information on the forums to do that.

---

### Post by Yellow Pasque on 2007-12-27
Does the BIOS see both drives?
Does the lshw command show both drives after you run:
```
sudo update-pciids
```

As for making another cdrom directory:
```
cd /media
sudo mkdir cdrom1
```

---

### Post by gishaust on 2007-12-27
Yes the bios sees both drives 
When i did the sudo update-pciids and then lshw it still shows no cdroms
I have create a directory in the media folder it now has the following,
cdrom  cdrom0  cdrom1  floppy  floppy0

---

### Post by gishaust on 2007-12-27
does anyone have any more direction

It would be greatly received

---

### Post by gishaust on 2007-12-28
I setup ubuntu 7.10 last night and now I have two cdroms when i lshw. So that is very good news. But if i put a dvd in the dvd drive it won't work but if I put and audio cd in the dvd drive it will work.  I have tried all the above suggestions and restarted but I have the same issue. has anyone got a suggestion on what i can do about it?

gishaust

---

