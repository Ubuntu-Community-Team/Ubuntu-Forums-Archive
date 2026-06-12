---
title: "Canon Pixma Ip1500 &amp; 64bit Ubuntu"
date: 2012-09-20
forum: Hardware
---

### Post by jozi on 2012-09-20
I'm trying to get a printer to work on a clean install of 12.04 64bit. I've tried some of the tutorials/posts but I can't get anywhere or don't fully understand what I should be doing.

---

### Post by pdc on 2012-09-22
Hi Jozi;

so this is an 8yr old printer; Canon are now providing linux drivers for ..all new printers they sell...........it seems to me...

......but back in 2004, there was less;

so I see the linux drivers for the ip1500 are rpm; 

either from Canon europe as a package that has them all bundled together

[http://www.canon.co.uk/Support/Consumer_Products/products/printers/InkJet/PIXMA_iP_series/PIXMA_iP1500.aspx?type=download&page=1](http://www.canon.co.uk/Support/Consumer_Products/products/printers/InkJet/PIXMA_iP_series/PIXMA_iP1500.aspx?type=download&page=1)

or from Canon Asia, where one can select what one wants

[http://support-asia.canon-asia.com/P/search?model=PIXMA+iP1500&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-asia.canon-asia.com/P/search?model=PIXMA+iP1500&menu=download&filter=0&tagname=g_os&g_os=Linux)

so you would need to use alien to convert them to .deb packages first;

and then install the .deb packages;

by using a 64bit system, it makes it harder to ensure an older printer works; as Canon's drivers are for 32 bit systems; so they look in /lib rather than in /lib64 and one needs to add symbolic links;

if you are keen on your printer; you could contemplate how attached you are to "a clean install of 12.04 64bit" and whether you would add a new, small install of 32bit 12.04 

if you just want to use the 64bit I can help with installing;

if you first describe what you have done...

if you subscribe to a thread; (top right of page: thread tools; you can get an email every time there is a response...........most people post and never seem to be heard of again....................)

---

### Post by jozi on 2012-09-22
Haha, yup 8yr old printer, it does it's job :p 

I've been tempted to just reinstall 32bit OS since it looks like less hassle than messing with drivers. There's not really any difference that my mam will notice between the two.

I'm wondering would I be better going with 11.10? I've also got problems with no-sound, maybe the older distro has drivers for the older mobo.

And I always subscribe, I browse occasionally but don't post very often cause I usually have nothing to add :(

---

### Post by pdc on 2012-09-22
enjoy the ip1500 as it works well; we have an ip series ourselves and they are very good printers;

how about we see if we can get the ip1500 going on your 64bit? If we can't, you can install the 32bit ......

this link

[http://ubuntuforums.org/showthread.php?t=2021854](http://ubuntuforums.org/showthread.php?t=2021854)

should give you the two steps you need to get it going

1) how to use alien to convert an .rpm package to a .deb package

2) how to create symbolic links so that the canon driver knows to look in /lib64 where it only thinks to look in /lib 

Install

go here 

[http://support-asia.canon-asia.com/contents/ASIA/EN/0900717603.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0900717603.html)

to download the Canon Bubble Jet Print Filter Ver. 2.50 for Linux (rpm **_Common package_**)

and then download the Canon Bubble Jet Print Filter Ver. 2.50 for Linux (**_rpm Package for iP1500_**)

[http://support-asia.canon-asia.com/contents/ASIA/EN/0900718001.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0900718001.html)

*you **MUST** install the common package first; then the dedicated 1500 package after*.............


if you open a terminal 

and type

> cd Downloads..and hit enter....

that should get you into your Downloads directory

> sudo alien -s bjfilter-common-250.3i386.rpm..hit enter *and enter sudo password*

should build you a bjfilter-common-250.3i386.deb package

and 

> sudo alien -s bjfilter-pixmaip1500-250.2i386.rpm

......should build you a bjfilter-pixmaip1500-250.2i386.deb package

as per the post I mention  above ..he recommends you next do 

> sudo ln -s /usr/lib /usr/lib64
sudo ln -s /usr/local/lib /usr/local/lib64

then 

> sudo dpkg -i bjfilter-common-250.3i386.deb

to get the common package installed.........

and then 

> sudo dpkg -i bjfilter-pixmaip1500-250.2i386.deb

to get the specific ip1500 package installed

.....if you then paste this into a spare browser window

[http://localhost:631/printers/](http://localhost:631/printers/)

you can check the printer is installed

______________________________________________

(I don't think you need the AppArmor detail that the thread mentions......

____________________________________________-

You ask about installing 11.10; I would stay with 12.04 as it is a long-term support version.............good for five years.......

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

......that can be very good;

great that you subscribe................

---

### Post by jozi on 2012-09-22
I just skimmed over that and appreciate the effort and your help in making the post, for that I will have to owe you a pint! It's a bit late now but I'll give all of the below a go tomorrow evening and let you know how I get on with it.

It's rare we need to print something at all really so doesn't make sense to buy a new printer - although it would be much easier to get working, but I'll learn less from that.

---

### Post by pdc on 2012-09-22
sure; sleep on it and have a go tomorrow!

---

### Post by jozi on 2012-09-23
I got this far before getting an error. Some of my file names were different to what you had but I just changed (copy/paste) the correct ones for each command.

> **pdc said:**
> 
then 



to get the common package installed.........

and then 



to get the specific ip1500 package installed

.....if you then paste this into a spare browser window

[http://localhost:631/printers/](http://localhost:631/printers/)

you can check the printer is installed

______________________________________________

(I don't think you need the AppArmor detail that the thread mentions......

____________________________________________-

You ask about installing 11.10; I would stay with 12.04 as it is a long-term support version.............good for five years.......

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

......that can be very good;

great that you subscribe................


The 2 file I made with alien are:
bjfilter-pixmaip1500-2.50
bjfilter-common-2.50

Should they have an extension or are these just hidden? The have  folder icon with a lock on them.

Here is where I got stuck:

```
rose@rose-desktop:~/Downloads$ sudo dpkg -i bjfilter-common-2.50
dpkg-split: error: error reading bjfilter-common-2.50: Is a directory
dpkg: error processing bjfilter-common-2.50 (--install):
 subprocess dpkg-split returned error exit status 2
Errors were encountered while processing:
 bjfilter-common-2.50
```

I also tried it with the following extension on the folder:

```
rose@rose-desktop:~/Downloads$ sudo dpkg -i bjfilter-common-2.50.debdpkg: error processing bjfilter-common-2.50.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 bjfilter-common-2.50.deb
```

---

### Post by pdc on 2012-09-23
I have just installed alien;

......my understanding was it would convert an .rpm package to a .deb package

I used alien convert the exact packages you have; that I downloaded here;

I create what you have......we both need to research this more; sorry;

if all else fails, we have the Canon MG2160: it was about $35 US and that ain't bad.......the ink refills cost more!

when I have more time later, I will research this more, but currently.. stuck

---

### Post by jozi on 2012-09-23
I'll try install alien again and look into it a little more. You've been great help so far! I'm tempted to get another printer but I can't afford one right now :(

---

### Post by pdc on 2012-09-23
I have just googled on 

> ubuntu ip1500 alien solved

and I get things like this

[http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html](http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html)

........if you add this ppa and see if you can select the ip1500 driver..

________________________--

and if you like to do it all yourself.............

[http://ubuntuforums.org/showthread.php?t=1517089](http://ubuntuforums.org/showthread.php?t=1517089)

here's a man who worked through it all

---

