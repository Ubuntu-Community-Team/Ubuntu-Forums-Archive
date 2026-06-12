---
title: "Scanning from Brother MFC-7860DW"
date: 2015-11-16
forum: Hardware
---

### Post by mblanco2000 on 2015-11-16
I installed Ubuntu 15.XX a while back.  This is my first run extensively with Ubuntu, and I must say it has gone great, and has been very easy.  I tried it years ago and found it a bit difficult, being familiar with Windows.  Anyway, when I first installed it I was able to get my printer/scanner Brother MFC-7860DW installed and working just fine.  I believe I had to do some Cups work and then identify the static IP address through the command line and everything worked great.  I was able to print and scan.  I recently had to change the ip address of the printer, due to a router upgrade.

Now I was able to go into the printer settings and change them and the printer works fine.  However, I can not get Simple Scan or Xsane to work.  I have tried unintalling the reinstalling Simple Scan and Xsane.  That did not work.

I have the printer installed as a network printer 192.168.1.3  What is the best way to get this scanner working.  Any help is greatly appreciated!!

---

### Post by gifford on 2015-11-16
I also have run into this problem when changing routers and IP addresses. 
See this link for your issue and how to correct. You must re-register the IP address for the scanner.
[http://ubuntuforums.org/showthread.php?t=2222027&p=13013698#post13013698](http://ubuntuforums.org/showthread.php?t=2222027&p=13013698#post13013698)

---

### Post by mblanco2000 on 2015-11-16
Gifford, thanks for the response.  I read your linked post, however could not re-register the IP address for the scanner specifically.  I tried running the command that is referenced in the post: (did not work for me)

mblanco@mblanco-MS-7680:~$ Brsaneconfig4 -a name=Scanner model=mfc-7860dw ip=192.168.1.3
Brsaneconfig4: command not found

Not sure what I am doing wrong here, but need a bit of help.  Thanks so much.

---

### Post by mblanco2000 on 2015-11-16
Got it, just had to run it in sudo.  Thanks for the help guys...

---

### Post by gifford on 2015-11-17
If the solution has worked, please mark the thread as solved.

---

### Post by mblanco2000 on 2015-11-17
Replying mobile not sure where the solved button is.

Solved....

---

### Post by Vladlenin5000 on 2015-11-18
Find the thread tools in your first post...

---

