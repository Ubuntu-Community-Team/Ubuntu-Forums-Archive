---
title: "HP LaserJet p1505n prints really  W I D E...."
date: 2010-03-05
forum: Hardware
---

### Post by manthony121 on 2010-03-05
I have just installed a HP p1505n printer on my office network.  All works fine for printing from various apps, like openoffice.  The problem comes when printing from a pipe, as in "ls|lp".  In that case, the print comes our very wide, about 5 cpi.  If I specify "ls|lp -o cpi=24", the output looks to be about 12 cpi.

The other problem is that any name with an underscore generates a backspace when printed, giving overlapping characters.

I am printing from Ubuntu 9.10, using the hpijs pcl3 driver, though using one of the alternative drivers did not fix this.

Any ideas?

---

### Post by Kyle_S on 2010-03-25
I had the same issues with text-printing on some CentOS boxes.  More or less, there are issues, often known-issues, with some of the text to postscript filters.  It's almost definately a filter issue.  Check the filters being used in /etc/cups/mime.convs, then head over to cups.org, and search through their forums there.  Very knowledgeable folks, and they can help you fix the filter-issue.

If you don't want to mess about with your filters, you can always use enscript, which is an older text to post-script filter, meant to be run on the command line.

enscript -d LaserPrinter test.txt


Good luck!
--Kyle

---

