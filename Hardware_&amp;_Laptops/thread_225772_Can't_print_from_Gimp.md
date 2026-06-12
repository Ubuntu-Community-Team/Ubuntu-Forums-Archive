---
title: "Can't print from Gimp"
date: 2006-07-30
forum: Hardware &amp; Laptops
---

### Post by pinkunicorn on 2006-07-30
I installed an HP Photosmart 3210 printer a while ago (via Ethernet), and it has been working nicely when printing from Mozilla, etc. Now I want to print from Gimp, and nothing works.

In the printing dialog for Gimp, I can't select my existing printer from Gnome. Instead there is a "New printer" button. If I click this to try to add the same printer again, the list of printers to choose from is different from the one that Gnome gives me (and the Photosmart 3200 series is gone).

If I try to print using the default setting of "(Default printer)", I get "lp: Error - no standard target available". 

Why can't Gimp just use the printer definition that all other Gnome programs use?

---

### Post by pinkunicorn on 2006-08-25
I still haven't been able to make this work. Any suggestions?

---

### Post by zxee on 2006-08-26
Do you have gimp-print installed?
I'm not totally positive about the name but I think you need that to print from gimp. Note: I did a search and that's the correct name [http://sourceforge.net/projects/gimp-print/](http://sourceforge.net/projects/gimp-print/) . It should be in the repos-but if apt or synaptic tell you that you already have the latest version installed try to go through the printer admin program and select gimp-print. It shouldn't take these gyrations to print from gimp-but if memory serves me sometimes-depending on the printer-it does. Hope that helps.

---

### Post by Matze on 2006-09-05
Hi there,
have you solved your problem?
I've the same here...My printer works perfectly out of gnome but isn't in the printer list from gimp :-(

---

### Post by HeyGabe on 2006-09-10
I, too, have this problem. Help would be helpful.

---

### Post by LotsOfPhil on 2006-09-30
Try going to System ---> Administration ---> Printing
Right click on the printer you want to use and select "Make Default."

---

### Post by pgilmon on 2006-11-15
That worked for me! :)

---

### Post by motin on 2007-06-25
It sure is a mystery why GIMP alone uses a separate printing system...

Workaround: When you are in the GIMP print dialogue, choose Setup printer and choose the File option. This will produce a postscript file of whatever you are printing, which you can double-click and then print to the real printer using the usual printing system. 

Hint: You can also use the tool ps2pdf to convert the "printed" file to a PDF document.

---

