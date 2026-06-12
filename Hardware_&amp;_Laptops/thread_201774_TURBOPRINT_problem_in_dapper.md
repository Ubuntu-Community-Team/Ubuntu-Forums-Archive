---
title: "TURBOPRINT problem in dapper"
date: 2006-06-22
forum: Hardware &amp; Laptops
---

### Post by dgrafix on 2006-06-22
Since i upgraded to dapper cannot get turboprint to work for cannon mp360
It says tp0 not accepting jobs.

There is a list of devs to stick it on the default is something like:
usb://Canon/MP360%20Series
Is this a valid hardware/device name?

however when i unplug/plugin printer i see a result on /dev/usblp0
so i assume its this i need

still no joy.

Installing this on breezy was smooth and worked first time



EDIT:

Ive gone into the Cups web setting on localhost(CUPS WEB browser administration)
and notice accept jobs is there in green. Trouble is to activate it i need a username and password?!?

Ive no idea what its asking for as there is no root in Ubuntu

---

### Post by Blue1k on 2006-06-28
I have an MP370 Canon and it stopped printing as well. You need to upgrade to the newest
Turborpint (you can use your old key for activiation)

HOWEVER, printing any doc or odf file with pictures (jpg, png etc) inserted results in very poor printing with the pictures barely visible.

I have asked numerous sites and even here and still have not got a response for this. Fedora 5 uses the same version of CUPS and I have had NO problem printing the same file using the newest turboprint. Obviously there is a problem in Ubuntu that has not been addressed.

Sucks that I had to dump Ubuntu because of this. :(

---

### Post by patrickfromspain on 2006-06-29
How did you add the printer? Try it the following way: turn on the printer, go into System  -> Administration -> Printers. There choose add a printer, and you printer should list under "Use a detected printer" choose it, and go fordward. When you have to select the model, search for Canon Turboprint and choose your printer. You should have no problems. If you do have problems, go to [www.cups.org](www.cups.org) and download and install cups 1.2.1. I had to do that to make the turboprint drivers work fine with my IP3000.

---

### Post by Blue1k on 2006-06-30
Ya the problem was that when I choose my printer through the Print Manager that Turboprint drivers were not listed even after setting up a printer through the turboprint interface.

I'mm reluctant to try again as I have wasted so much time on this and gotten no where :(

---

### Post by patrickfromspain on 2006-07-01
that's strange... are you sure you installed turborprint fine? (being root and all that..). I did install turboprint, and just after finishing my install, I went to the gnome cups manager, and added my printer with the Canon Turboprint drivers.. They were there. I'd say try again...

---

### Post by phibuntu on 2006-07-09
Same Problem with Epson Stylus Photo R300.
Prints fine using Breezy.
I upgraded to Dapper.

Installing the printer under Dapper leads to "lp: Destination xyz is not accepting jobs", where
xyz is the short description of my printer driver.

Using "xtpsetup" I can choose the driver (ID 142: Epson Stylus Photo R300) but the printer is "not accepting jobs".
Using "add new Printer" from the System menu I see the Printer and go "forward", but the Printer Driver List is empty.
So: both ways to install the printer driver fail.

Do I have to install additional drivers?
Is this a well known problem in dapper?
How can I "downgrade" the printer system to breezy? (Or how to downgrade the whole system?)

Every hint is wellcome.

---

### Post by phibuntu on 2006-07-12
Problem solved for me

**1st** hint from german ubuntu forum

(call as super user):
>    >cupsenable tp0
   >cupsaccept tp0

so I got rid of the "tp0 is not accepting jobs." message. But the printer was still not printing (it paused itself after a few seconds).

**2nd** hint came from the Turboprint seller itself:
upgrade turboprint to verion 1.94-4, which solves problems using ubuntu 6.06.
I upgraded to the newest cups-drivers (using synaptic), which is probably not necessary, but ...


... now it works for me using D*E*LL INSPIRON 9300 and Epson Stylus Photo R300. :)

---

### Post by Blue1k on 2006-07-27
Well after wanting to try Ubuntu again I am stuck with the same garbage.:-x 

IT STILL WILL NOT PRINT ANY embedded jps, png, or gif files from openoffice.

I am so frustruated at this point after wasting 3 hours tweaking this system to still have this problem.

Cups is updated to current as far as I can tell. So is turboprint

This is a home work station so if you can help then MUCH APPRECIATED as I need to print ASAP :D

---

### Post by Blue1k on 2006-07-27
No takers?

This problem only has occured with Dapper and hasn't happened in other Linux distro. I wish I could fix the problem myself but this is beyond my abilities.

Basically, the page is printed with normal text but very light or non-existant pictures that are part of the document. Normal text is printed perfect.

The print manager sees the printer and correctly identifies the drivers as turboprint driver for my model (MP370).  Weird?!!

I am using Suse right now (took me 1.5 hours to install) but I really would like to go back to Ubuntu.

Thanks!!

---

### Post by Blue1k on 2006-07-28
Help!! :-( 

...thanks in advance

---

### Post by Blue1k on 2006-07-31
Help!!...

Thanks again :)

---

### Post by Blue1k on 2006-08-02
Ok it's obvious no one can help me. 

So, is it possible to downgrade cups in Dapper?

I still can't figure out why the printing sucks for my computer in Dapper (stellar with Breezy)

---

### Post by Blue1k on 2006-08-02
I hate to be a bother but I am suprised by the lack of help.

Man, usually I find someone on here who can help lickity split.

Again, thanks in advance

---

### Post by Blue1k on 2006-08-04
Wow...I must be invisible..

Ok...how do I downgrade cups??? Seriously...I love Ubuntu too much to settle for something else but I really need some help.

---

### Post by Breepee on 2007-04-24
Was this fixed in Feisty?

---

