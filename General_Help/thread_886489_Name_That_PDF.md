---
title: "Name That PDF"
date: 2008-08-11
forum: General Help
---

### Post by raywood on 2008-08-11
I've got CUPS-PDF set as my default printer.  Now, how do I get it to prompt me for the filename of the PDF that I am creating?  Or do I need to use some other PDF printer instead?

---

### Post by Mgiacchetti on 2008-08-11
Save whatever you are printing as the filename you want the pdf to be named?

Kinda redundant, but hey its all i can figure.

---

### Post by raywood on 2008-08-11
It's a possibility for some things, but it won't work for printing webpages.

---

### Post by kaibob on 2008-08-11
> **raywood said:**
> I've got CUPS-PDF set as my default printer.  Now, how do I get it to prompt me for the filename of the PDF that I am creating?  Or do I need to use some other PDF printer instead?

I believe you can do this with the cups-pdf postprocessing function, although it takes a bit of work. Have a look at post 2 and the script attached to post 3 of the following thread:

[http://ubuntuforums.org/showthread.php?t=750426](http://ubuntuforums.org/showthread.php?t=750426)

---

### Post by brian_p on 2008-08-11
> **raywood said:**
> I've got CUPS-PDF set as my default printer.  Now, how do I get it to prompt me for the filename of the PDF that I am creating?  Or do I need to use some other PDF printer instead?

You won't be given a prompt and will have to change the filename after printing has taken place.

Discussion of this issue is here

[https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/158406](https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/158406)

and here

[https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/134671](https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/134671)

---

### Post by raywood on 2008-08-11
OK.  Is there perhaps something I can be using, other than CUPS-PDF, that will give me an option of printing to a filename.pdf of my choice?

In Windows, for example, I can set Adobe as my default printer, and it will ask me for the name of the PDF it is printing.

---

### Post by kaibob on 2008-08-11
> **raywood said:**
> OK.  Is there perhaps something I can be using, other than CUPS-PDF, that will give me an option of printing to a filename.pdf of my choice?

In Windows, for example, I can set Adobe as my default printer, and it will ask me for the name of the PDF it is printing.

This is a fairly frequent question, and I don't recall any linux alternative to cups-pdf. I use cups-pdf frequently and, lacking any alternative, I use the job-id option to prevent overwriting and then rename with Nautilus the pdf files that I want to keep.

BTW, Firefox 3 does have a print-to-file option that creates PDF files and requires a file name in advance, but that's not what you are requesting.

---

### Post by brian_p on 2008-08-11
> **raywood said:**
> 

OK.  Is there perhaps something I can be using, other than CUPS-PDF, that will give me an option of printing to a filename.pdf of my choice?


In firefox: Print.. --> PostScript/default --> Properties

Change 'Print Command' to:

```
ps2pdf - > $HOME/my_chosen_filename.pdf
```

---

### Post by raywood on 2008-08-11
That works.  For future reference by me and others, here's the verbose version and a couple of follow-up questions.

To name the PDF you are printing in Firefox 2.x within Ubuntu, use File > Print > Printer Name > PostScript/default and set its Properties > Print Command as "ps2pdf - > /folder/filename.pdf" where "folder" is the path to the folder in which you want to save the file.  Example:  ps2pdf - > /media/DATA/Current/NewPDF.pdf.  Then click Print.  If you use this twice in a row without changing the name of NewPDF.pdf, the latest one will overwrite the previous one.  The resulting PDF file contains searchable text, just like the PDFs produced by CUPS-PDF.

My first follow-up question is whether there is a way to set PostScript/default as, indeed, the default.  I don't see that option in System > Administration > Printing.

The second follow-up question is whether there is a way to generate a variable filename automatically instead of typing the filename in Properties.  (Example:  ps2pdf - > /folder/VariableFilename.pdf.)  In some instances, I want to print several PDFs in a row, and then I'll go to the target folder and merge them.  In such a case, it doesn't matter to me what those several PDFs are called, as long as none overwrites another.

---

### Post by kaibob on 2008-08-11
> **raywood said:**
> ...The second follow-up question is whether there is a way to generate a variable filename automatically instead of typing the filename in Properties.  (Example:  ps2pdf - > /folder/VariableFilename.pdf.)  In some instances, I want to print several PDFs in a row, and then I'll go to the target folder and merge them.  In such a case, it doesn't matter to me what those several PDFs are called, as long as none overwrites another.

Ghostscript (and I assume ps2pdf) supports the use of %d to indicate page or image numbers. I don't quite understand the command line you are using, but you might want to try filename-%d.pdf as the variable file name.

---

### Post by raywood on 2008-08-13
Unfortunately, that just produces a file named filename-%d.pdf.  Any other ideas?  

Still curious, too, on how to make PostScript/default the default printer.

Thanks ...

---

### Post by brian_p on 2008-08-13
> **raywood said:**
> Unfortunately, that just produces a file named filename-%d.pdf.  Any other ideas?

raywoods-script

```
#!/bin/bash

A=`date +%s`
mv $HOME/filename.pdf $HOME/filename-$A.pdf
```

```
chmod 755 raywoods-script
```

In firefox:

```
ps2pdf - > /folder/filename.pd ; /folder/raywoods-script

```

> Still curious, too, on how to make PostScript/default the default printer..

Not possible, I think. The CUPS printing system can not be made aware of firefox's PostScript/default option.

---

### Post by raywood on 2008-08-13
I must have done something wrong.  I'm still getting just NewPDF.pdf in the target folder.

Here's what I did:

(1) In Terminal, log in as root and then type "gedit /home/bin/firefoxpdfprint-script"

(2) In firefoxpdfprint-script, enter these lines:
> 
#!/bin/bash

A=`date +%s`
mv /media/DATA/CURRENT/NewPDF.pdf /media/DATA/CURRENT/filename-$A.pdf


Save and quit firefoxpdfprint-script.

(3) In Firefox > File > Print > Printer Name > PostScript/default > Properties > Print Command, type "ps2pdf - > /media/DATA/Current/NewPDF.pdf ; /home/bin/firefoxpdfprint-script" and then OK and Print.

Where did I go off the rails?

---

### Post by brian_p on 2008-08-14
> **raywood said:**
> 

Where did I go off the rails?

You did make the script executable?

---

