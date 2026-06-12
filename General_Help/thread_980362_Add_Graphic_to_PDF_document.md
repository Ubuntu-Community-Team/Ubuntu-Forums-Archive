---
title: "Add Graphic to PDF document?"
date: 2008-11-12
forum: General Help
---

### Post by dschaller on 2008-11-12
I need to add a graphic to an existing PDF file (a small barcode in this case). I've tried PDFedit and it is not able to do this. I know I could easily convert the PDF to an image and then add the graphic, but then I would no longer be able to search the text of the document. I figured this shouldn't be that hard, but I've been working on it for an hour now with no success.

---

### Post by cariboo on 2008-11-12
Check the properties of the document it may be set to uneditable.

Jim

---

### Post by dschaller on 2008-11-12
It is an editable document. Maybe I am missing something, but I don't even see an option to add graphics with PDFedit. In the last 45 minutes I have had partial success using OpenOffice 3 with the pdfimport extension. I was able to edit in OODraw and then re-export to PDF. It worked except that it did not preserve the full justification of the original document when I imported it. It changed all the text to flush left. The extension is beta, so I'm not too surprised it wasn't perfect.

I'm still wondering, though, if there's a better solution. Even if someone knew of a freeware Windows PDF editor that would do this. I've got XP in a virtual machine I can use.

---

### Post by ad_267 on 2008-11-12
Inkscape has pdf import, but I'm not sure if it works for multiple page documents.

---

### Post by dschaller on 2008-11-12
I haven't tried importing a single page in Inkscape. I did notice that PDF was not listed in the file type list when I clicked import in Inkscape.

I did discover that Foxit PDF Editor for Windows does exactly what I need, but it's not free ($99). Ugh.

---

### Post by ad_267 on 2008-11-12
You're right, it isn't listed there. But just find a pdf file and import it, it works. You can select what page you want to import and then save it again as a pdf. You should then be able to use a command line tool to insert that page back into the document. Not really the best solution but it should work.

---

### Post by dschaller on 2008-11-13
I get a "Failed to load requested file" error whenever I try to import a PDF with Inkscape. I'm using Ubuntu 7.10 with Inkscape 0.45. Maybe PDF import only works on newer versions?

---

### Post by ad_267 on 2008-11-14
Could be, I'm using 0.46 in Ubuntu 8.10.

---

