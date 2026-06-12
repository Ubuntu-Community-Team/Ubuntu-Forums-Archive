---
title: "Dot matrix printer in Ubuntu"
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by pravindra.kumar on 2009-09-04
Hi,
I have a Dot Matrix Printer which model is WeP LQ DSI 5235, i am facing problem to install this printer in Ubuntu9.04. I am unable to find supportable driver for the printer.
I used some drivers from list and choosed some Epson's models one by one but print quality is not good, we are unable to read text properly.
please help me, it's very urgent.
Thanks !!!!!!!

---

### Post by pravindra.kumar on 2009-09-04
please help guys.........

---

### Post by pravindra.kumar on 2009-09-05
No reply from anyone?

---

### Post by Whiffle on 2009-09-05
Here's a PPD for it:
[http://www.wepworld.com/wepportal/Uploads/Drivers/wep24pin136column20091152255.zip](http://www.wepworld.com/wepportal/Uploads/Drivers/wep24pin136column20091152255.zip)

From here:
[http://wepindia.com/Downloads/DownloadDrivers.aspx](http://wepindia.com/Downloads/DownloadDrivers.aspx)


If you need help installing the ppd for it, just ask.

---

### Post by pravindra.kumar on 2009-09-05
Thanks for reply dear,
i have used this ppd but while applying it's showing a message that "Printer 'WeP-24-Pin' requires the 'rastertowep' program but it is not currently installed.  Please install it before using this printer".

---

### Post by Whiffle on 2009-09-05
Oh I see.  Very few references to that.  I think I would try using different filters available in /usr/lib/cups/filter in place of rastertowep in the ppd file, one of them may work.   Beyond that, you may just have to call WeP and ask them.

---

### Post by pravindra.kumar on 2009-09-05
Dear,
I tried one by one filter from /usr/lib/cups/filter in place of rastertowep in ppd file, but it's printing some junk characters.
now i am trying to contact to wep support team.

If you have any other solution then please reply me, i am waiting for your reply.

Thanks

---

### Post by pravindra.kumar on 2009-09-08
Dear,
We talked to WeP support team but they have no solution, so now i do not understand that what should i do.
where from we can get "rastertowep" filter for Ubuntu9.04? so we can work with DMP printer.

Thanks

---

### Post by sanksaini on 2009-11-01
I faced similar issues with Wipro LQ 540. I have got "rastertowep" from wepindia.attaching file. with this post
 You paste it in user\lib\cups\filter. hope this solves your problem. 

I understand from personal experience what headache this can be.

---

### Post by sanksaini on 2009-11-01
the zip file also contains a ppd driver, I am not sure if your printer needs the same.

---

### Post by oldtraveller on 2010-01-27
I have the same problem in Ubuntu 9.10. guys any update.

---

### Post by twinklstar on 2010-01-28
> **sanksaini said:**
> the zip file also contains a ppd driver, I am not sure if your printer needs the same.
hello 
when extracting the zip file - ":  mismatching "local" filename (rastertowep),
         continuing with "central" filename version
mapname:  conversion of  failed" - this message comes. what to do. pls help

---

### Post by twinklstar on 2010-01-29
> **twinklstar said:**
> hello 
when extracting the zip file - ":  mismatching "local" filename (rastertowep),
         continuing with "central" filename version
mapname:  conversion of  failed" - this message comes. what to do. pls help
nobody to help...........................
pls......................

---

### Post by oldfred on 2010-01-29
In the old days we used to send our own control codes to dot matrix printers, if that that is something you are willing to try then something like this may work.

He could not get text print to work so he saved a file and used a script with lpr to print.
[http://ubuntuforums.org/showthread.php?p=8706234](http://ubuntuforums.org/showthread.php?p=8706234)

---

### Post by twinklstar on 2010-01-30
> **oldfred said:**
> In the old days we used to send our own control codes to dot matrix printers, if that that is something you are willing to try then something like this may work.

He could not get text print to work so he saved a file and used a script with lpr to print.
[http://ubuntuforums.org/showthread.php?p=8706234](http://ubuntuforums.org/showthread.php?p=8706234)
am a bigginer, any simpler methods please..

---

### Post by twinklstar on 2010-02-03
> **twinklstar said:**
> am a bigginer, any simpler methods please..
...........still waiting, pls help my masters..

---

### Post by chinna saaeb on 2010-03-15
I have successfully installed and my printer is running well.

I installed the wipro ppd file using the system/administration/printing.

Then I copied the rastertowep file as suggested on the forum earlier (to /usr/lib/cups/filter ). This file I had downloaded on the first page of the thread.
Then I changed the mode to 777 to make it accessible to all.
Now it is working well

---

### Post by smismdu on 2010-12-14
I am in a need of rastertowep filter. While browsing the forum,  I could not find where to get the filter file. Pl. guide for downloading the file.

---

### Post by pravindra.kumar on 2010-12-23
Dear smismdu,
pls check reply of **smismdu** at the first page in this thread and find attached .zip file. it has .ppd and rastertowep included.

Have a great day!!

---

### Post by pravindra.kumar on 2010-12-23
Sorry Dear, name was wrongly entered. It's **sanksaini**
Dear smismdu,
pls check reply of **sanksaini** at the first page in this thread and find attached .zip file. it has .ppd and rastertowep included.

---

### Post by chandraubunt on 2012-07-19
I have aDot Matrix Printer(WeP LQ DSI 5235) in office. when updated to Ubuntu 12.04   ,It is not working,  , please give me the details of installation

---

