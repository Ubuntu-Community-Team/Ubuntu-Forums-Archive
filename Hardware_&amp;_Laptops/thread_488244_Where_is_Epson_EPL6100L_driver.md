---
title: "Where is Epson EPL6100L driver?"
date: 2007-06-29
forum: Hardware &amp; Laptops
---

### Post by hounddog on 2007-06-29
Hi everyone,

                  I'm new to linux.  I have heard of it before and always wanted to try it.  I wanted to do some web-development and having heard that most web-servers these days run on linux computers I purchased a new computer just so I can run linux on it.  I have heard that Ubuntu is the best linux distribution out at the moment and the first time I used it I was very impressed.  The graphics were great, everything seemed to work well except for one thing ... I can't get my printer to work.  My printer is an Epson EPL6100L and the driver is not included with Ubuntu.  I have tried installing the one from the linuxprinting site and it doesn't seem to work with Ubuntu.  I read read the other posts on this site with the same problem with this printer but none of them seem to be solved.  Can I just ask for the printer to be supported?  It prints fine under PCLinuxos2007 but I really want to use Ubuntu.

Can anyone help me?  

Thanks.

---

### Post by joe.turion64x2 on 2007-06-29
> **hounddog said:**
> Hi everyone,

                  I'm new to linux.  I have heard of it before and always wanted to try it.  I wanted to do some web-development and having heard that most web-servers these days run on linux computers I purchased a new computer just so I can run linux on it.  I have heard that Ubuntu is the best linux distribution out at the moment and the first time I used it I was very impressed.  The graphics were great, everything seemed to work well except for one thing ... I can't get my printer to work.  My printer is an Epson EPL6100L and the driver is not included with Ubuntu.  I have tried installing the one from the linuxprinting site and it doesn't seem to work with Ubuntu.  I read read the other posts on this site with the same problem with this printer but none of them seem to be solved.  Can I just ask for the printer to be supported?  It prints fine under PCLinuxos2007 but I really want to use Ubuntu.

Can anyone help me?  

Thanks.
Have you tried gutenprint? It is available through Synaptic.

---

### Post by hounddog on 2007-06-30
Thanks for your suggestion.  I went to Synaptic Package Manager in System/Administration and installed all the gutenprint packages but they were not helpful at all.  The foomatic-db-gutenprint was already installed and the other packages don't have the EPL6100L driver either.  It is no where to be found.  I am sad to say I am still without printer support.  

Do you have any more suggestions?  I really appreciate your help.

---

### Post by joe.turion64x2 on 2007-06-30
> **hounddog said:**
> Thanks for your suggestion.  I went to Synaptic Package Manager in System/Administration and installed all the gutenprint packages but they were not helpful at all.  The foomatic-db-gutenprint was already installed and the other packages don't have the EPL6100L driver either.  It is no where to be found.  I am sad to say I am still without printer support.  

Do you have any more suggestions?  I really appreciate your help.
Is your printer a brand new model? Perhaps you should wait a little bit to get it supported in gutenprint.

---

### Post by joe.turion64x2 on 2007-06-30
Try this [http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-EPL-6100L](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-EPL-6100L)

---

### Post by hounddog on 2007-07-01
It is not a new model ... I bought it 4 years ago.  It still runs very well and I still have an extra toner cartridge for it.  I have installed that linuxprinting driver previously and configured that driver for my printer but it didn't work. My printer still couldn't print.  In addition, after automatic upgrade, the foomatic database was updated and that driver then disappeared from the list and I couldn't even select it anymore.  That's why I'm here looking for help.  As I said before, for some reason I can use my printer in PCLinuxos2007 but not in Ubuntu.  I really would like to be able to print in Ubuntu.

I wish someone can solve my problem.

Edit: Printing error.

---

### Post by joe.turion64x2 on 2007-07-01
> **hounddog said:**
> It is not a new model ... I bought it 4 years ago.  It still runs very well and I still have an extra toner cartridge for it.  I have installed that linuxprinting driver previously and configured that driver for my printer but it didn't work. My printer still couldn't print.  In addition, after automatic upgrade, the foomatic database was updated and that driver then disappeared from the list and I couldn't even select it anymore.  That's why I'm here looking for help.  As I said before, for some reason I can use my printer in PCLinuxos2007 but not in Ubuntu.  I really would like to be able to print in Ubuntu.

I wish someone can solve my problem.

Edit: Printing error.
If PCLinuxOs 2007 could do it, it would detect your kitchen's sink. Have you tried GNOME under PCLinuxOS? It can be easily installed through Synaptic, and is the fastest thing. Perhaps you should try it, that is very similar to Ubuntu.

---

### Post by hounddog on 2007-07-03
Thanks.  Hmmm ... not sure if that was the solution I was looking for.  PCLinuxos actually already has a Gnome version for download so I don't have to install Gnome through Synaptic ... which can be quite troublesome.  Anyway, I was hoping to use Ubuntu because the look and feel of Ubuntu is just so much nicer.  But alas, Ubuntu does not come with EPL6100L support.  I'm just very sad that it has turned out this way ... :cry: ... I hope you guys can correct this in the upcoming versions.

---

### Post by joe.turion64x2 on 2007-07-03
> **hounddog said:**
> Thanks.  Hmmm ... not sure if that was the solution I was looking for.  PCLinuxos actually already has a Gnome version for download so I don't have to install Gnome through Synaptic ... which can be quite troublesome.  Anyway, I was hoping to use Ubuntu because the look and feel of Ubuntu is just so much nicer.  But alas, Ubuntu does not come with EPL6100L support.  I'm just very sad that it has turned out this way ... :cry: ... I hope you guys can correct this in the upcoming versions.
It is good to know the thing is finally working for you. I know what you mean when you say you'd prefer to use Ubuntu, because I am in a similar case. My Epson Stylus CX3700's scanner (the printer works OK) refuses to work in Fedora Core 6 (or FC6 refuses to recognize it) and until this moment I have been forced to boot in Ubuntu 7.04 to take advantage of it (much better than booting in Windows). But once the scanning is done I go back to my familiar box.

Joe.

---

### Post by sooqing on 2007-09-29
been using ubuntu since 4.10 and sadly, I still cannot use my epl 6100L even though the driver is included with every version till gutsy...

---

### Post by hounddog on 2007-10-19
The included driver is actually the EPL-6100 driver and not the EPL-6100L driver.  Ubuntu Feisty and Gutsy both detected the printer as EPL-6100L but it could not load the driver because it just didn't come with either Feisty or Gutsy.  Makes me kind of disappointed.  Anyway, PClinuxOS is a superb distro and it comes with the EPL-6100L and prints off it very well.

---

