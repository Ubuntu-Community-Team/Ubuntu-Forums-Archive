---
title: "Uninstall-Ubuntu.exe"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by guysagy on 2009-04-08
Hi, 

I installed Ubuntu within (i.e. as an application, no dedicated partition) Windows XP Media Center edition. The installation went fine. 

Now I am trying to uninstall it from within Windows .... but Uninstall-Ubuntu.exe is simply not running. What may be wrong?
I ran it from a command line, no error message was emitted. 

Can I simply delete the D:\ubuntu directory? If yes, will it / how do get rid of the boot time menu to select Windows / Ubuntu?

Thank you,
Guy

---

### Post by lisati on 2009-04-08
It probably wasn't a good idea to run it from the command line. Anything show up on the control panel->add/remove programs?

---

### Post by guysagy on 2009-04-08
Hi, 

... and more information: 
- the Ubuntu is version 8.04.1.505. 
- selecting Change/Remove via the Add or Remove Programs utility gives same results (i.e. nothing happens). 
- the option for installing Ubuntu within Windows was one of the options on the CD

Thanks again,
Guy

---

### Post by guysagy on 2009-04-08
That was a quick answer ... I didn't even see it before my 2nd post ... using the command line was to see if any error message is emitted.  The CP->Remove option was my first attempt :-). 

Guy

---

### Post by lisati on 2009-04-08
> **guysagy said:**
> Hi, 

... and more information: 
- the Ubuntu is version 8.04.1.505. 
- selecting Change/Remove via the Add or Remove Programs utility gives same results (i.e. nothing happens). 
- the option for installing Ubuntu within Windows was one of the options on the CD

Thanks again,
Guy
I'm not sufficiently versed in the anatomy of Windows bootloader to offer any suggestions, and would welcome suggestions from others....

---

### Post by Partyboi2 on 2009-04-08
According to the [[COLOR=Blue]wubi guide[/COLOR]]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?") you should be able to delete it manually by deleting C:\ubuntu and C:\wubildr*. then editing your boot.ini file and removing the entry for ubuntu.

---

### Post by lisati on 2009-04-08
> **Partyboi2 said:**
> According to the [[COLOR=Blue]wubi guide[/COLOR]]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?") you should be able to delete it manually by deleting C:\ubuntu and C:\wubildr*. then editing your boot.ini file and removing the entry for ubuntu.

Now why didn't I think of suggesting that? (I think I'd better go off and give myself a severe telling off......)

---

### Post by guysagy on 2009-04-08
Hello, 

Thanks a lot all for the real quick help! 

I will follow these instructions (if I run into any problems, I will post more questions). 

Thanks again ):P, 
Guy

---

### Post by Partyboi2 on 2009-04-08
> **lisati said:**
> Now why didn't I think of suggesting that? (I think I'd better go off and give myself a severe telling off......)
I have moments like these all the time ;)

---

