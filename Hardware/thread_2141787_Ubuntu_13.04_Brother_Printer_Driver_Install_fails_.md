---
title: "Ubuntu 13.04 Brother Printer Driver Install fails with &quot;Unknown Job: lpd&quot;"
date: 2013-05-03
forum: Hardware
---

### Post by LarryMcMains on 2013-05-03
I'm trying to install the Brother Printer driver for an MFC-J825DW printer using Brother's instructions. I'm probably pushing the envelope because Brother says they've only tested through 12.04 LTS, but I really hope this can be made to work because I had to go to 13.04 in order to install on a new Toshiba notebook.

The error when I start the install is:
*larry@Satellite-S855:~/Downloads$ sudo dpkg -i --force-all mfcj825dwlpr-3.0.0-1.i386.deb*
*Selecting previously unselected package mfcj825dwlpr.*
*(Reading database ... 190630 files and directories currently installed.)*
*Unpacking mfcj825dwlpr (from mfcj825dwlpr-3.0.0-1.i386.deb) ...*
*Setting up mfcj825dwlpr (3.0.0-1) ...*
*initctl: Unknown job: lpd*

I believe I have satisfied the Brother "Pre-required Procedures". The only anomalies I've noted are


[LIST=1]
[*]ia32-libs _or_ lib32stdc++ are supposed to be installed. I have the former, can't successfully install the latter.
[*]For Debian distributions after Ubuntu 8.10, they require symbolic link /etc/init.d/lpd -> /etc/init.d/cups. I created the link but noted that on my old 10.04 system, /etc/init.d/cups is a shell script, but on 13.04 it is a link to /lib/init/upstart-job. After the failure above, I tried removing the /etc/init.d/lpd link and recreating it to point directly to /lib/init/upstart-job but this had no effect on the problem, so I've changed it back to point to /etc/init.d/cups again. The two scripts (cups and upstart-job) are very different, FWIW.
[/LIST]
Any ideas on how I might get around this?

Larry

---

### Post by gifford on 2013-05-03
The symbolic link is not needed when installing this printer. Your printer is not listed for this as a pre-required procedure. 
Is the connection to be USB or network?
I assume you that you are using 13.04 AMD64?

---

### Post by LarryMcMains on 2013-05-03
Good grief! You're right, of course, the symbolic link is not called for. I remembered having to do this for a previous printer a couple years ago and just concluded that it was needed. I removed the symbolic link that I had created and the install steps ran without a hitch - and so fast that I was sure something else was wrong, but all appears to be well. I just successfully printed a test page via printer properties and a web page via Chromium. I can't believe how much time I spent trying to solve a problem caused by inserting an unneeded step. Thank you very much for your help!

---

### Post by gifford on 2013-05-04
Glad it worked so easily!

---

