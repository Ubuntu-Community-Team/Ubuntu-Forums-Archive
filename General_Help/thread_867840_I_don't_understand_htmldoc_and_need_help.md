---
title: "I don't understand htmldoc and need help"
date: 2008-07-23
forum: General Help
---

### Post by OttifantSir on 2008-07-23
I have a folder with the owner's manual for my laptop, and the files are HTML. I wish to convert them to PDF and merge them with links to headings and chapters in that PDF-file. First off, I need to understand htmldoc. I have the man pages, yet I can't create a PDF-file.

My latest command was: ```
htmldoc about.htm --book -t pdf13 --no-strict --quiet about.pdf
```

Others I have tried: ```
htmldoc --book -t pdf13 --no-strict --quiet about.htm about.pdf
 htmldoc --format pdf14 about.htm about.pdf
 htmldoc --continuous --format pdf14 about.htm about.pdf
 htmldoc --continuous --format pdf14 about.htm
 htmldoc --book --format pdf14 about.htm
 htmldoc --book --format pdf14 about.htm /home/ottiserver1/Dokumenter/about.pdf
 htmldoc --book --format pdf13 *.htm /home/ottiserver1/Dokumenter/%f.pdf
 htmldoc --book --format pdf13 *.htm /home/ottiserver1/Dokumenter/%n.pdf
 htmldoc --book --format pdf14 *.htm /home/ottiserver1/Dokumenter/
```

Can someone please tell me what command I need to issue, or what information I need to find in order to compose the right command?

The output is some garbled text and a beeping symphony from my PC speaker.

---

