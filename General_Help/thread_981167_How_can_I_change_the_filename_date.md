---
title: "How can I change the filename date?"
date: 2008-11-13
forum: General Help
---

### Post by LsrLine on 2008-11-13
I'm scanning in all my old pictures, so I have a digital copy.  Unfortunately, F-Spot doesn't really change the date of the file, so if I copy the pictures over after an upgrade it won't carry the date over.  How can I change the date of these pictures to reflect the date at which they were taken (i.e. a picture from 1972 would actually show that the file is from 1972 when you click properties).  Thanks.

---

### Post by LowSky on 2008-11-13
Well I'm no genious but computers/scanners/digital cameras/any of the file extentions didn't exist back in 1972...lol, so you could really have a file with a date that old.
As for changing the file information in properties you really cant. It would be better to sort your picture in folders with date rather than by the files properties

EDIt well I was kinda wrong you can with software like this [http://www.febooti.com/products/filetweak/](http://www.febooti.com/products/filetweak/)

dont know if it works with linix, most likely not

---

### Post by LsrLine on 2008-11-13
> **LowSky said:**
> Well I'm no genious but computers/scanners/digital cameras/any of the file extentions didn't exist back in 1972...lol, so you could really have a file with a date that old.
As for changing the file information in properties you really cant. It would be better to sort your picture in folders with date rather than by the files properties

EDIt well I was kinda wrong you can with software like this [http://www.febooti.com/products/filetweak/](http://www.febooti.com/products/filetweak/)

dont know if it works with linix, most likely not

I might not have been as clear.  I want the file (maybe it's called meta data) to read as if it were from 1972.  Every file I scan in now will say 2008 obviously because it was created when i scanned it in.  I could try out that program, but it seems it's for windows. :(  I have Virtual Box and wine, so i can give it a shot, but I'd like to stay within Ubuntu.

---

### Post by philinux on 2008-11-13
Yes using the touch command.

This alters the modified date


touch -m -t 09082000 testfile  (thats MMDDYYYY)

---

### Post by snova on 2008-11-13
It depends. Are you trying to change the modification time on the file, or the metadata stored inside the image?

---

