---
title: "Xerox Standard Accounting Doesn't work"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by neonitron on 2009-02-26
Hi guys,

I hope this is in the correct forum. I'm just posting to see if anyone has a fix or workaround for printing to Xerox WorkCentre 7655, or any other model of Xerox for that matter, that has Xerox Standard Accounting enabled on it. I have looked through the forums but have found only 2 people with this issue with noone able to provide a fix for it.

Any other printers work for me, and I can print to my Xerox WorkCentre 7655, but when the job spits out it states the following: "The job was deleted due to invalid accounting IDs". I've downloaded the ppd file straight from Xerox's website and installed the printer correctly (I believe anyway), and in the properties of the printer you can enable accounting. 

In Windows when you go to print a job it prompts you for what account code, but in Ubuntu it does not prompt you at all, and simply prints out a page as I mentioned above.

**_[SIZE="5"]Does anyone know how an account code can be specified?[/SIZE]_**



Thanks,
Neil

---

### Post by wpshooter on 2009-02-26
I hate to be negative, but if this is like any of the other many printer related problems that I have run into when trying to get a printer device to work correctly under Ubuntu, then woooooooo, is you !!!

---

### Post by Mark Phelps on 2009-02-27
You could try the OpenPrinting forums -- to see if they have any drivers or any posts on getting your printer to work.  Link is below:

[http://forums.openprinting.org/index.php?18]("http://forums.openprinting.org/index.php?18")

---

### Post by neonitron on 2009-03-01
Thanks guys. I will post in the OpenPrinting User Forums to see if they have run into this or already have a solution.

Thanks,
Neil

---

### Post by jesse10581 on 2009-06-11
In Windows, for the Xerox 3635MFP with XSA, you can also specify a hardcoded Account ID from the driver, rather than having the driver prompt the user each time. Is this a possibility in Linux?

---

### Post by halitech on 2009-06-20
if the machine is under a year old, contact support. I know the people at first level won't be able to help you but tell them you want to speak to a tech in Second Level support about a Linux issue. Hopefully you'll get someone in Manilla who understands enough English that they will escalate you to second level instead of telling you they don't support linux and disconnecting the call. 

Unfortunately I don't work there any longer and don't have access to the machines so can't look into the issue and help you out directly here.

---

### Post by tgalati4 on 2009-06-20
There's no option in job control or advanced printer settings?  I've seen ID's for HP printers.

---

### Post by chaos51 on 2009-07-17
Did you ever get this to work?

I've been fighting with this for a couple of days (except I'm running Red Hat for my cups server).

