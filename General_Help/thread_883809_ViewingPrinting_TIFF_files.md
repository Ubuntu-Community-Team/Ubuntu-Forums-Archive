---
title: "Viewing/Printing TIFF files"
date: 2008-08-08
forum: General Help
---

### Post by RequinB4 on 2008-08-08
So, I just scanned a large file on Windows - (to put a long story short, it scanned each one as a tiff and put it in one directory.  When I went to that directory, there was one file with many pages on it - ok, that's good) - Everything loads fine in MS Office document viewer.  But I can't seem to view it in any ubuntu program - (it's NOT the program i'm using, it must be the file - I think it's jpeg compression if that matters).  The best I can get is evince, which displays multiple pages of all black

Any help is appreciated.  My ultimate goal is to print to a viewable pdf
Note: the image is OCR'd - not sure if that makes a difference

---

### Post by supradave on 2008-08-08
If you do 'file tiffile', what does it describe it as?

I use gqview for most of my viewing.  You can print out of that too.

---

### Post by linux_tech on 2008-08-08
I think there are more tiff to pdf converters for free or shareware available that have GUI.
For Linux you may look at tiff2pdf (cmdline) , It looks to be a free download from softpedia.  I havn't tried it so not sure how well it works.
[http://linux.die.net/man/1/tiff2pd](http://linux.die.net/man/1/tiff2pd)

---

### Post by silkstone on 2008-08-08
Slightly confused! A TIFF or JPEG will be just a single image - not multiple pages. If you OCR'd it, that should have converted it to a text format such as .doc or .rtf, which of course can have multiple pages.

So I'm not sure what sort of file you have here. :)

---

### Post by linux_tech on 2008-08-08
You can also should be able to insert the tiff images into 
openoffice writer document to create 1 document that will view or print 
in ubuntu.  Openoffice is a free downloadfrom [http://www.openoffice.org/](http://www.openoffice.org/)
is closest thing to MS word, also allows you to work with (save, view, etc) MSword docs

---

### Post by silkstone on 2008-08-08
OpenOffice should be pre-installed anyway, but is available from the repos through Synaptic. If the OP has created a normal text or word processor file, OOo Writer should be able to open it, but I guess he'll have tried that.

---

### Post by linux_tech on 2008-08-08
Yep- and another option is to scan the document as pdf directly using scan2PDF application software, that will allow you to scan multi-page document in as 1 pdf file.

---

### Post by RequinB4 on 2008-08-08
> **supradave said:**
> If you do 'file tiffile', what does it describe it as?

I use gqview for most of my viewing.  You can print out of that too.

"TIFF image data, little-endian"

To those about opening as text - No, it's not a text, doc, or odt file - apparently Windoze document imager simply recognizes the text (similar to what a pdf with recognizable text does)

I have already tried tiff2pdf, and OOo >.>

This is a bump.

EDIT:  Under normal circumstances, I would assume that the scan just went wrong, but 1) everything loads fine in MS Office Imaging (or whatever the name of hte program is) and 2) Weird error messages whenever I try to convert or open the file in any program I can think of...

I don't know if i mentioned it, but the file was scanned in color at 200DPI

EDIT2: Just re-ran tiff2pdf - Here is the output
```

TIFFReadDirectory: Warning, File.tif: unknown field with tag 512
TIFFReadDirectory: Warning, File.tif: unknown field with tag 513
TIFFReadDirectory: Warning, File.tif: unknown field with tag 514
TIFFReadDirectory: Warning, File.tif: unknown field with tag 37677
TIFFReadDirectory: Warning, File.tif: unknown field with tag 37678
TIFFReadDirectory: Warning, File.tif: unknown field with tag 37680

```
Repeated, etc.

---

### Post by RequinB4 on 2008-08-09
I'm kind of desperate for this;  I really don't want to re-scan page by page the entire file with no guarentee that'll work either...

Here is evince's log:

```

/home/RequinB4/ScannedFile.tif: Sorry, requested compression method is not configured
```

repeated about 9 times per page...

EDIT: Beginning to get to the bottom of this - Just put it on a windows box and it said the filetype was "mspaper.document" - Does that help?

---

### Post by linux_tech on 2008-08-09
I think it would be faster and a better solution for the future to get a 
method to scan directly to pdf that works and does not end up putting a bunch of tiffs in different folders.  Trying to work with the tiffs now and convert them to a pdf doesn't seem to be the best way.  My suggestion is try installing  a new program, then run a test scan of say 3 or 4 pages
to see if the programs scans both pics and text to 1 pdf file. If it does, then you should have a working solution to scan the whole document in.

1 program that looks promising is gscan2pdf-
download available here:
[http://linux.softpedia.com/get/Multimedia/Graphics/gscan2pdf-17005.shtml](http://linux.softpedia.com/get/Multimedia/Graphics/gscan2pdf-17005.shtml)
Here is the link for a short set of instructions:
[http://www.ubuntugeek.com/scan-to-pdf-using-gscan2pdf-in-ubuntu.html](http://www.ubuntugeek.com/scan-to-pdf-using-gscan2pdf-in-ubuntu.html)
Just add the following line to your /etc/apt/sources.list:
Code:

deb [http://gscan2pdf.sourceforge.net/download/debian](http://gscan2pdf.sourceforge.net/download/debian) binary/

If you are you are using Synaptic, then use menu Edit/Reload Package Information, search for gscan2pdf in the package list

From the command line:
Code:

sudo apt-get update
sudo apt-get install gscan2pdf


Windows also has a scan2pdf program that works well called scan2pdf.
If you have a windows box handy, then another choice would be to install scan2pdf on the windows box, rescan and then you would have a pdf that could also be viewed in Ubuntu.  The only catch here is you will see "scanned in by.. " backgrnd watermark in free version.  If you buy the full vers, the watermark is removed. Here is a link : [http://www.brothersoft.com/scan2pdf-37141.html](http://www.brothersoft.com/scan2pdf-37141.html)


Another Tip: For large documents I'd also recommend a adf (automatic document feeder) on the scanner.  If the scanner is for production type scanning(many large documents daily), Fujitsu has some excellent models.

---

