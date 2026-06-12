---
title: "canon pixma ip2702 wont print"
date: 2013-02-16
forum: Hardware
---

### Post by bxk5619 on 2013-02-16
So last week I purchased a Canon Pixma ip2702, thinking this would solve my unfortunate dilemma of not being able to print out forms and such I needed instead of driving out to the Library to do so. I hooked it up, and everything seemed to look okay, until it came time to print. I was about to print a photo out for a project I wanted to start, but after I hit print, nothing happened. Any tips as to why the printer is not responding to my requests to print?

---

### Post by pdc on 2013-02-17
hi there bxk5619

Canon supply printer drivers for their printers;

indeed they supply them as .deb packages and .rpm packages, as well as source code

if you go here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100272002.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100272002.html)

and download the deb package.....as ubuntu uses deb packages...... and SAVE it to your Downloads directory......

..... you don't tell us if you are using 32bit or 64bit..

..........if you open a terminal....

if 64bit do this

> [COLOR="Red"]sudo ln -s /usr/local/lib /usr/local/lib64[/COLOR]

and 

> [COLOR="Red"]sudo ln -s /usr/lib /usr/lib64[/COLOR]

and then do as below 

if 32bit..

> [COLOR="Red"]cd Downloads[/COLOR]

> [COLOR="Red"]tar -zxvf cnijfilter-ip2700series-3.30-1-i386-deb.tar.gz[/COLOR] 


> [COLOR="Red"]cd cnijfilter-ip2700series-3.30-1-i386-deb[/COLOR] 

> [COLOR="Red"]./install.sh[/COLOR]

---

### Post by bxk5619 on 2013-03-03
Oops, sorry, forgot to mention that I was using 64 bit... [CENTER][COLOR=#000000]:neutral: 
Anyhow, when I did all that, I then got this: 

> [/COLOR][/CENTER]hayley@hayley-desktop:~$ sudo ln -s /usr/local/lib /usr/local/lib64ln: creating symbolic link `/usr/local/lib64/lib': File exists
hayley@hayley-desktop:~$ sudo ln -s /usr/lib /usr/lib64
ln: creating symbolic link `/usr/lib64/lib': File exists
hayley@hayley-desktop:~$ cd Downloads
hayley@hayley-desktop:~/Downloads$ tar -zxvf cnijfilter-ip2700series-3.30-1-i386-deb.tar.gz
cnijfilter-ip2700series-3.30-1-i386-deb/
cnijfilter-ip2700series-3.30-1-i386-deb/packages/
cnijfilter-ip2700series-3.30-1-i386-deb/packages/cnijfilter-common_3.30-1_i386.deb
cnijfilter-ip2700series-3.30-1-i386-deb/packages/cnijfilter-ip2700series_3.30-1_i386.deb
cnijfilter-ip2700series-3.30-1-i386-deb/resources/
cnijfilter-ip2700series-3.30-1-i386-deb/resources/printer_zh_utf8.lc
cnijfilter-ip2700series-3.30-1-i386-deb/resources/printer_ja_utf8.lc
cnijfilter-ip2700series-3.30-1-i386-deb/resources/printer_fr_utf8.lc
cnijfilter-ip2700series-3.30-1-i386-deb/install.sh
hayley@hayley-desktop:~/Downloads$ cd cnijfilter-ip2700series-3.30-1-i386-deb
hayley@hayley-desktop:~/Downloads/cnijfilter-ip2700series-3.30-1-i386-deb$ 
hayley@hayley-desktop:~/Downloads/cnijfilter-ip2700series-3.30-1-i386-deb$ ./install.sh
==================================================


Canon Inkjet Printer Driver Ver.3.30-1 for Linux
Copyright CANON INC. 2001-2010
All Rights Reserved.


==================================================
Command executed = sudo dpkg -iG ./packages/cnijfilter-common_3.30-1_i386.deb
dpkg: error processing ./packages/cnijfilter-common_3.30-1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 ./packages/cnijfilter-common_3.30-1_i386.deb
hayley@hayley-desktop:~/Downloads/cnijfilter-ip2700series-3.30-1-i386-deb$ 


[CENTER][COLOR=#000000]

Am I correct in thinking this driver is not installed?[/COLOR][/CENTER]

---

### Post by pdc on 2013-03-03
hi Hayley; 

> [COLOR="#EE82EE"]Am I correct in thinking this driver is not installed?[/COLOR] ......indeed...... 

you can check by copying and pasting the command 

> [COLOR="#FF0000"]sudo dpkg -l | grep cnijfilter[/COLOR] .......and if you don't see cnijfilter ......the driver is not installed

...... having done the symbolic links, you can install by opening your Downloads directory using the mouse; right-click on the .tar.gz package and open with archive manager; then open the packages folder; then right-click on the COMMON package; and select "install with gdebi installer"; when done, then right-click on the ip2700 package and do as before ........

......perhaps copy and paste the grep command I gave you above.....it should now show the cnijfilter packages are installed......... you should then be good to go, and hopefully...........the symbolic links created before driver install will make it all work for you

---

### Post by condor 088 on 2013-09-20
I have been using a iP2700 series, (2703) on Win XP with no problems. Transitioning slowly to ubuntu 12.04.3LTS  a little at a time. Had trouble accessing the internet with my USB modem, and finally have it working after six days of search and try, caused by me not carefully reading the instructions.
It was now time to tackle the task of getting the printer to work in ubuntu 12.04.3. After searching and reading what I could find about Canon printers with linux;,I readied myself for another six day battle session. I decided to begin with the most simple approach; and went to System Settings>Printing>New Printer; (all graphic interface selections). Inserted Canon CD in the optical drive, and clicked on the "Forward" button. The window entitled "Searching for additioal drivers" came on screen. A seach box appeared with a rapidly moving progress bar; and continued for approximately 5 to 7 minutes. Then a sscreen appeared prompting to print a test page. What the heck, give it a try. The test page printed beautifully, with 8 circular dsics of different colors, with a different alphabetical letter in the center of each disc. Below the discs, was the following text:.
     Media Limits: 0.14 x 0.21  to 8.36 x 10.79 inches.
     Job ID: Canon iP 2700 series
     Driver: STP00052
     Driver Version:
     Description: Canon iP 2700 series
     Make and Model: Canon PIXUS iP2700 - CUPS+Gutenprint v5.2.8-pre1
     Printer: Canon-iP2700 series
Well, I was slightly impressed by this, but remembered  a thread on the forum , where a test page would print, but no other pages would print.
Went to a Libre Writer file, and proceeded to ask the machine to print it for me. The printer chattered a few times, a sheet was shifted into the printing position, and the document proceeded to print. When the text portion of the page was complete, the paper feed slowed to a crawl for the remainder of the page. But it was a good print. I was shocked by this performance after reading of the difficulty some ubuntu users were experiencing with Canon Drivers.
I can not explain where the driver came from, the Canon CD or the ubuntu libraries.
I shall now tackle the problem of getting my Visioneer 9020 scanner to work with Ubuntu. Wish me luck on this one.
Hope this may be some help to others out there with this Canon printer.
I sincerely hope this might be of some help to others out there with this Canon printer.

---

