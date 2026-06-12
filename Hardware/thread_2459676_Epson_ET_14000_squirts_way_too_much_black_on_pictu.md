---
title: "Epson ET 14000 squirts way too much black on pictures"
date: 2021-03-23
forum: Hardware
---

### Post by ffrr on 2021-03-23
Hi all,
   I was very happy with my Epson ET14000 printer until one day it squirted way too much black on pictures and kept doing that. I took it to the Epson service rep and got it back in exchange of 400+ francs. The defect persits. So the printer may not be not be at fault at all, rather the software processing the printer's input from the image file. I understand that there are color profiles, drivers, etc. They work very much in the background, so I don't know what and where they are. Anyone out there having or having had a similar experience, or a hunch what's going on?

Frederic

```
OS: Ubuntu 18.04 LTS
Printer: EPSON ET-14000 Series
Driver:    Epson WorkForce 1100 - CUPS+Gutenprint v5.2.13 (color)
Connection:    usb://EPSON/ET-14000%20Series?serial=574B47593030313666

fr@hatchbox-2:~$ sudo apt-get -s install cups
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cups is already the newest version (2.2.7-1ubuntu2.8).
```

---

### Post by slickymaster on 2021-03-23
*Thread moved to **Hardware**.*

---

### Post by dbergst on 2021-03-24
Have you tried Epson's Linux driver?

[https://esupportepson.com/epson-ecotank-et-14000-driver-download/](https://esupportepson.com/epson-ecotank-et-14000-driver-download/)

---

### Post by ffrr on 2021-03-25
Thanks for the tip. The driver comes as rpm file only. Had to download and install 'alien' to convert rpm to deb. Here is what 'alien' said:
. . .
epson-inkjet-printer-201311w-1.0.1-1lsb3.2.src.rpm is for architecture i386 ; the package cannot be built on this system
    find epson-inkjet-printer-201311w-1.0.1 -type d -exec chmod 755 {} ;
    rm -rf epson-inkjet-printer-201311w-1.0.1

[https://esupportepson.com](https://esupportepson.com) offers no contact facility or information. Neither does [https://epson.com](https://epson.com). I'm expecting a return call from the service representative that did the repair job.

---

### Post by yancek on 2021-03-25
I'm a little confused by your post as it appears that this Epson printer has been working for you on Ubuntu for some time then suddenly started spraying black ink on the page, is that correct?  
After taking it to the Epson service representative, did it again work properly?
Why do you think that it is software rather than hardware?  If it had been working with whatever driver you had before I'm wondering why you would think you need a new driver?  It's more likely to be a hardware problem.  The software shouldn't change unless we're messing with configuration files.

>   epson-inkjet-printer-201311w-1.0.1-1lsb3.2.src.rpm is for architecture i386 ; the package cannot be built on this system

Doesn't seem to be the correct driver for your system.

---

### Post by ffrr on 2021-03-26
ynacek, thanks for your response. Yes, the case is most confusing. The printer worked fine after I installed an Epson driver for the top-of-the-line 'Workforce' printer from the Epson website. It would have been a Linux driver, although googling away I keep coming across the remark that Epson doesn't provide Linux drivers. Anyway, when the color balance went bad, from one day to the next, without an intervening occurrence suggesting a cause, I confronted a line of suspects: foremost the printer, but also software conveying image data from the disk to the printer, a formatting diver, tweaking color profiles, possibly some processing firmware in the printer . . . Logically I took the machine to the Epson service representative. They overhauled it and put in a new printing head. They certainly wouldn't return it without testing. So I thought the prime suspect was off the hook and started this thread. figuring, if the printer had a design-related deficiency, it would be notorious by now, and also hoping to elicit some advice on drivers, profiles, that sort of thing. I reiterate: the defect causes the printer to print black where it shouldn't, giving all colors a dull, obscure appearance. I am expecting a return call from the service rep without expecting much help. They don't use Linux and as Epson doesn't seem to serve Linux, they can argue that Linux users are on their own.

---

### Post by Autodave on 2021-03-26
Hook it up to a Win machine and see if it prints normally.

---

### Post by yancek on 2021-03-26
Is your EPSON ET-14000 Series recently purchased?  Is the driver you reference in post #4 above the same driver you originally used?  If you modified some configuration files, you might try restoring these files you modified from the original files you backed up.  

> They overhauled it and put in a new printing head. They certainly wouldn't return it without testing 

Did you ask why they put in a new printing head?  Maybe just a guess on their part?  I would certainly expect they would have tested it although how they did this is unknown, likely using a windows machine.  As suggested above, you might try printing from a windows machine if you can which would eliminate hardware problems.

---

### Post by ffrr on 2021-03-26
ynacek, thanks for your response. Yes, the case is most confusing. The printer worked fine after I installed an Epson driver for the top-of-the-line 'Workforce' printer from the Epson website. It would have been a Linux driver, although googling away I keep coming across the remark that Epson doesn't provide Linux drivers. Anyway, when the color balance went bad, from one day to the next, without an intervening occurrence suggesting a cause, I confronted a line of suspects: foremost the printer, but also software conveying image data from the disk to the printer, a formatting diver, tweaking color profiles, possibly some processing firmware in the printer . . . Logically I took the machine to the Epson service representative. They overhauled it and put in a new printing head. They certainly wouldn't return it without testing. So I thought the prime suspect was off the hook and started this thread. figuring, if the printer had a design-related deficiency, it would be notorious by now, and also hoping to elicit some advice on drivers, profiles, that sort of thing. I reiterate: the defect causes the printer to print black where it shouldn't, giving all colors a dull, obscure appearance. I am expecting a return call from the service rep without expecting much help. They don't use Linux and as Epson doesn't seem to serve Linux, they can argue that Linux users are on their own.

---

### Post by ffrr on 2021-03-26
Forget the post preceding this one. It's a replay of a previous one. I have no idea why it repeats. Anyway, thanks for the good idea to hook up a Windows machine. I'll have to borrow one, though. I shall report back, probably not today.

---

