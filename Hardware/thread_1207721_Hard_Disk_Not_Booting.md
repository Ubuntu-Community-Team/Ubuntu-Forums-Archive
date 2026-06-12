---
title: "Hard Disk Not Booting"
date: 2009-07-08
forum: Hardware
---

### Post by spraveenitpro on 2009-07-08
Hi 

I have a Compaq C768TU which failed to boot , I put the Live CD in and tried to access the 120GB hitachi Hard disk and this is the error message that I am receiving.


[IMG]http://spraveenitpro.googlepages.com/Screenshot.png[/IMG]

Please let me know what could be the issue/mounting the HDD and how I could take a backup of the data on the Hard disk 

Thank you
Praveen

---

### Post by Dysport on 2009-07-08
Why doesn't it boot anymore? What does it say/do instead?
To me it looks like you have a hardware problem. Have you tried accessing your drive with GParted yet?

---

### Post by spraveenitpro on 2009-07-08
Yes, it doesn't Boot, it throws the error messages and loads the RAM FS, 

when I try to mount the /dev/sda1  as /media , this is the error that i get
> 
ubuntu@ubuntu:/dev$ sudo mount /dev/sda1 /media
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Pls let me know how to save the data.

---

### Post by Dysport on 2009-07-08
> **Dysport said:**
> Have you tried accessing your drive with GParted yet?

Also you can try to manually mount the partiton with the --force option (type "man mount" in a terminal to get more information).
As I said before it looks like you have a hardware issue. A good data recovery tool is Photorec, but I don't know whether that's useful in your case.

---

### Post by az on 2009-07-08
[http://ubuntu-rescue-remix.org](http://ubuntu-rescue-remix.org)


Image the drive using gddrescue and then pull files from the image using file-carving software.


Do not use photorec on the failing drive.  Image the drive before you do anything else to it.  Use photorec on the image.

---

### Post by spraveenitpro on 2009-07-08
yes , thanks for that, I can confirm that it is a HW issue as wierd noises are coming from the HDD,  will have it replaced, thx again :guitar:

---

### Post by az on 2009-07-08
> **spraveenitpro said:**
> yes , thanks for that, I can confirm that it is a HW issue as wierd noises are coming from the HDD,  will have it replaced, thx again :guitar:

Then gddrescue is the right tool to use.  It will read and re-read bad blocks until it can create a perfect image.  That's the only non-invasive way to rescue your data from a failing drive.  If the drive doesn't put out any data, though, then the only way to recover the data is through more invasive measures which usually means opening up the drive and transplanting the platters into an identical drive where most of the data can be read - that's very expensive to do.

---

