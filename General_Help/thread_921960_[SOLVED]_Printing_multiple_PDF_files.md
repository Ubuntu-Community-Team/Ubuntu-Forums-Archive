---
title: "[SOLVED] Printing multiple PDF files"
date: 2008-09-16
forum: General Help
---

### Post by geo909 on 2008-09-16
Hello,

I use bith KDE and Gnome.
I have about 100 single-paged PDF documents.
Is there a way to print them all at once?

 Thanks in advance.

---

### Post by kaibob on 2008-09-16
You could use lpr:

```
lpr file1 file2 file3...
```

Use of the above commandline with 100 files is not practical, so the following entered in a terminal window is probably the easiest:

```
for FILE in *.pdf ; do lpr "$FILE" ; done
```

You could also use lpr in a Bash script or a Nautilus script or a Nautilus Action.

As an alternative, you could merge the PDF files into one file with ghostscript or pdftk and then print the merged file with Evince or Acroread.

---

### Post by geo909 on 2008-10-07
Thanks so much! Yes, that did the job, and saved me a loooot of time!
Sorry for replying so late

---

### Post by TKoorn on 2009-03-08
Wow that is really good to know. Saved me hours of work too. Thanks

---

### Post by JeanJean on 2009-03-25
Thx, usefull :)

---

### Post by bdaman80 on 2011-01-03
Very useful. Thanks but how do I make this a script in nautilus so I can highlight several files , right click, and select to print only the highlighted scripts?

---

### Post by psychoelf on 2011-01-07
Go to your home folder.  
Press Ctrl+H to show hidden files/folders.
Navigate to /.gnome2/nautilus-scripts/
Right click and create document.
Put ```
for FILE in *.pdf ; do lpr "$FILE" ; done
``` in the file and save it as whatever you want the name to be.
Go to folder, select files, right click, select scripts and select your script.

It will print to your default printer.

Thanks to the code in the above post and to
[https://help.ubuntu.com/community/Nautilus_Scripts]("https://help.ubuntu.com/community/Nautilus_Scripts")

---

### Post by bdaman80 on 2011-01-07
First off, thanks for your reply. I got how to get custom scripts into my nautilus scripts menu. But it doesn't work for me on 64bit 10.04 to select files and run script from nautilus. 

I was maybe thinking of just adding a custom alias in .bashrc for terminal use

And  is their anyway to get a GUI pop up menu to ask for selected printer if ran from cli or nautilus?

Thanks again

---

### Post by psychoelf on 2011-01-07
Ya got me on that one, I'm not that familiar with the cli.  I would try making your own thread on that one since we are working in a 2+ year old thread. Hopefully someone else has that knowledge.

---

### Post by pvanerk on 2011-01-18
Check out:
[http://www.frenssen.be/content/printing-file-right-click-context-menu-nautilus](http://www.frenssen.be/content/printing-file-right-click-context-menu-nautilus)

to print files from nautilus with right-click.

---

### Post by pvanerk on 2011-01-18
Check out:
[http://www.frenssen.be/content/printing-file-right-click-context-menu-nautilus](http://www.frenssen.be/content/printing-file-right-click-context-menu-nautilus)

to print files from nautilus with right-click.

---

### Post by pvanerk on 2011-01-18
Check out:
[http://www.frenssen.be/content/printing-file-right-click-context-menu-nautilus](http://www.frenssen.be/content/printing-file-right-click-context-menu-nautilus)

to print files from nautilus with right-click.

---

### Post by pvanerk on 2011-01-18
Check out:
[http://www.frenssen.be/content/printing-file-right-click-context-menu-nautilus](http://www.frenssen.be/content/printing-file-right-click-context-menu-nautilus)

to print files from nautilus with right-click.

---

### Post by molli on 2011-12-01
> **kaibob said:**
> You could use lpr:

```
for FILE in *.pdf ; do lpr "$FILE" ; done
```You could also use lpr in a Bash script or a Nautilus script or a Nautilus Action.



you can save tons of CO2 and food if you just type:

```
lpr *.pdf
```or, if (ba)sh refuses to work because you have too many pdf's:

```
find /path/to/pdf-files -name "*.pdf" -exec lpr {} \;
```however - the last solution is a little less resource efficient.

---

### Post by nothingspecial on 2011-12-01
[attach]208316[/attach]

---

