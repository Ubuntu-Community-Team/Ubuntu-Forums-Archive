---
title: "How to Print from terminal"
date: 2008-10-14
forum: General Help
---

### Post by bryle on 2008-10-14
Is there a way that I can print from terminal just like in windows it uses the prn. I'm using Ubuntu v.8.04 LTS.

Thanks in advance...

Bryle

---

### Post by EnGorDiaz on 2008-10-14
i dnt think there is a way but you can copy and paste it into a text file and print it

---

### Post by john.nicholls on 2008-10-14
In a terminal the output is normally printed to the screen. If you want to redirect the output to a printer you can pipe it by using the pipe symbol | followed by lpr.

Thus to redirect the output of ifconfig -a to a printer you'd enter ```
ifconfig -a | lpr
```

---

### Post by plucky on 2008-10-14
> **bryle said:**
> Is there a way that I can print from terminal just like in windows it uses the prn. I'm using Ubuntu v.8.04 LTS.

Thanks in advance...

Bryle

See ```
man lpr
man lp
``` for terminal print commands.


Good Luck

---

### Post by Ganton on 2009-06-06
GOD BLESS YOU! It worked for me!. I executed
   cat file.prn | lpr
though it had to be executed in a computer with the same printer (or one compatible) (*). 


(*) Normally it's easier to "print" to a pdf file and later the pdf file can be printed easily anywhere. If you need to "print" to a pdf file in Windows, the best option is the free/libre software called PDF Creator in [http://www.pdfforge.org/products/pdfcreator](http://www.pdfforge.org/products/pdfcreator)

---

### Post by bforbes on 2009-07-17
Here's the command that works for me:

lpr -P MFC5460CN -o Resolution=Normal -o PageSize=A4

MFC5460CN is the name of my network printer, which I added through CUPS.

---

### Post by t4thfavor on 2009-07-18
Any college kid knows how to do this as soon as his school starts charging $.10 per page :) thats almost a pack of rahmen noodles for gods sake...

---

