---
title: "Convert PDF to JPG or PNG?"
date: 2008-11-25
forum: General Help
---

### Post by Johnsie on 2008-11-25
Hi, does anyone have any solution for converting a pdf to an image on Ubuntu?

Thanks in advance,

Johnsie

---

### Post by kaibob on 2008-11-25
You can use the convert command-line utility. It's part of the Imagemagick suite and can be installed through synaptic.

To convert a PDF file to PNG format, the command would be:

```
convert infile.pdf outfile.png
```

The following page provides more detail:

[http://www.imagemagick.org/script/convert.php](http://www.imagemagick.org/script/convert.php)

And, the following page lists formats supported by convert:

[http://www.imagemagick.org/script/formats.php](http://www.imagemagick.org/script/formats.php)

---

### Post by Johnsie on 2008-11-26
Thanks, that worked but the size of the image was alot smaller than the pdf.  Is there a way to keep the same page dimensions?

---

### Post by hyper_ch on 2008-11-26
open the pdf in gimp and save it as .jpg or .png

---

### Post by phillies on 2008-11-26
or you can tell 'convert' which size

usually more dots per inch [dpi] works. I'm not sure what's convert's default value but 300dpi or 600dpi are in general good values as you convert vector graphics to raster graphics (that's why you can zoom in in good pdfs and it wont get pixely while it does on pngs)

Edit: 
small example: An 8x11 letter/A4 (approx) with 72 dpi will result in a 576x792 pixel image -> quite crappy for a whole page, isn't it? Better with 300 dpi: 8x11 -> 2400 x 3300 pixel image, somehow better, isn't it?

---

### Post by Dewni on 2009-03-30
This answer might be a bit late, but perhaps good for the archive. I had a similar problem before. Change a bunch of oddly sized pdf documents to A4 format (portrait).

First, use pdftk to rotate the pictures:
```
pdftk your_input_file.pdf cat 1-endW output rotated.pdf
```

Then, use imagemagicks convert to generate a ps file, I used -density 300 to get a resonable 300dpi resolution, you might want more or less.
```
convert -density 300 rotated.pdf rotated.ps
```

And finally, use ghostscript to get everything in A4 format
```
gs -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=output.pdf rotated.ps
```

Of course this can be done using other tools, but I am very happy with all these utilities and the fact that I can use them from the commandline.

---

### Post by gusanto on 2009-05-28
I have 32 pages of pdf file and I want to convert it to png file with 4 images per page. Please show me how to do it. I have searched help but no luck.
Many thanks.

---

### Post by XCan on 2009-05-28
> **gusanto said:**
> I have 32 pages of pdf file and I want to convert it to png file with 4 images per page. Please show me how to do it. I have searched help but no luck.
Many thanks.

Perhaps you could open the pdf in evince, -> print to file -> page setup -> pages per side, and use 4? After the the new pdf with 4 pages per side has been created you can turn it into a png document using:

```
convert 4pages_per_side.pdf 4pages_per_side.png
```

---

### Post by rocksockdoc on 2011-11-29
> **Dewni said:**
> This answer might be a bit late, but perhaps good for the archive. 

I just want to say thanks for adding answers 'for the archive'!

Googling brought me here to find out how to convert, rotate, and resize a PDF to JPG without losing the quality of the results (the key being keeping the quality to a reasonable level).

These three commands came in useful:

**To convert a PDF to PNG with reasonable quality:**
convert -density 300 file.pdf file.png

**To rotate a PDF:**
pdftk nonrotated.pdf cat 1-endW output rotated.pdf

**To size a PDF to a desired size (this example is A4 but I would want 8.5x11):**
gs -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -sPAPERSIZE=a4 -sOutputFile=output.pdf input.ps

---

### Post by PALLAVI MANIK MANE on 2012-02-06
Thank you it really worked for converting and size as well.
Thanks all :D

---

