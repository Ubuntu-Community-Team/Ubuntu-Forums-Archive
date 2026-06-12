---
title: "Grep/search a PDF file"
date: 2008-08-16
forum: General Help
---

### Post by tekguy on 2008-08-16
Is there a command line way to search a series of PDF files? I scan all of my documents to PDF and keep them in a TrueCrypt container. I want to be able to search the files for a string value. As the folder depth gets deeper and the file count goes up, it is getting increasingly difficult to find what I'm looking for. I was disappointed when I found that grep would not work on PDF files.

---

### Post by ghostdog74 on 2008-08-16
if you have [xpdf](http://www.foolabs.com/xpdf/) tools, you can use pdftotext to convert pdf to text then search for the string using grep.

---

### Post by tekguy on 2008-08-16
> **ghostdog74 said:**
> if you have [xpdf](http://www.foolabs.com/xpdf/) tools, you can use pdftotext to convert pdf to text then search for the string using grep.

So I would convert all of my pdf files into text files then? So I would have for example:

somedoc.pdf
somedoc.txt
somedoc2.pdf
somedoc2.txt

and then which ever .txt doc it hits on, I can then go to the associated pdf?

---

### Post by ghostdog74 on 2008-08-16
> **tekguy said:**
> So I would convert all of my pdf files into text files then? So I would have for example:

somedoc.pdf
somedoc.txt
somedoc2.pdf
somedoc2.txt

and then which ever .txt doc it hits on, I can then go to the associated pdf?
yes.

---

