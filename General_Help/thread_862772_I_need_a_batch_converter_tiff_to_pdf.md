---
title: "I need a batch converter tiff to pdf"
date: 2008-07-17
forum: General Help
---

### Post by CameronCalver on 2008-07-17
Hello i  have around 150 or so documents scanned to tiff . i need them to be converted to pdf.
I am running dapper at the moment ( yes i no its old) so what does anyone recommend for this?

---

### Post by apswartz on 2008-07-17
Try a script like this...

```
#!/bin/sh

TEMPLIST=/tmp/ListOfTiffs.`date +%s`_$RANDOM
ls -- *.tif  >$TEMPLIST 2>/dev/null

while read FileFromList
	do
        convert ${FileFromList} ${FileFromList}.pdf
	done < $TEMPLIST
echo

rm -f $TEMPLIST

```

Save the code in a file like tif2pdf.sh
Then make the file executable...

```
chmod a+x tif2pdf.sh

```
and the run it in the directory or directories with your tifs. e.g.,...

```
/path/to/tif2pdf.sh
```

Let me know how it works.

PS. your files will renamed filename.tif.pdf

---

### Post by kaibob on 2008-07-17
You can use the mogrify commandline utility, which is a part of the Imagemagick suite. To do this, open a terminal window and change to the directory that contains the image files. Then, enter the following:

```
mogrify -format pdf *.tif
```

The PDF files will have the same basename as the TIF files but with a pdf extension.

---

### Post by apswartz on 2008-07-17
mogrify! sweet! I will have to try it out. convert is also from ImageMagick.

---

### Post by CameronCalver on 2008-07-18
yes yes mogrigy works great but that means i need to change the command every different file is there a way to just do everything in that folder?

---

### Post by kaibob on 2008-07-18
> **CameronCalver said:**
> yes yes mogrigy works great but that means i need to change the command every different file is there a way to just do everything in that folder?

I'm not sure what you mean by every different file. The mogrify command line as given in my above posting will create a PDF file for every TIF file in the folder. You execute the command only once.

---

### Post by jonabyte on 2008-09-08
I tried the mogrify command on a folder full of scanned documents and the pdf files ended up being in poor quality.
Anyway I can get a better quality version of the pdf from a tif file?

Thanks

---

### Post by Kikin-sama on 2009-06-19
What about OCR?

---

### Post by emrys on 2009-09-15
Thank you!!!

To do it recursively (all folders and subfolders):

find -execdir mogrify -format pdf *.tiff {} +

---

