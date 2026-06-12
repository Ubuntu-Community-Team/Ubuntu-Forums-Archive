---
title: "Rosewill RC-605 SATAII ExpressCard Supported??"
date: 2008-07-31
forum: Hardware
---

### Post by Ceemee on 2008-07-31
Just wondering if anyone has any experience or advice on this card's support under linux.  Newegg lists OS compatibility as "Windows 2000 /XP /Server 2003 /Vista /Mac OS" but since thats not un-common I decided to check here.  

The Rosewill site only has drivers for the Mac, and a Manual.

Any advice is much appreciated, i'm hoping to use an external to use Ubuntu with my laptop, but dont want to do it through USB if I dont have to.

Newegg product link:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16839200006]("http://www.newegg.com/Product/Product.aspx?Item=N82E16839200006")

---

### Post by Trmptxn on 2008-08-13
bump

i have the same card and am trying to get it to work under ubuntu, for some reason the lappy does not detect it.  but im not sure if it knows it has an express card slot either =P

i see a lot of people on the newegg reviews page saying it worked under different debian distros, i cant imagine why it wont work for me in ubuntu

EDIT:after looking around in the CD i found a lot of folders labled "linux", ill try to configure them and see if they work =P

---

### Post by Trmptxn on 2008-08-13
no go, i didnt see anything that could help in that folder =/, many other people on the newegg review sight said they ran it under other debian distros though so *Shrugs* it might just need a little work

dont take my word for it yet, i think the problem for me is probably my express card slot

---

### Post by xSauronx on 2008-09-19
> **Trmptxn said:**
> no go, i didnt see anything that could help in that folder =/, many other people on the newegg review sight said they ran it under other debian distros though so *Shrugs* it might just need a little work

dont take my word for it yet, i think the problem for me is probably my express card slot

ive got one of these as well and my t60 doesnt seem to notice it. anyone find anything out? the newegg review says it works no problem in Debian Sid so *shrug* maybe itll work with 8.10?

---

### Post by xSauronx on 2008-09-19
i found a solution. its not ideal, but it works, and is simple:

add the card before you boot, and connect the drive. ubuntu will find the drive when it boots, but WILL NOT mount the drive. this is using 8.04

if anyone has this and isnt familiar with manually mounting drives do the following:

sudo mkdir /media/$DIRECTORY
-- $DIRECTORY = whatever you like, example: esata_drive

sudo fdisk -l
-- this will output all detected disks with their storage amount, filesystem type and device name (ex: /dev/sdb), you need the device name and filesystem type to mount the drive

sudo mount /dev/sd$ -t $filesystem-type /media/$directory

where /dev/sd$ will be the device name (example: /dev/sda, /dev/sdb and so on) 

and where $filesystem-type will be...the filesystem type :)
example: ext3, ntfs-3g (for NTFS filesystems)

this will mount your drive to the directory you made and place a shortcut on the desktop, and youre gold :)

i havent had time to play with this. i dont know if unmounting will cause a problem where you have to reboot to mount again (i hope not) and i dont know if theres a way to solve this problem without having to boot up with the card/drive attached. i hope so, ill poke around later if someone doesnt make a suggestion before i get home from work :)

edit: the performance is crap. im averaging 5MB/sec writes while trying to move 2.6gb of data, thats what i usually got with usb 2.0 :(
i get 28MB/sec reads

so it works, but lousily.

---

