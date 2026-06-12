---
title: "Why do I have multiples of same printer?"
date: 2021-10-07
forum: Hardware
---

### Post by frittered on 2021-10-07
I originally installed Ubuntu on my wife's computer because it had a reputation for just working no-matter what.  It is rapidly losing that reputation at this locality.
I'm having a rabbit problem.  I couldn't resolve this with 18.04 and still have it after upgrade to 20.04.  (this has been going on for a few years)  A new problem has developed and I don't know if it's an extension of the same problem: The printers won't work until I re-install them now.  Besides the old problem where once I install a printer, more than one will appear with a slightly altered name (rabbits, ghost rabbits).  
After installation, the printer will function like a normal printer.  A day or so later, it won't function.  If I go into settings I might find a restart button that implies there is a problem to resolve with the printer.  If I re-install the printer, it will perform the print job during the installation procedure.
I'm getting tired of the nonsense with the printer.  If this won't go away with your help and assistance, I'm going to have to install a different distribution, other than ubuntu.

---

### Post by brian_p on 2021-10-08
It is traditional to mention:

[LIST]
[*]The connection method. USB? Network?
[/LIST]
[LIST]
[*]The printer model.
[/LIST]
[LIST]
[*]Any vendor drivers installed.
[/LIST]

---

### Post by ajgreeny on 2021-10-08
I have seen this happen for quite a long time, ie years, though I do not remember when it started.

In my case I use an HP Envy All in One printer and in any print dialogue it appears three times, all of which work fine, so I am not bothered by this duplication, which I suspect may partly be because the printer is detected by hplip and also by the CUPS system, though I accept that should be only two instances.
See screenshot

---

### Post by frittered on 2021-10-08
ok, I always use a network printer as I usually have more than one computer that needs access to a printer and my house and office are always "networked" since time began, I only buy printers that have an ethernet port and I turn-off any "wifi" crap on the printer.  I've been having this "rabbit" problem since 16.04 LTS, 14.04LTS did not have this problem.  The first time was with a HP deskjet, problem never resolved, symptoms were multiple instances of a printer install, one install would be the one I installed(functional instance), another would be named after the host computer and another would be something else but all would have the model name of the printer.  Only one of the installs would print, removing the non-functioning printers are futile, they just re-appear.

Presently, I have an Epson ink-jet and a Brother laser-jet (both have scanners and fax) installed and 6 printers installed according to the "settings" info.  Only two are real and right now it's a battle to get either one to function and take print-jobs.  Both of these printers were installed via company supplied install drivers using their supplied routine from their support web-site.  The rabbits appeared a day later, after a wake-up period.  My non-ubuntu systems do not have the rabbit issues.  There are no "Windows" systems to cause trouble here.

---

### Post by brian_p on 2021-10-08
> **frittered said:**
> ok, I always use a network printer as I usually have more than one computer that needs access to a printer and my house and office are always "networked" since time began, I only buy printers that have an ethernet port and I turn-off any "wifi" crap on the printer.  I've been having this "rabbit" problem since 16.04 LTS, 14.04LTS did not have this problem.  The first time was with a HP deskjet, problem never resolved, symptoms were multiple instances of a printer install, one install would be the one I installed(functional instance), another would be named after the host computer and another would be something else but all would have the model name of the printer.  Only one of the installs would print, removing the non-functioning printers are futile, they just re-appear.

Presently, I have an Epson ink-jet and a Brother laser-jet (both have scanners and fax) installed and 6 printers installed according to the "settings" info.  Only two are real and right now it's a battle to get either one to function and take print-jobs.  Both of these printers were installed via cI do not understandusing their supplied routine from their support web-site.  The rabbits appeared a day later, after a wake-up period.  My non-ubuntu systems do not have the rabbit issues.  There are no "Windows" systems to cause trouble here.

Epson ink-jet and a Brother laser-jet are not good enough. What are the precise models?

I do not understand what "company supplied install drivers " involves and what it does.

---

