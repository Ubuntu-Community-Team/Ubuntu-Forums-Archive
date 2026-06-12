---
title: "Epson Stylus DX 3850"
date: 2006-04-19
forum: Hardware &amp; Laptops
---

### Post by Jos_Havinga on 2006-04-19
I've just bought a Epson Stylus DX 3850 and I have Ubuntu 5.10. Can somebody tell me how te get my new printer working? Ubuntu doesn't know this printer and the cd doesn't help me anything.

---

### Post by Sef on 2006-04-19
This says it will support your printer, but not your scanner.

[http://sourceforge.net/project/shownotes.php?release_id=387201&group_id=1537]("http://sourceforge.net/project/shownotes.php?release_id=387201&group_id=1537")

For your scanner, try downloading libsane-extras

sudo apt-get install libsane-extras

---

### Post by kristalsoldier on 2007-03-08
> **Sef said:**
> This says it will support your printer, but not your scanner.

[http://sourceforge.net/project/shownotes.php?release_id=387201&group_id=1537]("http://sourceforge.net/project/shownotes.php?release_id=387201&group_id=1537")

For your scanner, try downloading libsane-extras

sudo apt-get install libsane-extras

Hi...

My experience: I have downloaded the above...but the scanner does not work...nor does the printer despite having the recommended drivers installed. Your mileage may, of course, vary!

Edit: The printer works. There was something wrong with the packages, which has now been fixed. But the scanner still does not work...yet!

---

