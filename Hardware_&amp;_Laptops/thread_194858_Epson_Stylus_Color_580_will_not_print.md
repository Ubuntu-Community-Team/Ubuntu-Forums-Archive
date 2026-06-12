---
title: "Epson Stylus Color 580 will not print"
date: 2006-06-12
forum: Hardware &amp; Laptops
---

### Post by pbakke on 2006-06-12
My Epson Stylus Color 580 printer worked fine with Ubuntu 5.10.  Yesterday, I loaded Ubuntu 6.06.  I added the printer with the printer wizard, just as before, configuring it as a local printer (it is attached to a USB port).  The system detects the printer OK, and assigns a diiver: High Quality Image (Gutenprint).

But, the printer will not operate.  When I send a print job, it does not respond.  When I open the printer properties window, the jobs are there in que, but the printer status reads "Printing: printer fault!"  And yes, I have thoroughly checked the cable, and note that the printer goes through its ink purge cycle when I disconnect it or turn off the computer.

What is different about Ubuntu 6.06 that I do not know?  How can I solve this very frustrating problem?

---

### Post by CyberRaven on 2006-06-13
I've got the exact same problem with my Lexmark Optra E310 BW laser. Worked as a charm under 5.10, and seems to install correctly under 6.06, but when trying to write something to it, it stalls... Neither test page, regular printing or konsole -> lpr works.

