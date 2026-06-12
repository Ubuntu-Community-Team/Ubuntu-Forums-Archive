---
title: "Cant' print some pdf files created by windowz pc's"
date: 2008-07-19
forum: General Help
---

### Post by ruipedroca on 2008-07-19
Hi,

I cant' print some pdf files created by windows pc's, but some I can!
This are work documents which I received by email and I must be able to print.
I'm using Kubuntu 8.04.
How can I solve this problem?

Regards

---

### Post by Sef on 2008-07-19
What word processor are you using to print them up?

---

### Post by pauper on 2008-07-19
Try converting *.pdf to *.ps and print as *.ps file.

```
sudo apt-get install ghostscript
```

Note: Conversion might not work at all in certain cases, or you will get a
slightly different document layout.
Example,
```
man pdf2ps
pdf2ps -dLanguageLevel=1 ~/path/to/file.pdf > ~/path/to/new_file.ps
```

Or:

```
pdf2ps ~/path/to/file.pdf > ~/path/to/new_file.ps
```

Or:

```
pdf2ps -dLanguageLevel=3 ~/path/to/file.pdf > ~/path/to/new_file.ps
```

For other utilities check:
[http://www.physics.usyd.edu.au/~rennie/ps_notes.html](http://www.physics.usyd.edu.au/~rennie/ps_notes.html)

---

### Post by kaibob on 2008-07-19
I'm occasionally unable to print PDF files with Evince. In many (but not all) instances, I am able to print these files by entering the following command in a terminal window:

```
lpr filename.pdf
```

I don't know if this will help, but it only takes a minute or so to try.

---

### Post by ruipedroca on 2008-07-21
Hi,

Thanks all for your kind support.

I've tested all the options and the only one that worked was doing this in the respective directory:
lpr filename.pdf
It opened a printer window, I've just hit "print" and it printed!

And I don't know what word processor was used to create the pdf file, because I've received it by email.

Best regards

---

