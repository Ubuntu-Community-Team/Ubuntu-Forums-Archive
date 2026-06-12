---
title: "Where is ps2pdf in Intrepid Ibex?"
date: 2008-12-26
forum: Installation &amp; Upgrades
---

### Post by unrater on 2008-12-26
Hi all,

Well, today I saw that the new Intrepid Ibex doesn't have the ps2pdf package. And I would like to install it.

How can i solve it?

Thanks for help ;)

---

### Post by taurus on 2008-12-26
You probably need the texlive-base-bin package.  It's in the repos so look for it in synaptic.

---

### Post by unrater on 2008-12-26
And then I have the terminal's command ps2pdf??

---

### Post by unrater on 2008-12-30
Sorry because of the double post, but, I searched so much and I can't understand why in others distributions have it and in Intrepid not.

Some help?

---

### Post by stderr on 2008-12-30
Seems to be in 'ghostscript' (from apt-file search ghostscript). 

```
sudo dpkg -L ghostscript
```

gives me:

/usr/bin/pdf2dsc
/usr/bin/pdf2ps
/usr/bin/pdfopt
/usr/bin/pf2afm
/usr/bin/pfbtopfa
/usr/bin/printafm
/usr/bin/ps2ascii
/usr/bin/ps2epsi
/usr/bin/ps2pdf
/usr/bin/ps2pdf12
/usr/bin/ps2pdf13
/usr/bin/ps2pdf14
/usr/bin/ps2pdfwr
/usr/bin/ps2ps
/usr/bin/ps2ps2
/usr/bin/wftopfa

amongst others, so I reckon

```
sudo apt-get install ghostscript
```

 should do the trick

---

### Post by unrater on 2008-12-30
wow, i didn't knew that first command.

Thank you very much!

Problem solved!

---

