---
title: "[SOLVED] Need network-printer help, HP DeskJet 810C"
date: 2008-10-24
forum: General Help
---

### Post by boof1988 on 2008-10-24
I have a printer connected to Computer #1 and want to use it as a network printer for Computer #2.

Computer #1:
    -HP DeskJet 810C plugged into parallel port
    -Desktop computer AMD64 processor
    -OS:  Ubuntu 8.04.1 for AMD64
    -Wired connection to home network
    -Share and publish printer options are checked

Computer #2:
    -Notebook computer
    -OS:  Ubuntu 8.04.1
    -Wireless connection to home network

I have tried using the following procedure (even though it's for Ubuntu 7.10):

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

Also tried using "System > Administration > Printing" and it doesn't detect the printer.

Here is some of the output when I type 'lpinfo -v' in Terminal [COLOR="Blue"]*of Computer #1*[/COLOR]:
[INDENT]network socket://192.168.2.3
direct parallel:/dev/lp0
direct hp:/par/DESKJET_810C?device=/dev/parport0[/INDENT]

I've learned how to use the CUPS (web-page-based) interface to look at printer stuff and I've installed the 'HPLIP Toolbox'.

Please help this noob.  :confused:

:guitar:

---

### Post by oldsoundguy on 2008-10-24
this may sound like a really dumb question, but is the desktop TURNED ON when you are trying to access the printer .. reason I ask is that I went around and around for several days with an individual that had the computer turned off .. they had just turned on the printer!  They could not figure out why it would not print and they blamed my network install!
(but they were Windows users and the printer was hooked up to a Windows box.)

---

### Post by boof1988 on 2008-10-24
> **oldsoundguy said:**
> this may sound like a really dumb question, but is the desktop TURNED ON when you are trying to access the printer .. reason I ask is that I went around and around for several days with an individual that had the computer turned off .. they had just turned on the printer!  They could not figure out why it would not print and they blamed my network install!
(but they were Windows users and the printer was hooked up to a Windows box.)

Thanks for the reply oldsoundguy,

I'm not offended by the question.:)

The computer is on and so is the printer.

FYI:  I just recently installed Linux on both computers (dual booting).  Eventually I hope to have Linux only.  I'm new to Linux (I was afraid to transition) so I need all the help I can get.

---

### Post by oldsoundguy on 2008-10-24
> **boof1988 said:**
> also tried using "System > Administration > Printing" and it doesn't detect the printer.

Please help this noob.  :confused:

:guitar:

Make sure you select new printer on this page.
You may have to manually enter the URI of the printer .. I did for one of mine.  You can get that from the desktop unit by taking the same path on it and the URI will be in the pop up box.

And we all were noob's once and we all were confused once!

---

### Post by confused57 on 2008-10-25
> **boof1988 said:**
> Thanks for the reply oldsoundguy,

I'm not offended by the question.:)

The computer is on and so is the printer.

FYI:  I just recently installed Linux on both computers (dual booting).  Eventually I hope to have Linux only.  I'm new to Linux (I was afraid to transition) so I need all the help I can get.

I also have an HP DESKJET_810C and was able to set up printer sharing between different computers, using this guide:
[http://www.funnestra.org/ubuntu/hardy/#ufw](http://www.funnestra.org/ubuntu/hardy/#ufw)

---

### Post by boof1988 on 2008-10-25
> **confused57 said:**
> I also have an HP DESKJET_810C and was able to set up printer sharing between different computers, using this guide:
[http://www.funnestra.org/ubuntu/hardy/#ufw](http://www.funnestra.org/ubuntu/hardy/#ufw)

Thanks for the link.  I'll try it and see.

:)

---

### Post by confused57 on 2008-10-25
Good timing, just logged in myself & noticed the above section from the linked site is just for firewall setup, here's printer sharing(if you haven't already found it):
[http://www.funnestra.org/ubuntu/hardy/#ipp](http://www.funnestra.org/ubuntu/hardy/#ipp)

I tried setting up printer sharing last night after reading your thread, since I had the same 2000 vintage printer...it was relatively easy to set up sharing in both Ubuntu 8.04 and Windows XP on a  dual boot computer to the Ubuntu computer with the physically connected printer.

In the URI section of the client pc, here's what I had to enter:
```
http://<ip address server pc>:631/printers/DESKJET_810C
```
for both Ubuntu and XP.

---

### Post by boof1988 on 2008-10-25
> **oldsoundguy said:**
> Make sure you select new printer on this page.
You may have to manually enter the URI of the printer .. I did for one of mine.  You can get that from the desktop unit by taking the same path on it and the URI will be in the pop up box.

And we all were noob's once and we all were confused once!

Thanks oldsoundguy,

I did click on the 'New Printer'.  The main problem I have is that I don't understand (yet) what's going on with the different settings, numbers, ports, 'IP' this, 'host' that etc.  Often, I don't understand what the different terms mean.  Need to take a little time to learn how to perform more action in the terminal. This might help me understand what is going on better.:?

I did have to manually enter the URI.  Tried several different ways and I probably (inadvertently) ignored/changed something different each time.

:???:

---

### Post by boof1988 on 2008-10-25
> **confused57 said:**
> Good timing, just logged in myself & noticed the above section from the linked site is just for firewall setup, here's printer sharing(if you haven't already found it):
[http://www.funnestra.org/ubuntu/hardy/#ipp](http://www.funnestra.org/ubuntu/hardy/#ipp)

I tried setting up printer sharing last night after reading your thread, since I had the same 2000 vintage printer...it was relatively easy to set up sharing in both Ubuntu 8.04 and Windows XP on a  dual boot computer to the Ubuntu computer with the physically connected printer.

In the URI section of the client pc, here's what I had to enter:
```
http://<ip address server pc>:631/printers/DESKJET_810C
```
for both Ubuntu and XP.

Many thanks to you, confused57,

I now can print from Ubuntu box to a Ubuntu box.  Two new tasks for me are:
[INDENT]-Set up network printing from/to Windows XP
-Set up file sharing[/INDENT]

Noticed that it was a link for the firewall settings.  I want to take a little time and try to understand how to change the settings/rules etc.

I'm really happy with how clear the instructions are.  Could still be improved just a tiny bit.  Think I might try to send a thank-you to the author.

I think there is a file-sharing method at the link you gave so I'll try it first.

Thanks Again

---

### Post by confused57 on 2008-10-25
Good to hear you were able to get printer sharing to work between
computers...I agree the instructions on the linked site were easy to follow, easy to set up, and just plain worked.  I use the Ubuntu machine 95% of the time, but there are occasions that I need to print from the other Ubuntu/Windows computer...thanks for the incentive for me to give it a try.  

You might want to look into ssh networking for file sharing:
[http://users.bigpond.net.au/hermanzone/p11.htm](http://users.bigpond.net.au/hermanzone/p11.htm)

---

### Post by boof1988 on 2008-10-26
> **confused57 said:**
> Good to hear you were able to get printer sharing to work between
computers...I agree the instructions on the linked site were easy to follow, easy to set up, and just plain worked.  I use the Ubuntu machine 95% of the time, but there are occasions that I need to print from the other Ubuntu/Windows computer...thanks for the incentive for me to give it a try.  

You might want to look into ssh networking for file sharing:
[http://users.bigpond.net.au/hermanzone/p11.htm](http://users.bigpond.net.au/hermanzone/p11.htm)

Thanks for the link.  I can now access files from each computer to the other.

My next (somewhat longer) challenge is to learn how to use command input more effectively.  Here's a link for anyone interested.

[https://help.ubuntu.com/community/CommandlineHowto](https://help.ubuntu.com/community/CommandlineHowto)

---

