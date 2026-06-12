---
title: "Japanese text in .pdfs not displaying properly?"
date: 2008-11-03
forum: General Help
---

### Post by bzzx on 2008-11-03
Hi,

Whenever I try to view a .pdf with Japanese text (for one of my classes), the parts within the pdf that have Japanese text are missing. This problem only popped up very recently because I upgraded to 8.10 this afternoon; I was having no problems displaying these same .pdfs prior to the upgrade. I've googled for the solution and found a few threads in the archive that say to install the xpdf-japanese package, but that hasn't worked for me.

Can anyone suggest a solution?

Cheers,
bzzx

---

### Post by tacutu on 2008-11-03
dunno about 8.10 but in 8.04 you need poppler-data installed. (assuming, of course, you use the default evince).
(or use acroread w/ the CJK fontpack installed)

---

### Post by bzzx on 2008-11-03
> **tacutu said:**
> dunno about 8.10 but in 8.04 you need poppler-data installed. (assuming, of course, you use the default evince).
(or use acroread w/ the CJK fontpack installed)

Yeah, like I said in my first post, the same .pdfs were showing up perfectly fine when I was running 8.04 (installed 8.10 today). And yes, I'm using the default evince.

---

### Post by tacutu on 2008-11-03
well, do you have poppler-data installed?

---

### Post by bzzx on 2008-11-04
Wow, installing poppler-data did the trick. I apologize for not reading your first post properly - it was late into the night for me and I was tired. :oops: I guess I skimmed over it and just saw something about using the default evince. Thanks for your time and patience!

---

### Post by tacutu on 2008-11-04
no problem!
happy to be of assistance!

---