The information I found ( [http://www.office.xerox.com/support/dctips/dc09cc0450.pdf]("http://www.office.xerox.com/support/dctips/dc09cc0450.pdf") ) basically implied that you add the following to the ppd file for the printer and restart cups:

*% Generic Accounting
*JCLOpenUI *JCLAccounting/Accounting: PickOne
*OrderDependency: 10.1 JCLSetup *JCLAccounting
*DefaultJCLAccounting: XSADisabled
*JCLAccounting XSADisabled/Disabled: ""
*JCLAccounting XSAUser/XSA User Based Accounting: "@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_USERID,MyUserID<22>;<0A>"
*JCLAccounting XSAGeneral/XSA General Based Accounting: "@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_USERID,MyUserID<22>;<0A>@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_GENERALACCT,MyGeneralAcctID<22>;<0A>"
*JCLAccounting XSAGroup/XSA Group Based Accounting: "@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_USERID,MyUserID<22>;<0A>@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_GROUPACCT,MyGroupAcctID<22>;<0A>"
*JCLAccounting XNAGroup/XNA Group Based Accounting: "@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_USERID,MyUserID<22>;<0A>@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_ACCTID,MyAcctID<22>;<0A>"
*JCLCloseUI: *JCLAccounting

and modify the ID's as necessary.

I've tried about every possible combination and still can't print.

I also tried install the printer and print queue using the Xerox CentreWare software (which gives the option to put in user_id, acct_id, etc..) but that also did not work.

---

### Post by chaos51 on 2009-07-17
Here is an example of what I tried putting into my ppd file in /etc/cups/ppd/xerox.ppd  (we are trying this with a Xerox Phaser 3635 ).


```
*% Generic Accounting
*JCLOpenUI *JCLAccounting/Accounting: PickOne
*OrderDependency: 10.1 JCLSetup *JCLAccounting
*DefaultJCLAccounting: XSAGroup
*JCLAccounting XSADisabled/Disabled: ""
*JCLAccounting XSAUser/XSA User Based Accounting: "@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_USERID,MyUserID<22>;<0A>"
*JCLAccounting XSAGeneral/XSA General Based Accounting: "@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_USERID,MyUserID<22>;<0A>@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_GENERALACCT,MyGeneralAcctID<22>;<0A>"
*JCLAccounting XSAGroup/XSA Group Based Accounting: "@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_USERID,999999<22>;<0A>@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_GROUPACCT,0001<22>;<0A>"
*JCLAccounting XNAGroup/XNA Group Based Accounting: "@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_USERID,MyUserID<22>;<0A>@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_ACCTID,MyAcctID<22>;<0A>"
*JCLCloseUI: *JCLAccounting
```

Not sure if the placement of the code makes a difference, I put it right above ```
*% Installable Options
```

I know that the userid is valid as I can login to the printer from the front panel and make a copy and I've verified that we are using XSA (Xerox Standard Accounting or Auditron) Group accounting.

---

### Post by illuminatedwax on 2009-07-23
> **chaos51 said:**
> Here is an example of what I tried putting into my ppd file in /etc/cups/ppd/xerox.ppd  (we are trying this with a Xerox Phaser 3635 ).


```
*% Generic Accounting
*JCLOpenUI *JCLAccounting/Accounting: PickOne
*OrderDependency: 10.1 JCLSetup *JCLAccounting
*DefaultJCLAccounting: XSAGroup
*JCLAccounting XSADisabled/Disabled: ""
*JCLAccounting XSAUser/XSA User Based Accounting: "@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_USERID,MyUserID<22>;<0A>"
*JCLAccounting XSAGeneral/XSA General Based Accounting: "@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_USERID,MyUserID<22>;<0A>@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_GENERALACCT,MyGeneralAcctID<22>;<0A>"
*JCLAccounting XSAGroup/XSA Group Based Accounting: "@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_USERID,999999<22>;<0A>@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_GROUPACCT,0001<22>;<0A>"
*JCLAccounting XNAGroup/XNA Group Based Accounting: "@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_USERID,MyUserID<22>;<0A>@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_ACCTID,MyAcctID<22>;<0A>"
*JCLCloseUI: *JCLAccounting
```Not sure if the placement of the code makes a difference, I put it right above ```
*% Installable Options
```I know that the userid is valid as I can login to the printer from the front panel and make a copy and I've verified that we are using XSA (Xerox Standard Accounting or Auditron) Group accounting.
I had the exact same problem with the Phaser 3635, and just doing this doesn't work. You have to edit the rest of the PPD file so that all the JCL options use @PJL COMMENT syntax rather than Postscript syntax. You can check out my changes at [http://pastebin.ca/1504991](http://pastebin.ca/1504991) (I also commented out a lot of unneccessary features just to make it work.) I was able to print using this PPD.

---

### Post by chaos51 on 2009-07-24
@illuminatedwax,
  Thanks, for the first time now in a month I was able to print to our xerox 3635.  I'll have to look over the changes you made to see if I can get it to also work for out WorkCentre 5225 and 5655.
  Once again the community forums fix a problem that our paid for support couldn't!!!
  thanks again,

---

### Post by illuminatedwax on 2009-07-24
> **chaos51 said:**
> @illuminatedwax,
  Thanks, for the first time now in a month I was able to print to our xerox 3635.  I'll have to look over the changes you made to see if I can get it to also work for out WorkCentre 5225 and 5655.
  Once again the community forums fix a problem that our paid for support couldn't!!!
  thanks again,
When I called Xerox tech support, he said that no one had ever tried to get XSA working with Linux lol

---

### Post by tog on 2009-12-26
I tried the changes that were suggested for printing to a Xerox 7655, and I keep getting an invalid account ID error. Anybody have any luck with printing to this printer?

Thanks.

Murali

P.S. Here is the relevant part of my ppd. I replaced the ???? with my user and group codes.

*%				Banner Sheet
*JCLOpenUI *JCLBanner/Banner Sheet: Boolean
*OrderDependency: 10.0 JCLSetup *JCLBanner
*DefaultJCLBanner: False
*JCLBanner True/Enabled: "@PJL COMMENT OID_ATT_START_SHEET OID_VAL_JOB_SHEET_FULL<0A>"
*JCLBanner False/Disabled: "@PJL COMMENT OID_ATT_START_SHEET OID_VAL_JOB_SHEET_NONE<0A>"
*JCLCloseUI: *JCLBanner
*%				Generic Accounting

*JCLOpenUI *JCLAccounting/Accounting: PickOne
*OrderDependency: 10.1 JCLSetup *JCLAccounting
*DefaultJCLAccounting: XSAGroup
*JCLAccounting XSADisabled/Disabled: ""

*JCLAccounting XSAUser/XSA User Based Accounting: "@PJL COMMENT
OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_USERID,MyUserID<22>;<0A>"

*JCLAccounting XSAGeneral/XSA General Based Accounting: "@PJL COMMENT
OID_ATT_ACCOUNTING_INFORMATION_AVP
<22>XRX_USERID,????<22>;<0A>@PJL COMMENT
OID_ATT_ACCOUNTING_INFORMATION_AVP
<22>XRX_GENERALACCT,????<22>;<0A>"

*JCLAccounting XSAGroup/XSA Group Based Accounting: "@PJL COMMENT
OID_ATT_ACCOUNTING_INFORMATION_AVP
<22>XRX_USERID,????<22>;<0A>@PJL COMMENT
OID_ATT_ACCOUNTING_INFORMATION_AVP
<22>XRX_GROUPACCT,????<22>;<0A>"

*JCLAccounting XNAGroup/XNA Group Based Accounting: "@PJL COMMENT
OID_ATT_ACCOUNTING_INFORMATION_AVP
<22>XRX_USERID,MyUserID<22>;<0A>@PJL COMMENT
OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_ACCTID,MyAcctID<22>;<0A>"
*JCLCloseUI: *JCLAccounting

---

### Post by tog on 2009-12-29
Well, not really sure how, but I have now managed to print to the Xerox 7655 from Ubuntu 9.10. A few details first:

1. We use a group based accounting, as such, in addition to a user id, we also have a group account id. Both IDs are numeric values.
2. While CUPS and Ubuntu Print Manager both find the Xerox 7655 on our network, setting up the printer by selecting it does not work. I still get "invalid account ID" error message.
3. When you set up the printer, choose AppSocket/HP Jet Direct method. So your address for the printer will be socket://Printer Host IP address:9100.
4. In the next step, indicate you have a PPD (I am attaching mine, which works for me).
5. Before you point at the PPD, make sure to edit the PPD, and put in your user id, and account ID in the PPD. In my case, as I use Group Based Accounting, I selected that portion of the code in the PPD.
6. Point to the modified PPD, and set up printer. Hopefully, it will work for you too.

I am attaching the PPD that works for me.

---

### Post by m0gely on 2010-02-18
I have the 7665,and have edited the ppd to use my account and group ID's per instructions here and [this Xerox doc]("http://www.office.xerox.com/support/dctips/dc09cc0452.pdf"). I get **Held - resources not available** in the status field on the web interface when sending a print. What resource it means is a mystery. Has any one seen this message and know how to debug it?

---

### Post by m0gely on 2010-02-18
Gah, nevermind. It was a mismatch of what paper size was in the default tray. It works great!

---

### Post by ruimrcabral on 2010-05-17
Did anyone manage to get it to work on 56xx and 3635?? If yes did you use LPD to create the queue and could you post the ppd? 
I cant get it to work :(

---

### Post by frabjous on 2010-07-06
> **ruimrcabral said:**
> Did anyone manage to get it to work on 56xx and 3635?? If yes did you use LPD to create the queue and could you post the ppd? 
I cant get it to work :(

This is probably coming too late to help you, but I managed to get Job Accounting working with our new Xerox WorkCentre 5645 today with my workstation running Lucid. Took all day to figure out.

I had to make a modified version of the driver found here:

[https://blinky.si.umich.edu/confluence/display/SIC/Linux+-+Printing+to+the+Xerox+WorkCentre+MFDs](https://blinky.si.umich.edu/confluence/display/SIC/Linux+-+Printing+to+the+Xerox+WorkCentre+MFDs)

I didn't have any luck with the ones from the xerox site.

2. When I first tried the PPD, I got an error about line 30. So I
changed line 26 from

*JobPatchFile: "

to

*JobPatchFile 0: "

following advice here:

[http://ubuntuforums.org/showthread.php?t=1500896](http://ubuntuforums.org/showthread.php?t=1500896)

3. The driver there has a section on "Generic accounting", but not
enough to support what we needed.

[http://ubuntuforums.org/showthread.php?t=1081388&page=2](http://ubuntuforums.org/showthread.php?t=1081388&page=2)

as well as info in this file from Xerox (linked in that thread):

[http://www.office.xerox.com/support/dctips/dc09cc0452.pdf](http://www.office.xerox.com/support/dctips/dc09cc0452.pdf)

I changed that section to the lines on accounting in the new version, which I'll quote below.

3. There seems to some bad conflicts set up in the options in the driver, whereby you are required to choose one of the options for what to do about interleaving when printing transparencies (put a sheet
between them or what), but if you choose any of those options, you can only print transparencies. So basically, you can only print transparencies. I got around this by removing all the *UIConstraints having to do with *MediaType Transparency and *Interleave in the PPD. I don't know exactly how those work, but removing these fixed the problem. They're located at lines 546-651 of the original driver from[ umich.edu]("http://umich.edu/"). I know from  playing around with them that the ones on the Xerox site have the same problem.

In order to use this, you'll still need to customize the part about Accounting. It now reads (starting at line 47):

```

*%                Generic Accounting
*JCLOpenUI *JCLAccounting/Accounting: PickOne
*OrderDependency: 10.1 JCLSetup *JCLAccounting
*DefaultJCLAccounting: **XSAUser**
*JCLAccounting XSADisabled/Disabled: ""
*JCLAccounting XSAUser/XSA User Based Accounting: "@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_USERID,**MyUserID**<22>;"
*JCLAccounting XSAGeneral/XSA General Based Accounting: "@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_USERID,**MyUserID**<22>;<0A>@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_GENERALACCT,**MyGenAcctID**<22>;<0A>"
*JCLAccounting XSAGroup/XSA Group Based Accounting: "@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_USERID,**MyUserID**<22>;<0A>@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_GROUPACCT,**MyGroupAcctID**<22>;<0A>"
*JCLAccounting XNAGroup/XNA Group Based Accounting: "@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_USERID,**MyUserID**<22>;<0A>@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_ACCTID,**MyAcctID**<22>;<0A>"
*JCLCloseUI: *JCLAccounting

```

The parts in bold will need to be changed to the appropriate values depending on your accounting type and account numbers.

The PPD worked just fine for me, adding through the normal means (Network printer using "AppSocket/HP JetDirect", specifying the Host address, and port 9100), provding this PPA.

---

### Post by ruimrcabral on 2010-07-09
Hi, 
thanks for the information. It's valid and it does work for me as well. 

I have noticed that you edited the ppd quite alot. 
I am trying to do some changes to it with no luck (getting invalida account ID always).

This is what made acc working:
*JCLBegin:"<1B>%-12345X@PJL JOB<0A>@PJL<0A>@PJL COMMENT XRXbegin<0A>"
*%                              Banner Sheet
*JCLOpenUI *JCLBanner/Banner Sheet: Boolean
*OrderDependency: 10.0 JCLSetup *JCLBanner
*DefaultJCLBanner: False
*JCLBanner True/Enabled: "@PJL COMMENT OID_ATT_START_SHEET OID_VAL_JOB_SHEET_FULL<0A>"
*JCLBanner False/Disabled: "@PJL COMMENT OID_ATT_START_SHEET OID_VAL_JOB_SHEET_NONE<0A>"
*JCLCloseUI: *JCLBanner

*%				Generic Accounting
*JCLOpenUI *JCLAccounting/Accounting: PickOne
*OrderDependency: 10.1 JCLSetup *JCLAccounting
*DefaultJCLAccounting: XSAUser
*JCLAccounting XSADisabled/Disabled: ""
*JCLAccounting XSAUser/XSA User Based Accounting: "@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_USERID,MyUserID<22>;"
*JCLAccounting XSAGeneral/XSA General Based Accounting: "@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_USERID,MyUserID<22>;<0A>@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_GENERALACCT,MyGenAcctID<22>;<0A>"
*JCLAccounting XSAGroup/XSA Group Based Accounting: "@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_USERID,MyUserID<22>;<0A>@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_GROUPACCT,MyGroupAcctID<22>;<0A>"
*JCLAccounting XNAGroup/XNA Group Based Accounting: "@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_USERID,MyUserID<22>;<0A>@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_ACCTID,MyAcctID<22>;<0A>"
*JCLCloseUI: *JCLAccounting

*%                              Print Quality
*JCLOpenUI *JCLPrintQuality/Print Quality: PickOne
*OrderDependency: 10.8 JCLSetup *JCLPrintQuality
*DefaultJCLPrintQuality: Standard
*JCLPrintQuality TonerSaver/Toner Saver: "@PJL COMMENT OID_ATT_PRINT_MODE OID_VAL_PRINT_MODE_DRAFT<0A>@PJL COMMENT OID_ATT_BLACK_OVERPRINT_ENABLED TRUE<0A>"
*JCLPrintQuality Standard/Standard: "@PJL COMMENT OID_ATT_PRINT_MODE OID_VAL_PRINT_MODE_STANDARD<0A>@PJL COMMENT OID_ATT_BLACK_OVERPRINT_ENABLED TRUE<0A>"
*JCLPrintQuality Enhanced/Enhanced: "@PJL COMMENT OID_ATT_PRINT_MODE OID_VAL_PRINT_MODE_PREMIUM<0A>@PJL COMMENT OID_ATT_BLACK_OVERPRINT_ENABLED TRUE<0A>"
*JCLCloseUI: *JCLPrintQuality
*%                              True Gray Graphics
*JCLOpenUI *JCLTrueGrayGraphics/True Gray Graphics: PickOne
*OrderDependency: 10.9 JCLSetup *JCLTrueGrayGraphics
*DefaultJCLTrueGrayGraphics: True
*JCLTrueGrayGraphics False/Off: "@PJL COMMENT OID_ATT_PROCESS_GRAYSCALE_GRAPHICS_ENABLED FALSE<0A>"
*JCLTrueGrayGraphics True/On: "@PJL COMMENT OID_ATT_PROCESS_GRAYSCALE_GRAPHICS_ENABLED TRUE<0A>"
*JCLCloseUI: *JCLTrueGrayGraphics
*%
*JCLToPSInterpreter:"@PJL COMMENT XRXend<0A>"
*JCLEnd:"<1B>%-12345X@PJL EOJ<0A><1B>%-12345X<0A>"


What I would like is to remove the call for True Gray Graphics, banner and Print Quality...

My attempt was:
*JCLBegin:"<1B>%-12345X@PJL JOB<0A>@PJL<0A>@PJL COMMENT XRXbegin<0A>"
*%				Generic Accounting
*JCLOpenUI *JCLAccounting/Accounting: PickOne
*OrderDependency: 10.1 JCLSetup *JCLAccounting
*DefaultJCLAccounting: XSAUser
*JCLAccounting XSADisabled/Disabled: ""
*JCLAccounting XSAUser/XSA User Based Accounting: "@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_USERID,MyUserID<22>;"
*JCLAccounting XSAGeneral/XSA General Based Accounting: "@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_USERID,MyUserID<22>;<0A>@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_GENERALACCT,MyGenAcctID<22>;<0A>"
*JCLAccounting XSAGroup/XSA Group Based Accounting: "@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_USERID,MyUserID<22>;<0A>@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_GROUPACCT,MyGroupAcctID<22>;<0A>"
*JCLAccounting XNAGroup/XNA Group Based Accounting: "@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_USERID,MyUserID<22>;<0A>@PJL COMMENT OID_ATT_ACCOUNTING_INFORMATION_AVP <22>XRX_ACCTID,MyAcctID<22>;<0A>"
*JCLCloseUI: *JCLAccounting
*%
*JCLToPSInterpreter:"@PJL COMMENT XRXend<0A>"
*JCLEnd:"<1B>%-12345X@PJL EOJ<0A><1B>%-12345X<0A>"

I tried as well without "*%" and the "*JCLToPSInterpreter:"@PJL COMMENT XRXend<0A>"" but no luck.

Is there anything its simple but im not getting? Couldn't I just get it working with the Accounting bit??

Thanks

---

### Post by carpex on 2010-07-26
@frabjous, thanks a bunch! Its the first time I can print at work from my laptop in over 6 months. Your ppd file worked fine for me on our Workcentre 5655.  Much appreciated!:o

---

### Post by Punkphysicist on 2010-09-02
Using the ppd provided by Tog I was able to pring to a Xerox 5675.

Thanks

> **tog said:**
> Here

---

### Post by vmunizfraticelli on 2010-10-29
The umich PPD that frabjous posted worked for me on a Xerox WorkCentre 5638. It lets me print successfully, but after completing each job it spits out an Error Notice (with the usual line "This job was deleted due to invalid accounting IDs"). 

By looking at the Jobs tab on the web interface, I've discovered that it seems to be printing an "extra" (invalid) job every time. Any idea why that might be?

---

### Post by flyingnorm on 2011-09-16
> **tog said:**
> Well, not really sure how, but I have now managed to print to the Xerox 7655 from Ubuntu 9.10. A few details first:

1. We use a group based accounting, as such, in addition to a user id, we also have a group account id. Both IDs are numeric values.
2. While CUPS and Ubuntu Print Manager both find the Xerox 7655 on our network, setting up the printer by selecting it does not work. I still get "invalid account ID" error message.
3. When you set up the printer, choose AppSocket/HP Jet Direct method. So your address for the printer will be socket://Printer Host IP address:9100.
4. In the next step, indicate you have a PPD (I am attaching mine, which works for me).
5. Before you point at the PPD, make sure to edit the PPD, and put in your user id, and account ID in the PPD. In my case, as I use Group Based Accounting, I selected that portion of the code in the PPD.
6. Point to the modified PPD, and set up printer. Hopefully, it will work for you too.

I am attaching the PPD that works for me.


This was my great solution as well. Thanks for posting the modified ppd. No I can print to 7655 from ubuntu 11.04.

---

### Post by fabfisc on 2013-02-14
Hi,
i'm facing some problem with XSA too.

In my WorkCentre 7545 configuration i've the following config (attachments).

I have added the lines in ppd, but, still now, cannot print using the "user_bn" account and "2" as groupID.

Can you help me to solve that?


Thanks in advance

---

### Post by oldos2er on 2013-02-14
Please start a new thread.

If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

