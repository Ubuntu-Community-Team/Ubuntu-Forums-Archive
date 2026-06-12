---
title: "trouble connecting Brother HL2280DW in 12.04"
date: 2013-08-09
forum: Hardware
---

### Post by john40 on 2013-08-09
Hi, I'm very new to this.

I recently got a ZaReason Ultralap 430, preloaded with Ubuntu 12.04. One thing I'm having trouble with is getting my Brother HL-2280DW printer/scanner to work well. I have tried setting it up a bunch of different ways, including following the instructions [here]("http://ubuntuforums.org/showthread.php?t=590793"), [here]("http://reformedmusings.wordpress.com/2013/01/26/setting-up-a-brother-hl-2280dw-in-ubuntu-12-10/"), on the company page [here]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html"), and also installing the thing Windows-style using the Printing application, and while the computer always recognizes the printer and sometimes gets it to print a test page, I've not been able to print from programs like LibreOffiice (well, maybe I got a page to print from there once). Each time, when I look at the printer in localhost, its status is something like 'Processing - "The printer is not responding."' Yet I don't seem to be getting any error messages during the install itself.

Help?

(Again, I am quite new to this, so directions may need to be painstakingly elementary.)

Thanks.

---

### Post by dominik2 on 2013-08-09
did you use a PPD file?

---

### Post by john40 on 2013-08-09
I don't believe that there is a PPD file for this model; see [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/evaluation.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/evaluation.html). Instead it uses lpr driver and cupswrapper driver.

Bizarrely, though, just now when I turned my laptop back on the printer sprang to life and printed out a page that I had sent to it hours ago from LibreOffice; and then it printed out another page that I sent as a test. So maybe it is working? I will update if this changes.

---

### Post by john40 on 2013-08-09
Update: I just sent the printer a six-page file from Document Viewer, and it didn't print, displaying the status as "Processing -- Not Connected?" But then after I restarted the computer, the file printed just fine.

Any idea what is going on here?

---

