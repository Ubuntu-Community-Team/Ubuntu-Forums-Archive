---
title: "Belkin F5D8055 v2 Working!"
date: 2010-01-21
forum: Hardware
---

### Post by gannggstaz on 2010-01-21
I am not sure where to post this because it is just a solution, but I have been running ubuntu for a year now. I had to reinstall, and owned a belkin F5D8055 v2 wireless usb adapter. I could not get it to work, until I found this forum and fixed it up a little bit myself:
[http://www.backports.ubuntuforums.org/showthread.php?t=1353044](http://www.backports.ubuntuforums.org/showthread.php?t=1353044)
The change was a modification to step 5
> Step 5 

Code: 
gedit os/linux/usb_main_dev.c

and add the following line 

Code: 
{USB_DEVICE(0x1737,0x0077)}, /* Linksys WUSB54GC */

Save and close 

Under the line "Code:" change the numbers. Plug in your belkin f5d8055 v2 and type in lsusb. There it will say:
```
ID 050d:825b Belkin Components
```
Change the contents of the parentheses to:
```
{USB_DEVICE(0x050d,0x825b)}, /* Belkin F5D8055 v2 */
```
The part in the slashes is only a tag so you know what it is. Follow the rest of the instructions and you will have a working Belkin usb adapter :D

---

### Post by tvrtuscan on 2010-02-25
Hi, for the F5D8055v2 did you use the RT3070 driver or the 2870?  I'm still having no luck with the 2870 driver.  It installs the driver but just won't scan.  I've tried pretty much everything in loads of threads.

---

### Post by tvrtuscan on 2010-02-25
Answered my own question.  After days of trying with the 2870 driver I tried the 3070 and it worked.  Just wish there was somewhere in the tech spec of the 8055v2 which said it was a 3070

---

### Post by christ8 on 2010-04-28
> **tvrtuscan said:**
> Answered my own question.  After days of trying with the 2870 driver I tried the 3070 and it worked.  Just wish there was somewhere in the tech spec of the 8055v2 which said it was a 3070

I have the same problem, trying to install F5D8055 Ver2010 (I am guessing it is V2, I just bought it recently packaged with Belkin N+ router).  I downloaded 3070 from Ralink, but there is no list of {USB_DEV... to be found. 

Please share with me what you did.

OK. I got it working.

Thanks.

---

### Post by adcore on 2010-05-26
Cheers for posting this its still useful and working fine on a 10.04 lts 64bit installation. 
Didn't need steps 17 and 18 in my case first reboot got it working and configured.
Used procedure A to get it working.

---

### Post by Lucifer The Dark on 2010-06-06
I'm also on 64bit 10.04 but I'm stuck at step 10 as it's refusing to make the directory, any pointers on how I get past that would be appreciated.

---

### Post by chuchutta on 2010-07-29
i just did the latest update, now my card stopped working again. i tried to "make && make install" and it only makes it half way through the process. It doesn't show any errors or warnings. Anyone know of any fixes?

thank you!

chuchutta

---

### Post by alien8er on 2010-08-07
> **chuchutta said:**
> i just did the latest update, now my card stopped working again. i tried to "make && make install" and it only makes it half way through the process. It doesn't show any errors or warnings. Anyone know of any fixes?

thank you!

chuchutta

Did the latest update on 10.4 x64bit with the same result: no wireless device.
Went back and reapplied step 10 and 11, replacing the text ** 2.6.31-14-generic** with  **2.6.32-24-generic**. Did step 12 then rebooted. Wireless is now working again.

Thanks gannggstaz

---

