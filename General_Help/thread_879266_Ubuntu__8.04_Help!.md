---
title: "Ubuntu  8.04 Help!"
date: 2008-08-03
forum: General Help
---

### Post by Systmdcln13 on 2008-08-03
Ok I am on Windows XP Home with SP3. AMD Athlon processor. I downloaded Ubuntu 8.04.1 and it went on my desktop in a WinZip folder. I followed everything the Ubuntu site says to do and my MD5's verified out etc. When I click on the Winzip folder in Infra Recorder it automatically goes right to the burn process and burns the CD. When I try to run in Windows it tells me "Invalid CD" when I reboot and try to go in to it I get to the language section and it eventually tells me it can't read the CD. I think I am just not burning the disc correctly. Can anybody give me a hand? Am I doing this correctly? If not is there a specific file that I should be burning to the disc?


*EDIT*

Ok my MD5 when I right click on the Winzip folder is: c69e34e92d5402d1b87e6babc739f774

and when I extract the Winzip folder and right click on the md5sum file it is: b4af7618d1f9aec3f6fbc021371878dd

---

### Post by phidia on 2008-08-03
You need to burn that downloaded iso as an image-not as data. I have used infra Recorder (which is sort of a poor clone of gnomebaker I think) You may need to go to another tab in Infra Rec. to select "burn image" I forget now it's been a while since I used Infra.

Added: I found the Ubuntu wiki Howto [here]("https://help.ubuntu.com/community/BurningIsoHowto").
That describes exactly how to burn the iso using infra recorder.

---

### Post by Tom_ZeCat on 2008-08-03
First, I wouldn't put the Ubuntu download zip file on your desktop.  I'd put it in its own folder.  Then unzip it with WinZip or WinRAR.  When you do that, what do you get?  Do you get an ISO file?  If that's the case I'd burn open up your favorite CD/DVD burning software suite like Roxio Easy Media Creator or Nero and use it to burn the ISO file to a CD.  I would prefer not to just double click on the ISO file and take whatever app Windows decides should run.  

If you're not getting an ISO file when you unzip, then you've downloaded a different package of Ubuntu that I got.  An ISO file seems the simplest and easiest way to burn an Ubuntu CD.  Any decent CD/DVD burning program should handle that.  

You also haven't given enough detail on what you intend to do.  Are you installing Ubuntu on its own computer where it will be the only OS or are you installing it on your Windows XP machine to be a dual boot?

---

### Post by phidia on 2008-08-03
> 
*EDIT*

Ok my MD5 when I right click on the Winzip folder is: c69e34e92d5402d1b87e6babc739f774

and when I extract the Winzip folder and right click on the md5sum file it is: b4af7618d1f9aec3f6fbc021371878dd

You really want to check the md5sum of the actual iso file itself.
For 8.04.1 these are the md5sums to check against:
> 38e3f4d0774a143bd24f1f2e42e80d63 *ubuntu-8.04.1-alternate-amd64.iso
bbd21ded02c06b41c59485266833937a *ubuntu-8.04.1-alternate-i386.iso
b78ef719e3361e726b89bab78c526ad0 *ubuntu-8.04.1-desktop-amd64.iso
c69e34e92d5402d1b87e6babc739f774 *ubuntu-8.04.1-desktop-i386.iso
e7351d79903588699a383ae77854f734 *ubuntu-8.04.1-server-amd64.iso
7232c6004ba438890cd09aded162dc8e *ubuntu-8.04.1-server-i386.iso

The 1st sum you listed matches the 8.04.1-desktop-i386.iso

Just burn the iso _image_ per the link I supplied earlier.

---

### Post by Systmdcln13 on 2008-08-03
Well I got it installed (writing this on Ubuntu as we speak) but i used Wubi. I still however would love to get a working CD. I did unzip it in it's own folder and I get several sub folders. (linuxiso..which has no iso in it, install and many other folders) I can't find a single .iso file however. I have downloaded the file I Know 4 different times from 4 different locations through the ubuntu site! But I will give the wiki a shot and post what I get. Thanks for the fast replies!

---

### Post by CatKiller on 2008-08-03
Some archive programs "helpfully" associate themselves with .iso files. I'm sure that the file you downloaded was the .iso, and didn't need unzipping at all. Just burn that file to disk as an image per phidia's instructions, and you'll have your cd.

---

