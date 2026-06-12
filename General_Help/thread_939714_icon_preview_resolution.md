---
title: "icon preview resolution"
date: 2008-10-06
forum: General Help
---

### Post by Patr!ck on 2008-10-06
Hi Everyone

I have a few hundred invoices that I would like to rename by invoice number. I can almost see the invoice numbers of the documents from the icon preview but not quite. Is there some way to alter the sampling resolution of the preview in icon mode?

Thanks for reading my post-Patrick

---

### Post by geirha on 2008-10-06
If you zoom in, the icons will be bigger and show more text in the preview. You can either use the magnifying glasses at the top right of the nautilus window, or hold down the CTRL-key while flipping the mouse wheel or hitting - and + on the keyboard.

Also, if these files are plain text files, it's probably easier to make a shell script that renames them based on the content of the first line or similar.

---

### Post by Patr!ck on 2008-10-06
Thanks Geirha

It's not the zooming that is actually the trouble but the resolution. The image is so badly pixilated at 400% it is not readable. There must be a sampling size variable somewhere. If it was 1K and I changed it to 10K I'd be all set. 

Thanks for your bash suggestion too but the trouble is I don't know what to rename the invoices to without opening each file.

---

### Post by geirha on 2008-10-06
What type of file is it? PDF?

---

### Post by Patr!ck on 2008-10-06
Hi Again Geira

Yes they are PDFs

---

### Post by geirha on 2008-10-06
Then I think it would be easier to install the package [poppler-utils](apt://poppler-utils) which provides the command pdftotext, and use that to extract the first portion of each pdf as text. (Not sure if poppler-utils is pre-installed or not)

Open a terminal, cd into the directory where all those pdfs are, and paste this:
```

for file in *.pdf; do
  echo "$file:"
  pdftotext "$file" - | head
done

```

It should show the first 10 lines of each file. If you want to limit it to two lines for example. then add " -n 2" behind "head". i.e.
```
  pdftotext "$file" - | head -n 2
```

Should give you a fairly nice preview to work with I hope.

The shell script could further parse the information for you and decide what to rename them to, but that depends on how the files look. If you provide some samples I could help you with that.

---

### Post by Patr!ck on 2008-10-06
Great Suggestion!

Thanks!!

---

