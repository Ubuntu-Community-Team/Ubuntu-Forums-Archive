---
title: "how do I make Gimp use the HPLIP print driver?"
date: 2007-07-27
forum: Hardware &amp; Laptops
---

### Post by bsmith1051 on 2007-07-27
I've got my HP Deskjet 5150 printer setup perfectly in Ubuntu's Print system, but when I go into Gimp it doesn't seem to share those settings -- instead it appears to have it's own 'private' list of print drivers ... which don't include my model.  How can I make Gimp use the system-default printer, which is HPLIP based?

---

### Post by coffeecat on 2007-07-27
I thought I would bump this thread for you. I have the same problem but I have no proper solution.

Most of the system uses CUPS which can print out through most Hewlett-Packards just fine. HPLIP is just a toolbox - I believe it still prints through CUPS. But the Gimp uses gimp-print (now guten-print, or so I believe). I just cannot work out how to get the Gimp to use CUPS.

I have a Deskjet 9800 (an A3 printer) which is listed in the CUPS manager and prints photo-quality beautifully through CUPS. But it's not listed in gimp-print.

This is what I have been doing so far:

1 Edit photo in Gimp and save.

2 Open firefox and go to localhost:631 to set paper size, photo paper and print quality.

3 Open either Eye of Gnome or gThumb and print photo(s).

It's a real pain because you can't select photo-quality output in EoG or gThumb - that's why you have to use the CUPS manager first. So if anyone has a solution I would also be interested to hear it.

---

### Post by bsmith1051 on 2007-07-27
Actually, I'd prefer to use Picasa to manage/edit my photos -- and it uses the OS printer settings i.e., CUPS/HPLID -- but it doesn't use them correctly.   My photos end-up the wrong size or with very poor quality.  So I was hoping to 'simply' use GIMP...

---

