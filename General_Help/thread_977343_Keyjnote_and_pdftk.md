---
title: "Keyjnote and pdftk"
date: 2008-11-10
forum: General Help
---

### Post by Jacob Collstrup on 2008-11-10
Heya,

I just installed keyjnote and pdftk, from the repo. But I don't know how to use them. I have 2 pdf-files I need to combine, and I have no clue how to do it. I downloaded to files from the pdftk site. Some gui-frontends, they have the .tar.gz-format. One contains an executable file (nothing happens when I double click it) and a config file:
guipdftk
guipdftk.config

And the other has 5 files called:
unit1.pas
project1.lpi
project1.lpr
unit1.lfm
unit1.lrs

This later one apparently requires lazarus(spelling?) compiler. I don't know how to make either one work. I thought I could direct the terminal to the directory and type 'make && install' but I got an error message saying that there is no 'target' file or something like that.

Jacob

---

### Post by kaibob on 2008-11-10
> **Jacob Collstrup said:**
> Heya,

I just installed keyjnote and pdftk, from the repo. But I don't know how to use them. I have 2 pdf-files I need to combine, and I have no clue how to do it....

I can't be of help with keyjnote but PDFtk is easy to use as a command-line tool. To combine two PDF files, open a terminal window, navigate to the applicable directory, and enter:

```
pdftk input1.pdf input2.pdf cat output output.pdf
```

You need to insert the actual input and output file names in the above.

Some additional help with PDFtk can be found at:

[http://www.accesspdf.com/article.php/20041129175231241](http://www.accesspdf.com/article.php/20041129175231241)

---

