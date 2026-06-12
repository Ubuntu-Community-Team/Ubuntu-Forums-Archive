---
title: "Printer: Epson Stylus DX4800"
date: 2006-09-26
forum: Hardware &amp; Laptops
---

### Post by Oliver W. on 2006-09-26
Hello Ubuntu community,

The problem I'm having is with my printer (Epson Stylus DX4800).
Ubuntu easily recognized the hardware, so I followed the easy guide and made it my general printer.

Having just printed a file for my classes at the end of this week, it came out rather poor. All pages start very close to the top of the page. I had first thought that it was an issue due to converting from the doc format, but when I printed a file I made in OpenOffice it gave me the same result. 
This time however, that same page also included an image, which was printed three times (with the basic colors, but about 0.7 cm from each other).
A PDF-file gave me the same result.

So then I started looking around. I installed mtink (for the future, because I like checking my printer levels). I then printed a test page from the printer properties. It didn't come out quite as expected. 
First, the Ubuntu-logo is too close to the top. 
Second, all colored blocks (print a test page, you'll see what I mean) were printed, but once again partially overlapping each other (vertically).

I opened up mtink with the console, but it stopped functioning ("crashed")  the moment I got to the main config panel.

My tech friend (who got me in to this Linux spirit) thinks it might still be a driver issue.

Any ideas?

---

### Post by Oliver W. on 2006-09-28
The source of the problem has been identified:
[LIST]
[*][https://launchpad.net/distros/ubuntu/+source/gutenprint/+bug/32343](https://launchpad.net/distros/ubuntu/+source/gutenprint/+bug/32343)
[*][http://sourceforge.net/tracker/index.php?func=detail&aid=1447115&group_id=1537&atid=101537](http://sourceforge.net/tracker/index.php?func=detail&aid=1447115&group_id=1537&atid=101537)
[/LIST]

Now all I need to do is wait I guess, because from the information on those websites, it would seem I am out of luck for now (AMD64).

Thought I should list this here as well, the more information provided, the easier some good results will pop up in a search. :)

---

### Post by Oliver W. on 2006-10-04
Finally, a solution!

Instead of using the DX4800 driver, use the CX4800 driver. Both the Ubuntu test page and the CUPS Printer Test Page came out nicely. :D 

Power to the people!

---

