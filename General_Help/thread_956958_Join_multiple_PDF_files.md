---
title: "Join multiple PDF files"
date: 2008-10-23
forum: General Help
---

### Post by Fibonacci on 2008-10-23
Hello.

I've got a book which was scanned on a weird format: each two consecutive pages are on a separate PDF file, turned 90 degrees to the right. Of course, this makes it a pain in the neck to read - literally.

I would like to know if there is a way to do the following on Ubuntu to make it readable:
1- rotate each file 90 degrees to the left.
2- join them all in one big PDF file.
3- (optionally) convert the resulting file to a more efficient format (e.g. DjVu).

Any help will be appreciated.

-Fibo

---

### Post by kaibob on 2008-10-23
There are a number of ways to do what you want. One is to use the command-line utility, pdftk. Just install pdftk from the repo's and then read the man page.

The following rotates the PDF's 90 degrees:

```
pdftk in.pdf cat L output out.pdf
```

The following command will combine the individual PDF's:

```
pdftk in.pdf cat output out.pdf
```

You would want to use a wildcard for the input PDF files.

---

### Post by Fibonacci on 2008-10-23
> **kaibob said:**
> There are a number of ways to do this. The command-line utility PDFtk is easiest.

Thanks, looks great! Can it rotate the images too?

EDIT: Nevermind, it says so right on the man page.

---

### Post by Fibonacci on 2008-10-24
Thank you for your help, I've just tested it and it works absolutely great!

Since there are two consecutive pages per image, I would now like to split the images in half so it's easier to read. Can PDFtk do that?

---

### Post by kaibob on 2008-10-24
> **Fibonacci said:**
> Thank you for your help, I've just tested it and it works absolutely great!

Since there are two consecutive pages per image, I would now like to split the images in half so it's easier to read. Can PDFtk do that?

Pdftk can do this with the burst command:

```
pdftk in.pdf burst
```

If you have multiple input PDF files in one directory and you want to split each file into separate pages, the following command entered in a terminal window will do the job:

```
for FILE in *.pdf ; do pdftk "$FILE" burst output "$FILE-%02d.pdf" ; done
```

You would probably want to place the output PDF files in a separate directory.

---

### Post by tacutu on 2008-10-24
if I understand you correctly, "two pages per image" means that one pdf page includes 2 scaned pages. Is that true?

If so, here's a solution: 
1. install imagemagick
2. use pdfinfo to find out the size in pixels of one pdf page: width x height
3. use "convert" (from imagemagick) to crop the pdf to width/2 x height
(try "man convert" for more info)
4. use pdftk to join the files

---

### Post by kaibob on 2008-10-24
> **Fibonacci said:**
> Thank you for your help, I've just tested it and it works absolutely great!

Since there are two consecutive pages per image, I would now like to split the images in half so it's easier to read. Can PDFtk do that?

> **tacutu said:**
> if I understand you correctly, "two pages per image" means that one pdf page includes 2 scaned pages. Is that true?...

Fibonacci,

I didn't read your post closely enough. If tacutu's  understanding is correct, then pdftk will not do what you want. I agree with tacutu that you can accomplish what you want by first using convert to crop the input PDF files and then pdftk to rotate and merge the cropped PDF files. This would most easily be done with a shell script.

---