The printer is detected correctly; ```
~$ lsusb | grep Lexmark
Bus 002 Device 005: ID 043d:000c Lexmark International, Inc. Optra E312 Printer
```
(yeah, I know, it's detected as an E312, but it says E310 on the housing:-) ). I also use the same drivers as I did under Breezy (E312 Postscript). Tried the E310 as well, of course.

So, I'm afraid this is no solution to the problem, but sometimes it helps to know that others struggle with the same things ;-)

**Edit:** typo...

---

### Post by viper52b on 2006-06-13
I seem to be having exact same problem... with konica minolta 2300w. It is detected just fine and installation gives no problems (using the correct opensource drivers).  But when I print something, nothing happens...

If I check the status of the printer on the cups page (localhost:631) it does say "printer off-line" :sad: .

Anybody with an answer to this problem ?

Lots of thanks in advance!

---

### Post by mooreted on 2006-06-19
Same problem here: Epson Stylus C88.

---

### Post by twotonz on 2006-06-20
#viper52b,
Hello, I just wanted to ask if you could tell me if you have any progress with your Minolta2300W? I have the unfortunate task of getting the same printer working for a friend. 
 I have put myself in a bit of a spot, as I have just spent months trying to talk him into converting over to linux, and as we have simular computers was quite confident that I would have little problem in setting up his box. I have now 2 problems, printing with the minolta 2300w, and fax services over isdn & an usb modem. 
 With the printer, I have exactly the same as you, everything hunky-dory, with the device being recognised, drivers are in, .... "printer off-line". I have read on another forum (general linux) that the Minolta 2300W is a gdm printer that will not work under linux. As a very tempory solution, I have installed the printer on a vm winxp, and that works, after a bit of "cheating", but a poor solution, of course my friend is asking, why all the bother of installing linux, when he has to run winxp inside to get his hardware to work. 
 I would be very gratefull, if you could perhaps tell me, anything that could be of help in order to try to fix this, or have you given up trying?

Love & Peace
anthony

---

### Post by RawMustard on 2006-06-21
Add me in as well, Minolta 2300DL color laser.  Tried through cups, smb and direct.  All detected, ready status and all, nothing, not a peep from the printer :(

Same with a HP DesignJet 100. Detected, correct driver available and all, but nadda again, not a single razoooo :(

I guess it's back to windows, its printing sucks, but at least I can get my jobs out!

---

### Post by pbakke on 2006-06-21
How disappointing - lots of people with the same issue, but no suggestions on how to fix it!  If I don't hear from anyone about fixes soon, I'm going back to version 5.10, which had no trouble printing.
I somehow thought that I with Ubuntu Linux I would be able to do all the "basic" things (printing is a basic thing in my opinion) and then learn about Linux and Unix at my liesure.  Hah!

---

### Post by twotonz on 2006-06-22
Hi all,
If anybody reads this & has a Minolta 2300w Working in dapper, please let me know, I desperatly need a bit of a boost here. 

Love & Peace
anthony

---

### Post by CyberRaven on 2006-06-22
Funny thing; I tried my Lexmark laser (se #2 above) on a simple D-Link ethernet print server last weekend, and it worked marvellous! So, I know the driver works, at least.

Still no luck getting it to work throught USB, though... Rumors has it that Dapper features a tweaked version of CUPS, and that the tweaking might be a little buggy. However, I am far from capable of determining this on my own.

Any CUPS-gurus out there with some knowledge about this?

TIA for all hints and suggestions!
CyberRaven :-)

**edit:** typo

---

### Post by coolclassic on 2006-06-23
This may having something to the usb issues some people are having with auotmount. Have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=184786](http://ubuntuforums.org/showthread.php?t=184786)

---

### Post by twotonz on 2006-06-25
Hi all,
#CybeRaven, I think you have hit the nail on the head. After spending a few days with the subject of CUPS (phwee), I have also boiled the whole thing to a problem with the cups that comes with ubuntu. The enwickler (so I understand things) have decided that the cups 1.2 was too insecure, & therefore disabled the web-admin for all users. I have a feeling this is affecting the print que, here is an excerp from the cups-error...........
E [25/Jun/2006:14:40:22 +0200] Creating missing directory ```
"/var/run/cups/certs"
E [25/Jun/2006:14:50:09 +0200] Creating missing directory "/var/run/cups/certs"
E [25/Jun/2006:15:07:09 +0200] Creating missing directory "/var/run/cups/certs"
E [25/Jun/2006:15:20:52 +0200] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [25/Jun/2006:15:21:21 +0200] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [25/Jun/2006:15:21:32 +0200] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [25/Jun/2006:15:23:23 +0200] CUPS-Add-Modify-Printer: Unauthorized
E [25/Jun/2006:15:23:26 +0200] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [25/Jun/2006:15:23:26 +0200] CUPS-Add-Modify-Printer: Unauthorized
E [25/Jun/2006:15:23:41 +0200] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [25/Jun/2006:15:23:42 +0200] CUPS-Add-Modify-Printer: Unauthorized
E [25/Jun/2006:15:26:27 +0200] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [25/Jun/2006:15:26:27 +0200] CUPS-Add-Modify-Printer: Unauthorized
E [25/Jun/2006:15:26:34 +0200] cupsdAuthorize: Empty Basic password!
E [25/Jun/2006:15:26:34 +0200] CUPS-Add-Modify-Printer: Unauthorized
E [25/Jun/2006:15:27:28 +0200] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [25/Jun/2006:15:27:28 +0200] CUPS-Add-Modify-Printer: Unauthorized
E [25/Jun/2006:15:28:04 +0200] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [25/Jun/2006:15:28:05 +0200] CUPS-Add-Modify-Printer: Unauthorized
E [25/Jun/2006:15:28:29 +0200] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [25/Jun/2006:15:28:29 +0200] CUPS-Add-Modify-Printer: Unauthorized
E [25/Jun/2006:15:29:56 +0200] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
```

it goes on much longer than this, I am now thinking of deinstalling cups 1.2, and going to try and downgrade (using source, and see if that improves matters)

Love & Peace
anthony

EDIT++++UPDATE
Ok, got rid of everything to do with cups, went to the cups h-p & downloaded the version 1.2.1, ok I know it's an upgrade not a downgrade, anyway, installed the newie from source. I now do not have any more problems with the Authorize thingy, & I can now log in on the admin-page, butit now stops on 
> ERROR Quota limit reached.

Oh well. back to the drawing board!

---

### Post by coolclassic on 2006-06-26
Have you tried the diffrent drivers:

CUPS+Gutenprint
Foomatic+Gitenprint
Foomatic + Gimp-print

Gimp print didn't work for me

---

### Post by pbakke on 2006-06-26
Say, that sounds like a good idea, but I have no clue how to do it.  How do I install 
CUPS+Gutenprint
Foomatic+Gitenprint
Foomatic + Gimp-print
??

---

### Post by twotonz on 2006-06-27
Hi all,
#pbakke, the Gutenprint drivers you have allready, foomatic proberly also, you can install using Synaptic. However, I doubt this is going to bring you much success. The best driver known to man is not going to help if the cups-server is broken, or at least a bit wobbely. I have read many many docs & forum threads on this subject, and it is looking like there is a problem with the cups 1.2.0 (if you read on the cups homepage, then you shall see the long list of bugs). As mentioned before, an upgrade to cups 1.2.1 has brought a few improvements, but I still cannot print. 
 I still think that for the people experiancing problems, the best solution is to downgrade to the working 1.1(although this can cause more complications, and should be planned carefully beforehand). However I am no expert, and unfortuantly, the machine I was tring to get the printing working, is now running windows again, my friend just could not wait any longer to use his printer :-/ .
 Anyway, Ubuntu is still sitting on another partition, so I shall have another go at the weekend.
 By the way, nice to speak to the original poster, I was getting a bit worried that you had thought I had hijacked your thread......;-)

Love & Peace
anthony

---

### Post by coolclassic on 2006-06-27
Your drivers should be installed if not use synaptic to install.

In kubuntu I go to system settings>printer

---

### Post by CyberRaven on 2006-06-27
An update from Norway...

@twotonz:
Thanks for trying out the newest cups, allthough it didn't solve the problem! Your competence on cups (and linux, most likely :-) ) goes far beyond mine, so I'm afraid that I can't contribute much to the outputs you posted... Your efforts are therefore ever more appreciated! (Sad to hear about your friend's computer, btw :-D Shame that a little bug like this should keep you from converting a Wintendo'er...)

@coolclassic:
Read the tread about the USB automounting issues, but didn't recognize the problems... Have used several USB memory sticks, and they've all worked properly. But thanks for the hint! Regarding the drivers, I have established that the driver I use (Foomatic/Postscript) works, through testing the printer via a couple of print servers. This, however, might be different for other printers...

...and to anyone interested;
I found a pretty crude and expensive solution:By a broadband router/switch with an integrated print server (I ended up with the ZyXEL P-355WT), and set up the printer through that! Lifts you of approx. 1000 Norwegian kroner (£100, $150 or €130 or something), but makes the printer work, and you get a flashy new router :-D

Seriously, though, that is mere a temporary solution... So I greatly appreciate all effort put into this matter!

Best regards,
CyberRaven

---

### Post by DoubleMalt on 2006-07-25
The problem is probably related to this [CUPS Bug]("http://www.cups.org/str.php?L1738+P0+S-2+C0+I0+E0+Qusb") ... 
Let's hope there is an updated Cups package soon *please*

[edit] 
PS: The workaround proposed in the CUPS Bug Thread does not work with my System. There is no /dev/usb/lp0 file and even file:/dev/usblp0 does not work ...
[/edit]

---

### Post by coolclassic on 2006-07-25
There is a printer driver from turboprint that supports your printer. This driver can bypass cups if there is a problem or work with cups.
 
 [http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)
 
 This driver provides ink quantity, cleaning, alignment and nozzle checks.

---

### Post by Sef on 2006-07-26
[LinuxPrinting]("http://linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Color_580") says it works fine.  Click the link to see what drivers it can take.  Most of them should be in the repositories, so check to see what you got installed, and what you need to download.

---

### Post by Dukester on 2006-08-03
Hi

For what its worth your log file entries seem to point in the right direction.

I had exactly the same problems trying to get printing going with kubuntu.

What I did to resolve it was simply comment out the following from the /etc/cups/cupsd.conf file.

# Restrict access to configuration files...
<Location /admin/conf>
#  AuthType Basic
#  Require user @SYSTEM
  Order allow,deny
  Allow localhost
</Location>

And again here

  # All administration operations require an adminstrator to authenticate...
  <Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Add-Printer CUPS-Delete-Printer CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs CUPS-Reject-Jobs CUPS-Set-Default>
#    AuthType Basic
#    Require user @SYSTEM
    Order deny,allow
  </Limit>

While I am sure this is not "the" way to get a result here it works.  Time was short and the need to have printing working was high ;-)

I will be most interested if anybody can point out how this "should" be done.

D

---

### Post by pzazz on 2006-08-31
After doing this ...

   67  gpasswd -a cupsys shadow
   68  /etc/init.d/cupsys restart

... I can add printers in cups 1.2. 

I am asked for username and password. Normal user, not root (which I have enabled) suffices.

---

