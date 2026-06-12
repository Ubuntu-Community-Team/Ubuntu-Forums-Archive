---
title: "Printing command line"
date: 2008-10-23
forum: General Help
---

### Post by Flynn555 on 2008-10-23
hi i have brother MFC-544CN printer.  i have successfully gotten it to work under cups...the printer works fine when i FILE>PRINT but in command line the lp and lpr commands dont work...

i receive this,
```

~/Documents$ lp lab_report.odt
request id is MFC-5440CN-49 (1 file(s))

```
but nothing is printed.

---

### Post by prshah on 2008-10-23
> **Flynn555 said:**
> hi i have brother MFC-544CN printer.  i have successfully gotten it to work under cups...the printer works fine when i FILE>PRINT but in command line the lp and lpr commands dont work...


In ubuntu, the default printer is usually set to the PDF printer; maybe the job is being sent to the PDF printer (if it is set as default)? Check under ~/PDF.

Set your Brother printer as the default, and then try the command again; does it clear your problem?

Or try```
lp -c lab_report.odt
``` and/or ```
lp -d printer_name lab_report.odt

``` (Replace printer name with the name of the Brother printer as shown in CUPS)

---

### Post by Flynn555 on 2008-10-23
hmmm i believe that the brother printer is my default 

```

$ lpstat -d
system default destination: MFC-5440CN

```

---

### Post by kaibob on 2008-10-24
Did you try to print a different type of document? I use lp to print PDF and TXT documents but it does not print ODT documents.

A command-line alternative to print OpenOffice Writer documents is:

```
oowriter -p filename.odt
```

---

