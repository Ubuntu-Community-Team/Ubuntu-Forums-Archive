---
title: "Can't print after updates?"
date: 2010-01-14
forum: Hardware
---

### Post by kuchi36 on 2010-01-14
I am pretty new to Ubuntu and am currently running 9.10 for a couple months now. A couple of weeks ago my system downloaded a set of updates and since then my printer (PSC 1510) HP has not been working. I was running the hplip prior and my printer is connected via USB.
This is my only printer in my house and my son has some school work he needs printed.

Can anyone give me a place to start?

When I go into printer properties it is listed as my default. When I try and print a test page...nothing. It does not have any "location" listed on the dialog box. When I try and check toner levels (which I could do several weeks ago just fine) I get this error msg. 

There was an error during the CUPS operation: 'client-error-document-format-not-supported'.

Thanks,

T.

---

### Post by garvinrick4 on 2010-01-14
First try add new printer then add your printer and its driver and select it as default printer and see if that works before you do anything else. If it works delete the first printer.

---

### Post by kuchi36 on 2010-01-16
Tried that, still no luck...


What's next.

From the research I have done, it sounds like a USB problem/issue.

Tim

---

### Post by kuchi36 on 2010-01-16
Can anyone help me figure out if my USB connection is working properly?

Thanks,

Tim

---

### Post by PRC09 on 2010-01-16
Not sure if it is a usb problem but there might be some ideas here.I also had some problems with my usb printer after updates.I re-installed hplip and re-setup the printer and that solved it for me....

[http://ubuntuforums.org/showthread.php?t=1378950](http://ubuntuforums.org/showthread.php?t=1378950)

---

### Post by kuchi36 on 2010-01-18
installed new HPLIP. Still can't print at all. The computer does not appear to recognize that I have a printer, even though I have it "installed" and listed as the default.

???

Tim

---

### Post by PRC09 on 2010-01-18
Sorry,been out of town all day. My Google search for the error you mentioned showed that there was problems with CUPS and Ghostscript so maybe a re-installation of those would solve it.The link for troubleshooting is:

[https://wiki.ubuntu.com/DebuggingPrintingProblems#USB%20printer](https://wiki.ubuntu.com/DebuggingPrintingProblems#USB%20printer)

Hope this will help...

---

### Post by kuchi36 on 2010-01-18
THANK YOU

THANK YOU

THANK YOU!


All is well in the world again and I just printed out my son's report which is due on Tuesday.

Cheers,

Tim:D

---

