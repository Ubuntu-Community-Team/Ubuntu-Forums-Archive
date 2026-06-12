---
title: "Canon LBP6020B installation problem"
date: 2013-04-05
forum: Hardware
---

### Post by oylum on 2013-04-05
Hi,

I unfortunately was misinformed and bought a Canon LBP6020B printer. I can not install it. My computer sees it but it does not print anything  I send. I use ubuntu 12.04. Please help...

Thanks.

---

### Post by pdc on 2013-04-05
**[COLOR="#EE82EE"]there is a Canon linux driver for the LBP6000B[/COLOR]**;

[http://www.canon.de/Support/Consumer_Products/products/printers/Laser/i-SENSYS_LBP6000B.aspx?type=download&page=1](http://www.canon.de/Support/Consumer_Products/products/printers/Laser/i-SENSYS_LBP6000B.aspx?type=download&page=1)

*but not one for your 6020B;*

however.................I have an **LBP3100** working well: it uses the same [COLOR="#0000FF"]CAPT driver[/COLOR] that the 6000B does; ............[I]so I would assume the 6020B is the same and would use the [COLOR="#0000FF"]CAPT driver[/COLOR]; if it had the correct ppd to look for;
[/I]
I enclose a screenshot of the file CNCUPSLBP6200CAPTK.ppd.......it came with the CAPT driver from Canon when I installed it; ......CN means Canon ....CUPS is ..CUPS............LBP6200 refers to the printer and CAPTK is a CAPT driver in english (K) and a CAPTJ means for Japan!!

and you can see from the screenshot that all it is .........is the 6200 mentioned..............I imagine one could just edit any of the existing ppd files from Canon; change the text so it says LBP6020B; save it as that and ........crucially..............tell your system you want to use the LBP6020B.ppd 

.........or you could ask whoever you bought it from if they can do a swap, and give you a 6000B instead...................

let me know if you want to go ahead with editing the ppd...........I think it should be easy............

you need to tell me two things if you do:

1) are you using 32bit ubuntu

2) have you got gedit on your system: it is a text editor...........check with your Search function

---

