---
title: "CD/DVD drive lost on HP laptop"
date: 2008-11-11
forum: Hardware
---

### Post by J-Morris on 2008-11-11
My CD/DVD drive used to work very well, but now it doesn't seem to be recognized by Kubuntu. I am using an HP dv 2000 laptop. I haven't done anything to my knowledge to cause this except I tried to watch a DVD (failed because of missing DVD menu libraries - still an unresolved problem) and letting my friend use my laptop briefly to play some sound effects on Halloween. K3b, when it starts up, reports that it is unable to find any CD/DVD drives. 

I do have a /media/cdrom0/ folder on my computer, but it doesn't seem to do anything. 

What steps should I use to diagnose and hopefully restore my drive to working? 

Thanks!

---

### Post by phidia on 2008-11-11
The directory /media/cdrom0 won't do anything unless a disk is in the drive, and k3b may need to be configured. 

You can find your drive with > wodim -checkdrive from a terminal but that may give you mixed information. 

What happens if you insert a disk in the drive?

---

### Post by J-Morris on 2008-11-13
The wodim output that this:

```
j@cardboard-box:~$ wodim -checkdrive
Device was not specified. Trying to find an appropriate drive...
wodim: No such file or directory.
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.

```


When I put a disc in the drive, the amber LED comes on and the drive spins up, also the LED comes on during boot. 

Keep in mind that everything worked until recently, so in my efforts to get DVD menus to work

---

