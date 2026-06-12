---
title: "Epson Stylus CX9400F"
date: 2008-11-09
forum: Hardware
---

### Post by Daktyls on 2008-11-09
I got the Epson Stylus CX9400 Fax to print (properly) under Hardy Heron (8.04) using the following method.

After plugged in and turned on Hardy autodetected it and it could printer, but there were miscolorations in the test page. So to fix I went to the Printer Configuration window (System -> Administration -> Printing), and changed the "Make and Model" to

"Epson Stylus CX9400F - CUPS+Gutenprint(OpenPrinting LSB 3.2) v5.2.1 Simplified)"

Then, switching the the 'Printer Options' tab, I changed the Colormode to "CMY Color".

After that, it printed the test page properly, and with no miscolorations.

To get the scanner to work, I just installed 'libsane-extras' with:

```
sudo apt-get install libsane-extras
```

After that, the scanner was detected by Xsane and it worked fine.

---

### Post by SadaBena on 2009-03-04
Greetings! I am very new to the Ubuntu world as well as to these good ol' forums, and I am finding myself in a predicament. I'm currently using Intrepid and I cannot get my CX9400f to print proper colours. On the test print, the red is coming up quite orange, and so on.
 I tried walking through the steps stated before, but when I went to(System -> Administration -> Printing), and renamed the printer "Epson Stylus CX9400F - CUPS+Gutenprint(OpenPrinting LSB 3.2) v5.2.1 Simplified)"  
I got an error message saying "CUPS Server Error, there was an error during the CUPS operation: 'client-error-bad-request'"  
I then attempted to simply change the Colour mode to "CMY colour", but when I tried a test print there was a printing error, so I went through the troubleshooter, the printer's state message was 'Specified ColourSpace not supported'.  It  turns out that the only colour spaces that I can get to work are RBG Colour and CMYK, both of which are off colour.

And to add insult to injury, I can't get xsane to recognise the scanner portion either, even after installing 'libsane-extras'. (grrrrrrr)
 Any thoughts or comments on either problem would be greatly appreciated.

---

