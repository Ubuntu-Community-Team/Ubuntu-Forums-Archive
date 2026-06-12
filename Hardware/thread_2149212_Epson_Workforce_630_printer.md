---
title: "Epson Workforce 630 printer"
date: 2013-05-28
forum: Hardware
---

### Post by patriot56 on 2013-05-28
Greetings Forum.  I am posting here because I wasn't sure where else to post this issue.    I am using Ubuntu 12.04.2 LTS - Precise.   The printer installed is, as mentioned in the subject, an Epson Workforce 630 "all-in-one" printer, and it was working just fine until a few days ago.    I suspect that it was an update that caused the printer to stop working but I have nothing more to go on than just that suspicion.  I don't have any evidence to substantiate this guess.  I wish I knew more about how to diagnose these problems but I don't.    Should I just download and install the drivers from Epson's web site and reinstall them?  (Is this is the correct proceedure)?  Or am I getting ahead of myself?    I have looked in the repositories for the drivers for this Epson printer and all I can find is a utility for checking ink levels.   Any help is greatly appreciated and most certainly welcome.    Thank you in advance.  patriot56

---

### Post by pdc on 2013-05-28
sorry to hear your printer is playing up; can I suggest an ubuntu helpsheet

[https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems)

you sound like the sort of soul who could work through this and logically tick things off; 

I think ubuntu is now set up with Epson to install drivers from their site; when an Epson printer is detected; 

the command

> [COLOR="#FF0000"]sudo dpkg -l | grep epson-inkjet-printer[/COLOR] should show you what drivers you have installed from Epson

looks like this link

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=16857&DSCCHK=4334d3487503d7f916ccf5d58071b05b7687294f](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=16857&DSCCHK=4334d3487503d7f916ccf5d58071b05b7687294f)

is for printer drivers for the 630

and this [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=21580&DSCCHK=ea245da3525f56d8ca2ab9408ed2d6d8b481d435](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=21580&DSCCHK=ea245da3525f56d8ca2ab9408ed2d6d8b481d435) for the scanner

---

### Post by patriot56 on 2013-05-28
> **pdc said:**
> sorry to hear your printer is playing up; can I suggest an ubuntu helpsheet

[https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems)

you sound like the sort of soul who could work through this and logically tick things off; 

I think ubuntu is now set up with Epson to install drivers from their site; when an Epson printer is detected; 

the command

 should show you what drivers you have installed from Epson

looks like this link

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=16857&DSCCHK=4334d3487503d7f916ccf5d58071b05b7687294f](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=16857&DSCCHK=4334d3487503d7f916ccf5d58071b05b7687294f)

is for printer drivers for the 630

and this [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=21580&DSCCHK=ea245da3525f56d8ca2ab9408ed2d6d8b481d435](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=21580&DSCCHK=ea245da3525f56d8ca2ab9408ed2d6d8b481d435) for the scanner


Thank you **pdc** for your resopnse and suggestions.

Though I have only been using Linux for about 3 years now, I have learned a great deal about the OS and I really love this OS.  I *do* prefer to work through a problem myself if possible, however, sometimes I get hung up on that whole "*error on the side of caution*" thing.  :smile: 

I'll check out the links that you provided and work through the driver installations.  I will post back if there are any problems or questions.

Thanks again mate.

Patriot56

---

