---
title: "USB disk drive - can't access"
date: 2008-11-20
forum: Hardware
---

### Post by ursus262 on 2008-11-20
I have a problem with my external USB disk drive which used to work a treat, but now I cannot save files on it.

The device mounts perfectly, with an icon on the desktop.  But I cannot save files to it.  I get the message:

Error opening file '/media/disk/JS Record.ods': Permission denied

JS Record.ods is a spreadsheet file and is simply an example.  Nothing else will save on that disk either.

I Used the chmod command to open up the read/write priveleges so that everyone can access it, but to no avail.

If I right-click on the icon, and look in "permissions", I get the message:"the permissions of "disk" could not be determined".  I formatted it with gparted to use the ext3 filesystem.  It used to work, until I used it as a back up drive with Keep and, although I've reformatted it and deleted and recreated a single partition, it simply won't work.

My USB memory stick, however, works perfectly.

Anyone have any suggestions, as this is really frustrating.

---

### Post by taurus on 2008-11-20
Who is the owner of /media/disk?

```
ls -la /media/disk
```
And since it's an ext3 filesystem, you can just change the ownership of /media/disk from root to your login name so you can write to it anytime you want.  Assuming your login name is john, try

```
sudo chown -R john:john /media/disk
ls -la /media/disk
```

---

### Post by ursus262 on 2008-11-20
Taurus

I've followed your instructions and it works.  

I'm going to study the commands and the syntax so I can learn from this experience and the info you supplied.

Thanks mate. Much appreciated :KS

---

### Post by dionp2 on 2009-01-17
I have an external NTFS drive I am trying to mount automatically but all I get is permission denied. Same with the thumb drive also. 

They seemed to mount just fine on the debian server when I added them to the plugdev group but not on the Kubuntu laptop.

Any help would be greatly appreciated.

Cheers,

D

---

### Post by dionp2 on 2009-01-17
Ok well I became so p*##@d o$f I turned the bloody thing of and went and did something else.

I just got back now and booted up and it works.

So it had to have been one of these things

1. Installed pmount
   apt-get update
   apt-get install pmount
2. In Kubuntu
   Start (or the equivalent I think K menu) -> System Settings ->
   Administrator mode -> Users -> Choose your user -> Modify -> 
   Add that user to every Privilege and Secondary Group there is -> OK
3. Start (or the equivalent I think K menu) -> System Settings ->
   Administrator mode -> Groups tab -> make sure your user is part of the 
   plugdev group. -> OK -> Close
4. Yelling profuse abuse at the machine and threatening to rip it's disk 
   off!!!!

For Debian etch
In Deian for a user to have access to USB drives hdd you need to add them
to the plugdev group through user manager.
It appears that Debian already has pmount installed.

---

