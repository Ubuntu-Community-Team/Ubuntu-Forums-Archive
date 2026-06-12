---
title: "Curious printing behavior - wants to &quot;save&quot; instead of &quot;print.&quot;"
date: 2023-01-06
forum: Hardware
---

### Post by jonfisher on 2023-01-06
Curious printing behavior - wants to "save" (as a pdf) instead of "print."

So I end up saving the requested printing job to the desktop, then if I open the file it will allow me to print then...

?

---

### Post by ajgreeny on 2023-01-07
Printing what sort of file and from which application, or is it all print jobs?

How do you start the print process, using ***Ctrl+P*** or ***File - Print***?
The dialogue that you see will normally show the options

Print to file
or
Printer name 

You need to choose the printer,  not Print to file.

---

### Post by jonfisher on 2023-01-08
It doesn't happen all the time, but much of the time when I choose CTRL+P to print most any document....

---

### Post by jonfisher on 2023-01-08
As I just did a CTRL+P and got it again

---

### Post by ajgreeny on 2023-01-08
If you look top right you will see that it is set to print to PDF, or saving as a PDF,  as I suspected.

Click on that drop-down box and you should see your real printer as an option which you can choose and then print to paper as you want.

---

### Post by jonfisher on 2023-01-12
Clicking that only gives me the option to save a PDF - no option to print.

see attached screenshot

Now, if I save it to desktop then open it from desktop and do a CTRl+p AGAIN, IT will let me print that time

?

---

### Post by ajgreeny on 2023-01-13
It sounds as if your printer goes off sometimes and is not woken up when needed.  

What printer do you have, how is it connected and is it listed if you go ***Printers*** in your settings or if you use the CUPS webman page at ***localhost:631*** in a web browser?

---

### Post by jonfisher on 2023-01-15
> **ajgreeny said:**
> It sounds as if your printer goes off sometimes and is not woken up when needed.  

What printer do you have, how is it connected and is it listed if you go ***Printers*** in your settings or if you use the CUPS webman page at ***localhost:631*** in a web browser?

Hmm, I've used this same printer for many years - HP LaserJet Pro MFP M127fn

---

### Post by jonfisher on 2023-01-15
My printer is connected USB.
Like I said, if I save it to desktop, then do *another* Ctrl-P it will print with ease  -  ?

p.s. tell me how to get to cups with the browser and what to look for

---

### Post by ajgreeny on 2023-01-16
In the address-bar of any web browser just type ***localhost:631*** and you will be taken to that webmin page.

Click on ***Printers*** at the top and it will take you to where you should be able to look for your printer and change any of its settings.
If you don't see the printer we will have to look further though as you can sometimes print I assume it will be found.

---

### Post by jonfisher on 2023-01-16
> **ajgreeny said:**
> In the address-bar of any web browser just type ***localhost:631*** and you will be taken to that webmin page.

Click on ***Printers*** at the top and it will take you to where you should be able to look for your printer and change any of its settings.
If you don't see the printer we will have to look further though as you can sometimes print I assume it will be found.

Below is what I get under Printers in localhost:631, which is reporting my correct printer (which is the HP LaserJet Pro MFP M127fn)

[TABLE="class: list"]
[TR]
[TH]Queue Name[/TH]
[TH]Description[/TH]
[TH]Location[/TH]
[TH]Make and Model[/TH]
[TH]Status[/TH]
[/TR]
    [TR]
[TD][HP-LaserJet-Pro-MFP-M127fn]("http://localhost:631/printers/HP-LaserJet-Pro-MFP-M127fn")[/TD]
[TD]Hewlett-Packard HP LaserJet Pro MFP M127fn[/TD]
[TD]michael-HP-EliteDesk-800-G1-SFF[/TD]
[TD]HP LaserJet Pro MFP m127fn, hpcups 3.22.10[/TD]
[TD]Idle[/TD]
[/TR]
  [TR]
[TD][HP-LaserJet-Pro-MFP-M127fn-Fax-2]("http://localhost:631/printers/HP-LaserJet-Pro-MFP-M127fn-Fax-2")[/TD]
[TD]HP Fax 2[/TD]
[TD]michael-HP-EliteDesk-800-G1-SFF[/TD]
[TD]HP Fax2 hpcups[/TD]
[TD]Idle[/TD]
[/TR]
[/TABLE]

---

### Post by jonfisher on 2023-01-16
Screenshot attached to this

---

### Post by jonfisher on 2023-01-16
Update:  I have discovered that this only occurs in Firefox browser....

---

### Post by ajgreeny on 2023-01-18
In the Firefox browser type ***about:config*** and in the configuration option that appear search for your printer model number using the search box at the top
.
I expect many lines will appear which you will need to search manually to see if you can find anything about ***save to pdf*** being the default behaviour.

I think you may also be able to find your printer if you scroll to the bottom of that firefox print dialogue and choose ***Print using system dialogue*** which will open the print dialogue you normally see in other applications, and where you will hopefully see the options ***Print to file*** and also your installed printer listed.
If there is no printer showing there it is a general printer problem and nothing to do with firefox.

---

### Post by jonfisher on 2023-01-22
I got the solution at Linuxquestions.org 

Which is:

Open the Ubuntu Software Center application.
Search for Firefox.
Click the Permissions button.
Confirm that its Printing permission is set to ":cups-control".

---

### Post by ajgreeny on 2023-01-22
Ah!
Yet another result of my lack of knowledge of the snap version, now the default, of firefox and many other applications in Ubuntu which create difficulties and remove some normal practices without making the sort of configuration changes you had to.

I do not use any snap applications in any of my OSs and have completely removed the whole snap system infrastructure.

---

