---
title: "Persistent A4 page size (bewitched)"
date: 2006-11-03
forum: Hardware &amp; Laptops
---

### Post by Jorge on 2006-11-03
I had set up several printers and I always select Letter as the default page size (in the "page size" pull down menu, and in the "page area" selector). But nevertheless, every time I have to print from some specific programs (i.e. open office, or DIA) I had to set up the page size again, because it is set to A4 (default size when I installed the printer). :-k 

If I go to System/administration/printers and look up at the printer settings, the page size is "Letter", but if I open the printer/page setup dialog from inside the program I'm printing from, it is set to A4. 

Am I bewitched?

Any ideas?

---

### Post by ReaderRat on 2006-11-03
There was a thread here about a week ago from someone who was trying to change the paper size in OpenOffice.org. Sorry, but I can't find it. You might search "paper size" in the forum. I will keep looking.

---

### Post by ReaderRat on 2006-11-03
Try looking in these posts:[http://www.ubuntuforums.org/search.php?searchid=9471325](http://www.ubuntuforums.org/search.php?searchid=9471325)

---

### Post by Jorge on 2006-11-04
Thank you ReaderRat! But the link you offered is a temporary one (every search you make, the forum system generates a new reference) so I couldn't follow it.

But it doesn't matter, I had already search for "A4 page" or "size page" with no results... I will look at the OO forum, although it happens in more applications than OO... 

Maybe I am the only bewitched with this page size?

---

### Post by ReaderRat on 2006-11-04
Jorge,
Do an Advanced Search (under "Searches" at the top of the page) on--> paper,size,A4,printer <--,  for the last month, and you will see some people's posts about this problem....ReaderRat....No, you are not bewitched....

---

### Post by Jorge on 2006-11-05
OK, thanks to you, I found this thread that looks promising:
[http://www.ubuntuforums.org/showthread.php?t=78596]("http://www.ubuntuforums.org/showthread.php?t=78596")

I am going to try. I can't do it right now because it involves reinstalling the printers, which I cannot do, because I will not be at my office until Monday. I need the network environment to reinstall & test the printers...

I will post the result.

---

### Post by Jorge on 2006-11-09
Solved!

a) I edited the file /etc/paper, removed "a4" and wrote "Letter" (without quotes).
b) I removed and reinstall every printer.

:)

---

### Post by hikaricore on 2006-11-09
i'll have to remember to look into this tomorrow at work :)

---

