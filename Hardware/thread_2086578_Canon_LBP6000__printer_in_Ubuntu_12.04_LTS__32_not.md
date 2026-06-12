---
title: "Canon LBP6000  printer in Ubuntu 12.04 LTS  32 not working"
date: 2012-11-21
forum: Hardware
---

### Post by sysone on 2012-11-21
On Canon website downloaded their latest driver for Linux:
CAPT Printer Driver for Linux Version 2.50 --10/25/12 --43.28 MB
'Linux_CAPT_PrinterDriver_V250_us_EN.tar.gz' extracted -->

'Linux_CAPT_PrinterDriver_V250_us_EN'  ---> '32-bit_Driver' folder -->'Debian' folder + 'RPM' folder; 

Debian --> 'cndrvcups-capt_2.50-1_i386.deb'  + '32-bit_Driver'.

And I opened both above with Ubuntu software Center. Synaptic lists both as installed.

But the printer does not respond at all when I try to print a file (says that it was sent to printer).
And  a search for drivers says that no proprietary drivers are in use on this system.
Too late I see that Linux users have had problems with Canon printers.

 I read that Radu Cotescu has a script for installing Canon LBP printers in Linux but that is for 64 bit machines and besides, LBP6000 is not listed : 
[http://radu.cotescu.com/how-to-install-canon-lbp-printers-in-ubuntu/](http://radu.cotescu.com/how-to-install-canon-lbp-printers-in-ubuntu/) 

For earlier drivers Canon gives intructions for installing the printer :
```
 Ubuntu 12.04 Install

For a new install please see the html guide in the 2.4 driver download:

    Download 32/64 Bit Linux CAPT Printer Driver v2.40 English. 

Find the debian packages in the v2.40 drivers deb folder:

    cndrvcups-capt.deb

    cndrvcups-common.deb 

Install from the v2.40 driver as you would any other package with Ubuntu Software Center. Then follow the canon guide v2.40 carefuully making sure that you change this line accordingly:

sudo /usr/sbin/lpadmin -p LBP5000 -m CNCUPSLBP5000CAPTK.ppd -v ccp://localhost:59787 -E

The manual says ccp://localhost:59687 but Ubuntu by default is using 59787. This will give you a headache if you do not change it. (The file /etc/ccpd.conf defines UI_Port 59787 and PDATA_Port 59687. So, both these ports need to be open in the firewall setting.)

* Note: Ubuntu 12.04 has again blacklisted the usblp module which creates the /dev/usb/lp0 device link. To solve this problem do this

sudo nano /etc/modprobe.d/blacklist-cups-usblp.conf

Then comment the file to look like this, canons driver does not talk to the printer through cups:

# cups talks to the raw USB devices, so we need to blacklist usblp to avoid
# grabbing them
# blacklist usblp

* Note: The later sections of this article under 'Adding a printer' and 'Troubleshooting' suggest using 'ccp:/var/ccpd/fifo0'. That works, but you have to ensure /var/ccp/fifo0 exists with correct ownership/mode. Using 'ccp://localhost:59787' is simpler as it requires no extra steps involving fifo file.  
```


But I am not sure that I can follow the instructions without help.
Any help appreciated.

---

### Post by pdc on 2012-11-21
have a read at post #2 

[http://ubuntuforums.org/showthread.php?t=2061614](http://ubuntuforums.org/showthread.php?t=2061614)

.....see if it gets you printing.............

............seems like you have installed the printer drivers?

If you copy and paste the command below into a terminal, and copy and paste the results back here

> [COLOR="Red"]sudo dpkg -l | grep Canon[/COLOR]

.. *I trust you installed the common driver and then the capt drive*r ..

---

### Post by offgridguy on 2012-11-21
Printers; I can share your frustration.](*,)](*,)

Good luck anyway, in my case it happens to be a brother printer.

---

### Post by sysone on 2012-11-22
> **pdc said:**
> 

.. *I trust you installed the common driver and then the capt drive*r ..

1:~$ sudo dpkg -l | grep Canon
ii  cndrvcups-capt                         2.50-1                                  Canon CAPT Printer Driver for Linux
ii  cndrvcups-common                       2.50-1                                  Canon Printer Driver Common Modules Ver.2.50


Synaptic also confirms it.
But your link raised my hopes - even if it refers to a different printer.
Thanks for that

---

### Post by pdc on 2012-11-22
> But your link raised my hopes - *even if it refers to a different printer*.

indeed .......in the thread I mentioned .........

the command to register the LBP6000 printer would be

> sudo /usr/sbin/lpadmin -p LBP2900 -m CNCUPSLBP6018CAPTK.ppd  -v ccp://localhost:59787 -E 

......the ubuntu howto

