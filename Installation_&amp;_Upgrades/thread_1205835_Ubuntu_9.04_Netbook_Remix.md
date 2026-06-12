---
title: "Ubuntu 9.04 Netbook Remix"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by Yumpin_Yimminie on 2009-07-06
I decided to give Ubuntu another try on my Acer Aspire. It's been about 7 months since I looked at Linux or this computer.

Not having much luck with "**Ubuntu 9.04 Netbook Remix**" package. I've downloaded from a couple of sites (Purdue & MIT). When I check the hash with **winMD5Sum** it checks out just fine.

However after using **Win32DiskImager** to IMG file to flashcard I am having problem. I can check the directory on the flashcard and have no problems seeing it. But when I put the flashcard in the aspire and boot from the flashcard. I then choose the "Check file for errors" option. I consistently get a report of error in one file. I've tried this numerous times with downloads from either of the above mentioned sites.

So I decided to go the DVD route. I've used a couple of different packages for burning the ISO. The one's I've used are "**InfraRecorder**" and "**IsoBurner**." Haven't had any success with this route. After finishing the burn with either package. I attempted to read the directory using Windows XP Windows Explorer. All four of the times the system has been unable to read the directories. I've tried connecting the external DVD writer/reader to the Acer Aspire and boot from it. It gives me the boot menu option of loading from the DVD but then ends up loading the old Ubuntu version that was currently on the computer.

I'm looking for suggestions. From what I've read the file '**Ubuntu 9.04 Netbook Remix**' is supposed to have taken care of a lot of issues that I was having with the previous Ubuntu. But after so many failures, I'm beginning to wonder if the file has been changed and is non-operable now.

Help would be greatly appreciated.

Thank you.

Have a Great Day,
Jim

---

### Post by Yumpin_Yimminie on 2009-07-06
<bump>

How does one go about reporting this problem to the powers that are?  I've gone searching through the forums and have found post by other people about problems with trying to get the Netbook Remix Running.  No responses to their posts either.

---

### Post by darolu on 2009-07-06
I personally didn't have a single problem when I installed it; so all I an recommend is reading the official documentation, I found you can create the flash drive via command line, whic can be more secure as you need less resources decreasing chances of data corruption while creating the drive. Have you tried creating the booting USB flashcard with flashnul?
Here's the documentation, try following the command line interface method:
[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

Also you may want to download the .img file again, I usually download from Xmission and never have had a problem:
[http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook)

Good luck.

---

### Post by Yumpin_Yimminie on 2009-07-07
> **darolu said:**
> I personally didn't have a single problem when I installed it; so all I an recommend is reading the official documentation, I found you can create the flash drive via command line, whic can be more secure as you need less resources decreasing chances of data corruption while creating the drive. Have you tried creating the booting USB flashcard with flashnul?
Here's the documentation, try following the command line interface method:
[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

Also you may want to download the .img file again, I usually download from Xmission and never have had a problem:
[http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook)

Good luck.

Thanks much for taking the time to reply.  I went ahead and followed all of your instructions.  I downloaded from XMISSION and I also used the command line 'flashnul.'  Unfortunately it has given me the same results.  

Although I did learn one thing.  That Wiki sure offers a lot of answers.  I had sidestepped using the flashnul at the command prompt because the flashnul page that is cited is in Russian.  But the Wiki at [http://wiki.archlinux.org/index.php/Install_from_USB_stick](http://wiki.archlinux.org/index.php/Install_from_USB_stick) spelled it all out.  

I really think there is something wrong with the downloads on this file.  Other ISO files that I've tried to download work fine.  

But once again thanks for taking the time to respond.

Have a Great Day,
Jim

---

### Post by drcrash on 2009-07-07
This is a known minor bug.

There's an error in the Ubuntu Netbook Remix images that causes this error, at least on some platforms.  (Some ASUS Eee PC's, at least, like my 900A.)

The problem is that a file in the pool/main/p/ppp subdirectory has the wrong name, maybe due to the long/short name mangling of FAT and a problem with a tilde.

If you ignore this (ONE) error, the install will work fine except that you can't install ppp from the image.  You CAN install it from a repository and everything will be fine, or so I read somewhere.

Alternatively, you can fix the filename and the checksum will check out, and ppp install will work.  (I think...)  I didn't try that.

[https://bugs.launchpad.net/ubuntu/+source/mobile-meta/+bug/360925](https://bugs.launchpad.net/ubuntu/+source/mobile-meta/+bug/360925)

---

### Post by Yumpin_Yimminie on 2009-07-07
Thanks much for taking the time to respond!  

Glad to here it wasn't a little gremlin hiding in my computer system.

Have a Great Day,
Jim

---

### Post by mightyiam on 2009-07-08
Glad to see you found the answer.

---

