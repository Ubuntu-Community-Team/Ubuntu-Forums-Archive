---
title: "Boot error: &quot;Try (hd0,0): NTFS5:&quot;"
date: 2008-09-01
forum: General Help
---

### Post by Retor on 2008-09-01
I have a dual boot set up with Ubuntu. Ubuntu renders this error: 

> Try (hd0,0): NTFS5:

And then promptly halts. 

Any suggestions? Interpretations? Solutions?

---

### Post by porchrat on 2008-09-01
I found this...should help

[http://ubuntuforums.org/showthread.php?t=798283]("http://ubuntuforums.org/showthread.php?t=798283")

Is it a true dual boot or a Wubi install?

---

### Post by Retor on 2008-09-02
Thanks for the link. My error, however, doesn't go away. It just hangs. But I gather it means it can't find the partition - or something.

So i'm unable to perform all the steps in the other thread. 

I thought the install wasn't wubi, but then I found som wubi-named files in the ubuntu directory "winboot" and a uninstall file that says "wubi uninstall" when i launch it. So I guess it is.

---

### Post by StoopidPyro on 2009-09-22
> **Retor said:**
> Thanks for the link. My error, however, doesn't go away. It just hangs. But I gather it means it can't find the partition - or something.

So i'm unable to perform all the steps in the other thread. 

I thought the install wasn't wubi, but then I found som wubi-named files in the ubuntu directory "winboot" and a uninstall file that says "wubi uninstall" when i launch it. So I guess it is.

has this issue been resolved?  i've run in to the same issue with Karmic Koala Alpha 6.

---

### Post by jawadahmed on 2009-11-28
Any body got a workaround? I have same problem. i have installed ubuntu 9.10 desktop using Wubi.

---

### Post by schoft on 2010-03-21
Same problem with wubi!

---

### Post by sapa2ler on 2010-05-05
For solution, visit 
 
[http://nizam-online.blogspot.com](http://nizam-online.blogspot.com)
 
 
Hopefully it helps!!!!
 
:KS

---

### Post by piezack on 2010-05-06
Where are the wubildr.mbr and wubildr files located when doing the guide posted at 
[http://nizam-online.blogspot.com]("http://nizam-online.blogspot.com/") ? He didn't say where they are.

---

### Post by sapa2ler on 2010-05-06
Hi,
 
wubildr and wubildr.mbr should be in the C: drive.  For example;
 
c:\wubildr
c:\wubildr.mbr
 
and its also can be found in your windows installation folder. for example;
 
c:\ubuntu\winboot\wubildr
c:\ubuntu\winboot\wubildr.mbr
 
 
Hope it helps...
 
:KS

---

### Post by kamark on 2010-06-01
You can try this solution as well if you really cant boot into ubuntu

[Solution]("http://www.kamarkhan.com/2010/06/01/try-hd00-ntfs5-no-wubildr-after-installing-wubi-windows-7/")

---