### Post by frittered on 2021-10-10
Brother model is a MFC-L3750CDW  Epson is a WF-3640.  This is so not helpful to the problem as the same symptoms are presented by a host of other models of printers.  The problem behaves like malware and occurs immediately after a wake-up from a sleep-cycle.  Both Brother and Epson have drivers available from the websites.  I'm not into writing my own code as I am not a device resource with vast support utilities.  I don't like having to battle wits with an obstreperous OS just to get a print-job done.
I'm talking my wife into using a different brand of Linux that does not have this printer problem.

---

### Post by brian_p on 2021-10-10
> **frittered said:**
> Brother model is a MFC-L3750CDW  Epson is a WF-3640.  This is so not helpful to the problem as the same symptoms are presented by a host of other models of printers.  The problem behaves like malware and occurs immediately after a wake-up from a sleep-cycle.  Both Brother and Epson have drivers available from the websites.  I'm not into writing my own code as I am not a device resource with vast support utilities.  I don't like having to battle wits with an obstreperous OS just to get a print-job done.

You have decided that a printer model and the way you deal with it on a modern printing system is
irrelevant. It is hardly worthwhile carrying on, especially with all the moaning.
> 
I'm talking my wife into using a different brand of Linux that does not have this printer problem.
All distributions use the same printing system. The problem is between the chair and the keyboard.

---

### Post by frittered on 2021-10-11
Obviously not, as the RedHat based system I use does not have a duplicity issue the Ubuntu system is having and it never has! (I use it daily and have been using it for more than a decade, actually closer to two decades)(printing is never an issue with it after the printer is installed)
I have a similar opinion of yourself.  Now that we have exchanged insults perhaps we can move to resolving the problem?  Since the multiplicity of printers in the settings menu has nothing to do with the manufacturer of the printer has been established! 
 What has Ubuntu done to correct the problem?
I'm severely tired of attempting to correct the problem of print-jobs not happening just because it's the next day or an hour later after the system went to sleep because the user left the system to do something else.

---

### Post by frittered on 2021-10-11
> **ajgreeny said:**
> I have seen this happen for quite a long time, ie years, though I do not remember when it started.

In my case I use an HP Envy All in One printer and in any print dialogue it appears three times, all of which work fine, so I am not bothered by this duplication, which I suspect may partly be because the printer is detected by hplip and also by the CUPS system, though I accept that should be only two instances.
See screenshot

I have had this problem for years, but it's getting worse.  Not only do I have multiple printers of which only one worked, the one that did work is now having problems.  What did you do to fix your problem?  I've been having these issues since about 14.04LTS and it's becoming a major issue.
I usually get 3 printers showing.  The one installed has a "-series" added to it's name, another has a".local" and a third will have the "hostname" tacked on.  Usually the one installed with a "-series" is the one that works, but something has changed since a recent update and now I have to re-install the same printer over and over again to resolve it not performing an accepted print-job.  This printer is an MFC-L3750CDW.  When it prints, the job looks pretty nice.  
Recently, after the previous updates, the 2nd printer: Epson wf-3640 has quit re-duplicating itself after deleting it's duplicates, I'm not sure if this has to do with making the other printer the default printer.  

Thank you in advance for your assistance

---

### Post by ajgreeny on 2021-10-13
I didn't do anything to solve this as it has not become a problem for me; whichever of the instances of my wireless printer I choose in the print dialogue makes no difference and the print job happens as expected.

My printer connects by wireless only, no ethernet or USB cable is used and it uses a static IP ad&#271;ress on my LAN, so I wonder if this is the reason for your problem.

---

