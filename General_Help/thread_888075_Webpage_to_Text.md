---
title: "Webpage to Text"
date: 2008-08-12
forum: General Help
---

### Post by wbryan6 on 2008-08-12
I couldn't think of a better place to enter this thread, so I went for the general page.  Feel free to move it (moderators) as necessary.  Here's my situation:  I want some kind of script that I can setup in cron (can be in perl or whatever) that will read the information in a text file and call a particular event based on the returned value.  I want that text value to be the text information from a website.  My problem is I have tried both "html2text" and "lynx -dump", but neither will read some of the pages I want to save.  Some of these pages have php/asp/jsp front-end applications with a database back-end, so I just want the finished product and I want to be able to treat it as text (no needed formatting or anything), but I can't figure out how to extract it.  Does anyone know of an add-on (or anything) that could help me achieve this?  Thanks.

---

### Post by wbryan6 on 2008-08-12
A better summary of my previous post would be that I effectively want to do the following:

firefox [http://www.yahoo.com](http://www.yahoo.com) >> txt

This line should use Firefox to open yahoo.com and save all of the output to txt.  I realize this is not a practical command, but it is what I am after ultimately.

---

### Post by brian_p on 2008-08-12
> **wbryan6 said:**
> A better summary of my previous post would be that I effectively want to do the following:

firefox [http://www.yahoo.com](http://www.yahoo.com) >> txt

This line should use Firefox to open yahoo.com and save all of the output to txt.  I realize this is not a practical command, but it is what I am after ultimately.

Use wget and pipe it through htmal2txt if necessary. Having said that the front-end/back-end references are unclear to me so this may not be what you want.

---

