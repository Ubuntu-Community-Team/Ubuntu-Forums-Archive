---
title: "power down hard drive?"
date: 2006-05-19
forum: Hardware &amp; Laptops
---

### Post by djheadley on 2006-05-19
I've got a friend - long time Win user - who's trying Ubuntu.  He wants to power down his hard drives like he can in Windows.  Is there a way to do this in Ubuntu?  Right now this is his only stumbling block.

---

### Post by kaamos on 2006-05-19
I'm not sure if this is what you are looking for, put *man hdparm* gives the following:
> 
[...]
       -y     Force an IDE drive to immediately enter the low power consumption standby mode, usually causing it to  spin
              down.  The current power mode status can be checked using the -C flag.

       -Y     Force  an  IDE  drive to immediately enter the lowest power consumption sleep mode, causing it to shut down
              completely.  A hard or soft reset is required before the drive can be accessed again (the Linux IDE  driver
              will  automatically  handle  issuing a reset if/when needed).  The current power mode status can be checked
              using the -C flag.
[...]

So the syntac would be "sudo hdparm -y /dev/hdX" or "sudo hdparm -Y /dev/hdX"

---

### Post by djheadley on 2006-05-19
After looking at the man page, I think the -S would work better, now if I could only decifer the timing...:confused:

Thanks.

Any more suggestions?  I want to make it as easy for him as possible.  Oh, yeah, he wants this to be run at start-up.

---

### Post by djheadley on 2006-05-27
I'm still having trouble decifering the timing.  Has anyone used this before?:confused:

---

### Post by lozenge on 2006-09-03
Every increment of one in the command is 5 seconds in the timing.

1 would be 5 seconds.
5 would be 25 seconds.
10 would be 50 seconds.

ad infinitum!

---

### Post by lukon on 2007-01-24
I used this hdparm command (in the "Terminal" accessory application) to set power down times on my 3 hard drives separately.

> luke@VOID:~$ sudo hdparm -S60 /dev/hdd

/dev/hdd:
 setting standby to 60 (5 minutes)
luke@VOID:~$ sudo hdparm -S60 /dev/hda

/dev/hda:
 setting standby to 60 (5 minutes)
luke@VOID:~$ sudo hdparm -S240 /dev/hdc

/dev/hdc:
 setting standby to 240 (20 minutes)
luke@VOID:~$


If you want to try it, only type in the "sudo hdparm -S60 /dev/hdd" part. The rest of the quoted text above is what the computer replies with. 
The "hdd" part you must change to indicate the drive for which you want to set this parameter. 
hda = Primary, Master
hdb = Primary, Slave
hdc = Secondary, Master
hdd = Secondary, Slave
And if you hadn't recently used a "sudo" command, the first one of these commands you try will prompt the computer to ask you for your password.

And "-SXXX" values don't mean increments of 5 seconds for numbers over 240. The hdparm manual says:

> Values from 1
to 240 specify multiples of 5 seconds, yielding timeouts from  5
seconds to 20 minutes.  Values from 241 to 251 specify from 1 to
11 units of 30 minutes, yielding timeouts from 30 minutes to 5.5
hours.   A  value  of  252  signifies a timeout of 21 minutes. A
value of 253 sets a vendor-defined timeout period between 8  and
12  hours, and the value 254 is reserved.  255 is interpreted as
21 minutes plus 15 seconds.  Note that  some  older  drives  may
have very different interpretations of these values.

It seems to work. I just heard a drive turn off in my machine. That would be 2 drives truning off, actually.


Note: The ones that turn off in 5 minutes are MS Windows drives.

---

### Post by SirKeats on 2007-06-10
i seem to be having trouble with this... can someone help?

when i type in "sudo hdparm -S10 /dev/hda" i get a "no such file or directory" message. (i set to 10 just to test it obviously)

what am i doing wrong? i definitely have a primary master hdd.

i tried using /dev/sda5 instead of /dev/hda because i was thinking that maybe that was my hdd, and though i didn't get an error message, nothing seemed to happen after a minute.

any help with this would be greatly appreciated.

thanks!

---

### Post by lukon on 2007-06-11
This is just a wild guess because I haven't tried this.

Perhaps you are issuing the command from a directory from which the command cannot find some other needed command or file. Are you in your home or root directory when you give the command?

---

### Post by maybeway36 on 2007-07-03
Try sda instead of hda. Ubuntu Feisty uses SCSI emulation for some reason.

---

### Post by Pyro_Killer on 2008-06-30
Just set it to 0, LOL

sudo hdparm -S000 /dev/sdx

totally works

---

### Post by mikazo on 2008-07-02
Is there a way to reset it to not powering off at all? And when I tried it, the hard disk spins back up again every so often, so I'm assuming something is trying to use it.

---

