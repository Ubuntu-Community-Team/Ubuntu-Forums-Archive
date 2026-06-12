---
title: "How do i install Openoffice/apps from a Ubuntu 8.0 OS CD"
date: 2008-07-16
forum: General Help
---

### Post by Avinash.Rao on 2008-07-16
Dear all,

I have installed Ubuntu Studio 8.0, I want to install Openoffice writer, calc, Presentations, help files and other apps from the Ubuntu 8.0 - hardy CD. I added the CDROM in synaptic package manager, but i was not able to install from the CD.

I have also checked the option to install from CD in software sources.

Can i install openoffice without downloading it from the internet? can i do this from the CD?

Can i use dpkg/aptitude, i tried all this but couldn't access the packages in the cd.

Thanks
Avinash

---

### Post by tuxxy on 2008-07-16
OpenOffice.org Office Suite from the Applications > Add/Remove menu, or install the openoffice.org package in synaptic. 

or in terminal


```
sudo apt-get install openoffice.org
```

---

### Post by tuxxy on 2008-07-16
Its in the repos, OpenOffice.org Office Suite from the Applications > Add/Remove menu, or install the openoffice.org package in synaptic. 

or in terminal


```
sudo apt-get install openoffice.org
```

---

### Post by DynamicMouse on 2008-07-16
I maybe missing the point but doesn't apt-get try to access the internet, so the earlier responses wouldn't solve the original problem.

When I lost my internet connection to a machine I had to install updates by using an alternate ubuntu ISO rather than the usual live-cd.

from here
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
there is a checkbox at the bottom that says
"Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer."

I obviously had to download this on another machine and write it to a cd but it did the trick

---

### Post by Avinash.Rao on 2008-07-16
Thanks for your replies, but i don't want to download and install openoffice, apt-get will access the internet. My question was, i have a machine installed Ubuntu studio and a Ubuntu 8.0 OS CD. Can i install openoffice or any other applications using this cd??? 

Or imagine, i don't have an internet connection and i have a Ubuntu OS CD, can i install openoffice using this CD?? 

Avinash

---

