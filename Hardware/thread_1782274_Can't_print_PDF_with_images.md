---
title: "Can't print PDF with images"
date: 2011-06-14
forum: Hardware
---

### Post by Ginosal on 2011-06-14
Hi. I've got an Epson Stylus Color DX4400 and Ubuntu 11.04. I've never had problems printing pdf docs, but now I've found a file with images and I can print only the pages with no images inside. The file is the following one:

[http://www.google.it/url?sa=t&source=web&cd=17&ved=0CHIQFjAQ&url=http%3A%2F%2Fdocenti.unimc.it%2Fdocenti%2Fstefano-perri%2Ffondamenti-di-economia-e-micro%2Fdispense-del-i-semestre%2Fpiero-sraffa%2Fat_download%2Ffile&ei=Zab3TbGVEZDHtAbm9LyKCQ&usg=AFQjCNGZcYjNQ3RQlcSl0O1eq75hAJU0Sw&sig2=zcQGQt8flXeuKda4RNFXAw](http://www.google.it/url?sa=t&source=web&cd=17&ved=0CHIQFjAQ&url=http%3A%2F%2Fdocenti.unimc.it%2Fdocenti%2Fstefano-perri%2Ffondamenti-di-economia-e-micro%2Fdispense-del-i-semestre%2Fpiero-sraffa%2Fat_download%2Ffile&ei=Zab3TbGVEZDHtAbm9LyKCQ&usg=AFQjCNGZcYjNQ3RQlcSl0O1eq75hAJU0Sw&sig2=zcQGQt8flXeuKda4RNFXAw)

I can't print pages 6, 14... all the pages with pictures!

The message I get is: */usr/lib/cups/filter/pdftoraster failed*

Is there anything I can do?

---

### Post by dandnsmith on 2011-06-14
Maybe your sig gives the clue - OK for me with Ubuntu 10.04 and Adobe 9.4.2

---

### Post by Ginosal on 2011-06-15
> **dandnsmith said:**
> Maybe your sig gives the clue - OK for me with Ubuntu 10.04 and Adobe 9.4.2
Dandnsmith, I think that too... maybe I should go back to a former cups version? Or just use Adobe!

---

### Post by dandnsmith on 2011-06-15
I assumed that you might also be displaying the quoted page directly, and that you have an Adobe plugin to interpret the pdf.
Anyway, I suspect that pdftoraster gets invoked when printing it.

---

### Post by Ginosal on 2011-06-19
Solved with Adobe Acrobat Reader instead of Evince. Thank you! :)

---

