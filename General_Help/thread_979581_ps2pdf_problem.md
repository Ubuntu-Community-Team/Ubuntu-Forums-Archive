---
title: "ps2pdf problem"
date: 2008-11-12
forum: General Help
---

### Post by g.a. on 2008-11-12
Hi,

I'm experiencing a problem with ps2pdf when kpdf is open. What I usually do (and used to work perfectly) is to work on my tex file with Kile, the corresponding pdf file is open with kpdf.

From the shell I execute the compilations commands, latex, dvips and ps2pdf.

Recently, running ps2pdf I obtain the following

```
ps2pdf -dPDFSETTINGS=/prepress filename.ps
Error: PDF file is damaged - attempting to reconstruct xref table...
Error: Couldn't find trailer dictionary
Error: Couldn't read xref table
Error: PDF file is damaged - attempting to reconstruct xref table...
Error: Couldn't find trailer dictionary
Error: Couldn't read xref table
```

However, the pdf file, that is currently opened under kpdf, update regularly.

Any hints of what could be happened?

Thanks in advance,
g.

---

### Post by spibou on 2008-11-12
Could you show us the commands you're executing? Cut and paste from the command line including any messages you get. Also how kpdf was started.

---

### Post by g.a. on 2008-11-12
the command is actually what I posted above. I run kpdf from the shell:

```
kpdf filename.pdf &
```

I then work on the tex file from kile and, from the shell, I run a make that does all the compilations at once.

Even if I just run ps2pdf I got an error.

```

ps2pdf filename.ps
Error: PDF file is damaged - attempting to reconstruct xref table...
Error: Couldn't find trailer dictionary
Error: Couldn't read xref table
```

However, if kpdf is not running no error message shows up.

Notice that until a couple of weeks ago I used to do it in this manner without problems (i.e., with kpdf open).

Thanks,
g.

---

### Post by spibou on 2008-11-12
What happens if, *without* kpdf running, you update your latex file, do the make and then start kpdf? Does kpdf display properly the updated PDF file?

---

### Post by g.a. on 2008-11-12
kpdf shows properly the pdf file in both cases (i.e., run before or after the tex compilation).

however, if it is running, the command ps2pdf causes the occurrence of those error messages.

best,
g.

---

### Post by spibou on 2008-11-12
The only explanation I can come up with is that kpdf tries to read the updated PDF file before ps2pdf has finished writing  it so kpdf sees a damaged PDF file and prints an error. Try to reload the file from kpdf after ps2pdf has finished its job.

---

### Post by g.a. on 2008-11-12
well, it could be. if I run kpdf when kpdf is running it opens an additional window without any error message.

I guess I can just ignore those messages and I will stay with the curiosity why, after one year of use, it just started few days ago showing this message...

bye,
g.

---

### Post by roquentin on 2008-11-13
the errors you're seeing aren't from ps2pdf, but from kpdf

what happens here is:

- you start kpdf and put it on background
- kpdf automatically monitors your file for changes to reload it when needed
- you execute ps2pdf which modifies your pdf
- kpdf tries to reload your file too early (ps2pdf hasn't finished writing yet) and    complains (your file is corrupt!)
- ps2pdf completes its job 
- kpdf reloads and all is good now

to prove i'm right try to start kpdf and ps2pdf from two different terminals and check who writes what

to get rid of these messages, just start kpdf redirecting stdout and stderr to /dev/null :

$ kpdf &> /dev/null

or start kpdf from a menu, or from another shell...

---

