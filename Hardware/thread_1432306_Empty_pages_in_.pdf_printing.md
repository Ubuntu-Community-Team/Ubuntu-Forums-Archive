---
title: "Empty pages in .pdf printing"
date: 2010-03-17
forum: Hardware
---

### Post by Liveman on 2010-03-17
Anyone knowing why Brother HL 2030 Prints empty sheet after every page of .pdf print?
Very annoying, removing all those empty pages.

//Liveman

---

### Post by Sef on 2010-03-19
Moved to Hardware and Laptops.

---

### Post by srs5694 on 2010-03-19
Check the page size options. It could be the PDF was formatted for European A4 and you're printing on US letter sized paper (or some other similar mis-match of PDF and physical sheet sizes). Since A4 is slightly narrower but longer than US letter, the result can be an attempt to print about half an inch of the bottom of each PDF "page" on its own sheet. (Going the other way could produce similar results as the system tried to print the right or left edge of the US letter page on an A4 sheet.) Depending on your PDF viewer, there may be a print option to shrink the page to fit, and that will probably do what you want. Alternatively, you could track down some A4 (or whatever) paper, configure CUPS to use it, and print it that way. Obviously, clicking a "shrink to fit" check box is likely to be easier.

---

