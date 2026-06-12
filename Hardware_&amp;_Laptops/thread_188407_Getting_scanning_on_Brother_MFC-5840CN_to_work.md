---
title: "Getting scanning on Brother MFC-5840CN to work"
date: 2006-06-04
forum: Hardware &amp; Laptops
---

### Post by jbrader on 2006-06-04
I've only got one complaint with dapper, my scanner won't work. I have a Brother MFC-5840CN multifunction printer, using [this how-to]("http://ubuntuforums.org/newthread.php?do=newthread&f=135") under breezy worked perfectly and I also used it to get printing to work under dapper, but when I run xsane now i get the scanning for devices message and then it freezes. Any ideas?

---

### Post by disturbed1 on 2006-06-04
Brother has a dedicated Linux support site, don't know how helpfull it will be, but I'd check there

[http://solutions.brother.com/linux/en_us/](http://solutions.brother.com/linux/en_us/)

And here's where to get their scanner driver
[http://solutions.brother.com/linux/sol/printer/linux/linux_faq.html](http://solutions.brother.com/linux/sol/printer/linux/linux_faq.html)

---

### Post by jbrader on 2006-06-04
Thank you, but I already know about that site and have the scanner driver. Like I said I had scanning working under breezy.

---

### Post by cky1billion on 2006-07-19
Ok, I figure out why these printer drivers dont work on ubuntu. Perhaps its very simple but it took me about 15 mons to figure out. First enable the universe repositories in your sources.list file. There may be a simpler way in synaptic but I use it infrequently so I dont know. This also asumes that you installed the .deb's from the brother site and followed the instructions there already. Next install csh using apt, or synaptic. The driver requires that you use csh, as the script it runs is written for that shell. Once csh, not tcsh which is the only one available if you didnt enable the universe repositories, is installed you need to edit the script in /usr/local/Brother/cupswrapper/, named cupswrapperMFC5840CN-1.0.0, ```
vi /usr/local/Brother/cupswrapper/cupswrapperMFC5840CN-1.0.0
```
using your favorite text editor, I used VI, and change all ```
/etc/init.d/cups
``` to ```
/etc/init.d/cupsys 
```

Alternatively I suppose you could write a symlink pointing from cups to cupsys, but that's up to you. It could also be possible that most of this is not even necessary if you just make that symlink before atempting to install the .debs for the lpr and cupswrapper drivers. So:

```
sudo ln -s /etc/init.d/cupsys /etc/init.d/cups
```

Good Luck, This is my first tutorial of any sort, so my apologies if it is not fresh. 
-Ian

---

