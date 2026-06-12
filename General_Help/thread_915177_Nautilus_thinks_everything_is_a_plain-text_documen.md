---
title: "Nautilus thinks everything is a plain-text document"
date: 2008-09-09
forum: General Help
---

### Post by russlar on 2008-09-09
Hello all,

I've got some .pdf and .tar.gz files that somehow are being recognized as plain-text documents, and not PDF documents or archives. This is problematic, as I can't open PDF files in Document viewer, not can I add GDM themes, as those need to be archives. I'm currently running a fairly fresh install of Hardy 64-bit, with Firefox 3.0.1.

---

### Post by mc4man on 2008-09-09
if you r. click on a .pdf or .tar.gz file ->** properties** -> open with, what do they show for app to open with?

---

### Post by russlar on 2008-09-09
> **mc4man said:**
> if you r. click on a .pdf or .tar.gz file ->** properties** -> open with, what do they show for app to open with?

I manually changed the .tar.gz to Archive Manager, but this hasn't cleared up the issue with the Login Manager control being able to open the file.

UPDATE: It appears that this issue is isolated to the Login Window config utility, and it not recognizing .tar.gz as archives, and it's lack of a "View all files" filtering option

---

### Post by fragos on 2008-09-09
mime type can be identified by file content and by extension like .pdf. Do these unrecognizable files have the correct extension?

---

### Post by russlar on 2008-09-09
> **fragos said:**
> mime type can be identified by file content and by extension like .pdf. Do these unrecognizable files have the correct extension?

Yes. .tar.gz archives are being downloaded from the internet (gnome-look.org), and they have the .tar.gz extension. Either Firefox is mangling them, or GDM/Nautilus is mangling them.

---

### Post by russlar on 2008-09-09
Just had Archive Manager try to open a .jpg. :confused:

---

### Post by russlar on 2008-09-09
I'm now also unable to change my desktop background, as no files are being recognized as images.

---

### Post by fragos on 2008-09-09
The only time I've experienced any strangness with mime type is when I've downloaded a file whose actual type disagreed with the file extension. I've never seen anything quite like what you're experiencing.

---

### Post by russlar on 2008-09-10
> **fragos said:**
> The only time I've experienced any strangness with mime type is when I've downloaded a file whose actual type disagreed with the file extension. I've never seen anything quite like what you're experiencing.

yeah, it's like every file I downloaded was written with the same MIME headers. :confused:

A fresh OS load fixed it.

---

