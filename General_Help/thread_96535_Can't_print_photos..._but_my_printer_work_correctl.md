---
title: "Can't print photos... but my printer work correctly!"
date: 2005-11-29
forum: General Help
---

### Post by indypende on 2005-11-29
I've configure correctly my printer and i can print everything i want:
webpages, documents... evrything!
now i'm trying to print some photo on a 4x6 photo paper and i see my print work appearing in the queue... then desappearing without reults!
I've try all the apps like gimp gthumb and others... no RESULTS!
my printer it's an hp deskjet 3420!
no one can help me please??
i've only ubuntu and i need the photos.......
thanks

---

### Post by indypende on 2005-12-01
please... i want only know if this is a printer problem or an ubuntu bug!
printer work correctly in hoary!
help

---

### Post by kairu0 on 2005-12-01
If I understand you correctly, the print job enters the print queue and then disappears without any error. Is that right?

Your printer does absolutely nothing when this happens?

---

### Post by Zimmer on 2005-12-01
I am investigating a similar occurence with the Gimp on an HP 930C. Tried to print from there today and it just kept feeding  paper..job stayed in the queue with no error message..
and printed one line of apparently random text . I have seen this problem a few years back over a network..can't remember the outcome..

I have used the printer previousy to print labels and images in OpenOffice and a map from the Internet.
Was in a hurry so I booted a XP box and printed from an Adobe app. (same printer.) Will post asap when I have fixed it.
OK..fixed ! The GUI for Gimp printing shows your current printer queue.(which is headed <Printer Name>).
That is it..just the name, underneath is a text line saying  <Printer model: PostScript Level 2>.
you need to click the button underneath marked <Setup Printer> to associate a model of printer with your Printer Name. You will get a list of Printer Models
The Printer Model: text will then display the Model printer  you have selected.
If you do not save the settings with the buttons at the bottom of the gui it will be back to square one when you next try and print....
Unfortunately, I don't see your model on the list.. A quote fom the help files:_
 Scroll through the Printer Model section of the window until you find a printer which matches yours. If you cannot find the precise model, pick something close and **_hope for the best_**. There are selections for a wide array of Postscript, inkjet, and laser printers. After you have selected a printer, you will see the printer command displayed.

Zimmer

---

