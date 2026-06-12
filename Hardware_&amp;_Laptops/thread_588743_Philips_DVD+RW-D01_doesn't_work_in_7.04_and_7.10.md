---
title: "Philips DVD+RW-D01 doesn't work in 7.04 and 7.10"
date: 2007-10-23
forum: Hardware &amp; Laptops
---

### Post by Falconix on 2007-10-23
Since Ubuntu Feisty Fawn (7.04) i haven't been able to install Ubuntu from DVD/CD device because it doesn't find my DVD device (Philips DVD+RW-D01), with Edgy Eft there where no problems. 

If I want Feisty Fawn or Gutsy Gibbon installed on my system I have to install Edgy Eft first, then do an upgrade, but when the upgrade is done and I have rebooted the computer the DVD device disappears.

It doesn't even exist in /dev/ 
when i do an dmesg i cant see it there, so there is something weird and new with Feisty Fawn and Gutsy Gibbon.

I have no idea why its not working, there is NO problem with the hardware because i Install OpenSUSE 10.3 without any problem and could use the DVD device, I could even burn CD's with it also so there is some big problems with Ubuntu, i have my theory about it could be the cdrom module which is changed but I don't know.

Some one who is good at this could help me isolate the problem, because I have no idea where I should start.

---

### Post by Falconix on 2007-10-25
I have output demsg's from Edgy eft and Feisty Fawn, it shouldn't be  big different  between Feisty Fawn and Gutsty Gibbon.

The dmesgs are of course  taken from the same machine with the same hardware configuration 

Here is the Edgy Eft dmesg
[http://paste.ubuntu-nl.org/42071/](http://paste.ubuntu-nl.org/42071/)

And the Feisty Fawn dmesg 
[http://paste.ubuntu-nl.org/42072/](http://paste.ubuntu-nl.org/42072/)

---

### Post by Falconix on 2007-10-26
Anyway i have done a bug report about this issue, if you have a Dell Dimension 8200 with Philips DVD+RW-D01 driver or your drive doesn't work in Feisty fawn or Gutsy Gibbon, please provide information about your problem at
[https://bugs.launchpad.net/ubuntu/+bug/157260](https://bugs.launchpad.net/ubuntu/+bug/157260)

---

