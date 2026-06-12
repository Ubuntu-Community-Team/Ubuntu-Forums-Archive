---
title: "Brother DCP-7065 DN how do I install it?"
date: 2012-08-09
forum: Hardware
---

### Post by izquierdista on 2012-08-09
Hi everyone, 
I purchased a brother DCP-7065DN multifunction device (Printer, scanner, copier) based on the fact that I needed a robust printer and scanner for my office. I also purchased it because when I searched on the internet I noticed that people had successfully gotten this printer with all its functions working correctly.

I currently have Ubuntu 12.04 LTS installed on my laptop. 

so far I have tried the following

1) plug the printer to the computer using the USB connector
2) gone to the printing setup 
3) the printer is correctly detected
4) The print setup searches for drivers and finds DCP-7045N drivers (recommended)
5) I select those drivers and the printer is setup 
6) I press the print "test page" 
7) the PRINTER ITSELF says "receiving data" but it NEVER PRINTS A PAGE :(

what should I do??

---

### Post by kurt18947 on 2012-08-09
> **izquierdista said:**
> Hi everyone, 
I purchased a brother DCP-7065DN multifunction device (Printer, scanner, copier) based on the fact that I needed a robust printer and scanner for my office. I also purchased it because when I searched on the internet I noticed that people had successfully gotten this printer with all its functions working correctly.

I currently have Ubuntu 12.04 LTS installed on my laptop. 

so far I have tried the following

1) plug the printer to the computer using the USB connector
2) gone to the printing setup 
3) the printer is correctly detected
4) The print setup searches for drivers and finds DCP-7045N drivers (recommended)
5) I select those drivers and the printer is setup 
6) I press the print "test page" 
7) the PRINTER ITSELF says "receiving data" but it NEVER PRINTS A PAGE :(

what should I do??

For printing,  using Brother's installer script seems to work pretty well.  You can take a look at this thread.  I uploaded the installer, see post #4.  The scanner portion takes a bit of tinkering.

[http://ubuntuforums.org/showthread.php?t=1999216&highlight=brother](http://ubuntuforums.org/showthread.php?t=1999216&highlight=brother)

---

### Post by izquierdista on 2012-08-09
YAY, I got it to work thanks for everyones help I GOT BOTH THE SCANNER AND PRINTER TO WORK PERFECTLY

Here are the steps I followed: 

PART A. INSTALL PRINTER

1) Installed the lpr and cups PRINTER drivers for this specific printer using gdebi found here: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#DCP-7065DN](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#DCP-7065DN)

2) After installing those two drivers I followed these instructions in order to properly install the Printer and be able to use it with a USB connection following STEP 5a on this page: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)

keep in mind that when you select the driver you might need to scroll up or down but you will find the driver called DCP-7065DN and choose that one. 

to make sure the printer works go ahead and print a test page and it should come out fine..

PART B. Installing the scanner
1) I installed the drivers Brscan4 32bit  AND scan-key-tool 32 bit using Gdebi you find those drivers here:[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html#brscan4](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html#brscan4)

2) After I installed those two drivers I followed these instructions: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html)

make sure that in order to edit the file indicated you open it from a terminal after you have logged in as a Super user... after you make the appropriate edits you save it,  then you restart your computer

3) to make sure everything works with the scanner open up the xsane or gscan  and it should recognize and be able to use your scanner without any problems..


so there you have it friends....thanks for everyone's help, I am so happy now that I have a great printer/scanner/copier for my office.

---

### Post by pdc on 2012-08-11
well done; a great guide for others to follow 

when you advise folks 

> *make sure that in order to edit the file indicated you open it from a terminal after you have logged in as a Super user*.

I think the correct command for anyone to edit the file is to copy and paste 

> sudo gedit /lib/udev/rules.d/40-libsane.rules

---

### Post by mrag on 2012-08-17
I also have 12.04 and I recently got the Brother MFC-J430w. Wow, do I wish I found this post days ago.  I would still have half my hair. Some notes if I may add:
a)  I thought a short YouTube video at 
[http://www.youtube.com/watch?v=pWyp400rzzg](http://www.youtube.com/watch?v=pWyp400rzzg)
a very helpful addition. I did have to "ignore" warnings on the printer and scanner files, but otherwise it speeded things up for me. YMMV

b)  I never needed to install Xsane or Gscan, just used Ubuntu's 'scan.'

