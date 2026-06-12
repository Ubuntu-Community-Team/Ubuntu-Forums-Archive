---
title: "My brothers MFC j430w printer will print but won't scan , I'm using xsane for scanner"
date: 2013-08-01
forum: Hardware
---

### Post by Jon Anderson on 2013-08-01
I'm using Mint15 and Having problems , If you have the solution please pass it on to me.  

 My Brothers MFC j430w won't scan the drivers for both the printer and the scanner are downloaded . I get a error message saying “Failed to open device brother4:bus2;devl':invalid argument”
 

 

 When  I check with “scanimage -l” I get device `brother4:bus2;dev1' is a Brother MFC-J430W USB scanner

---

### Post by kurt18947 on 2013-08-01
Have you done this?[INDENT]**I cannot use my USB scanner  with a normal user.** 


The Brother Linux scanner driver works only with a superuser by default.
To use it with a normal user, you will have to make some settings.
[Setting for normal users]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html")
[/INDENT]

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u13.04](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u13.04)

There is also an installer glitch when installing on 64 bit systems.  I don't know if it's been fixed or not.  Here is the Brother info

You'll need to scroll down a bit to find the appropriate brscan version.  I think the 430 uses brscan4 but I'm not certain.

[URL="http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00106"]
[/URL]
[LIST=1]
[*]Install the scan driver. 
[*]Copy the following files under /usr/lib64/ to /usr/lib/ 
[*]**For brscan4 Users:**
/usr/lib64/sane/libsane-brother4.so.1.0.7
/usr/lib64/sane/libsane-brother4.so
/usr/lib64/sane/libsane-brother4.so.14/ to /usr/lib/. 
[/LIST]

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00106](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00106)

You'll probably need to restart after applying these fixes.
[URL="http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00106"]




[/URL]

---

### Post by Jon Anderson on 2013-08-01
Thanks for the quick responce, I've had trouble with this so your help is much appreciatedcd , I got the first part but the second part I'm a little confused, maybe you can help. It says to copy files from /usr/lib64/ to /usr/lib/, so do I errase them from /usr/lib64/ after I copy them to /usb/lib. Also do I cd to /lib/ and then type in each line seperately or all together seperately. (line after line),Hope I"m not to confusing.

---

### Post by Jon Anderson on 2013-08-01
> **kurt18947 said:**
> Have you done this?[INDENT]**I cannot use my USB scanner  with a normal user.** 


The Brother Linux scanner driver works only with a superuser by default.
To use it with a normal user, you will have to make some settings.
[Setting for normal users]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html")
[/INDENT]

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u13.04](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u13.04)

There is also an installer glitch when installing on 64 bit systems.  I don't know if it's been fixed or not.  Here is the Brother info

You'll need to scroll down a bit to find the appropriate brscan version.  I think the 430 uses brscan4 but I'm not certain.

[URL="http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00106"]
[/URL]
[LIST=1]
[*]Install the scan driver. 
[*]Copy the following files under /usr/lib64/ to /usr/lib/ 
[*]**For brscan4 Users:**
/usr/lib64/sane/libsane-brother4.so.1.0.7
/usr/lib64/sane/libsane-brother4.so
/usr/lib64/sane/libsane-brother4.so.14/ to /usr/lib/. 
[/LIST]

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00106](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00106)

You'll probably need to restart after applying these fixes.
[URL="http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00106"]



[/URL]

I m really new to this and don't want to screw up the system, I went to dolphin , thats my file manager to see what was in /usr/lib64/ and I opened every file that was in there , in office writer and it's just giberish . In the terminal I got to/usr/lib64 and I have know idea how to look in this file to copy from there to /usr/lib  and does copy mean copy and paste. Or do I just go to /usr/lib in terminal and just type in the three line. (/usr/lib64/sane/libsane-brother4.so.1.0.7
/usr/lib64/sane/libsane-brother4.so
/usr/lib64/sane/libsane-brother4.so.14/ to /usr/lib/. )

---

### Post by kurt18947 on 2013-08-01
> **Jon Anderson said:**
> I m really new to this and don't want to screw up the system, I went to dolphin , thats my file manager to see what was in /usr/lib64/ and I opened every file that was in there , in office writer and it's just giberish . In the terminal I got to/usr/lib64 and I have know idea how to look in this file to copy from there to /usr/lib  and does copy mean copy and paste. Or do I just go to /usr/lib in terminal and just type in the three line. (/usr/lib64/sane/libsane-brother4.so.1.0.7
/usr/lib64/sane/libsane-brother4.so
/usr/lib64/sane/libsane-brother4.so.14/ to /usr/lib/. )

No need to apologize for being unfamilar with this stuff, we've all been there.  I think those of us who have some familiarity with DOS and CLI (command line interface) have a small head start.  You don't need to open any files, just copy those in /usr/lib64 to /user/lib.  The installer is copying files to the wrong location. The reason those files look like gibberish is they're binaries, not text or config files that are human readable and editable.   The only files I had in usr/lib64 were the incorrect Brother files so it was pretty easy, copy everything from here to there.  I left the original files in their location and copied so there are two copies of the subject files, in /usr/lib and in usr/lib64.  My machine uses brscan3 which is a little more involved than brscan4.  I just checked and brscan4 is correct for the MFC-j430W.

---

### Post by Jon Anderson on 2013-08-01
/usr/lib64/sane/libsane-brother4.so.14/ to /usr/lib/ should be /usr/lib64/sane/libsane-brother4.so.1 Somehow you copied the wrong third line. but your advice was the advice that made it work , So thank very much and I really appreciated your time and help.

---

### Post by Jon Anderson on 2013-08-01
How do I mark it as solved

---

### Post by sonny3 on 2013-08-30
1 copy paper but much copy not this may printing paper how to setting that?

Filename:
Directory:
template:

title:
subjeck:
author:
keywords:
comments:
creation date:
change number:
last saved on
last saved by:
total editing time:
last printed on:


****!! -_-

---