### Post by s4ub on 2013-06-15
> **pdc said:**
> **[COLOR="#EE82EE"]there is a Canon linux driver for the LBP6000B[/COLOR]**;  [http://www.canon.de/Support/Consumer_Products/products/printers/Laser/i-SENSYS_LBP6000B.aspx?type=download&page=1](http://www.canon.de/Support/Consumer_Products/products/printers/Laser/i-SENSYS_LBP6000B.aspx?type=download&page=1)  *but not one for your 6020B;*  however.................I have an **LBP3100** working well: it uses the same [COLOR="#0000FF"]CAPT driver[/COLOR] that the 6000B does; ............*so I would assume the 6020B is the same and would use the [COLOR="#0000FF"]CAPT driver[/COLOR]; if it had the correct ppd to look for; * I enclose a screenshot of the file CNCUPSLBP6200CAPTK.ppd.......it came with the CAPT driver from Canon when I installed it; ......CN means Canon ....CUPS is ..CUPS............LBP6200 refers to the printer and CAPTK is a CAPT driver in english (K) and a CAPTJ means for Japan!!  and you can see from the screenshot that all it is .........is the 6200 mentioned..............I imagine one could just edit any of the existing ppd files from Canon; change the text so it says LBP6020B; save it as that and ........crucially..............tell your system you want to use the LBP6020B.ppd   .........or you could ask whoever you bought it from if they can do a swap, and give you a 6000B instead...................  let me know if you want to go ahead with editing the ppd...........I think it should be easy............  you need to tell me two things if you do:  1) are you using 32bit ubuntu  2) have you got gedit on your system: it is a text editor...........check with your Search function  I see this discussion hasn't been continued. I have exactly the same problem, the same printer, the same ubuntu distribution, but 64-bit. I downloaded the CAPT driver, installed the two files it contained for 64 bit version, but when I reached to that ppd registration, I stuck because the list of ppds doesn't have one for my printer. Now I read what you're suggesting in the above post but I don't know where that ppd file is, so I could edit it. And how I must use that file later. Could you pls explain that to me a little bit in detail, as I'm not experienced in such things? Thanks.

---

### Post by s4ub on 2013-06-15
I found the ppd file in usr/share/ppd, edited and renamed it, but when I try register it as explained in the CAPT driver manual ( /usr/sbin/lpadmin -p [printer name] -m [PPD file name] -v ccp://localhost:59687 –E), it says:   lpadmin: Unknown argument "–E".  What to do?

---

### Post by pdc on 2013-06-15
sorry to hear you are having problems;

I have the 2.4 CAPT driver installed: have you installed the 2.6 version? The reason I ask is I wonder if the 2.6 has had a ppd for the 6020 and the 6020B added to the list?

If you can copy and paste back the direct error message you get........that might be helpful.........I copied and pasted what you gave into a text editor and compared it to the official syntax........it seems the same to me ......

Have you seen this guide?

[http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp](http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp)

If you copy and paste it into something google translate, it is a very good guide........the only issue is that when google translates, it adds spaces in various of the linux syntax areas, so one has to edit those before running them.....I hope I make myself clear..

with 64bit, one does seem to need extra files installed.....Sivella, who maintains the french site, ,..gives a good guide to this

If I copy and paste what I think is the syntax for registration;

> sudo /usr/sbin/lpadmin -p [printer name] -m [ppd] -v [uri device] -E

and then for an LBP5000 it would be

> sudo /usr/sbin/lpadmin -p LBP5000 -m CNCUPSLBP5000CAPTK.ppd -v ccp://localhost:59787 -E

and then you give 

> sudo /usr/sbin/lpadmin -p [printer name] -m [PPD file name] -v ccp://localhost:59687 –E

and then the AH-HA!! moment............you are using > ccp://localhost:**[COLOR="#FF0000"]59687[/COLOR]**

whereas Ubuntu

[https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190)

advises to use [COLOR="#0000FF"]59787[/COLOR]

so the Ubuntu advice would be

> ccp://localhost:[COLOR="#FF0000"]**59787**[/COLOR]

I wonder if that clears things at that stage......but I think you should install what Sivella would call the 64bit pre-requisites before you move on to register the printer with the ccpd daemon

__________________________________

it all looks complicated but I was pleasantly surprised when I set up our LBP printer on an older (32bit install) of Ubuntu......it went very smoothly and was just a couple of lines of command in the terminal

---

### Post by s4ub on 2013-06-16
> **pdc said:**
> sorry to hear you are having problems;  I have the 2.4 CAPT driver installed: have you installed the 2.6 version? The reason I ask is I wonder if the 2.6 has had a ppd for the 6020 and the 6020B added to the list?  If you can copy and paste back the direct error message you get........that might be helpful.........I copied and pasted what you gave into a text editor and compared it to the official syntax........it seems the same to me ......  Have you seen this guide?  [http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp](http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp)  If you copy and paste it into something google translate, it is a very good guide........the only issue is that when google translates, it adds spaces in various of the linux syntax areas, so one has to edit those before running them.....I hope I make myself clear..  with 64bit, one does seem to need extra files installed.....Sivella, who maintains the french site, ,..gives a good guide to this  If I copy and paste what I think is the syntax for registration;    and then for an LBP5000 it would be    and then you give     and then the AH-HA!! moment............you are using   whereas Ubuntu  [https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190)  advises to use [COLOR="#0000FF"]59787[/COLOR]  so the Ubuntu advice would be    I wonder if that clears things at that stage......but I think you should install what Sivella would call the 64bit pre-requisites before you move on to register the printer with the ccpd daemon  __________________________________  it all looks complicated but I was pleasantly surprised when I set up our LBP printer on an older (32bit install) of Ubuntu......it went very smoothly and was just a couple of lines of command in the terminal  Thank you very much, pdc. I'll now install those packages for 64-bit and then pass to the following steps suggested by that French tutorial. Then I'll return to this conversation to tell if everything is OK or there are still problems.

---

### Post by s4ub on 2013-06-16
Fail :(  I installed the dependencies, then the ia32-libs, I blocked the latter. All of this was done exactly  according to the commands provided by that French page. Everything was OK.  

Then I restarted cups and passed to the registration of the ppd, using 59787 as told by you. That is, I typed in the terminal:*    sudo /usr/sbin/lpadmin -p LBP6020B -m CNCUPSLBP6020BCAPTK.ppd -v ccp://localhost:59787 -E*    

It returned:  *lpadmin: Unable to copy PPD file.* 

   That ppd file was created by me, editing the ppd file for LBP6200, because there isn't a ppd file for my printer in the list of ppds provided by CAPT driver (I had installed the version 2.56, I cannot find the 2.6 version).

 What must I do now? Or what have I done incorrectly?   
By the way, in the list of all those ppds that the CAPT has, there is no ppd ending in B. Here is a portion of the list of the ppds that I have:

   > .......
Canon LBP6300n (CNCUPSLBP6300nCAPTK.ppd)     LBP6300n      
Canon LBP6200 (CNCUPSLBP6200CAPTK.ppd)     LBP6200      
Canon LBP6000/6018 (CNCUPSLBP6018CAPTK.ppd)     LBP6018/LBP6000      
Canon LBP5300 (CNCUPSLBP5300CAPTK.ppd)     LBP5300       
Canon LBP5100 (CNCUPSLBP5100CAPTK.ppd)     LBP5100 
etc etc

    In the whole list, there is no ppd with the ending B.

---

### Post by pdc on 2013-06-17
I confess that I do not know everything about everything

when I look for the ppd file for my Canon 3100B; (which is the CNCUPSLBP3150CAPTK.ppd)

the search function tells me it is in > [COLOR="#0000FF"]/usr/share/cups/model[/COLOR]

so I was wondering where you saved the 6020ppd file that you created; 

to open [COLOR="#008000"]CNCUPSLBP3150CAPTK.ppd[/COLOR] and edit it, I would type

> gksudo gedit /usr/share/cups/model/CNCUPSLBP3150CAPTK.ppd 

it was an assumption I made that if one edited the file; and changed the defined printer; and saved the file as /usr/share/cups/model/CNCUPSLBP6020CAPTK.ppd

(I don't think you need to add the B in the ppd title; and again, I can't see how that would matter if you were to do it ...............)

___________________________________________________________________________________________________________________

so if I were editing CNCUPSLBP6018CAPTK.ppd

I would use the command > gksudo gedit /usr/share/cups/model/CNCUPSLBP6018CAPTK.ppd and ensure the altered ppd was saved in /usr/share/cups/model

_______________________________________--

sorry if I am spelling out the obvious to you..

________________________________________


so I am thinking we need to make sure the correct ppd has been created; and then that lpradmin knows where to look to find it

______________________________________________________________________________________________________--

in your post, I see there is a ppd CNCUPSLBP6018CAPTK.ppd ............ I wonder if that isn't good enough for the system to point to ...............

with the CAPT driver, there seem to be 2 steps: register with the print spooler (as you are working on); and then register the ccpd daemon

(other Canon drivers; such as the ubiquituous UFR driver; just require register with print spooler)

---

### Post by s4ub on 2013-06-17
> **pdc said:**
> I confess that I do not know everything about everything

when I look for the ppd file for my Canon 3100B; (which is the CNCUPSLBP3150CAPTK.ppd)

the search function tells me it is in 

so I was wondering where you saved the 6020ppd file that you created; 

to open [COLOR=#008000]CNCUPSLBP3150CAPTK.ppd[/COLOR] and edit it, I would type



it was an assumption I made that if one edited the file; and changed the defined printer; and saved the file as /usr/share/cups/model/CNCUPSLBP6020CAPTK.ppd

(I don't think you need to add the B in the ppd title; and again, I can't see how that would matter if you were to do it ...............)

___________________________________________________________________________________________________________________

so if I were editing CNCUPSLBP6018CAPTK.ppd

I would use the command  and ensure the altered ppd was saved in /usr/share/cups/model

_______________________________________--

sorry if I am spelling out the obvious to you..

________________________________________


so I am thinking we need to make sure the correct ppd has been created; and then that lpradmin knows where to look to find it

______________________________________________________________________________________________________--

in your post, I see there is a ppd CNCUPSLBP6018CAPTK.ppd ............ I wonder if that isn't good enough for the system to point to ...............

with the CAPT driver, there seem to be 2 steps: register with the print spooler (as you are working on); and then register the ccpd daemon

(other Canon drivers; such as the ubiquituous UFR driver; just require register with print spooler)

Thanks, pdc. This time I was able to register the ppd, the printer with my ppd was added, all was successful in that part, but the test page wasn't printed. An error message says: ccp send_data error, exit.

Then I deleted that printer, added a new one, this time registering my printer with the ppd of LBP6018. Again the registration of the ppd, printer etc was OK, the printer was added. But again, it doesn't print, showing the same data error. I tried several times, restarting the computer or the printer, no result. :(

---

### Post by pdc on 2013-06-17
sorry this is not working for you; Canon seem to provide CAPT drivers for the Mac and windows for this device; so one could assume the CAPT might somehow work for linux; at present, I can't make any helpful suggestions; sorry

---

### Post by s4ub on 2013-06-17
> **pdc said:**
> sorry this is not working for you; Canon seem to provide CAPT drivers for the Mac and windows for this device; so one could assume the CAPT might somehow work for linux; at present, I can't make any helpful suggestions; sorry

No need to say sorry :) Thank you for your efforts to help. I just want to add that I deleted B from the name of my printer everywhere, registered the ppd  and printer without that B (just LBP6020), now the printer test page  doesn't bring that data error, but doesn't print either, hanging on *"Idle-Sending data to printer"*.  I changed the ppd again to that of LBP6018, with just LBP 6020 printer  name (without B). Same story. The printer is dumb. No error message, but  no printing either. 

Oh well, I'm giving up on this printer. Thank you again.

---

### Post by Tuomas_Jaakola on 2013-09-01
Canon released Linux CAPT drivers 2.60 that include support for LBP6020:
[http://support-sg.canon-asia.com/contents/SG/EN/0100459601.html](http://support-sg.canon-asia.com/contents/SG/EN/0100459601.html)

I installed the drivers on Ubuntu 13.04 and now printing works with my LBP6020B! \\:D/

---

### Post by pdc on 2013-09-02
well done; glad it is all working;

did you have to do the additional steps Sivella mentioned here;

[http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp](http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp)

of 

installing the printer in CUPS 

and 

registering the printer with the ccpd daemon

??

---

### Post by Tuomas_Jaakola on 2013-09-02
I followed the installing instructions included in the driver package; I didn't have to to anything else to get it working.
So no, I didn't have to do the additional steps.

---

### Post by pdc on 2013-09-02
that's very interesting (and encouraging!!)

thanks very much

---

