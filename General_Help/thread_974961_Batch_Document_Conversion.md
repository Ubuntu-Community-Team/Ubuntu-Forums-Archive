---
title: "Batch Document Conversion"
date: 2008-11-08
forum: General Help
---

### Post by deathbox on 2008-11-08
Hey I was wondering if anyone was aware of a way to do batch file conversion on .rtf files. I have about 5,000 RTFs that need to be converted into PDF. I actually have Adobe on another machine, and I have been doing the batch method in that program, but it acts as if it is printing each RTF to create the PDF and the process is super slow. There has to be a faster and better way to do this in Ubuntu.

---

### Post by cmnorton on 2008-11-08
PDF is a printing format. I believe you have to print. For flat text files, we use txt2pdf.pl, which is a very nice tool that creates perfect Acrobat files. But that is still a printing process, and the files are nice flat, ascii files without formatting.

I don't know if open office can read an rtf file. If it could, I don't know if you can control open office from the command line. That is tell open office to open a document and then extract it to pdf and control that in a loop. You might be able to do that in Windows with VBA and WSH, but is it worth all that work?

---

### Post by geirha on 2008-11-08
A quick search for rtf in the repositories found the package [apt://unrtf](apt://unrtf) - «RTF to other formats converter».

It doesn't convert to pdf, but it converts to ps which is close. You can further convert ps to pdf with ps2pdf. Try this on a couple of samples:

```
unrtf --ps filename.rtf | ps2pdf - > filename.pdf
```

If that looks ok, you can loop through all files with something like
```

for file in *.rtf; do
  unrtf --ps "$file" | ps2pdf - > "${file/%rtf/pdf}"
done

```

---

### Post by deathbox on 2008-11-08
Ah yes, I just came across unrtf as well. I am going to check it out and see how it goes. I suppose this really is only worth it to me because I work in the litigation support market, and many times we get crazy amounts of RTF (or many many other formats) and they need to be converted into whatever format they need. I am just trying to automate these mundance processes. 

And vista...forget about it. That OS is trash. I can't even run 800 PDFs on a nice system without it failing.

---

### Post by mbeach on 2008-11-08
I've been meaning to give the following a try (haven't had a chance) but it may do what you want - have no idea of the speed in a batch situation - the online demo seemed quick but not a great test if you are sending a gazillion files of varying sizes.  

[http://www.artofsolving.com/opensource/jodconverter](http://www.artofsolving.com/opensource/jodconverter)
or
[http://www.artofsolving.com/opensource/pyodconverter](http://www.artofsolving.com/opensource/pyodconverter)

One note to be aware of
"PyODConverter requires OpenOffice.org to be running as a service and listening on port"

---

### Post by kingrolo on 2010-05-12
Hi deathbox. I need to do the exact same thing as you. I've been trying for 2 days with varying results. I'm using PHP to generate documents from MySQL data. I start with a 'template' doc and then use PHP to search and replace keywords to generate each new doc (rtf works well for search-and-replace). Then I need to convert them to PDF for download from the webpage. So this is 100% server side with no graphics capabilities.

I've got CUPS-PDF up and running on the server and can print to it from other clients, but it seems it's the client program that dictates the end result. MSWord on Windows7 and OpenOffice Writer on Ubuntu work fine from clients, but command line programs from the server only seem to work on rtf docs with _no_ embedded images. Even then the output quality is not great. I've played with abiword and unrtf.

So which non-graphics-dependent command line app prints rtf files with embedded graphics in them???

---

### Post by geirha on 2010-05-12
kingrolo, there are many pdf libs for php. It's probably easier to use one of those libs to generate pdf files directly. E.g. [http://www.php.net/manual/en/pdf.examples-basic.php](http://www.php.net/manual/en/pdf.examples-basic.php)

---

### Post by kingrolo on 2010-05-12
funny, i have just stumbled across this myself. Looks like a bit of a learning curve, but I'll give it a go in the absence of anything simpler. My doc contains a graphic banner (header & footer) plus a table and about 3 different font sizes. Let's hope this isn't too complicated ;)

---

