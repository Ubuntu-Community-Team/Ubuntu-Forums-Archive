---
title: "Ubuntu 11.04 and BlackBerry"
date: 2011-07-09
forum: Hardware
---

### Post by zolub on 2011-07-09
Hello
I am new with ubuntu I installed right now the 11.04 version.
I need to use my desktop for emailing, calendars and contacts. (simple office work)
Since I and my friends use BalckBerry the first thing I tried to set up the synchronization between evolution and the BlackBerry device. I found this link with the description how to do this:
[http://www.netdirect.ca/software/packages/barry/sync.php](http://www.netdirect.ca/software/packages/barry/sync.php)

The text describes these commands:
>  
        msynctool --delgroup EvoBarry         
msynctool --addgroup EvoBarry 
        msynctool --addmember EvoBarry evo2-sync         
msynctool --addmember EvoBarry barry-sync         
msynctool --configure EvoBarry 1 
        msynctool --configure EvoBarry 2         
msynctool --showgroup EvoBarryI tried install every possible package to make this commands work with no success.
1. msynctool command is not recognized at all. Instead of this it suggested to use osynctool.
2. I didn't get to work the msynctool so I tried do this steps with osynctool. Here I get another trouble with barry-sync plugin. It tells > 
osynctool --addmember EvoBarry barry-sync
ERROR: Unable to find plugin with name barry-sync

 I cannot find it in the package repository. On sourceforge there was only an 10.04 version of barry. 
[http://sourceforge.net/projects/barry/files/barry/barry-0.17.1/](http://sourceforge.net/projects/barry/files/barry/barry-0.17.1/)
It is possible to get work my BlackBerry device with ubuntu 11.04??

I am aware of the fact that such non-standard packages may come with delay for new OS versions - but it is possible to solve this situation right now?

Thanks

---

### Post by An Sanct on 2011-07-09
Its not that bad to use the 10.04 (Lucid) version, it works okay on my 10.10 (Maverick).

But I have some bad news for you as a Blackberry and Linux user ... there is _**zero**_ from RIM for Linux and even barry is community driven.

[Sadly ....]("http://www.blackberryforums.com/general-blackberry-discussion/18622-rim-blackberry-linux-usb-driver-support-petition.html")
> BlackBerry Wireless Handheld devices developed by Research In Motion.  Ltd. do not have Linux USB drivers. The specification for said drivers  is also not available.

---

### Post by iurpas on 2011-08-10
> **zolub said:**
> Hello
I am new with ubuntu I installed right now the 11.04 version.
I need to use my desktop for emailing, calendars and contacts. (simple office work)
Since I and my friends use BalckBerry the first thing I tried to set up the synchronization between evolution and the BlackBerry device. I found this link with the description how to do this:
[http://www.netdirect.ca/software/packages/barry/sync.php](http://www.netdirect.ca/software/packages/barry/sync.php)

The text describes these commands:
I tried install every possible package to make this commands work with no success.
1. msynctool command is not recognized at all. Instead of this it suggested to use osynctool.
2. I didn't get to work the msynctool so I tried do this steps with osynctool. Here I get another trouble with barry-sync plugin. It tells > 
osynctool --addmember EvoBarry barry-sync
ERROR: Unable to find plugin with name barry-sync

 I cannot find it in the package repository. On sourceforge there was only an 10.04 version of barry. 
[http://sourceforge.net/projects/barry/files/barry/barry-0.17.1/](http://sourceforge.net/projects/barry/files/barry/barry-0.17.1/)
It is possible to get work my BlackBerry device with ubuntu 11.04??

I am aware of the fact that such non-standard packages may come with delay for new OS versions - but it is possible to solve this situation right now?

Thanks

I have exactly the same problem. Tried a lot of different solutions that can be found on these and other forums, never could sync..oddly..found a number of threads where people seem to achieve it, maybe older versions of ubuntu? (although i had the same problem with karmic and lucid)..

did you got around it?

Can someone redirect us to the solution?

Thanks

Rui

---

### Post by santidavid on 2011-08-12
Hey l have the same problem with Maverick (10.10). 
Barry supports Ubuntu versions until 10.04 (l think there is an extra package for 10.10, which l can't install, but l have read nothing on supporting 11 version.

Hey Here's a petition for RIM to support Linux users: [http://www.petitiononline.com/bb1d1234/petition.html](http://www.petitiononline.com/bb1d1234/petition.html)

Would help a lot if you sign it too!

---

