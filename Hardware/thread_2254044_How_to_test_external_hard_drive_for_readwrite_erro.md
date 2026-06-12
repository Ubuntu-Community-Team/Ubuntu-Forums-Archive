---
title: "How to test external hard drive for read/write errors?"
date: 2014-11-24
forum: Hardware
---

### Post by mynick2 on 2014-11-24
As in subject, I've just ordered Seagate Backup Plus 1TB external hard drive. And as I always test my hardware after arrival I wonder what software should I use?

For testing USB pendrives I use F3 program:
[http://oss.digirati.com.br/f3/](http://oss.digirati.com.br/f3/)

to be honest I see no cons to test 1TB hard drive with this program but I'm not a hardware geek so I prefer to ask - is this software ok for such a task or should I maybe give something else a go?

---

### Post by weatherman2 on 2014-11-24
Hard drives have built-in self-test programs in their firmware.  You can access these tests with S.M.A.R.T.  In Ubuntu, you can install GSmartControl and run tests that way.  There are only a few tests.  I usually run the extended test, an exhaustive test that takes several hours - probably best to run overnight.  (The computer itself is doing nothing with the drive while such a test is running - it's all being run by the drive's firmware.)

You can also try a Linux boot disk like Parted Magic (GsmartControl is called "Disk Health" on the desktop).  Still a free version of Parted Magic on MajorGeeks I think.

Sometimes you have to add options like -T permissive or -d sat to the smartctl command to get recognize an external drive correctly.

---

### Post by weatherman2 on 2014-11-24
Seagate may also have a boot disk like Seatools you can burn/boot to run these same tests.  You can run Parted Magic from a USB flash drive - perhaps also Seatools.

---

### Post by mynick2 on 2014-11-24
Thank you so much for those infotmation! Will look into that and post if I have any problems but I gues I'm good to go from now on. Take care.

EDIT:
Hey there, just want to inform which way did I choose. I used Seatools for linux(it's command line tool), the disk got through Long Generic Test(did it when I was in work) so I guess it's all ok and ready to go :).

I didn't use Seatools for DOS(this is the only one that can be put on CD/DVD/Pendrive) as I assume it is able only to check disks that are "in" your computer/laptop as I doubt that DOS program will have USB support. That's why I used the Linux version instead of a DOS one.

---

