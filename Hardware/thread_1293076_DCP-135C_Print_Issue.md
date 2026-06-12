---
title: "DCP-135C Print Issue"
date: 2009-10-16
forum: Hardware
---

### Post by Zedlum on 2009-10-16
I'm having a small issue with a Brother DCP-135C, basically when A4 is selected or when printing the test page (set to A4) the print starts to high on the page (off the page in some instances!)

When I installed the printer I had a few problems relating to an unset password, but I basically followed the instructions here...

[http://solutions.brother.com/linux/en_us/download_prn.html#DCP-135C](http://solutions.brother.com/linux/en_us/download_prn.html#DCP-135C)

Print quality is fine & everything is fine if you tell the software its printing US Letter size (except for it only prints 2/3s of the A4 page!)

Do you think the generic postcript PPD might be better?

Its a neighbors machine which I upgraded as a favor and at the same time talked them into trying Ubuntu over Windoze... They are very happy with the new found speed etc but the printer and scanner really need to work (scanner is the next issue!)

Thanks!

---

### Post by Zedlum on 2009-10-16
I found this on the Brother site #3 looks promising....[B]

----------------------------------------------------------------------------

_The printed portion of the page has shifted up, down, left or right._[/B] 

Incorrect margin settings can be caused by an incorrect paper size setting.

1. If you are using OpenOffice (e.g. OpenOffice Word Processor), change the document size in "Menu -> Format -> Page" to match your paper size.

2. Change the paper size setting from the cups web interface ("http://localhost:631/printers" -> "Set Printer Options")

3. Edit the paper size parameter in "/usr/local/Brother/inf/br(model name)rc" or "/usr/local/Brother/Printer/(model name)/inf/br(model name)rc" to the paper size.

***The available parameter value is in the /etc/cups/ppd/(model name).ppd file.
***This action will change the default printout paper size.

---

### Post by Zedlum on 2009-10-16
#3 did it, hard coded reference to Letter I changed it to A4.

---

