---
title: "Lexmark Printers"
date: 2006-03-23
forum: Hardware &amp; Laptops
---

### Post by gymsmoke on 2006-03-23
I have an X6150 that I thought I'd give a shot to on my first Ubuntu install... Yak! I love Ubuntu - hate Lexmark.  Ubunut recognized the usb printer right off, and recommended the X125 driver... test page shows up, but never prints... I tried every swinging driver under Lexmark, with the same results.
I did try going through the archives here, installed the 600 driver (from the hoary forum), and got the same results...  I googled all over the place and only found the api on Lexmark's page (which doesn't work for anything other than 1 or 2 specific printers at this time)...

Before I just relegate this to someone else in the office who wants to run M$ (ARGH), if anyone has a suggestion, I'd love to hear it...  ](*,)

---

### Post by Mustard on 2006-03-23
I take it you have visited [http://linuxprinting.org/](http://linuxprinting.org/) already?  This is the first place I would recommend someone with a lexmark printer goes.

---

### Post by gymsmoke on 2006-03-23
yes, I did.  And linux print doesn't even know that the X6xxx series of printers exists.

---

### Post by Mustard on 2006-03-23
[QUOTE=gymsmoke]yes, I did.  And linux print doesn't even know that the X6xxx series of printers exists.[/QUOTE]

Yeah, I had a look over the website after I pasted the link to see what I could find and as you say, your series isn't even listed.

I googled up some reference to using the printer as a 'paperweight'. :rolleyes:

---

### Post by gymsmoke on 2006-03-24
hehe - another M$ peripheral bites it!

Not like i'm totally sorry to see it go... I was seriously relieved at dumping winBloze in the can and going to Ubuntu full bore... aside from some minor annoyances (printer, webcam/audio), and a bit of a learning curve, i'm so happy i don't know how to act...8) 

I've heard good results with HP printers, as well as Lexmark Optra's ...

---

### Post by Sef on 2006-03-24
Best printers to buy for Linux are either HP or Epson.  Still check Linuxprinting as a few of those are paperweights too.

I have an HP PSC 1650.  Overall works real well.

---

### Post by Studymore on 2006-03-24
I really am looking for a response to my problem.

I had a Lexmark installed- worked once printing the test page, never got it to work again.  So, I went out to buy an HP, updated all the necessary CUPS packages, and now:

Here are the error messages:

In the KDE Control Center (running as root.)
Peripherals -> Printers ->
Unable to retrieve the printer list. Error message received from manager:
Connection to CUPS server failed. Check that the CUPS server is correctly installed and running. Error:
connection refused.

> From there, we can hopelessly attempt to add a printer.  This will be unsuccessful, of course,

because it can not connect, but I want to show you the error message:

Add -> Add Printer/Class ->

An error occurred while retrieving the list of available backends:

Connection to CUPS server failed. Check that the CUPS server is correctly installed and running.

Then, we can go into the Add Printer Wizard, which (since a retrieval of the available backends was
unsuccessful) will be unfruitful.  Backend selection is empty because backends were not retrieved.

When we try to open localhost:631 in Konqueror, we receive this message:

An error occurred while loading [http://localhost:631/:](http://localhost:631/:)
Could not connect to host localhost (port 631).

Pinging localhost shows the same problem,
localhost:631 does not respond.

Both commands:
sudo /etc/init.d/cupsys restart    &
sudo /etc/rc2.d/S19cupsys restart
yield this response:
* Restarting Common Unix Printing System: cupsd                      [ ok ]

But,. when we run this command:
ps -Al | grep cupsd
We get no reply.

Cups is obviously not running, but Linux is lying to
me....  arrggghhhhh!!!!

---

