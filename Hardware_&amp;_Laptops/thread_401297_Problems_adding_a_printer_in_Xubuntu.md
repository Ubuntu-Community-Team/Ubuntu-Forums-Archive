---
title: "Problems adding a printer in Xubuntu"
date: 2007-04-04
forum: Hardware &amp; Laptops
---

### Post by theDentist on 2007-04-04
I'm going mad (well, more than usual:mad: ) trying to add a printer to my laptop Xubuntu installation,  I fired up the web browser and entered localhost:631 to get to Cups.  Going through the links to add a printer I found my printer - no problems there - but then I was stopped, it asked for my "Cups" username and password, or root username and password before I could continue.  Well, I created a root account just to be on the safe side (so I could log on in terminal with 'su'). Try as I could, it will not accept anything I throw at it my normal user name and password, or my root username and password( the passwords are the same by the way).  HELP anyone, what does it want for access!!!    :(

---

### Post by theDentist on 2007-04-04
After much looking, I found my own answer.  For all those in the same situation, To add a printer in Xubuntu, first your have to modify the shadow group in "Users and Groups". Select the "show all groups" option in the groups tab. Click on the group "shadow" and select it's properties.  Add "cupsys" to this group. You must then reactivate Cups with the following command:
      
                    $sudo /etc/init.d/cupsys restart

Then open a browser (firefox) and go to localhost:631. Click on Add a printer and follow the instructions.

It worked for me        :)

---

### Post by penman242 on 2007-04-06
Hi Doctor,

I am curious,  which version of xubuntu are you running?  I am about to pull out my hair trying to get my xubuntu to print.  I now have it printing pages from firefox, but it fails when trying to print a text document from mousepad with "client-error-bad-request".

When I go to Users and Groups I don't see a Groups tab or show all groups but there there is a Manage Groups button that brings up a long list, unfortunately Shadow is not in that list.

I am running xubuntu 704 beta on an i686 machine.  Are you running a different version?

Thanks, Steve

---

### Post by penman242 on 2007-04-06
I would like to throw this open to more discussion, and hopefully find a solution to my printing problem.  

I am using xubuntu feisty 7.0.4 on a pentium 4 1.6 with 768 mb ram and have an epson C84 printer.  I can print from firefox but not from mousepad.  I noticed the printer dialog boxes are different when printing from firefox as opposed to mousepad.  The printer dialog box that opens when I print a page from firefox says "print" at the top, while the one from mousepad says "xfprint".

I have tried the following: installed foomatic-db-gutenprint. then setup the printer using Applications -> Settings -> Printing, choosing foomatic:Epson-Stylus_C84-gutenprint-ijs.5.0.ppd.  This failed.

Then tried using firefox localhost:631 and choosing Epson Stylus C84 - CUPS+Gutenprint v5.0.0.99.1 (en).  this also failed.   The error message reads "client-error-bad-request".

Tried $ sudo chmod a+rw /dev/usblp0 and adding FileDevice Yes to /etc/cups/cupsd.conf followed by sudo /etc/init.d/cupsys restart as recommended here: [http://ubuntuforums.org/showthread.php?t=341777&highlight=feisty+epson](http://ubuntuforums.org/showthread.php?t=341777&highlight=feisty+epson)  Still no printing from mousepad.

Finally, I made sure my name was checked in lpadmin in Users and groups as recommended in the pdf version of Xubuntu Desktop Guide.  It was already checked, so I also tried installing and using gnome-cups-manager which is recommended as a last resort in that same document.  I am still getting the error message.

Does anyone know how to fix this?  Is this a 704 beta issue or a Xubuntu issue in general?  Thanks in advance for any advice.    steve

---

### Post by PhilJ on 2007-05-20
to print from mousepad install a2ps and log off and on
that worked for me 

Philj

---

