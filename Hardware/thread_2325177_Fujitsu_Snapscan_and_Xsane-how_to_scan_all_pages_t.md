---
title: "Fujitsu Snapscan and Xsane-how to scan all pages to one PDF?"
date: 2016-05-19
forum: Hardware
---

### Post by flyingsolo on 2016-05-19
Xsane is working with my Snapscan but I haven't figured out how to get it to make a single, multipage PDF from a scan of a document, such as a financial statement.
Right now, it auto-feeds and scans all the pages but makes individual PDFs and advances the counter by one to name them each, such as: Doc001, Doc002, Doc003 for a 3 page document.
Hopefully it's do-able! Probably something simple. Thoughts?

---

### Post by him610 on 2016-05-19
Never gave much thought to that. I have a scanner but don't scan that much. 

I found this discussion, or rather a Q&A about it that may be of interest to you.
[http://askubuntu.com/questions/2799/how-to-merge-several-pdf-files]("http://askubuntu.com/questions/2799/how-to-merge-several-pdf-files")

Let us know how it turns out.

---

### Post by flyingsolo on 2016-05-19
Thanks for the link/suggestion. I've got pdfchain available to combine the output pages which works but it's just another step.
Most scanners will auto-collate the scanned pages into one PDF without resorting to other software. In fact, this Snapscan does so under Mac OSX, but I was hoping to use it on Ubuntu.
There is a multipage function in Xsane but it seems to still create separate page scans as .pnm files without making a single, combo PDF, even though I've chosen PDF as the output file format.
So, I'm confused still.

I also tried to experiment with simplescan but it doesn't even seem to "see" the scanner which Xsane at least, does.
OK, I at least fixed this last bit about simplescan not recognizing the scanner. It needed the following:

sudo gpasswd -a <YOUR-USER-NAME> scanner

to allow it access.

---

