---
title: "Install MP600 Ubuntu 9.04"
date: 2009-04-20
forum: Installation &amp; Upgrades
---

### Post by BorisPlankton on 2009-04-20
OK Iam new too Linux and cannot get my Canon MP600 printer to install/work on Ubuntu 9.04. I found this on the web and followed it through:
-=================================================================
Re: HOWTO: Canon PIXMA MP600
I HAVE FOUND THE WONDER SOLUTION FOR THE MP600 PRINTER DRIVER TROUBLE IN UBUNTU 8.10!!! !!!


Intro: I did every step described here and elsewhere,... and everywhere!
And it did not help.
Then, after a full day of script-wrestling, I had and idea ...


Development: I've unpacked all the Australians archives, made a search for "MP600.ppd" and the result was: !"canonmp600.ppd"! I did include that file in that post!

Solution!:
...
...
"main menu" ---> "System" ---> "Administration" ---> "Printing"

In the Printer Proprieties window, choose: Settings ---> Make and Model ---> Change ---> Provide PPD file
And select the "canonmp600.ppd".

Attached Files
File Type: zip 	canonmp600.ppd.zip (3.3 KB, 24 views)
Last edited by 5daniil5; February 26th, 2009 at 02:17 AM.. Reason: Correction and Precision 
=======================================================================
I have saved the ppd file noted above to my desktop. Now when I get to the Provide ppd file I am presented with two options: 1) Use the new PPID as is 
and 2)Try to copy the old settings over from the old PPID

I select 1) and get the message 
''Printer 'MP600' requires the 'pstocanonij' program but it is not currently installed.  Please install it before using this printer''

No idea what to do now. Had a look on the web and thoroughly confused myself.Grateful for any help you can give me - baby steps for me I am afraid.
All my installation has gone well apart from this.

Kind regards
Paul

---

### Post by BorisPlankton on 2011-05-15
I will answer this myself. After much angst I paid for Turboprint and this does does the job fine.

---

