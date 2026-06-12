---
title: "PDF program that's less of a RAM hog?"
date: 2008-09-22
forum: General Help
---

### Post by Melindrea on 2008-09-22
I have a huge problem.

Whenever I try to open a PDF, evince starts automatically, and then I need to take a coffee break for half an hour while the computer freezes. This can't be normal.

It happens both on my laptop (fairly new, AMD 64 Athlonx2, 1GB RAM, 2gb swap) and on my desktop (not so new, Pentium 4, 512GB RAM, 1GB swap). When I check on conky now, it ate up 54% of my RAM, on my desktop. Laptop is x64, desktop is i686, both are Hardy.

Is there anything that would either a) make it less of a RAM hog, or b) a better program to use?

---

### Post by danwood76 on 2008-09-22
Is this both opening the same pdf?
It could be a bug in evince and possibly a bug in the pdf file you are viewing.

I never have issues with evince, aside from the fact you cant change many of the viewing settings.

Its worth testing with a few different pdfs just to check.

---

### Post by Melindrea on 2008-09-22
No, but it's all from the same place (drivethrurpg.net, White Wolf PDFs). They're fairly large though, since they're full game books.

---

### Post by mikewhatever on 2008-09-22
You could try using xPDF or ePDFViewer, both from the repositories, as well as several others, Adobe Reader including. Here is a nice, although not very uptodate review of PDF readers for Linux [http://polishlinux.org/apps/pdf-viewers-for-linux-compared/](http://polishlinux.org/apps/pdf-viewers-for-linux-compared/)

---

### Post by scouser73 on 2008-09-23
I would suggest Adobe Reader, [http://www.adobe.com/products/acrobat/readstep2_allversions.html]("http://www.adobe.com/products/acrobat/readstep2_allversions.html") make sure you select the x86 (.deb) installer.

---

### Post by Melindrea on 2008-09-23
Hrm.

I just tried to install Acrobat reader, and it failed... Any suggestions on what's wrong?

```
dpkg: error processing /home/(user)/Download/AdobeReader_enu-8.1.2_SU1-1.i386.deb
```

---

### Post by tacutu on 2008-09-23
install Acrobat from the repos (i.e. using synaptic).
I've had some problems with encrypted pdfs, they would hog my system. Are yours encrypted, by any chance?

---

### Post by Melindrea on 2008-09-23
HOw do I know if they're encrypted?

Edited to add: Don't ask me why, but it's apparently installed. *goes to check how good it's at opening files*

And second question: How do I turn of evince-thumbnails. That's another huge "gonna crash you!" sign.. =)

---

### Post by joao82 on 2008-11-04
ePDFviewer works fast and smooth here, I'm replacing Evince with it.

---