### Post by richardlc on 2022-01-31
I have had the same problems with 20.04 LTS over a couple of years or so with a Brother DCP-J152 which is shown as two versions in the Printer settings one as "driverless" the other as CUPS. The names of each are slightly different, the driverless is called Brother_DCP_J152 while the CUPS one is reported as being called BrotherDCPJ152 and both are "ready"  but only one prints at random apparently, and then only if I go through the printer's own installation process and switching on the modem's network connection (WPS). (Occasionally three printers are shown as connected(!!) Only two HP laptops are in the network.  The computers are usually turned off at night as are the satellite modem and router, but not the printer because we are off grid on solar power.  This description is very similar to those reported above.  How does this occur?  Is there a solution anyone?  The driver is as imported from Brother web site.  A very good scanning programme I think Vuescan seems able to communicate well.  Often the "system printer" as appears when printing emails sees to work  regularly and best.

---

### Post by Autodave on 2022-01-31
I have an HP Color Laser Jet Pro MFP M277dw, and it is the only printer, with the same prob as the OP, so I do know that what he is telling you is true.  I have 3 printers listed, but only one works: you have to pick the correct entry.  I am hooked to this printer via wifi.  My wife is connected to the same printer via USB and she has 2 printers listed.....either one will print.  This started shortly after 20.04 was released.  Prior to that neither of us had any issues.  On my machine, I can delete the 2 entries that don't work, but they will both return in a day or so.

---

### Post by brian_p on 2022-01-31
Print queues may be 

[LIST]
[*]Auto-setup with cups-browsed (order your birthday cake from a bakery).
[/LIST]

[LIST]
[*]Manually set up (bake your own cake).
[*]
[/LIST]

Doing both gets you two cakes :D.

---

### Post by bobunderwood99 on 2022-01-31
Hello,

This seems to be right on point:

[https://www.linuxupdate.co.uk/2021/05/19/how-to-stop-gnome-auto-printer-discovery-on-fedora-ubuntu-mint/](https://www.linuxupdate.co.uk/2021/05/19/how-to-stop-gnome-auto-printer-discovery-on-fedora-ubuntu-mint/)

It explains getting three logical printers - manual install, cups-browsed and avahi.

---

### Post by richardlc on 2022-02-05
Thank you very much ... will give it a go.

---

### Post by richardlc on 2022-02-08
I followed all the instructions but now cannot access the printer which now is reported to be "non-responding"  though the procedure has stopped the multiple printers appearing!  Only the one printer is reported to be connected!   I am not sure how to wake it up.

---

### Post by bobunderwood99 on 2022-02-09
I'd purge and reinstall the driver.

---

### Post by richardlc on 2022-02-15
Thank you.  I shall be grateful to know how one purges the printer driver and then re-installs it.

---

### Post by mIk3_08 on 2022-02-15
> **frittered said:**
> Brother model is a MFC-L3750CDW. I do have this brother printer scanner with my Ubuntu Operating System. Im using this for many years now. Once again this printer/scanner is running with Ubuntu Operating System and the scanner runs smoothly with xsane scanner application software what i did is just, I installed the driver coming from brother printer  website and I just follow the instructions during installation. so far so good, I haven't encountered any errors or failure in my printer/scanner. so good luck and cheers. If you want to reinstall your brother printer driver just [click here.]("https://support.brother.com/g/b/downloadtop.aspx?c=us_ot&lang=en&prod=mfcl3750cdw_us_eu_as") If you want to reinstall the driver be sure to remove all the brother printer driver you installed.

---

### Post by bobunderwood99 on 2022-02-16
See below to remove.

[https://help.brother-usa.com/app/answers/detail/a_id/164937/~/uninstall-the-printer-driver-or-scanner-driver-%28deb%29---linux](https://help.brother-usa.com/app/answers/detail/a_id/164937/~/uninstall-the-printer-driver-or-scanner-driver-%28deb%29---linux)

Then install as you did originally.

---

### Post by aj34 on 2022-02-18
Similar problem here. Are there versions of Linux I could try that won't have this apparently widespread problem? If not, is there a simple and complete guide that contains all the info. necessary to sort the problem - start to finish? My knowledge of the workings of PC's and operating systems is minimal so when I attempt to follow the guidance (incl. links in this thread) I don't get the results suggested or any outcome I can understand. Have to say I would not have anticipated such printing problems with a mature OS like Ubuntu 20.04.3 LTS.

---

### Post by brian_p on 2022-02-18
> **aj34 said:**
> Similar problem here. Are there versions of Linux I could try that won't have this apparently widespread problem? If not, is there a simple and complete guide that contains all the info. necessary to sort the problem - start to finish? My knowledge of the workings of PC's and operating systems is minimal so when I attempt to follow the guidance (incl. links in this thread) I don't get the results suggested or any outcome I can understand. Have to say I would not have anticipated such printing problems with a mature OS like Ubuntu 20.04.3 LTS.

What problem do you have? Please include info on the printer and printing.

---

