---
title: "Printing Adobe Files, I don't know where this goes"
date: 2011-12-13
forum: Hardware
---

### Post by Residentx10 on 2011-12-13
I have this irritating problem with Ubuntu. I tried to print pages 2-3 of this pdf but the print preview doesn't show_ these pages_ and the print job skips these two pages. 
 
I would like to know whether this is a 
 
1. PDF problem
2. Ubuntu problem 
3. Vendor Printer driver problem
 
I've posted screenshoots. 
 
Document problems with

---

### Post by Residentx10 on 2011-12-13
the pages I'm trying to print are 3 & 4 of 20. If I go from 2 to 3 then it skips the 2 pages I mentioned.

---

### Post by garolou on 2011-12-13
First off, raise the 'print queue' window...
System->Administration->Printing->Printer->View Print Queue

Print your documents or pages of.

What does the queue show? this will give some clues to what is happening.

---

### Post by Residentx10 on 2011-12-13
I'll do it now and add it to this post.  Give me 10 minutes.

---

### Post by Residentx10 on 2011-12-13
Is this what you want?
 
 
I don't have admin rights to this machine.

---

### Post by Residentx10 on 2011-12-13
Can someone just print the document on a unbuntu workstation that I posted and tell me their results?

---

### Post by garolou on 2011-12-13
The status says it is 'processing'... meaning it is sending it to the printer.
Does the status remain like this forever/timeout after a while with an error or just clear itself?

You say you don't see anything in the preview, yet your first 2 posted images do show the pages clearly in the preview. Maybe I'm not getting what your saying..?


Try to print using Evince, you may get some different results. I have trouble printing some documents with Evince, sometimes with Adobe reader. It seems to be a memory issue. On difficult documents it can take several minutes to print. Sometimes I get an error message printed.

---

### Post by Residentx10 on 2011-12-13
the jobs prints but without the two pages I mentioned. Look at my new comments up top. I've edited them.

---

### Post by garolou on 2011-12-13
George... I think I know what you are trying to explain here.

If you open the document and start at the first page you will see
[ 1 ] (1 of 20)

press page down or the 'next page arrow'

[ 2 ] (2 of 20) and so on...
[ 1 ] (3 of 20)
[ 2 ] (4 of 20)

the numbering resets itself entering the chapter.

This leads to the same 'confusion' when you want to print.

To circumvent this bug
  
go to page [1] 3 of 20... hit the print button and select 'current page'

and 'ok'

you should be able to print that page. Repeat for the other.

---

### Post by Residentx10 on 2011-12-13
I'll try what you said but let me say this first. Even when I print everything I can't get those two pages. This is driving me crazy.

---

### Post by Residentx10 on 2011-12-13
I was able to print it that way. I'm trying to print the full document again...it worked too.
 
I had someone working the pdf angle and they redid the document. I have problems on Ubuntu before with printing but it's clear now it isn't Ubuntu but a pdf problem. 
 
Thanks for your help.

---

### Post by garolou on 2011-12-13
Glad I was of help. By the way, unless you don't care and love to receive spam, you may want to remove those images as they do reveal your email to unscrupulous individuals. As well as the pdf.

Cheers

---

### Post by Residentx10 on 2011-12-13
> **garolou said:**
> Glad I was of help. By the way, unless you don't care and love to receive spam, you may want to remove those images as they do reveal your email to unscrupulous individuals. As well as the pdf.
 
Cheers
 
Thanks for comment, I'll remove the links in the posts. Thanks again.

---