c) on adding those two lines, make sure you put them in the right place as instructed. I put them lower down the first time and surprisingly (!) nothing worked-Duh.

So far I'm fine. The printer still even accepts printing from my iPad. I do have a minor issue in that I still cannot use the scan button on the printer to directly 'scan to file.' 

Thanks!!

---

### Post by aNovitiate on 2012-12-01
... some, hopefully, helpful clarifications:

When I first discovered the Brother DCP7065 Linux drivers page:
[http://http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#DCP-7065DN](http://http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#DCP-7065DN)
I was unsure as to whether to use the CUPS or LPR driver.  I thought that only the CUPS driver was necessary ... and experienced the same as the first post i.e. the printer lit up but didn't print.

When I downloaded and installed the second (LPR) driver ... and re-ADD'd the printer, it printed the Test Page.  Yea !

btw, all I had to do to install each of those drivers was:

[LIST]
[*]double-click on the downloaded** .deb** file
[*]which opened the Ubuntu Software Center
[*]which, after maybe 5 seconds, provided the "*Install*" button (top-right) ...
[/LIST]
During that install, it pops a dialog box, saying "The Package is of bad quality" etc.     However, it offers a *'Ignore and Install*' button, which I clicked ... and the install completed, just fine.   I figured it was 'ok' to 'Ignore and Install', since those .deb's were posted by Brother.

My DCP-7065DN is installed via an **ethernet** connection, rather than just USB.  Nevertheless, the twin CUPS/LPR drivers worked just fine, thank you very much.

I deleted my previous DCP-7065DN printer in "Printers" ... and re-added it.  

Wait ~10 seconds after clicking "Add ..." before clicking "> Network Printer" (left-column) - to give it a chance to '*see*' your DCP-7065DN and its IP address. 

 "Add ... printer" recognized a "Brother" printer and displayed the models list box.  The newly-added (driver) DCP-7065DN choice was at the **top** of the list.  Before adding the LPR driver (i.e. with only the CUPS driver) the DCP-7065DN choice was not labeled "recommended".  After adding the LPR driver, the DCP-7065DN choice was labeled "recommended" ... and the ensuing "Test Page" print worked.  Yabadabadoo !  :P

---

### Post by aNovitiate on 2012-12-02
After adding the Brother scanner .deb's (same method as in previous post), neither Ubuntu Simple Scan nor xSane could '*see*' the 7065DN over the ethernet connection.

I installed the Brother Windows software on a different PC and the Windows XP Brother software '*saw*' the 7065DN just fine (and worked beautifully) over the ethernet connection.

Next, I  connected a **USB** cable between the 7065DN and my Ubuntu PC and, finally, both Ubuntu Simple Scan and xSane could 'see' the 7065DN just fine.  In fact, the scanning was WAY faster than using my old Canon CanoScan flatbed scanner ... for whatever reason.

Looking through that */lib/udev/rules.d/40-libsane.rules* file, I saw no ethernet references e.g. to inform Ubuntu that that a scanner is available over the ethernet connection.

If anyone can shed any light on why the scanner drivers work via USB, but not ever ethernet connections, I'd be pleased to learn that ... and even more pleased to learn if there's some other configuration file or whatever to get the Brother scanner drivers to work via ethernet connections.

---

### Post by pdc on 2012-12-02
I wondered if you had a chance to work your way through the documentation that Brother provide:

eg **[COLOR="Blue"]Scanner driver install for network[/COLOR]**

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1b.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1b.html)

I note they say at the beginning 

> Scanner driver does not support print server connections.

........... you seem to have the printer side working well, so that should proviso should not apply to you ........

I see here 

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html)

that your DCP-7065DN is a brscan4 model

---

### Post by aNovitiate on 2012-12-02
From post #3, above, last night, I installed the scanner drivers from:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html)

As you pointed out, pdc, they DCP-7065DN scanner drivers were from the *bottom* group (**brscan4**).  Naturally, I selected the .deb drivers:
[**brscan4 32bit**]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brscan4-0.4.1-2.i386.deb&lang=English_lpr")
[**scan-key-tool 32bit**]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brscan-skey-0.2.4-0.i386.deb&lang=English_lpr")

Per your above/previous note, from this page:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1b.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1b.html)
tonight, I noted:
*Step 5. Setting for your network scanner*

