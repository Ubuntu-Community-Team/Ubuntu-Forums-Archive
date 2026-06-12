---
title: "Another scanner quandry"
date: 2006-07-04
forum: Hardware &amp; Laptops
---

### Post by Steve S. on 2006-07-04
Hello all.  Started figuring out this all-in-one via this thread [http://ubuntuforums.org/showthread.php?t=203508](http://ubuntuforums.org/showthread.php?t=203508) 

Well, now I have to figure out the scanner driver.

This is a USB all in one printer, but I don't know where to find the driver for the scanner.

Is there some easy way to set this up? I'm welcome to any input on this I can get. I can scan via Windows on a dual boot, but it's a shame to...well, let Windows win, as it were.

I checked this one on how to install the driver (is this a good thread?) [http://www.ubuntuforums.org/showthre...to+usb+scanner](http://www.ubuntuforums.org/showthre...to+usb+scanner) but I haven't been able to find the driver as of yet. The only sites that have any promise at all are those that make you log in and then run you through a series of marketing scams...no real luck at all.

Please help!

---

### Post by coolclassic on 2006-07-04
Did you have a look at lexmarks web site there appears to be linux drivers for suse and redhat, check here and read driver guide:

[http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=227:5:0:133:0:0&emeaframe=&fileID=1030&searchLang=en&searchLang=en](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=227:5:0:133:0:0&emeaframe=&fileID=1030&searchLang=en&searchLang=en)

---

### Post by Steve S. on 2006-07-04
Well, coolclassic, I checked lexmark's site and there were no drivers that I saw.  The link that you gave me seems to be a program that is meant to be run in Mac os...please prove me wrong.  I looked on the site and still found nothing.

Googled around, found this:
[http://www.mepislovers.org/modules/newbb/viewtopic.php?topic_id=16493&forum=30&PHPSESSID=7cea1649f84181e1daf51a5a4d36958b](http://www.mepislovers.org/modules/newbb/viewtopic.php?topic_id=16493&forum=30&PHPSESSID=7cea1649f84181e1daf51a5a4d36958b)
and followed what it said.

Had already run sane-find-scanner, but did it again for fun, and found out the vendor and product numbers to be entered at [http://www.sane-project.org/cgi-bin/driver.pl?manu=&model=&bus=any&v=413c&p=5103](http://www.sane-project.org/cgi-bin/driver.pl?manu=&model=&bus=any&v=413c&p=5103)
but it showed me that the printer/scanner was not supported.

So, as it stands now, it appears that I can print but not scan.

Once again, someone please prove me wrong...

---

### Post by coolclassic on 2006-07-05
Go to the link I provied then click on the unix driver guide then goto page 6 where it tells you the linux systems supported. Although this does not mention ubuntu I'm sure it could be made to work.

---

### Post by coolclassic on 2006-07-05
Further to my last post Lexmark will give you an rpm file. I would sudjest reading this post to install an rpm file:

[http://ubuntuforums.org/showthread.php?t=209112&highlight=install+rpm](http://ubuntuforums.org/showthread.php?t=209112&highlight=install+rpm)

---

### Post by Steve S. on 2006-07-05
[QUOTE=coolclassic]Further to my last post Lexmark will give you an rpm file. I would sudjest reading this post to install an rpm file:

[http://ubuntuforums.org/showthread.php?t=209112&highlight=install+rpm](http://ubuntuforums.org/showthread.php?t=209112&highlight=install+rpm)[/QUOTE]

I hate to be a pest, coolclassic, really I do.  I went to the link, checked out the Unix guide, read the other thread (on the rpm) and it's all great stuff, clearly invaluable...you do great work.

However, I followed up with the Unix systems manual and went to [http://www.lexmark.com/drivers](http://www.lexmark.com/drivers) and it doesn't provide "lexmark-print-drivers-linux-glibc2-x86.rpm.gz."  I looked through the driver listing, nothing.  I clicked on the only Linux system listed (Caldera Openlinux) and it simply returns to itself.

Am I really missing something that badly?  It seems I now know how to install the driver, but I still don't have it to start with.;-)

---

### Post by coolclassic on 2006-07-05
Hers a link to the driver:

[http://www.downloaddelivery.com/srfilecache/print-drivers-linux-glibc2-x86.rpm.gz](http://www.downloaddelivery.com/srfilecache/print-drivers-linux-glibc2-x86.rpm.gz)

I found it here:
[http://www.usalug.org/phpBB2/viewtopic.php?p=55782](http://www.usalug.org/phpBB2/viewtopic.php?p=55782)

---

### Post by Steve S. on 2006-07-05
[QUOTE=coolclassic]Hers a link to the driver:

[http://www.downloaddelivery.com/srfilecache/print-drivers-linux-glibc2-x86.rpm.gz](http://www.downloaddelivery.com/srfilecache/print-drivers-linux-glibc2-x86.rpm.gz)

I found it here:
[http://www.usalug.org/phpBB2/viewtopic.php?p=55782](http://www.usalug.org/phpBB2/viewtopic.php?p=55782)[/QUOTE]

Ahhh...this must be why you make the big bucks!  Thanks, coolclassic...I'll try to set it up tonight!

---

### Post by coolclassic on 2006-07-05
BIG BUCKS: You are kidding I work in the National Health Service.

I hope you have luck in installing the driver you may find you will hit dependency problems and files installing in locations which Ubuntu can't find.

Good luck

---

