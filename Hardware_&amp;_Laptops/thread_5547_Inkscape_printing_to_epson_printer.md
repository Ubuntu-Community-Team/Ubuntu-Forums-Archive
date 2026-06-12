---
title: "Inkscape printing to epson printer?"
date: 2004-11-19
forum: Hardware &amp; Laptops
---

### Post by lhtown on 2004-11-19
I just started using Inkscape a few days ago. It is an great program companion program for my needs which include fliers and newsletters and other simple print jobs.

I am using Ubuntu Warty. My difficulty is that I can't get Inkscape to print to my printer (Epson stylus C83). I select print and either postscript or bitmap and leave the command line to lp and nothing happens. I have tried entering lpr -P StylusC83-1 and it still won't print.

 In short nothing happens. It seems to try to do something judging by the pull on system resources, but there are no onscreen indicators of activity and the printer does nothing while the print dialog box just disappears.

Perhaps someone who has it working successfully can give me a hint as to what to do.

---

### Post by adbak on 2004-11-20
Are you able to print with other programs?
Do you have your printer set up as a Stylus C83 or is it using the generic Stylus Color driver instead?
If the latter is the case, then download packages ```
cupsys-driver-gimpprint
cupsys-driver-gimpprint-data
``` from universe, delete your preexisting printer configuration, and try adding the Stylus C83 driver.  It should work after that, if that is the case indeed.
If not, does Inkscape have a place where you can select the printer?
Or maybe it's just not probing your computer in the right places for the printer.  You may have to manually tell the printer config to look at Parallel Ports or USB Ports, depending on what kind you have.

Sorry to have thrown so many questions at you, but it's hard to diagnose your problem with such scant information (not to mention I've never used Inkscape (but I do have a C82)).

---

### Post by lhtown on 2004-11-20
I have my printer installed as an epson C83 as you say. Other programs print fine. Inkscape only has a command line to select a printer. It suggest "lp" and then I don't know what to put after that since I have never printed from the command line, but it seems to me that I need to fill it out with a complete command for it to work.

---

### Post by ayam on 2004-12-23
I also have similar problem.

You select Print from the File menu you get this option:

Print Properties
[] Print using Postscript operators
[] Print as bitmap

Print Destination
Using '> filename' to print to file
Use '| prog arg...' to pipe to a program

[lp ______________________________ ]

The 'lp" bit is the part where the above poster describes having the option of putting in command lines.

---

### Post by ayam on 2004-12-23
Ok I did a bit more investigation and I read this

[http://www.inkscape.org/doc/inkscape-man.html](http://www.inkscape.org/doc/inkscape-man.html)
Specificially it says

-p PRINTER, --print=PRINTER
    Print document(s) to the specified printer using `lpr -P PRINTER'. Alternatively, use `| COMMAND' to specify a different command to pipe to, or use `> FILENAME' to write the PostScript output to a file instead of printing. Remember to do appropriate quoting for your shell, e.g. 

    inkscape --print='| ps2pdf - mydoc.pdf' mydoc.svg

So I typed 
lp -P EPL-5900 

where 'EPL-5900' is the name of my printer 


I also sellect print as bitmap. Then my printer flashes once on its 'data receiving'     indicator and nothing else happens. the data receiving usually is abit more continous as a picture has a bit of data.

My printer is a Epson EPL-5900 and is ocnnected via USB. The URI  is usb://EPSON/EPL-5900
The printer works fine with other programmes --- Firefox, gedit, etc etc

---

### Post by ayam on 2004-12-24
Solved,
I set my command to lp -P EPL-5900 and select Postscript Operators and the printing works.

---

### Post by lhtown on 2005-01-15
Thanks,
In a quick test, 

lp -P Epson-C83

works for me too.

---

### Post by tenoca on 2006-02-12
OK,
I'm printing to :
lpr -P LaserJet-1300
and the problems is i get  multiple copies.

---

### Post by lhtown on 2006-02-12
What version of Inkscape are you using and by "multiple copies" do you mean two or three or 5,000?

---

### Post by fizgig on 2006-02-15
Just for the record - if you want to print with transparency, the only way I've figured out how to do it true to size (not print 5x too big for the page) is to export from inkscape as a png at whatever res you want (I used 300dpi).

Open it up in Gimp and print from there.  For some reason, I had to remove the -s in the print string.  Worked great.

---

