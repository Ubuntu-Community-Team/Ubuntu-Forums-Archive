---
title: "Printing to PDF - without headers or footers"
date: 2008-10-21
forum: General Help
---

### Post by cendant on 2008-10-21
Creating PDFs is very easy - just print to PDF.

Unfortunately, the created PDFs also contain web page names, URLs in the header and page numbers, date in the footer.

In Intrepid you can disable those settings in the Print dialog in Options tab. 

However, you have to set the to <blank> every time you print. Annoying!

Do you happen to know how to disable adding stuff to headers/footers in PDFs for good?

---

### Post by shawnrgr on 2008-10-21
Firefox ... file->print->options->header and footer

---

### Post by cendant on 2008-10-22
Thanks. 

But that is my point - you have to change those settings for every PDF you create. With 

Is it possible to set them to --blank-- permanently somewhere in config files?

---

### Post by shawnrgr on 2008-10-22
navigate to "about:config"
search for "_header"
clear all string values for each entry

---

