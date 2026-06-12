---
title: "Gnome Baker error"
date: 2008-09-18
forum: General Help
---

### Post by lsutiger on 2008-09-18
I am trying to image a disk to the hard drive using gnome baker. I am getting the following error:```

Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.

Error trying to open /dev/sr0 exclusively (Device or resource busy)... giving up.
readom: Device or resource busy. Cannot open '/dev/sr0'. Cannot open SCSI driver.
readom: For possible targets try 'wodim -scanbus'. Make sure you are root.
readom: For possible transport specifiers try 'wodim dev=help'.

```
 When I run wodim -scanbus I get :```
wodim: No such file or directory. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.

```

I can access the disk through nautilus and read the files.

What could be happening here?
Thanx in advance!

---

### Post by lsutiger on 2008-09-18
Ahhh...found it.
The cd drive was being referenced incorrectly.  /dev/sr0 should have been /dev/scd0.

But I found this out by opening another program that had the cd listed as that device. How could I have figured this out by CLI?

---

