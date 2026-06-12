---
title: "Canon LBP7110Cw sometimes prints almost completely black pages"
date: 2018-04-15
forum: Hardware
---

### Post by jet-bundle on 2018-04-15
I suspect that this might be a driver problem, but would be grateful for advice if anyone else has experienced a similar problem.

I have a pdf file of a scanned document. When printing it from document viewer, each sheet is printed with an array of miniature page images across the top, followed by a large black rectangle covering the rest of the page (and so wasting a lot of toner). The problem has arisen only with this document and one other.

I have tried printing the document on another printer (from the same computer, again using document viewer), without any problems.

 I have extracted a page from the document using pdf mod, and then printed the extracted page from document viewer, but the problem is still there. But, if I open the single page in Firefox, it prints correctly. Finally, I have copied the whole document to a Windows computer, and it prints correctly on the LBP7110Cw.

I am using Lubuntu 16.04 LTS. I have installed CUPS, and obtained the driver from the Canon Support website.

---

### Post by ajgreeny on 2018-04-15
Is it just that pdf file, all pdf files, or do all printed items show all black?
I suggest you also try another pdf viewer as I have in the past occasionally found that evince, the default in Ubuntu, has not printed some particular pdf files properly, though I never found the reason for this problem.

---

### Post by jet-bundle on 2018-04-16
> **ajgreeny said:**
> Is it just that pdf file, all pdf files, or do all printed items show all black?
Most pdf files are fine; just the two specific files give the problem (but see below).
> **ajgreeny said:**
> I suggest you also try another pdf viewer as I have in the past occasionally found that evince, the default in Ubuntu, has not printed some particular pdf files properly, though I never found the reason for this problem.
If I open the problem file in Firefox, then print from there, there's no problem. But I don't think that the problem can lie in the Evince document viewer, for the following reason.

I've now been given a third file which shows a variant of the problem.. In this document, the top 20% of the first page comprises an image, and the rest is text. The text prints correctly, whereas area which should be the image is completely black, and has a small distorted multiple representation of the image above it. (At least that's what I think it is -- for readers old enough to remember old-fashioned televisions from fifty years ago, it looks like the "horizontal hold" adjustment is incorrect!)

 But: the file is an MS Word doc file, not a pdf file, and the problem appears when I open it in LibreOffice Writer and print from there. So it can't just be Evince causing the problem. (Though if I use Writer to make a pdf version of the doc file, and print that from Evince, the problem is still there.)

---

