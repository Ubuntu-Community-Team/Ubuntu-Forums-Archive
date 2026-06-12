---
title: "Installing ATI Radeon HD 3200 Driver on Ubuntu 12.10"
date: 2013-12-16
forum: Hardware
---

### Post by AdHoc92 on 2013-12-16
I've been having a lot of trouble downgrading xorg and installing the AMD Legacy Drivers. I've looked at a dozen different old threads and help pages on the issue, but none of them worked. I did find [This Page]("http://www.upubuntu.com/2012/10/how-to-repair-failed-amd-catalyst.html") that seemed to work, but I ran into a problem at: > Now download the latest version of AMD driver  (**12.9**) with these commands 

Here's what happens when I enter the cmds into Terminal:

 **cd ~/; mkdir catalyst12.9; cd catalyst12.9/** 

Result: > File Exists 

 **wget -c [http://goo.gl/mHnCA](http://goo.gl/mHnCA)[B] -O [B]amd-12.9-9.00-EDG_Direct.zip **[/B][/B]

Result: 
> Connecting to goo.gl (goo.gl)|74.125.225.7|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://www2.ati.com/drivers/embedded/9.00-120815a-146426C-EDG_Direct.zip](http://www2.ati.com/drivers/embedded/9.00-120815a-146426C-EDG_Direct.zip) [following]
--2013-12-16 14:36:56--  [http://www2.ati.com/drivers/embedded/9.00-120815a-146426C-EDG_Direct.zip](http://www2.ati.com/drivers/embedded/9.00-120815a-146426C-EDG_Direct.zip)
Resolving www2.ati.com (www2.ati.com)... 23.60.138.87
Connecting to www2.ati.com (www2.ati.com)|23.60.138.87|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://support.amd.com/en-us/download/incomplete](http://support.amd.com/en-us/download/incomplete) [following]
--2013-12-16 14:36:56--  [http://support.amd.com/en-us/download/incomplete](http://support.amd.com/en-us/download/incomplete)
Resolving support.amd.com (support.amd.com)... 207.109.221.176, 207.109.221.169
Connecting to support.amd.com (support.amd.com)|207.109.221.176|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `amd-12.9-9.00-EDG_Direct.zip'

    [    <=>                                ] 48,605      62.8K/s   in 0.8s    

2013-12-16 14:36:57 (62.8 KB/s) - `amd-12.9-9.00-EDG_Direct.zip' saved [48605]

But, when I enter** [B]unzip [B]amd-12.9-9.00-EDG_Direct.zip**[/B], [/B]the result is:

> Archive:  amd-12.9-9.00-EDG_Direct.zip
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of amd-12.9-9.00-EDG_Direct.zip or
        amd-12.9-9.00-EDG_Direct.zip.zip, and cannot find amd-12.9-9.00-EDG_Direct.zip.ZIP, period.
myname@Minerva:~/catalyst12.9$ 

I have no idea what the problem is. If anyone can help, I'll love them forever.

---

### Post by fortune2008 on 2013-12-16
Hi adhoc from my experience with the legacy drivers it wasn't worth it at the end of the day i just used the driver that was provided by default

---

### Post by Bashing-om on 2013-12-16
AdHoc92; Hey,

You are beating your head against a stone wall.
> 
IF its an HD 2x/3x/4x then you are out of luck as AMD announced <last> summer that it is relegating these chipsets to legacy status and will not be developing new drivers for them. Existing restricted drivers from AMD won't work either, because they require X-server v1.12 and Ubuntu 12.10 uses X-server v1.13.
That's because, starting with Ubuntu 12.04.2, the X-server version was updated to a newer version that is now incompatible with the HD 2x/3x/4x series AMD cards.
(Mark Phelps)


Hate to be the harbinger of bad news, but, better now than later. Blame AMD.

[INDENT][INDENT]work with what works
[/INDENT][/INDENT]

---

### Post by AdHoc92 on 2013-12-17
> Hi adhoc from my experience with the legacy drivers it wasn't worth  it at the end of the day i just used the driver that was provided by  default                 

That would be fine if I just had to run normal applications, but I really want to play MineCraft and Starmade again. I would just use Windows, but the HDD conector on the MoBo broke, so I have to use an external HDD. Windows won't install on externals. Do older versions of Ubuntu or another Linux distro support the old Radeon HDs?

---

### Post by Bashing-om on 2013-12-17
AdHoc92; Hey:

Yes:
> 
 Do older versions of Ubuntu or another Linux distro support the old Radeon HDs?


Install the current Long term Support version 12.04.1 Must be version XX.1 to have the required X-server.
[http://old-releases.ubuntu.com/releases/12.04.1/](http://old-releases.ubuntu.com/releases/12.04.1/)
Then you may install the proprietary drivers.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by QIII on 2013-12-17
It's not really a matter of whether newer versions of Ubuntu support the older cards.  AMD/ATI does not maintain a driver that supports newer versions of X Server for those cards.

---

### Post by AdHoc92 on 2013-12-18
So is there any way to do it at all?

---

### Post by AdHoc92 on 2013-12-18
Oh, I'll try this. Thank you.

---

### Post by Bashing-om on 2013-12-18
AdHoc92; Roger that ,

Let us know how it goes. Installing version 12.04.1 is the solution to installing the proprietary drivers for that graphics card.
I might suggest that if the default - open source - drivers do not have the performance you want, next try the proprietary drivers available from 
launcher -> System Settings -> Addition Drivers; Then as a means of last resort install the drivers from AMD .. be aware that you will have to maintain your system's updates ! .. Some updates WILL break that driver and require it to be (RE-)installed. A pain that you will learn to live with.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

