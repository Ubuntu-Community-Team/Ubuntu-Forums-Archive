---
title: "canon Pixma iP4000 printing in quarters"
date: 2006-10-18
forum: Hardware &amp; Laptops
---

### Post by weird_c00kie on 2006-10-18
after messing up and reinstalling ubuntu 5 times i've finally got most things running smoothly. the one thing i just can't figure out though is my printer.
it's a Canon Pixma iP4000. i installed the drivers for it and all that, so it 'works'. the problem is that whenever i try printing, it always shrinks the page to fit into a quarter of the actual A4 sheet. i've looked through any settings i could find for the printer and i saw nothing that would be making it print like that.
when i print a Test Page it prints fine, covering the entire length of the page without any shrinking, but for anything else, from ANY application i've tried so far, it shrinks the page being printed to a quarter of the A4 sheet.

does anyone have any idea what's going on there?


by the way, if it makes any difference, i'm running ubuntu 6.06 on an amd64

any and every bit of help will be very much appreciated :)

---

### Post by John.Michael.Kane on 2006-10-18
Did you have a look over the info here [http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP4000](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP4000)

---

### Post by weird_c00kie on 2006-10-20
hey, thanks for the response :)

i don't really understand what they're saying on that page though. all i get is that i need the "gutenprint" drivers. i looked on synaptic, but i'm not sure which package it is i'm meant to have
if it helps, i already have these installed:

footmatic-db-gutenprint
ijsgutenprint
libgutenprint2
libgutenprintui1-1
libgutenprintui2-1

---

### Post by weird_c00kie on 2006-10-26
*bump*

anyone else have any ideas?

---

### Post by weird_c00kie on 2006-10-29
this problem is just bizarre...

yesterday i tried printing directions from [www.whereis.com.au](www.whereis.com.au) and what it did was... it printed the image across the page like normal, and the lines from the table as well, but it still shrank and wrapped all the text to fit on one quarter of the page.

the other annoying thing is that i told it to print grayscale, but it printed in something more like bluescale instead.

the drivers just don't seem to be working very well at all :/

---

### Post by dacut on 2006-10-30
I'm also having the same problem, also on an AMD64.  I suspect the issue might lie in 64-bit incompatibilities with the Gutenprint driver.

---

### Post by weird_c00kie on 2006-10-30
i hope it gets addressed at some point. it's a real hassle having to restart and boot into XP everytime i need to print :(

---

### Post by weird_c00kie on 2006-11-03
*bump*

problem still there... any ideas anyone?

---

### Post by Sef on 2006-11-03
Do you have an amd 64 bit computer?

---

### Post by weird_c00kie on 2006-11-03
i curse myself everyday for buying it, but yes i do

---

### Post by dacut on 2006-11-04
My workaround idea here is to install cups and gutenprint into a 32-bit chroot environment.  Still banging my head against the wall on silly CUPS/PAM interaction errors ("CUPS-Add-Modify-Printer: Unauthorized" and "cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!").

This is all well off the beaten path, though, so...

---

### Post by weird_c00kie on 2006-11-04
what's a 32-bit chroot environment? heheh


so is my problem a known problem for 64-bit AMDs?

---

### Post by skenliv on 2006-12-11
No, im having the exact same problem.

---

### Post by budgie9 on 2006-12-11
You may like to try using one of the other Canon drivers. I did have the same problem with my Canon at first until I downloaded the correct drivers from the Canon Japan site. Then all worked fine.
I did use the 7000 and 4000 drivers in the list and they printed fine albeit slightly to the left of the page.
Hope this helps.

---

### Post by weird_c00kie on 2006-12-21
budgie, would it be possible to provide me with a direct URL to the drivers? i looked on the canon site but i can't find any drivers for linux :(

---

