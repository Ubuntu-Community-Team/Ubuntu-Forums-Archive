---
title: "How to convert PDF to RTF/DOC/ODT format"
date: 2008-10-01
forum: General Help
---

### Post by varun.net on 2008-10-01
Is there a program available for linux that can convert PDF to RTF/DOC/ODT format?

---

### Post by Pro-reason on 2008-10-01
Since PDF is a final presentation format, the conversion to PDF is generally one-way (i.e. lossy).

You can, if you like, simply open the PDF in Evince, highlight all the text, and then copy and paste it into OpenOffice writer.  Edit it, and save in whatever format you like.

One neat little feature in Evince is that OCR is built-in, so you can even copy and paste text from PDFs that consist of images.

---

### Post by varun.net on 2008-10-01
> **Pro-reason said:**
> Since PDF is a final presentation format, the conversion to PDF is generally one-way (i.e. lossy).

You can, if you like, simply open the PDF in Evince, highlight all the text, and then copy and paste it into OpenOffice writer.  Edit it, and save in whatever format you like.

One neat little feature in Evince is that OCR is built-in, so you can even copy and paste text from PDFs that consist of images.

Is there any tool/scipt available that can automate the process and also convert the images. When I google pdf 2 rtf/doc I find a lot of tools but they are for windows.

I looked at xpdf which is good in converting the text but pdf2images[pdfimages] option does not work.

---

### Post by varun.net on 2008-10-01
The pdf's that I am trying to convert are also available in postscript. Is there a way I cna convert postscript files into RTF/DOC/ODT with the images intact.

---

### Post by HermanAB on 2008-10-01
Gimp, Abiword and Scribus can import PDF and save in a different format.

---

### Post by Pro-reason on 2008-10-01
If you want to convert a batch of such files, I can't think of anything but the *ps2ascii* command (from the *ghostscript* package), or *pstotext*.  Or will lose formatting though.

What exactly is your purpose?

---

### Post by varun.net on 2008-10-02
> **Pro-reason said:**
> If you want to convert a batch of such files, I can't think of anything but the *ps2ascii* command (from the *ghostscript* package), or *pstotext*.  Or will lose formatting though.

What exactly is your purpose?

I am trying to convert a few pdf files which also include images [images are important in this case].

I do not care about the if they are formatted or not.

---

### Post by varun.net on 2008-10-02
> **HermanAB said:**
> Gimp, Abiword and Scribus can import PDF and save in a different format.


Gimp - couldn't convert images
Scribus - couldn't open the pdf file

---

### Post by Pro-reason on 2008-10-02
A bit cagey about your purposes?  Never mind; perhaps it's personal.  Don't blame me if the suggestions aren't helpful, though.

Both postscript and PDF?  Sounds almost like LaTeX output.

Since these files are intended to be final documents, you're going to have to expect to do some work if you want to convert them back into something similar to the working documents they were created from.

Let's say you have a file called Report.pdf.  Do this:

```

*sudo apt-get install ghostscript pstotext poppler-utils openoffice.org*
ps2ascii Report.pdf > Report.ps2ascii.txt
pstotext Report.pdf > Report.pstotext.txt
pdfimages -j Report.pdf Report-
oowriter Report.*.txt

```

That will open two versions of the document.  Pick the one that you think is best.  Use OpenOffice Writer's *Insert* menu to put the images in.  Tidy up the document.  Save as *.odt*.

Note that the *ps** commands work on both actual PostScript and PDF.  The pdfimages command is available from either the *poppler-utils* or *xpdf-utils* package.

I'm quite surprised that GIMP didn't work because of images.  GIMP is an image-editing program!  It works great at importing PDFs; the only problem is that it rasterises everything.

---

### Post by fragos on 2008-10-03
You can extract all images from a pdf file into a folder.

pdfimages -j <file.pdf> <image_name_root>

All image files will have the same name with a sequencial number added.

---

### Post by quill3033 on 2008-10-08
What about tables? I always get tables for uni subjects that go over two pages unnecessarily and I would like to be able to copy the table to a text/word processor and then shift them up to fit onto one page so then I can print them and put them on the wall as one page. 

I've tried copying and pasting with evince and then converting to table but the format is lost so that there is only one column and text is all over the place and there is no one to one correspondence to be able to split at tabs or paragraphs...

---

### Post by Pro-reason on 2008-10-09
> **quill3033 said:**
> What about tables? I always get tables for uni subjects that go over two pages unnecessarily and I would like to be able to copy the table to a text/word processor and then shift them up to fit onto one page so then I can print them and put them on the wall as one page. 


You may have success with the *pdfedit* package.

---

