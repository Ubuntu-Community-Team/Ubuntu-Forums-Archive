---
title: "Cups-pdf pipe to xpdf or similar"
date: 2008-08-12
forum: General Help
---

### Post by tigerbaiter on 2008-08-12
Hi, 

I've got the cups-pdf printer installed, enabling me to print to a pdf file. What I'd like to do is postprocess it so that it opens xpdf or similar with the contents of the pdf.

Any ideas?

---

### Post by brunovecchi on 2008-09-21
I'm not sure if I understand you to the detail. But if you are using a command to generate your pdf file, you can append this to instantly open that file if the process succeded:

```
$ your-pdf-command out.pdf && xpdf out.pdf 
```

xpdf could be replaced with evince, acroread, okular or any other pdf reader application. The double ampersands mean that the command to the right of them should only be executed if the comand to the left succeded.
Hope it helps.

---

### Post by Whiffle on 2008-09-21
If you look in /etc/cups/cups-pdf.conf , at least under arch, there is a section around line 250 that allows you to do this sort of thing.

---

### Post by kaibob on 2008-09-21
The following post describes how I used the postprocessing function of cups-pdf to name the PDF file. To open the PDF file with xpdf, you would simply change the last two lines of the script.

[http://ubuntuforums.org/showthread.php?t=893968](http://ubuntuforums.org/showthread.php?t=893968)

---