So, I tried it ... in a Terminal ...
**brsaneconfig4 -a name=DCP-7065DN model=DCP7065DN ip=192.168.1.201**

The *201* is just my internal, DCHP-assigned Brother ethernet IP.

As it advises, I typed the Confirm command:
**brsaneconfig4 -q | grep DCP-7065DN**
It came back looking happy, including my internal IP address.

So, I gave it a shot ... I opened Ubuntu's "Simple Scan" ... and lo and behold, the 'no-scanner found' dialog box ceased to appear !   I clicked the "Simple Scan" Scan button ... and, after a couple seconds pause, it scanned !   Yippee !!!

To double-check, I opened xSane and, again, no more 'no-scanner found' dialog box.  About 7 seconds after clicking the xSane "Acquire Preview" button, it, too, scanned ... and scanned F A S T !

In short, after installing the drivers, by just double-clicking the .deb files and following through, as noted above, all that was missing was that command:
**brsaneconfig4 -a name=DCP-7065DN model=DCP7065DN ip=192.168.1.201**

**pdc**, as my Dad used to say, "You're a prince among men." ... and I THANK you.   Merry Christmas.

---

### Post by pdc on 2012-12-02
that's very kind of you aNovitiate: delighted it is all working for you ... you have the hardware and do the hard work on your computer so your learning is really helpful for all........ I must bookmark what worked for you.

Enjoy!

............oh.......if you can mark the thread SOLVED....the moderators like that.........only you can do it ..........

---

### Post by aNovitiate on 2012-12-02
> **pdc said:**
> that's very kind of you aNovitiate: delighted it is all working for you ... you have the hardware and do the hard work on your computer so your learning is really helpful for all........ I must bookmark what worked for you.

Enjoy!

............oh.......if you can mark the thread SOLVED....the moderators like that.........only you can do it ..........
Unless I misunderstand, the original poster already marked the thread 'Solved'.  I looked up and down and so no way for me to makr the thread 'Solved'.

I was very careful in writing up my findings - so that all others might benefit.

Many Thanks again.

---

### Post by pdc on 2012-12-02
you're right again! You didn't initiate the thread.......but it should have all that is needed in it now to solve for all

---

### Post by aNovitiate on 2012-12-03
It would be neat (i.e. a LOT easier), if one could specify a network (ethernet) scanner IP from Simple Scan (Document | Preferences) or xSane, rather than having to  remember (look up) to specify the ethernet scanner location via a terminal command, like:
**brsaneconfig4 -a name=DCP-7065DN model=DCP7065DN ip=192.168.1.201**

For instance, a little Simple Scan Document | Preferences dialog box, asking for:

[LIST]
[*]name:
[*]model:
[*]IP:
[/LIST]
It seems like the primary purpose of the **brsaneconfigX** command is to specify the scanner ethernet IP address, as the drivers are/were already installed and network capable, except that they couldn't locate the scanner (IP).

---

### Post by pdc on 2012-12-03
well here is the contact at xsane

