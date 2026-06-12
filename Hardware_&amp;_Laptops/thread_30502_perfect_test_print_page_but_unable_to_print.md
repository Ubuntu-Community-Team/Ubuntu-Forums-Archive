---
title: "perfect test print page but unable to print"
date: 2005-04-28
forum: Hardware &amp; Laptops
---

### Post by jboyd on 2005-04-28
Hello folks,

My problem is this , I installed printer in the standard fashion through System>Administration>Printing. I did the test print and I got a perfect test print with the ubuntu symbol on top and rows of bars of different colours. However I am unable to print from other applications. The printhead moves and sounds as if it is printing but no print. 

The setup is as follows:

Ubuntu Hoary Hedgehog 5.04
Foomatic -db              20041203-1
Foomatic -db-engine  3.0.2-2
foomatic -db-hpijs      1.5-20041013-1
foomatic -filters          3.0.2-3 ubuntu1
foomatic -filters -ppds  20041013-1ubuntu
cupsys        1.1.23-1ubuntu12

Printer :
HP Deskjet 840c on the parallel port

800 Mhz computer Pentium 3 with 327mb ram

I have attached my error log ( i don't see any errors) ,my cupsd.conf,and my ppd file. 

i am really stumped. 


I am absolutlely new to this so please forgive any indiscretions in my posting.

Best regards,

john.

---

### Post by lukem on 2005-04-28
John
what applications have you tried to print from
and
does the printer feed paper when it is trying to print?

---

### Post by jboyd on 2005-04-29
Hello Lukem,

i am trying to print from Openoffice (1.1.3 I believe) the paper feeds, also the printhead moves and makes sound as if actually printing.

John.

---

### Post by lukem on 2005-04-29
I'm using warty right now so I can't look at hoary but there is a printer setup in open office also.  I recall that you need to set up your printer in that application also before it will print.  Give that a try if you haven't done so already.

---

### Post by jboyd on 2005-04-29
unfortunately, there seems to be no Oo Printer Administration in Hoary,

John.

i've got to go now so talk to you again tomorrow.

---

### Post by David Haas on 2005-04-29
John--Open Office 1.1.3 does have a Printer Settings GUI. I opened the Word Processor and went to File>Printer Settings. However, I don't know whether selecting you printer here will solve your problem. I recall that Open Office automatically listed my Epson printer when I installed it with the Printer set-up GUI.
David Haas

---

### Post by jboyd on 2005-04-29
Hello David,

You are right, under printer settings my printer was automatically detected as CUPS:Deskjet 840-C , however no change in situation.

John.

---

### Post by lukem on 2005-04-29
This may sound silly, but did your test page have any black on it?  On more than one occasion I have known someone (don't make me say who) who thought there was a printer problem when they were just out of black ink.  All those colors printed ok on the test page but I (oops) was only trying to print black from the word processor or spreadsheet.

---

### Post by jboyd on 2005-04-30
hello again Lukem,

Yeah there was black , I even saw another thread where a guy used spadadmin in a hidden folder (/home/.openoffice/spadadmin) , i tried it , again got a perfect test print page, but unable to print from any application.

john.

---

### Post by David Haas on 2005-05-01
John--I've had no experience with HP printers, but I see listed in foomatic these PPD files for the 840c: 
HP-DeskJet_840C-cdj550.ppd.gz
HP-DeskJet_840C-cdj670.ppd.gz
HP-DeskJet_840C-cdj880.ppd.gz
HP-DeskJet_840C-cdj970.ppd.gz
HP-DeskJet_840C-hpijs.ppd.gz
HP-DeskJet_840C-pcl3.ppd.gz
Which one did you select from the printer set up GUI? 
I also see that a PPD file for the 840 is listed in gimp-print/4.2:
 pcl-840.ppd.gz.
I wonder whether trying one of the other PPD files might work. 
I have found, with my Epson, that if a PPD file is mistakenly selected, then one should go through the printer selection beginning with "New Printer."
David

---

### Post by jboyd on 2005-05-01
Hello David,

To answer your question , I chose 840C-hpijs (as recommended by printer setup gui). However I absolutely needed to print so I have installed Fedora Core 3 , and its works perfectly. I plan on matching files between both distros to see if any clue will be yielded.

I initially installed Ubuntu on my desktop because it was the only distro that worked out of the box on my hp zv5346 laptop. I suspect that printing probably does not work on the laptop. 

Please forgive me if I do not get back to you in a timely fashion, but hopefully we will be able to solve this problem because I am partial to Ubuntu.

Best regards,

John.

---

### Post by albanmonk on 2008-01-12
Hi, I hope this is the right place to post this comment...

I have the same issue with my HP lj 4l.  It's installed ok, the initial test page came out perfectly.  now, anything I try to print (openoffice, firefox, another test page) prints a header on p1 then reems of blank pages!

The header says:

%!PS-Adobe-3.0
                    %%creator: (openoffice.org 2.3)
                                    %%for: (mike)
                                             %%creationDate: (sat

That's it.....  I'm new, but learning fast.  Any ideas?

Oh, I'm using Kubuntu 3.5.8

Thanks in advance

---

