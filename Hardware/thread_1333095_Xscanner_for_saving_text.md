---
title: "Xscanner for saving text?"
date: 2009-11-21
forum: Hardware
---

### Post by Camilia on 2009-11-21
Having problems saving scanned article as text so that I can edit it. Have been trying the options out with no success. How do I do this? Are there any articles on how to do this? The help button on scanner only gives me page not found.

Top area have options:
Viewer, save, copy, multipage, fax, email

When use save have type options: 
by ext, jpeg, pdf, png, pnm, postscript, text, tiff.  

Also when I start it up I get notice failed to create file. Permission denied. Could this be causing problems?

---

### Post by IcarusR on 2009-11-21
I believe you need to use an OCR software, gocr perhapse.

---

### Post by Camilia on 2009-11-21
I have ocr programs:
ocrad, tesseract-ocr, tesseract-ocr-dev, tesseract-ocr-eng, tesseract-ocr-deu.

When I use copy option in converts document and saves it. I can't find where it saves it.  In preverences> setup> copy I see printer selection is new printer. 

In preverences>setup>save it has temp directory /tmp/. I change it to documents but it reverts back.

---

### Post by IcarusR on 2009-11-21
Found this howto... [http://www.howtoforge.com/ocr_with_tesseract_on_ubuntu704]("http://www.howtoforge.com/ocr_with_tesseract_on_ubuntu704")
Says should result in files result.txt, result.map and result.raw

Sorry I can n't be more help you. I've never used either Xsanner or any of the ocr packages listed. 
I use xsane & gocr.

---

### Post by jesuisbenjamin on 2009-12-03
Hello there!

I am interested in GOCR, but the Debian Packages link is not working. I cannot find GOCR with synaptic. How can i get GOCR or any good OCR program?
(i have to convert large amounts of scanned pages).

Also can it convert roman unicode, or letters with diacritics such as &#257; &#275; ect?

Thanks.B.

---

### Post by Camilia on 2009-12-11
> **IcarusR said:**
> Sorry I can n't be more help you. I've never used either Xsanner or any of the ocr packages listed. 
I use xsane & gocr.
Do you use these programs to save text? What programs have you downloaded to use xsane & gocr?

---

### Post by Statik on 2009-12-15
```
sudo apt-get install gocr
```

worked for me!

Statik

---

