---
title: "Xsane 8.04 can't find printer to make copy!"
date: 2008-07-15
forum: General Help
---

### Post by wkulecz on 2008-07-15
Had problems finding our Cannoscan USB scanner in 7.04 but after the "scanbutton" hack Xsane would usually find it and then find the printer to make copies.

Now in 8.04 the scanner is found out of the box, but when I set scan type to copy, no printers can be found.

Printing from OpenOffice, Mozilla, Thnuderbird, and everything else I've tried work.

Ideas on how to fix?

I can scan to a file, and then open the appropriate application to print it, but this is just not going to fly for my wife when she needs to copy something before she drops it in the US Mail.

Other than this she's pretty much 100% ex-Windows user now at home.  She still uses XP at work, but OO is a good enough MS Office clone for what she does she's figured out everything she needs on her own.

--wally.

---

### Post by Robin T Cox on 2008-07-15
Have you set your printer as the default printer?

Which printer do you have?

---

### Post by wkulecz on 2008-07-16
Printer is a Samsung CLP-300.  I believe it is set as the default since its the only real printer other than the PDF Creator "virtual printer" driver.  As I said printing web pages works fine.

I'll check when I get home, it'd be great if its that simple, but I was expecting the Xsane printer drop down box to show selections for CLP-300 and PDF Creator, but all it shows is "New Printer".

If I could choose PDF Creator as Xsane's output printer for a copy I think my wife would love this as she uses PDF a lot at work.

--wally.

---

### Post by Robin T Cox on 2008-07-16
OK. Do check that the printer is set as default, as I found that this fixed the problem in my case.

I have set up my printer (an HP Deskjet1460) using the HPLIP utility, but I have also used the gnome-cups-manager, which is simple and reliable and I recommend it to you.

I hope this helps, as this is about as far as I can go to be of assistance.

---

### Post by wkulecz on 2008-07-18
Unfortunately this does not seem to be the problem.  I had hopes initially as the "Default Printer" tool showed now printer, but then it didn't seem to set one either.  So I when to the "Printers" control and made CLP-300 the default.

Still Xsane doesn't see a printer and clicking "add printer" button does nothing.  I then re-installed Xsane and its parts using symantic.  Still no go :(

--wally.

---

### Post by plucky on 2008-07-18
Don't know if this will help,because I have a different All-in-one printer/scanner,but my Xsane **copy** prints using the terminal command **lpr**.

To see what your default printer in a terminal window please post output of ```
lpstat -v && lpq
```

and to see if your printer accepts terminal commands ```
lpr <some small text file>
``` should send that text file to the printer.


Good Luck

---

### Post by wkulecz on 2008-07-20
Here is the command output:

laura@laura:~$ lpstat -v && lpq
device for CLP-300: usb://Samsung/CLP-300
device for PDF: cups-pdf:/
CLP-300 is ready
no entries

Everything seems fine to me and lpr smallTestFile worked fine.

I'm stumped!

--wally.

---

### Post by wkulecz on 2008-07-23
Bump!

No progress.  Could someone who can actually use Xsane to do a copy please post a screenshot of their Setup->Copy tab?

Maybe I can see something to give me a clue.  

This worked fine in 7.04, although I had to go thru a bunch of rigamarole to have Xsane find the scanner. Now scanner works great out of the box.  Printer works great in everything but Xsane :(

--wally.

---

### Post by plucky on 2008-07-23
> Could someone who can actually use Xsane to do a copy please post a screenshot of their Setup->Copy tab?

See below.The file that changes is **xsane.rc** located in **~/.sane/xsane/xsane.rc**. If you edit that file in your home directory,you may be able to specify your printer.

Good Luck

---

### Post by wkulecz on 2008-07-29
Thanks, my setup looks exactly like yours except I've entered my CLP-300 printer queue name where your Brother printer is.

Mine is just a printer not an all-in-one.

If instead of choosing scan to "copy" I choose "pdf" I can then open the output pdf file and print it.  Work around of sorts.

--wally.

---

### Post by tatster on 2008-08-04
Hi,

I had the same issue and a fix I found elsewhere worked for me.
an lpr <somefile.txt> worked fine from terminal but not from Xsane with just **lpr** in the command field....However with the command field of **lpr -P i865** it works a treat!  i865 is the name of my printer, as it appears in my Printer settings.

Hope this works for you guys as well.

Tatster.:)

---

### Post by wkulecz on 2008-08-07
Still no go.  I misread your font and tried lpr -p CLP-300 first and got "broken pipe errors".  Unfortunately lpr -P CLP-300 does the same as the original lpr, which is nada.  No errors, no printout.

--wally.

---

### Post by JonnyB29 on 2008-09-26
Hi

Hi was having the same problem, no errors and no printing and find the solution [here]("https://help.ubuntu.com/community/XSane") and resolves my problem, when i unselect the option **"Create zlib compressed postscript image for printing"** the print work.

hope it helps

by

---

