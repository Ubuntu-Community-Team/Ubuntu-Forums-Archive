---
title: "[SOLVED] Help setting up brother printer (not printing right)"
date: 2007-10-25
forum: Hardware &amp; Laptops
---

### Post by ruialexbarbosa on 2007-10-25
Hi,

I'm on Feisty and have a Brother MFC425CN (similar to the MFC210C) on a small home network which works flawessly printing with my ibook, but not with UBUNTU.

The problem is it prints everything 2cm more to the top of the sheet than it should... I'm sure it is a problem with the driver, but there are no other drivers available...

Can someone help me setting this up to print properly?

Thanks

Alex

---

### Post by froy02 on 2007-10-26
See if you can set it up using firefox by typing "http://localhost:631".  Click on the printers tab when it comes up then choose modify printer.

---

### Post by mknox on 2007-10-28
Firefox Printer Settings to keep printing within the margins:
Start at the menu bar of Firefox:
Goto File/Page Setup...
Select the Margins & Header/Footer Tab and set the top,bottom,left,right to 0.3 inches
Goto File/Print...
Select Properties Button in Printer box and set the "Gap from edge of paper to Margin", Top,Bottom,Left,Right to 0.1 inches
The key is that the 0.3 is larger than the 0.1 inches, its a arbitrary number.
The Firefox Browser is now set to print correctly.

---

### Post by ruialexbarbosa on 2007-10-29
Thanks a lot guys,

will do some tests now.

---

### Post by ruialexbarbosa on 2007-10-31
How about if I want to print in openoffice?

---

### Post by tubasoldier on 2007-10-31
that was kind of a large hack for your printer paper. I have a brother and for some reason it trys to print to an A4 sheet of paper instead of US letter. I had to change the page type to "letter" instead of "a4". Works like a charm now.

---

### Post by ruialexbarbosa on 2007-11-10
I wrote to Brother's Solutions Center and they helped me sorting the problem. It's great now. Here's the instructions I followed:

1.Are you setting the paper size at the CUPS Web interface
"http://localhost:631/printers"?
Click on "Configure Printer" or "Set Printer options" of your printer
entry, and check the setting.


2.If you are printing directly text files without converting them to the
PostScript files,
margin problems would be generated.

Would you please try the following?
1.Find /usr/local/brother/Printer/lpd/filterMFC210
2.Find a line which includes
  A2PS_OPT="--output=-     &#12539;&#12539;&#12539;&#12539;" (around 55th line)
3.<A4>
  Edit A2PS_OPT="--output=-     &#12539;&#12539;&#12539;&#12539;"
  to  A2PS_OPT="--medium=A4  --output=-     &#12539;&#12539;&#12539;&#12539;"
  <Letter>
  Edit A2PS_OPT="--output=-     &#12539;&#12539;&#12539;&#12539;"
  to  A2PS_OPT="--medium=Letter  --output=-     &#12539;&#12539;&#12539;&#12539;"

---

