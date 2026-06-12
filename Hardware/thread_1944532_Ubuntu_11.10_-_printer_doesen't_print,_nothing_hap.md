---
title: "Ubuntu 11.10 - printer doesen't print, nothing happens when printing"
date: 2012-03-21
forum: Hardware
---

### Post by firekage on 2012-03-21
Hi.

I've recently switched from Slackware because i wanted to tray new Ubuntu and i'm with 11.10 so far.

I've got one problem. The problem is that i can't install hplip, also when printing with HP 2200d LJ nothing happens. 

I've posted similar thread on LinuxQuestions:

[http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-11-10-printer-doesent-print-nothing-happens-when-printing-934179/](http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-11-10-printer-doesent-print-nothing-happens-when-printing-934179/)

Can you help me?

I downloaded hplip, but when installer is working there is a problem:

 
 > Running 'sudo apt-get install --assume-yes python-qt4'                                 
can't download this.

Also with this:

 
>  warning: Qt/PyQt 4 initialization failed.
error: hp-systray requires Qt4 GUI and DBus support. Exiting.          
                       
Another is with plugging it printer - it's plugged, i enable re-plug in, nothing happens - printer setup looks like hangs up.

---

### Post by ajgreeny on 2012-03-21
How are you trying to install hplip?  You should be able to do it with command ```
sudo apt-get install hplip
```without a problem.

---

