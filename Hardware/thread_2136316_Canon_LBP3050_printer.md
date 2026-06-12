---
title: "Canon LBP3050 printer"
date: 2013-04-17
forum: Hardware
---

### Post by petercool on 2013-04-17
Hello guys,
Anyone who knows how to install a canon LBP3050 printer on a (( ubuntu,kubuntu 12.04 x64 )) desktop?
I've been searching and testing since last year...just succeed once on a kubuntu 12.04 x32 notebook.Sigh!!!

I had tried to use google translate reading that french post about installing Canon LBP3050...
but translation and my limited english made me not succeed i guess.Or my intelligence sucks?haha.....who knows?

:KS Anyway,anyone can tell me how to solve this problem?Thanks a billion!:popcorn:

P.S.My system is kubuntu 12.04 x64.
-------------------------------------------------------------------------------------------------------------[Solved]
Problem Solved....according to Sivella's 7 post in :[http://ubuntuforums.org/showthread.php?t=1983091&highlight=canon+lbp]("http://ubuntuforums.org/showthread.php?t=1983091&highlight=canon+lbp")
I succeed to print something now.
Thank you!Sivella
Thank you!Others who had replied to my quetions and ready to reply my questions even just in their mind! :P

---

### Post by TheFu on 2013-04-17
Not what you wanted to hear, but ... 

My Mom had a Canon printer - not the same model.  There was some proprietary software for $50 that worked. We used the trial to verify that.  
In the end, I decided that getting her a natively supported printer from a manufacturer who supported current linux drivers was the better choice. We gave away the Canon and got either a Samsung or Brother - can't recall.  I have both a Brother All-in-One and a Samsung laser printer here that "just work" with every version of Linux I have, even the scanning works great with gscan2pdf/sane out of the box.

I've read since that time that Canon makes linux drivers available on some non-USA websites, so you might find the drivers you need there. I dunno.  There are multiple Linux hardware compatibility lists. Before purchasing any hardware, I check those. When Linux is supported, Windows is generally even better supported too.

---

### Post by SeijiSensei on 2013-04-17
A quick Google search took me here:  [http://software.canon-europe.com/products/0010177.asp](http://software.canon-europe.com/products/0010177.asp)

---

### Post by petercool on 2013-04-17
> **TheFu said:**
> Not what you wanted to hear, but ... 

My Mom had a Canon printer - not the same model.  There was some proprietary software for $50 that worked. We used the trial to verify that.  
In the end, I decided that getting her a natively supported printer from a manufacturer who supported current linux drivers was the better choice. We gave away the Canon and got either a Samsung or Brother - can't recall.  I have both a Brother All-in-One and a Samsung laser printer here that "just work" with every version of Linux I have, even the scanning works great with gscan2pdf/sane out of the box.

I've read since that time that Canon makes linux drivers available on some non-USA websites, so you might find the drivers you need there. I dunno.  There are multiple Linux hardware compatibility lists. Before purchasing any hardware, I check those. When Linux is supported, Windows is generally even better supported too.

Thx,Canon only provide 64-bit rpm and 32-bit deb!!!What I want most is 64-bit deb! Sigh!
I had tried to use alien to change rpm file to deb,but I just couldn't print anything.So I had tried different ways!Till now still not succeed!
I also have a Brother all-in-one printer,but I haven't used it for a long time since I bought this laser printer.

---

### Post by petercool on 2013-04-17
> **SeijiSensei said:**
> A quick Google search took me here:  [http://software.canon-europe.com/products/0010177.asp](http://software.canon-europe.com/products/0010177.asp)

Don't know if that old driver still work for my laser printer.'Cause they already have  'Canon CAPT Printer Driver for Linux (2.50) '.
So....Anyway,thx

---

### Post by pdc on 2013-04-17
to install the CAPT driver it would be best to delete all you have already set up:

please copy and paste back what you get from  

> [COLOR="#FF0000"]sudo dpkg -l | grep Canon[/COLOR]

when you [COLOR="#0000FF"]copy[/COLOR] and [COLOR="#0000FF"]paste[/COLOR] this command into a terminal: use the top line of the terminal .....file.......Edit and down to Paste

________________________________________________________________________
for a renewed attempt at a 64bit install, Canon show how to delete any existing entries

1. Delete the registered printer from the ccpd daemon setup file. > [COLOR="#FF0000"]sudo /usr/sbin/ccpdadmin -x LBP3050[/COLOR]

2. Delete the printer's spooler registration. > [COLOR="#FF0000"]sudo /usr/sbin/lpadmin -x LBP3050[/COLOR]
_________________________________________________________________________________________________________________

then you could best help us by showing a screenshot of Synaptic (package manager) with the entry ia32-libs

ie we need to know what you have installed 

as Sivella insists 

> [COLOR="#EE82EE"]It is therefore necessary to manually install the ia32-libs package from a previous version ( 11.10 )[/COLOR]. 

---

### Post by petercool on 2013-04-18
I had tried different methods according to many posts including that french guy about using ia32-libs from earlier ubuntu 11.10 too....but maybe some procedure not completely executed!such as some components not found or installed,so...maybe...that's the reason it didn't succeed to even print 1 page!
Maybe i'll try the whole procedure again according to his article!I'm afraid that it still can't help any....sigh!Till one day i'll turn into an old 32-bit machine user again. :P Who knows?
Thx for  you advice!

---

### Post by TheFu on 2013-04-18
You can use the 32-bit Debian drivers, there is just a dependency with the ia32-libs package. If you install that (not certain what the actual name is), then 32-bit programs should work fine.

Nothing works, until it does.  When we are doing something new, it is hard to tell if we are 1 or 20 steps from a working solution. After you get the ia32-libs package installed, I think you'll be almost there to a working configuration .... or time to do what I described in my initial reply. ;)  Good luck!

---

### Post by petercool on 2013-04-19
> **TheFu said:**
> You can use the 32-bit Debian drivers, there is just a dependency with the ia32-libs package. If you install that (not certain what the actual name is), then 32-bit programs should work fine.

Nothing works, until it does.  When we are doing something new, it is hard to tell if we are 1 or 20 steps from a working solution. After you get the ia32-libs package installed, I think you'll be almost there to a working configuration .... or time to do what I described in my initial reply. ;)  Good luck!
I had tried to use 32-bit deb drivers,even a french guy's old ia32-libs package...not succeed!
But today I tried the way according to Sivella's post #7 :[http://ubuntuforums.org/showthread.php?t=1983091&highlight=canon+lbp]("http://ubuntuforums.org/showthread.php?t=1983091&highlight=canon+lbp").
I succeed to print now..hope it can last untill the printer declared dead one day.Amen!...:P
Thanks for your answers!

---

