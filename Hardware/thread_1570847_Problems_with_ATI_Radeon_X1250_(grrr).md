---
title: "Problems with ATI Radeon X1250 (grrr)"
date: 2010-09-08
forum: Hardware
---

### Post by Shanazon on 2010-09-08
From what I understand, this is not an uncommon compatability issue...even across multiple linux distributions...

I've been culling through the forums trying to find some kind of answer that's going to work.

I went to AMD and downloaded the Linux driver and installed it...nothing.

when I ran:

$ sudo update-pciids
$ lspci

I got:


01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]

...so it is recognized, but there is no GL support...none.

I'm running 10.04 on a Toshiba Satellite L305D.
I've tried going to Toshiba in the hopes that I may find some kind of Toshiba-specific information or PDFs that they might have available to give me some answers, but alas there were none.  Any help would be greatly appreciated!

---

### Post by arrimapirate on 2010-09-08
I have the exact same card and had this problem. 

The non-open source drivers only work with an older xorg driver. You have to use the opensource ones that come with Ubuntu or attempt to downgrade using this forum for help:
[http://ubuntuforums.org/showthread.php?t=1171445](http://ubuntuforums.org/showthread.php?t=1171445)

---

### Post by Shanazon on 2010-09-09
Thanks for all the help.  I looked thru the forum threads and pages and stuff.  It all looks really involved to get GL working...it was pretty much in the hopes of getting Quake going, but if it's going to be that big of a deal then I had best not chance it just yet.  Hopefully some better open source drivers come along, seeing as this is an issue for many Radeon users.

---

### Post by Yellow Pasque on 2010-09-09
Make sure you remove the proprietary drivers (they don't support your card): [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver)

After that, you can try the latest open-source drivers: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by Shanazon on 2010-09-09
Temujin..wow...thanks.  Everything works properly now...I'm amazed, considering the mess of horror stories that were going around.  Beautiful!  Thanks!

---

