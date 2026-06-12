---
title: "PDF to HTML"
date: 2008-09-07
forum: General Help
---

### Post by WildeBeest on 2008-09-07
Can anyone point me to an editor that will convert a pdf document to html?

Thanks

---

### Post by DirtDawg on 2008-09-07
Hi. I found a [tutorial here]("http://www.ubuntugeek.com/howto-convert-pdf-files-to-html-files.html"). It's a command line tool, but it looks fairly simple and there's lots of examples. I should also say I haven't tried the suggested method before, but Ubuntu Geek is usually a great source of info and this is a relatively recent article. 

Good luck

---

### Post by brian_p on 2008-09-07
> **WildeBeest said:**
> Can anyone point me to an editor that will convert a pdf document to html?

There is poppler-utils. But it is not an editor.

---

### Post by fragos on 2008-09-07
Package "poppler-utils" give you the command line tool "pdftohtml". I tried it on a huge PDF -- over 300 pages. It gave me 3 HTML files. The 1st using the name I entered on the command line is a short HTML which displays 2 frames. One is the document and the other is an index by page number. You can of course edit the HTML output which you'll probably have to. No CSS is provided so you'll want to create one and the conversion doesn't convert special chacters to their & markup format. It also uses "<br>" for every end of line. Still this may be better than cut and paste from the PDF to a text file.

---

### Post by An85Zk9tc8rfjV8i on 2008-12-13
[http://packages.ubuntu.com/hardy/xpdf-utils](http://packages.ubuntu.com/hardy/xpdf-utils)

[http://packages.ubuntu.com/hardy/poppler-utils](http://packages.ubuntu.com/hardy/poppler-utils)

what is the hierarchy ?

I have xpdf-utils installed and to  install poppler-utils

synaptic wants to remove stuff

```

An85Zk9tc8rfjV8i@ubuntu:~$ sudo apt-get install poppler-utils
[sudo] password for user:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  xpdf-utils
The following NEW packages will be installed:
  poppler-utils
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 79.0kB of archives.
After this operation, 4489kB disk space will be freed.
Do you want to continue [Y/n]?

```
:mad:

---

### Post by sstusick on 2008-12-13
I think you could probably use OpenOffice for this, as well. Open the HTML in OpenOffice and then convert it to PDF.

---

