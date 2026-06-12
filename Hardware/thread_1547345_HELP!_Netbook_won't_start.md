---
title: "HELP! Netbook won't start"
date: 2010-08-06
forum: Hardware
---

### Post by needgreathelp on 2010-08-06
Hello, I turned on my Toshiba NB100 netbook today and it won't startup. I do see the initial screen that gives me the option of pressing F2 or F12 to go to the boot menu but then theres just a blank screen that just hangs there. Fortunately I had a USB key with ubuntu netbook installed which I'm using to write this. 

First of all I was worried the hard drive had died. But I tried accessing it from the usb and got the following error message - 


> Error mounting: mount exited with exit code 21: mount: according to mtab, /dev/sda1 is already mounted on /media/26DC5FFBDC5FC3A9
Then I tried plugging a USB key and and USB MP3 player in and both produced an exit code 13, although after the error is displayed, I can access both external hard drives. But I can not access the main hard drive which has just XP installed on it.

I also can't unmount anything, although I haven't tried it with the terminal, just with the GUI. Do have to use some sort of command? Is this a problem with the file system or partitions?

As my warranty's run out I have no idea of what to try next. Any help would be very, very,very much appreciated.

---

### Post by needgreathelp on 2010-08-07
Any ideas? If not fixing it is there anyway to recover files? 

I used Disk Utility to see the drive details (Which listed the SMART Status as "Disk is healthy") and clicked mount, to which I got the following output.


>   Error mounting: mount exited with exit code 21: mount: according  to mtab, /dev/sda1 is already mounted on /media/26DC5FFBDC5FC3A9

This is strange since there is no /etc/mtab file, or even a /media/26DC5FFBDC5FC3A9.

I have no idea whats happening.

---

### Post by viper250 on 2010-08-07
from what I understand of your post windows gui is not loading 
the usual error code that comes up with a black screen in xp is ntloader missing
have you had a few bluescreens come up?
its possible that files have been corrupted.
did it have a recent update?

its not a hardware (video) issue or it would affect booting from the usb stick

puppy linux has some great software for recovering data even from damaged files, but there are more distros as well
like clonezilla system rescue

---

### Post by needgreathelp on 2010-08-10
Thanks, I've now tried Slax Linux and it lets me access my harddisk and backup my files. So does that mean it can't be a hardware issue? 

I can run linux of my USB, so video, RAM, CPU and Motherboard must all work.

Since I can get files off my harddisk, that seems to work too.

What then could be wrong? If I get a blank screen after the bios self test, that would assume the test failed. So what component could be failing?

Is there a tool on linux that would help me find the problem?

Thanks.

---

