---
title: "laptop  sound not working"
date: 2012-05-06
forum: Hardware
---

### Post by clynn3 on 2012-05-06
I just put Ubuntu 10.04 on my wifes's laptop and everything went smooth except the sound isnt working.  I went to help.ubuntu.com/community/SoundTroubleshooting and got to

 #5. Do you have the sound modules installed?
 this is what i got...

:~$ find /lib/modules/`uname -r` | grep snd
find: '/lib/modules/uname -r': No such file or directory

so i went on with 
:~$ sudo apt-get install linux-resricted-modules- 'uname -r' linux-generic

and i got back this.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-resricted-modules

I look for answers what i should do next but i could find anything.

any help would be great
thank you

---

### Post by Kevin1164 on 2012-05-06
One possible situation:have you uninstalled any programs lately? try checking your audio driver if its properly functioning, right click My Computer then click on Manage, then in the computer management window click on Device Manager to see all the drivers currently found on your system. if every thing's fine you shouldn't see any drivers there that is colored yellow, else reinstall the driver needed, and i got this from my  [HDC A9100]("http://www.lovebargaining.com/Wholesale/A9100-is-1-sid-1.html")
Another:You might need to reinstall your sound card driver.
Download form [http://www.downloadatoz.com/driver/artic…](http://www.downloadatoz.com/driver/artic…)
Source(s):
[http://www.downloadatoz.com/driver/](http://www.downloadatoz.com/driver/)

---

