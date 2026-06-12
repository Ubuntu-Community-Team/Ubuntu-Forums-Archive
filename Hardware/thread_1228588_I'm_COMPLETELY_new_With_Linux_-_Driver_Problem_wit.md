---
title: "I'm COMPLETELY new With Linux - Driver Problem with Wirless"
date: 2009-08-01
forum: Hardware
---

### Post by Sean.v.Niekerk on 2009-08-01
HI there Guys...

I AM VERY VERY new with Linux, but fed up with windows... I am having problems installing a wireless driver for my Acer Aspire one Netbook... IT came preinstalled with Linux but not Ubuntu. So i formatted and reloaded Ubuntu. 

Tried using the Hardware installation Application, but no matter how many times I enable or disable the Driver it just does not seem to work...

Thanks in advance

Sean

---

### Post by pastalavista on 2009-08-01
You should probably connect to the internet via wired ethernet to be able to download and install the wireless driver you need.

---

### Post by Sean.v.Niekerk on 2009-08-01
I have tried that, and I even updated to the newest version of Linux... Except the Hardware Drivers Application, is there another program i should run to download the driver? I have downloaded and installed NDISWRAPPER, i don't know what for but someone said the Linux uses it for the wireless, when i googled it...

---

### Post by wyliecoyoteuk on 2009-08-01
Are you running the Ubuntu netbook remix, or the full thing?
I run UNR on my AA1, and everything works fine.

---

### Post by arez on 2009-08-01
> **Sean.v.Niekerk said:**
>  I have downloaded and installed NDISWRAPPER, i don't know what for but someone said the Linux uses it for the wireless, when i googled it...

yea ndiswrapper is emulator driver..it will emulate windows wireless driver.inf so  that it can be used on linux..GO to administration,launch Ndiswrapper(Windows Wireless Driver)..Enter password then install new driver..Give it a try by browsing ur wireles driver.inf(can be found in the same dir of the driver)..and apply..
Now u should surfing hepily...:D

---

### Post by Sean.v.Niekerk on 2009-08-01
Cool man... I think i have made a messup with the NDISWRAPPER installation, i cannot find it under the Administration panel? I went into Terminal and installed it form there? 

Thanks man... apreciate your help!!

I am running the full version on Ubuntu, you think it is a problem?


Thanks

---

### Post by Sean.v.Niekerk on 2009-08-01
Thanks You Guys... I Googled a "How to" on the ndiswrapper Application. Followed the steps and all is working... I made the mistake on not downloading the Windows .inf and .sys files and putting them into the same directory " ~/drivers". 

Linux is Awesome By the way!!!!


Thanks for your help!!!

---

