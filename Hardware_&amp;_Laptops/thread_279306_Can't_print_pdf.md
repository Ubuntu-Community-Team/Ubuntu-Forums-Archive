---
title: "Can't print pdf"
date: 2006-10-17
forum: Hardware &amp; Laptops
---

### Post by mangsman on 2006-10-17
I have an hp 1315 and I added the printer successfully as well as installing the hplip driver. I can print everything except for pdfs. What might be the the problem?

---

### Post by meng on 2006-10-17
When you print the pdf (you didn't specify which program you are using - Adobe Acrobat, kpdf, xpdf), are you sure you're outputing to a printer and not a file? and is that printer accessed with the command "/usr/bin/lpr"?

---

### Post by mangsman on 2006-10-17
I was trying to print in Adobe and Evince and the command was /usr/bin/lp

---

### Post by meng on 2006-10-17
I guess /usr/bin/lp should give the desired result, I've never understood what the difference between lp and lpr was anyway.

---

### Post by mangsman on 2006-10-18
So i still can't print pdfs...does anyone have any advice?

---

### Post by johantc on 2008-02-14
I've had the same problem. I normally use a work around for this problem.
pdf2ps <your document>. You might want to specify an output destination. My default is /home

Then open the .ps file and print :)

---

