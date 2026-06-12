---
title: "How do I install fonts on Ubuntu?"
date: 2008-08-25
forum: General Help
---

### Post by Guyon on 2008-08-25
Sorry, I'm brand new to Linux. How would I install a random font such as this: [http://www.dafont.com/bleeding-cowboys.font](http://www.dafont.com/bleeding-cowboys.font) on Ubuntu?

Problem solved, thanks guys.

---

### Post by Steve1961 on 2008-08-25
> **Guyon said:**
> Sorry, I'm brand new to Linux. How would I install a random font such as this: [http://www.dafont.com/bleeding-cowboys.font](http://www.dafont.com/bleeding-cowboys.font) on Ubuntu?

Just create a .fonts directory in your home folder and drop the fonts in there.

---

### Post by Brebs on 2008-08-25
```
mkdir -p ~/.fonts/
cp blah.ttf ~/.fonts/
```

---

### Post by silkstone on 2008-08-25
Download the zip file and extract the ttf file.

Then create a new folder called **.fonts** in your home folder (i.e. /home/yourusername/.fonts)

Copy the .ttf file to that folder and it should be recognised. (Can't remember if you have to log off and on again for it to be picked up.)

---

