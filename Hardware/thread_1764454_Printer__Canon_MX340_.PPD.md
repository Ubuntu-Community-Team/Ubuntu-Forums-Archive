---
title: "Printer:  Canon MX340 .PPD"
date: 2011-05-21
forum: Hardware
---

### Post by corrytonapple on 2011-05-21
I have been trying to set up wireless printing on the MX340 for three hours now.  I am come to the conclusion I need the .ppd, since my printer is not in the list of the installed Ubuntu 11.04 software.  After trying to unpack the .deb and not seeing it, and Googling with no one seeming to have it, I come to ask you guys.
Thanks in Advanced.

---

### Post by corrytonapple on 2011-05-24
Bump.  I am sure that someone knows where to get it or has one....

---

### Post by demonipuch on 2011-05-25
Hello

The .ppd file you're looking for should be in /usr/share/ppd

---

### Post by corrytonapple on 2011-05-25
Thanks, it was there.  I Owe you one :D

---

### Post by Roasted on 2011-06-05
Hey question for you guys. I just got my Canon MX340 running by using the .deb's I found on Canon's site. I found the link on Google, however when I searched Canon's site directly I did not find Linux drivers. Nonetheless, I got them off the Google link. Okay, fine. 

By doing that, does that put the .ppd files in /usr/share/ppd? Prior to me installing those .deb's, is it likely the .ppd files were not there in /usr/share/ppd? 

More or less, while my issue is resolved, I'm trying to learn about how printer out-of-the-box support with Linux differs from additional drivers, as I've *never* had to install additional drivers until now. Thanks!

---

### Post by demonipuch on 2011-06-05
> **Roasted said:**
> Hey question for you guys. I just got my Canon MX340 running by using the .deb's I found on Canon's site. I found the link on Google, however when I searched Canon's site directly I did not find Linux drivers. Nonetheless, I got them off the Google link. Okay, fine. 

By doing that, does that put the .ppd files in /usr/share/ppd? Prior to me installing those .deb's, is it likely the .ppd files were not there in /usr/share/ppd? 

More or less, while my issue is resolved, I'm trying to learn about how printer out-of-the-box support with Linux differs from additional drivers, as I've *never* had to install additional drivers until now. Thanks!

yep canonmx340.ppd is copied during deb's installation

---

### Post by Roasted on 2011-06-05
> **demonipuch said:**
> yep canonmx340.ppd is copied during deb's installation

Is the .ppd kind of like a "driver file" like a .inf for Windows?

Also, is there a location to download the direct .ppd, or is that entirely dependent upon the manufacturer?

---

