---
title: "Automatic printing scale"
date: 2008-07-10
forum: General Help
---

### Post by yadayada2 on 2008-07-10
I want to print [http://en.wikipedia.org/wiki/Test_market](http://en.wikipedia.org/wiki/Test_market), but it comes out on five pages with a very huge font. I don't want to scale that down manually. How can I tell firefox to print it out as it is displayed on the monitor automatically?

Thx!

---

### Post by MasterXandrex on 2008-07-10
It should print the font size used in the page, this sounds more like a glitch in your browser or printer setup. 

Try saving the page and opening and printing in another program as a temporary workaround. I'm not sure how to fix the issue though.



Xan

---

### Post by yadayada2 on 2008-07-10
Hmm, if you go to the page and click on print preview, how many pages appear?

---

### Post by yadayada2 on 2008-07-11
Please.

---

### Post by avtolle on 2008-07-11
I just checked the page, and Print Preview gives 5 pages. I've no clue...

---

### Post by yadayada2 on 2008-07-12
Thanks. Maybe someone else has an idea?

---

### Post by Vivaldi Gloria on 2008-07-12
I asked the same thing a couple of days ago. This reply worked like a charm:

> 1) in the URL box (i.e. where you normally enter a web address like [http://support.mozilla.com](http://support.mozilla.com)) enter about:config and hit enter

1b) on some systems you may be prompted by a bogus warning from mozilla joking that this might affect your firefox 3 warrantee (FF is free so the warrantee is a moot point); ignore the warning and proceed.

2)a special configuration settings screen will appear in you browser window; enter the following parameter name in the 'Filter:' box: print.whileInPrintPreview

3)FF 3 will quickly search for this parameter (i.e. print.whileInPrintPreview ) and display it and it current settings in the browser window (just below the filter box).

4) Double click on this parameter to change it from FALSE to TRUE

5) now when you print preview, you should see new buttons that let you scale the print out as well as portrait and landscape buttons (just like in windows) - enjoy.


---

### Post by yadayada2 on 2008-07-12
Perfect! Exactly what I was looking for! THX!

---