[http://www.xsane.org/xsane-contact.html](http://www.xsane.org/xsane-contact.html)

and here is the team that look after Simple Scan

[https://launchpad.net/~elementary-simple-scan-maintainer](https://launchpad.net/~elementary-simple-scan-maintainer)

much of linux is organic; ......it happens because folks do things....

.......contact these folks...........report back when you get some results..

---

### Post by vap1485 on 2013-10-18
Greetings. I'm on 12.04 and I went through this process, installed the correct drivers and the scanner program does recognize my DCP7065DN When I hit scan it tells me 

"Failed to scan
Unable to start scan"

Any idea what's happening?


dpkg -l | grep Brother
ii  brother-udev-rule-type1                     1.0.0-1                                 Brother udev rule type 1
ii  brscan-skey                                 0.2.4-1                                 Brother Linux scanner S-KEY tool
ii  brscan4                                     0.4.1-6                                 Brother Scanner Driver
ii  cupswrapperdcp110c:i386                     1.0.2-3                                 Brother DCP110C CUPS wrapper driver
ii  cupswrapperdcp7065dn:i386                   2.0.4-2                                 Brother DCP7065DN CUPS wrapper driver
ii  dcp110clpr:i386                             1.0.2-1                                 Brother lpr Inkjet Printer Definitions
ii  dcp7065dnlpr:i386                           2.1.0-1                                 Brother DCP-7065DN LPR driver
ii  printer-driver-ptouch                       1.3-3ubuntu0.1                          printer driver Brother P-touch label printers

XSANE says
"Failed to start scanner: Invalid argument"

---

### Post by fscacl on 2014-02-16
Thank you, aNovitiate. Your instructions were clear, helpful, and just excellent! :P

I would add two things, though.

One, for me, while the LPR .deb file worked exactly as you described, I could not get the CUPS driver to install via the Software Center. For some reason, it never completed installing.  I had to install it manually, using the Brother CLI instructions as follow:

dpkg  -i  --force-all  (cupswrapper-drivername)

For me that was as follows:
dpkg  -i  --force-all  cupswrapperDCP7065DN-2.0.4-2.i386.deb

Second, when I re-added the printer, under the connections section, I opted for the “LPN Network Printer DNS-SD.” I am not certain that was the best choice, but it works for me. If there was a smarter option, please feel encouraged to let me know.

Again, thank you for taking the time to document your procedure.

> **aNovitiate said:**
> ... some, hopefully, helpful clarifications:

When I first discovered the Brother DCP7065 Linux drivers page:
[http://http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#DCP-7065DN](http://http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#DCP-7065DN)
I was unsure as to whether to use the CUPS or LPR driver.  I thought that only the CUPS driver was necessary ... and experienced the same as the first post i.e. the printer lit up but didn't print.

When I downloaded and installed the second (LPR) driver ... and re-ADD'd the printer, it printed the Test Page.  Yea !

btw, all I had to do to install each of those drivers was:

[LIST]
[*]double-click on the downloaded** .deb** file
[*]which opened the Ubuntu Software Center
[*]which, after maybe 5 seconds, provided the "*Install*" button (top-right) ...
[/LIST]
During that install, it pops a dialog box, saying "The Package is of bad quality" etc.     However, it offers a *'Ignore and Install*' button, which I clicked ... and the install completed, just fine.   I figured it was 'ok' to 'Ignore and Install', since those .deb's were posted by Brother.

My DCP-7065DN is installed via an **ethernet** connection, rather than just USB.  Nevertheless, the twin CUPS/LPR drivers worked just fine, thank you very much.

I deleted my previous DCP-7065DN printer in "Printers" ... and re-added it.  

Wait ~10 seconds after clicking "Add ..." before clicking "> Network Printer" (left-column) - to give it a chance to '*see*' your DCP-7065DN and its IP address. 

 "Add ... printer" recognized a "Brother" printer and displayed the models list box.  The newly-added (driver) DCP-7065DN choice was at the **top** of the list.  Before adding the LPR driver (i.e. with only the CUPS driver) the DCP-7065DN choice was not labeled "recommended".  After adding the LPR driver, the DCP-7065DN choice was labeled "recommended" ... and the ensuing "Test Page" print worked.  Yabadabadoo !  :P

---

### Post by foresto on 2014-03-11
I was trying to get a Brother DCP-7065DN working via USB on a 64-bit Ubuntu 13.10 (saucy) system, and didn't have any luck with the above instructions. The scanner simply was not found when I used the drivers that Brother links from their product page:

[http://welcome.solutions.brother.com/bsc/public/us/us/en/dlf/download_index.html?reg=us&c=us&lang=en&prod=dcp7065dn_all&dlid=&flang=English&os=128&type2=-1](http://welcome.solutions.brother.com/bsc/public/us/us/en/dlf/download_index.html?reg=us&c=us&lang=en&prod=dcp7065dn_all&dlid=&flang=English&os=128&type2=-1)

Eventually, I came across this other page, which has 64-bit packages: 

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html#brscan4](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html#brscan4)

I purged the i386 scanner packages and installed the 64-bit brscan4 and scan-key-tool debs. I might have rebooted after that (I don't remember for sure) but I don't think so. The scanner was then detected and worked just fine.

Why Brother pushes their 32-bit drivers (even to the point of telling users to manually install 32-bit support libraries) on 64-bit systems is beyond me.

---

### Post by kurt18947 on 2014-03-12
I agree with you.  To my knowledge, there are no 64 bit printer drivers but there are 64 bit scanner drivers.  It's all rather a mish-mash and Brother rather clearly expects users to install from the command line.  They have released a new installer script - 2.0.0.5 I think -  that installs printer **and** scanner drivers.  The installer script doesn't fix the two issues related to the "scanner not found" type error messages to my knowledge though.  I think I understand why Brother prefers the command line install,  one set of instructions covers most distros & desktops.  It can be a little intimidating to beginners though.

---

### Post by izquierdista on 2014-04-28
Ironically Im the original poster of this thread and now when I upgraded to Ubuntu 14.04 I went ahead and did the following:

I went to this link: [http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=dcp7065dn_all&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=dcp7065dn_all&os=128)

1) Installed the Driver Install tool

the printer worked but the scanner DID NOT 

so I went ahead and installed the:
2) Scan-key-tool 64bit (deb package)

and I can load up xsane but when I press "scan" I get a message saying "Invalid Argument"

I tried using the program gscan and I get the same "Invalid Argument" message

Edit: Xsane doesnt work no matter how many times I press scan 
Gscan works but I have to press "scan" twice the first time the "Invalid argument" appears the second time it scans fine!! 


what can I do to resolve this???

---

### Post by kurt18947 on 2014-05-05
I believe you're using a USB connection?  If so, you need to do two steps.  The first is here:

[http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101)

The second is here:

[http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#6](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#6)

I have Brother MFDs installed on a couple 14.04 gnome installs and as long as I make the above changes everything works.  On that same FAQ page are questions about scan-key. I have little experience with scan-key so am of no help there.

---

### Post by pwabrahams on 2014-08-24
I'm running Kubuntu 12.04.  Using the Brother-provided driver, I got the printer working -- but I got stuck on the scanner.  It asked me for the IP address, but couldn't find it anywhere in the Printer section of System Settings.  How can I determine that IP address?

Also, I note that my first installation attempt was just using the software associated with System Settings.  It recognized the printer, all right, but wouldn't actually print anything.  I had to remove the Ubuntu-generated printer and use the printer generated by the Brother software.

Also, when I was asked for the Device URI, I was given several choices.  Ultimately I found one that worked: **dnssd://Brother%20DCP-7065DN._printer._tcp.local/**.  But how could I have known that this was the correct choice?

---

### Post by kurt18947 on 2014-08-26
> **pwabrahams said:**
> I'm running Kubuntu 12.04.  Using the Brother-provided driver, I got the printer working -- but I got stuck on the scanner. ** It asked me for the IP address, but couldn't find it anywhere in the Printer section of System Settings.  How can I determine that IP address?**

Also, I note that my first installation attempt was just using the software associated with System Settings.  It recognized the printer, all right, but wouldn't actually print anything.  I had to remove the Ubuntu-generated printer and use the printer generated by the Brother software.

Also, when I was asked for the Device URI, I was given several choices.  Ultimately I found one that worked: **dnssd://Brother%20DCP-7065DN._printer._tcp.local/**.  But how could I have known that this was the correct choice?

I'm not certain how to determine the correct connection type.  Like you, I sometimes try different one 'til I find one that works.  I generally assign a static I.P. address to the machine.  I've had good luck using using AppSocket/HP Jetdirect which AFAIK requires assigning an I.P. address.  If the machine's I.P. address were to change, the printer would not be found, it'd be like moving without leaving a forwarding address.  The same is true when installing the scanner as a network scanner.  It's necessary to type one line in a terminal like this:

```
5-1. Add network scanner entry Command  :  

brsaneconfig(2,3,4)  -a  name=(name  your  device)  model=(model  name)  ip=xx.xx.xx.xx
 

```

[http://support.brother.com/g/s/id/linux/en/instruction_scn1b.html?c=us_ot&lang=en&redirect=on](http://support.brother.com/g/s/id/linux/en/instruction_scn1b.html?c=us_ot&lang=en&redirect=on)

Using the method/protocol/whatever you used may give the printer address a "follow me" capability if the machine's I.P. address were to change  but I don't see a similar capability for the scanner.  I assign the machine's boot method (static) and I.P. address via the machine's control panel.

I'm no expert, just saying what works for me.

---

### Post by pwabrahams on 2014-09-12
The critical step that I missed was using the menu key on the printer's control panel to set the IP address.  It's pretty obvious how to do that: after pressing Menu, choose 3-Network, then 2-TCP/IP, then 1-IP Address.  Once I did that, xsane and the scanner worked flawlessly.  Just to finish icing the cake, the correct call on xsane is **xsane brother4**, which avoids the selection screen if you happen to have more than one visible scanner.

---

