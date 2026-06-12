---
title: "Canon Pixma mg5150 Printer"
date: 2011-10-30
forum: Hardware
---

### Post by GodveX on 2011-10-30
hey guys i ran into a small problem i downloaded the proper print and scan drivers for my printer and installed them using terminal i can now scan documents by typing scangearmp into the terminal and i can print too.

the problem is that when i print a document my printer will keep the printing the same document over and over again it seems like there is a never ending print job going on any ideas how to fix this please ?

How I fixed this problem:
in order to fix this problem from my research done is first check the printer settings and look for a parameter copies and make sure it is set to 1 if it is set to one like mine was i installed cups with this command in the terminal 
```
sudo apt-get install cups-pdf
``` and my printer started printing fine

---

