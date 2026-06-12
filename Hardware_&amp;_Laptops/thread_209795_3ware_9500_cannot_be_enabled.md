---
title: "3ware 9500 cannot be enabled"
date: 2006-07-05
forum: Hardware &amp; Laptops
---

### Post by ghee22 on 2006-07-05
I can't seem to enable my harddrive on my ubuntu server setup.  It properly sees the array as a harddrive with the correct size, but it says it is unformatted.

Anyone have any directions?

---

### Post by cracker on 2006-07-05
If it's fake hardware raid, you're going to have a hell of a time. Linux doesn't like those very well. If you have the option, I would recommend going with either full software raid, or, even better, true hardware raid.

Others will be more able to help you if you list your raid controller and specific hardware setup, as well as how exactly you plan to use it.

---

### Post by ghee22 on 2006-07-05
[QUOTE=cracker]If it's fake hardware raid, you're going to have a hell of a time. Linux doesn't like those very well. If you have the option, I would recommend going with either full software raid, or, even better, true hardware raid.

Others will be more able to help you if you list your raid controller and specific hardware setup, as well as how exactly you plan to use it.[/QUOTE]

The 3ware 9500 has true hardware raid.  It sticks into a pci slot.  Ubuntu correctly loads the 3ware 9xxx driver.  Linux kernel has builtin support for this for a while.  What i don't understand is why I can't enable the hard drive in the disk manager, hence can't use it!

The raid controller is 3ware 9500 Raid 5 into a 32 pci slot.  hardware setup is using NF3 motherboard, and I'm planning on using this disk array to record mythtv recordings.

Thanks for the reply and I'm eagerly looking for help!

---

### Post by ghee22 on 2006-07-09
^^^bump^^^

sorry, if anyone can post anything i can try to give out diagnostics, i'd be pleased to post them here.  I just don't know how.

^^^bump^^^

---

### Post by ghee22 on 2006-07-11
ok i reinstalled ubuntu 6.06 completely using the shipit! cds.  instead of installing as a server, i installed as desktop.  Ubuntu still correctly sees how much space the 3ware drive offeres but cannot enable the drive.

Does anyone else have a 3ware 9500 PCI to SATA card?  I'm using 4 Seagate brand new 250 GB HDs.

Please list all steps taken after installing ubuntu.  Is there a different kernel required?  Perhaps a better driver?

Please, i'm getting desperate  ](*,)

---

### Post by ghee22 on 2006-07-11
The following ubuntuforums.org posts have to do with the same problem:
[http://www.ubuntuforums.org/showthread.php?t=84217&highlight=3ware](http://www.ubuntuforums.org/showthread.php?t=84217&highlight=3ware)
[http://www.ubuntuforums.org/showthread.php?t=124921&highlight=3ware](http://www.ubuntuforums.org/showthread.php?t=124921&highlight=3ware)
[http://www.ubuntuforums.org/showthread.php?t=51911&highlight=3ware](http://www.ubuntuforums.org/showthread.php?t=51911&highlight=3ware)
[http://www.ubuntuforums.org/showthread.php?t=28080&highlight=3ware](http://www.ubuntuforums.org/showthread.php?t=28080&highlight=3ware)

All of the above have no solutions. :-k 

Here's a website from 3ware.com that gives an iso for Debian Sarge 3.1 that has an iso with the kernel precompiled for support for the 9500:
[http://www.3ware.com/kb/article.aspx?id=14860](http://www.3ware.com/kb/article.aspx?id=14860)

The 3ware.com page shows no support for Ubuntu.  :confused: 

ataylor seems to have gotten this card working with no special configuration.  I have asked him to post details of any steps taken on this forum post.  Let's see what he has to say...

Thanks, in advance, ataylor! :KS

---

### Post by ghee22 on 2006-07-11
In [this 3ware article]("http://www.3ware.com/kb/article.aspx?id=11757"), it states:
[I]The current versions of the CLI and 3DM2 (from the 9.0 and 9.01 code sets) do not support the 3ware 9500S driver (3w-9xxx) that is included in the kernel and in Linux distributions that include the 3w-9xxx driver.  You can download a beta version of the CLI and 3DM2 from the 3ware web site.  Go to this link ([http://www.3ware.com/support/index.asp)](http://www.3ware.com/support/index.asp)), click on "Download 'In Engineering Phase' Software", then download the CLI and/or 3DM2 for the 9000 series.  These will work with the in kernel 9500S driver.

Future versions of the CLI and 3DM2 included in the 9.x code set will support the in kernel 3w-9xxx driver.[/I]

---

### Post by ghee22 on 2006-07-11
[Here's how to compile the 3ware driver into the kernel]("http://www.3ware.com/kb/article.aspx?id=12690") straight from 3ware.com

---

### Post by ghee22 on 2006-08-21
Conclusion:  This hardware does not work in Ubuntu Dapper 6.06.  This does work completely fine in Debian using the Net Install for Testing CD.

Oh well...

* crosses fingers that it works in edgy eft *

---

### Post by ghee22 on 2006-09-17
downloading edgy eft knot 3 and trying to see if it works tonight

---

### Post by ghee22 on 2006-09-17
[https://wiki.ubuntu.com/3ware_9500](https://wiki.ubuntu.com/3ware_9500)

---

