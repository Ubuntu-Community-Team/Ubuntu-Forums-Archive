---
title: "Create PDF from large amount of image files"
date: 2008-10-06
forum: General Help
---

### Post by duncanbell on 2008-10-06
I have around 190 A4 page scans (TIFF image files) of a book I would like to make into a PDF.

I have tried using F-Spot and "printing" as a PDF, but it crashes while trying to make the PDF, I think due to the large amount of files involved. It performs fine when I only use a small selection of the pages to try and make a PDF.

I have also tried using a program called gscan2pdf (in the repositories I belive), which seems to perform the task well, but when trying to open the PDF in any PDF reader (windows or linux) crashes the reader instantly.

I would be very grateful of any suggestions. Thanks!

---

### Post by denn0069 on 2008-10-06
Have you considered the possibility of combining the files using 'cat', or a similar command and pipes, before attempting to convert it to PDF? It may relieve some stress on the PDF printing programs.
Not sure if it will help, but could simplify the process.


EDIT: Wow, did not read that properly. Not sure if it can be done on Image files safely, ignore my stupidity.

---

### Post by geirha on 2008-10-06
[imagemagick](apt://imagemagick) should be able to do that. Install it and run ```
convert *.tif output.pdf
```

Not 100% sure it will work as you want, but it's worth a try.

---

### Post by ju2wheels on 2008-10-06
> **geirha said:**
> [imagemagick](apt://imagemagick) should be able to do that. Install it and run ```
convert *.tif output.pdf
```

Not 100% sure it will work as you want, but it's worth a try.

If it does work then you use pdftk and merge the pdf files:
```

pdftk *.pdf cat output combined.pdf

```

(Double check the pdftk man page, I dont recall if that is exactly correct).

---

### Post by john_spiral on 2008-10-09
> **ju2wheels said:**
> If it does work then you use pdftk and merge the pdf files:
```

pdftk *.pdf cat output combined.pdf

```

(Double check the pdftk man page, I dont recall if that is exactly correct).

Worked a charm!

*tip* the below command creates a pdf in the order a,b,c.

pdftk a.pdf b.pdf c.pdf cat output combined.pdf

---

