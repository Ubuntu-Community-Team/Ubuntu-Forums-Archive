---
title: "Changing PDF paper size (A4 to US letter)"
date: 2008-10-19
forum: General Help
---

### Post by yang on 2008-10-19
Hi, is there any tool to let me convert a PDF from A4 to US letter? I'm interested in anything at the moment - cropping, scaling, etc. I'd prefer a command-line tool like pdftk or the pdfjam suite, but I'm interested in hearing all suggestions. Thanks in advance for any help!

---

### Post by shawnrgr on 2008-10-20
why don't you 'print to pdf' and set paper size to letter ;)

---

### Post by yang on 2008-10-30
The main reason is because I have a large number of such documents.

---

### Post by yang on 2008-10-30
Also, I can't tell how to choose the paper size from the print dialog in evince.

---

### Post by yorkie on 2008-10-30
> **yang said:**
> Also, I can't tell how to choose the paper size from the print dialog in evince.
In evince go to FIle click on print setup ,widow opens choose paper size

---

### Post by teddks on 2008-12-12
That isn't a very good solution, as it can't be automated and it ends up chopping off the top margin leaving a huge bottom margin.

---

### Post by TeXtonyx on 2008-12-12
> **yang said:**
> Hi, is there any tool to let me convert a PDF from A4 to US letter? I'm interested in anything at the moment - cropping, scaling, etc. I'd prefer a command-line tool like pdftk or the pdfjam suite, but I'm interested in hearing all suggestions. Thanks in advance for any help!

[http://home.hccnet.nl/s.vd.palen/](http://home.hccnet.nl/s.vd.palen/)
"FreeDist 3.9  The Freeware equivalent of Adobe distiller. Drop 
your postscriptfiles in a "watched" folder and the PDF files 
will roll out automatically."  

My idea for this requires that you have the source files that the
original .pdf documents were created from. There is likely a .ps
script/Pstill that will convert several source documents into .ps

(Coherent) Cpdf I think would convert the .pdf files back to .ps
and manipulate them for page format and then rebuild them as .pdf

It seems like a bash script could handle multiple files in a
directory. This will be easier with the source files than with 
the original .pdfs which were formatted into A4 page format. 

I think I would post this question on a Usenet forum, such as 
adobe.postscript.programming or comp.lang.postscript

---

### Post by TeXtonyx on 2008-12-12
> **yang said:**
> Hi, is there any tool to let me convert a PDF from A4 to US letter? I'm interested in anything at the moment - cropping, scaling, etc. I'd prefer a command-line tool like pdftk or the pdfjam suite, but I'm interested in hearing all suggestions. Thanks in advance for any help!

[http://home.hccnet.nl/s.vd.palen/](http://home.hccnet.nl/s.vd.palen/)
"FreeDist 3.9  The Freeware equivalent of Adobe distiller. Drop 
your postscriptfiles in a "watched" folder and the PDF files 
will roll out automatically."  

My idea for this requires that you have the source files that the
original .pdf documents were created from. There is likely a .ps
script/Pstill that will convert several source documents into .ps

(Coherent) Cpdf I think would convert the .pdf files back to .ps
and manipulate them for page format and then rebuild them as .pdf

It seems like a bash script could handle multiple files in a
directory. This will be easier with the source files than with 
the original .pdfs which were formatted into A4 page format. 

I think I would post this question on a Usenet forum, such as 
adobe.postscript.programming or comp.lang.postscript

---

### Post by scsl on 2009-04-22
> shawnrgr:	

why don't you 'print to pdf' and set paper size to letter 

Thanks a lot!  This solved my problem.  I have been having a hard time printing out some good pdf e-books set in A4 size onto our standard Letter size paper here.  I never knew I could do that.  Thanks very much again!

---

