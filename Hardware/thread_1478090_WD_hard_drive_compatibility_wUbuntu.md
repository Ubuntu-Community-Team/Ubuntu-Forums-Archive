---
title: "WD hard drive compatibility w/Ubuntu"
date: 2010-05-09
forum: Hardware
---

### Post by tyler9 on 2010-05-09
Hi--I'm building a home/office machine for the usual general tasks and want to use Ubuntu as my primary OS.

Was considering this Western Digital hard drive:
Western Digital Caviar Blue WD5000AAKS 500GB 7200 RPM 16MB Cache SATA 3.0Gb/s 3.5"
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136073](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136073)

...but I'm seeing posts on this and other forums about possible compatibility problems with WD hard drives and Ubuntu. Hard to know how much to weight these reports--just random data points, or indicative of serious problems?

Western Digital doesn't help much, when on this chart:
[http://www.wdc.com/en/products/resources/DriveCompatibilityguide.asp#os](http://www.wdc.com/en/products/resources/DriveCompatibilityguide.asp#os)
...they say:
"Your operating system, as well as your hardware, must support the hard drive you choose:"
...but they list only Mac and Windows OS--even Win98! No mention of Linux. Not encouraging. I recognize that ~90% of their drives go in Windows machines, but to ignore Linux is...annoying. Unless in fact they *don't* support Linux.

I'd greatly appreciate help here, as I want to order hard drive and start build--what hd would be best?--Seagate, Samsung, or WD?

Thanks for help!

---

### Post by cascade9 on 2010-05-09
The 'compatibility problems' with WD drives is from WD changing from the old 512bytes sector size to 4kB. Its somethign that all the drive manufacturers will be doing, sooner or later- part of teh reason why they are doing it is to get around the 2TB limit.

There are various fixes for the 4kB sector problem. :)   

As far as I can tell, the WD5000AAKSis still using 512B sectors, so you dont have to do anything apart from plug it in, partition and then use ;) 

Personally, I like WD over Samsung and Seagate (or Fujitusu and Hitachi) . Not that any of them make bad drives. (Well, if you want to look around you can find dodgy models from any of the HDD manufacturers). I've just had better luck with WD than anyone else.

---

### Post by tyler9 on 2010-05-09
Thanks, cascade9--great info. I saw a WD5000AAKS spec showing it does have a 512 sector size. 

I'd like to go w/WD--for a newbie builder, the WD site has good support info, clear and discoverable; has a forum too. 

I was also considering a Samsung Spinpoint, but Samsung site offers less support. This probably doesn't matter to an experienced builder, but as a first-timer, I don't assume everything will go perfectly!

tyler9

---

### Post by cascade9 on 2010-05-09
Honestly, you shouldnt really need any support with 512k sector hdds. It should be just pulg in the SATA/IDE cable, partition and off you go! Probably part of why the 4kB sector WD drives have had lots of bad reports (if they are not 'aligned' they are pretty slow), people are use to just pluging the drive in and going. 

But understandable to worry about it for your 1st build. Good luck ;)

---

### Post by srs5694 on 2010-05-09
Note that, as currently implemented, 4096-byte sectors do *nothing* to help with the 2TiB barrier. This is because the current implementation uses 4096-byte sectors in hardware, but the drive's firmware continues to present 512-byte sectors to the computer. This helps with compatibility, but it can cause serious performance problems if the disk isn't partitioned properly, as detailed [in this article of mine.](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html) The fix is fairly easy if you know about it, but WD does a poor job of educating its customers about the problem, so some people end up with improperly partitioned disks.

Of course, current drives are all still under 2TiB in size. I don't know what WD or other manufacturers will do once they finally release larger disks. They could start revealing the true sector size to the computer, use a jumper to give the user an option on this score, or continue with the 512-byte logical sector size and tell users to use GPT for partitioning. Fortunately, [Linux is well prepared for GPT,](http://www.ibm.com/developerworks/linux/library/l-gpt/index.html) but you need to know enough to set the disk up that way.

---

### Post by fishtoprecords on 2010-05-09
I had a related problem with a 1.5TB green WD disk. My main, and new, Ubuntu system handled it flawlessly, but I tried it in two older computers ~circa 2005, the disk was not recognized.

Apparently the SATA 3gbs was not falling back to 1.5gbs as expected, and the old motherboards could not handle/recognize the disk. There is a jumper that tells the drive to talk 1.5, and with it set, all is wonderful.

Yes, SATA drives do have jumpers. I didn't know that until last week.

---