[https://help.ubuntu.com/community/CanonCaptDrv190#Ubuntu_12.04_Install](https://help.ubuntu.com/community/CanonCaptDrv190#Ubuntu_12.04_Install)

say to use CNCUPSLBP6018CAPTK.ppd

---

### Post by sysone on 2012-11-23
> **pdc said:**
> indeed .......in the thread I mentioned .........
the command to register the LBP6000 printer would be

......the ubuntu howto

[https://help.ubuntu.com/community/CanonCaptDrv190#Ubuntu_12.04_Install](https://help.ubuntu.com/community/CanonCaptDrv190#Ubuntu_12.04_Install)

say to use CNCUPSLBP6018CAPTK.ppd

Hi pdc
Actually, the above command is for LBP2900.
the ppd for my machine is reportedly         [U]Canon LBP6000/6018 (CNCUPSLBP6018CAPTS.ppd) 
[/U]


_So the command would be :_

```
        
  /usr/sbin/lpadmin -p LBP6000 -m CNCUPSLBP6018CAPTK.ppd -v [ccp://localhost:59687](ccp://localhost:59687) –E
     
```


But it is not working - just keeps asking if I want to do a test page and is sending it to the printer  which does nothing.


I'll delete the drivers and start all over .
Thanks

---

### Post by sysone on 2012-11-23
when I try :
```
:~$ sudo  /usr/sbin/lpadmin -p LBP6000 -m CNCUPSLBP6018CAPTK.ppd -v ccp://localhost:_59787_ &#8211;E

lpadmin: Unknown argument "&#8211;E".
 
```same for ```
 :~$ sudo  /usr/sbin/lpadmin -p LBP6000 -m CNCUPSLBP6018CAPTK.ppd -v ccp://localhost:_59687_ &#8211;E 

lpadmin: Unknown argument "&#8211;E". 
```Well somebody said somewhere else that LPB6000 does not work in Linux -'Period'  but I'll try some more.

---

### Post by pdc on 2012-11-23
.........I don't know Sooty .........not sure if you remember Harry Corbett?

I see you have an extra space before the /usr/sbin/lpadmin

> sudo  /usr/sbin/lpadmin -p LBP6000 -m CNCUPSLBP6018CAPTK.ppd -v ccp://localhost:59787 &#8211;E

whereas it might be better as

> sudo /usr/sbin/lpadmin -p LBP6000 -m CNCUPSLBP6018CAPTK.ppd -v ccp://localhost:59687 &#8211;E 

from issuing the command in a terminal

> man lapadmin

I get in relation to -E

>  -E
            Enables the destination and accepts jobs; this is the same as running the cupsaccept and cupsenable programs on the destination.


........so -E should be fine ............try again without the extra space before /usr ?

You were right about my proofreading error in my last post:

---

### Post by sysone on 2012-11-24
> **pdc said:**
> 
  ............try again without the extra space before /usr 



I did better :  cut/paste your link (just changed to LBP6018 and it was accepted with no protest!

Like before, I have 2 icons as printers : LBP6000/6018 (active)  and LBP6000 inactive.

The one or the other says  that they send a test page to printer but nothing happens.
I also tried" cupsenable" and "cupsdisable"  and again nothing happens.
Also deleted the inactive printer and again nothing.

Somebody wrote that Precise cups need replacing but developers have not done this.

BTW,           man lpadmin  -->.... ' the -E option forces  encryption when connecting to the server.'  ....
    which of course is of no importance at this stage.

Thanks again for your support

---

### Post by pdc on 2012-11-24
so the printer is still not working......is that correct?

from here

[http://ubuntuforums.org/showthread.php?t=2061614](http://ubuntuforums.org/showthread.php?t=2061614)

after registering the printer;

one registers it with the ccpd daemon

and then starts ccpd

and then tries a test print ........

what does

> captstatusui -P LBP6000

or 

> captstatusui -P LBP6018

give you?

this link

[http://www.imagestore.co.in/canon-lbp-6018-b-colour-printer.html](http://www.imagestore.co.in/canon-lbp-6018-b-colour-printer.html)

says the 6018 is a colour printer but then says it only prints B&W !!

I imagine the 6000 is B&W also

---

### Post by sysone on 2012-11-25
> **pdc said:**
> 

I imagine the 6000 is B&W also

Yes it is B&W and not printing in Ubuntu (prints fine in Windows)

At some point 
**:~$ captstatusui -P LBP6000-LBP6018**
brought up the 'StatusMonitor' with Message: -power saving
another try gave : 'ready to print'  but it did not print
another try :'Communication error:
                           'Check the following:
                            - Is the printer turned on?
                            - Is the cable properly connected? '

After Restart and
 **:~$ captstatusui -P LBP6000-LBP6018**  
'StatusMonitor'  no longer shows (cursor keeps blinking in terminal like forever)

Rigt-click on Printer icon shows either 
Printer State : idle
or  Printer State :  Processing

And just some outputs from what I tried to read  (without really understanding)

**:~$ lsmod | grep usblp**
usblp                  17885  0 

**:~$ ls -l /var/ccpd**
total 0
prw-r--r-- 1 lp lp 0 Nov 25 07:11 fifo0

[B]:~$  sudo /usr/sbin/ccpdadmin -p LBP6000-LBP6018 -o /dev/usb/lp0
 CUPS_ConfigPath = /etc/cups/[/B]
 LOG Path        = None
 UI Port         = 59787
 Entry Num  : Spooler    : Backend    : FIFO path        : Device Path     : Status 
 ----------------------------------------------------------------------------
     [0]    : LBP6000-LBP6018     : usb         : //Canon/LBP6000/LBP6018?serial=<....>    : /dev/usb/lp0     : Modified


Thanks again

---

### Post by pdc on 2012-11-26
I don't know where the problem(s) lie with your printer

I thought to compare the various results you give

for me: 

> [COLOR="Red"]ls -l /var/ccpd[/COLOR]
[COLOR="Blue"]total 0
prw-r--r-- 1 root root 0 Jul  3 10:15 fifo0[/COLOR]


for you:

> ls -l /var/ccpd
[COLOR="SeaGreen"]total 0
prw-r--r-- 1 lp lp 0 Nov 25 07:11 fifo0[/COLOR]

I note root owns my LBP: lbp seems to own yours............

captstatusui -P LBP3100 gives me: ready to print

---

