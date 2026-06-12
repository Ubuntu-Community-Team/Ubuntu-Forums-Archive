---
title: "Ubuntu Server Hard Drive"
date: 2009-04-25
forum: Hardware
---

### Post by JumpForJoy on 2009-04-25
I have recently turned an old computer of mine into an ubuntu server. I also added a 350 gb hard drive to the computer. I mounted it under media, and edited my fstab. This is where my knowledge ends, and my unskilled experience(none) starts. I noticed that my hard drive doesn't spin down. On other of my computers, the hard drive stops spinning(saving the life of the hard drive and energy), but on my ubuntu server, the hard drive is constantly spinning. My question is, do I need to worry about my hard drive always spinning, should I run a command to turn the hard drive off every time I'm not using the server, or should I edit a file to have the hard drive shut off after a period of inactivity?
Thanks,
JumpForJoy

By The Way: I also posted this in the Absolute Beginner section, but I decided to post it here instead.

---

### Post by MrWES on 2009-04-25
Install hddtemp and check the drive temp:

sudo apt-get install hddtemp

hddtemp /dev/xxx

Bill

---

### Post by JumpForJoy on 2009-04-25
Thanks,
As I mentioned, I have 2 hard drives.

I used sudo hddtemp /dev/sda1 and I got(my old master hd):
WARNING: Drive /dev/sda1 doesn't seem to have a temperature sensor.
WARNING: This doesn't mean it hasn't got one.
WARNING: If you are sure it has one, please contact me (hddtemp@guzu.net).
WARNING: See --help, --debug and --drivebase options.
/dev/sda1: QUANTUM FIREBALLP AS60.0                ?:  no sensor

I used "sudo hddtemp /dev/sdb1" and I got(this drive is my slave):
/dev/sdb1: WDC WD3200JB-00KFA0: 44°C

Thanks,
JumpForJoy

---

### Post by MrWES on 2009-04-25
> **JumpForJoy said:**
> Thanks,
As I mentioned, I have 2 hard drives.

I used sudo hddtemp /dev/sda1 and I got(my old master hd):
WARNING: Drive /dev/sda1 doesn't seem to have a temperature sensor.
WARNING: This doesn't mean it hasn't got one.
WARNING: If you are sure it has one, please contact me (hddtemp@guzu.net).
WARNING: See --help, --debug and --drivebase options.
/dev/sda1: QUANTUM FIREBALLP AS60.0                ?:  no sensor

I used "sudo hddtemp /dev/sdb1" and I got(this drive is my slave):
/dev/sdb1: WDC WD3200JB-00KFA0: 44°C

Thanks,
JumpForJoy

/dev/sdb1 is the drive that seems to be spinning constantly? 44C is a nominal temperature for a drive that's in use.

/dev/sda1: SAMSUNG SP1604N: 14°C -- internal server drive -- not very active

/dev/sdb1: WDC WD10EADS-00L5B1: 31°C -- external eSATA drive in an enclosure w/ fan.

might try hdparm --help

I believe there is a sleep flag

Bill

---

### Post by JumpForJoy on 2009-04-25
Ok, I messed with the flags, but it didn't reduce the noise of my server(the point of this + hd life).  I'm starting to think that it might me the fan that is making all this noise, is there a way to tell if it is the harddrive?
Thanks,
JumpForJoy

---

### Post by MrWES on 2009-04-25
> **JumpForJoy said:**
> Ok, I messed with the flags, but it didn't reduce the noise of my server(the point of this + hd life).  I'm starting to think that it might me the fan that is making all this noise, is there a way to tell if it is the harddrive?
Thanks,
JumpForJoy


Did you open the case up and look to see if the fan is dirty? Excessive dust and debris and make the fan unbalanced, and can cause noise.

Bill

---

