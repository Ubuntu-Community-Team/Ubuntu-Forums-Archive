---
title: "Printer problems - spool queue"
date: 2007-06-06
forum: Hardware &amp; Laptops
---

### Post by Pixtu on 2007-06-06
I am trying to work out if a printer driver is working with full functionality and test all of the options.  
However, I want to avoid using lots of paper and more importantly, lots of ink.

So I came up with the idea of 'pausing' the printer so that I can interrogate the print job without actually having to print anything. I would like to see what options were set/sent with the job, or failing this, perhaps to be able to at least compare two jobs (files) and see if the actual output is different. It will hopefully help me to learn a little about Linux and Ubuntu at the same time.;)

My questions are:-
i) Where are the print jobs (or output files) held?
ii) Are the print driver 'options' held with the output in some way, or are they built into the output file?
iii) What will be the best way of comparing them? I know about 'diff' but this might not provide enough detail?

Thanks in advance and anticipation.:)

---

### Post by mitch.c on 2007-06-07
> **Pixtu said:**
> 
My questions are:-
i) Where are the print jobs (or output files) held?
/var/spool/cups/ ... paused jobs will be something like: d00202-001
> **Pixtu said:**
> ii) Are the print driver 'options' held with the output in some way, or are they built into the output file?
If it's a PS printer, I'm not sure about others.
> **Pixtu said:**
> iii) What will be the best way of comparing them? I know about 'diff' but this might not provide enough detail?
Depends on the PDL. diff may work, but some files may be binary.

[[COLOR="Red"]UAResolved[/COLOR]]("http://ubuntuforums.org/showthread.php?t=377083")

---

### Post by Pixtu on 2007-06-07
Mitch, thanks for the response.

I had managed to work out where the spool queue was after a little more searching.

The printer in question is a Canon iP4300 - I don't know whether this is a PS printer or not, but the print job files are viewable with an editor (Gedit) and do give results with diff.

However, when I use the command line to print a file (which the userguide suggests you can do) the print job file only contains the text that I sent, with no extra info regarding options. Could they be held elsewhere, or is it that the printer driver/options arn't being used after all (or not working)?

---

### Post by mitch.c on 2007-06-07
Using lp and lpr to print a text file does just that, prints the text file... nothing fancy. Use lpr with '-o key=value' to use print options and see what happens. I've never tried it. You can get a list of options (for the default printer) using:
```
$ lpoptions [-l]
```

---

### Post by Pixtu on 2007-06-07
Yes, that's what I tried. The actual command line was:-

lpr -P IP4300 test-1.text -o PaperSize=a4 -o MediaType=superphoto

The result was just the contents of the text file - one line, four words.

I had assumed that there would/should be some kind of 'wrapping' to tell the printer about the options.

---

