---
title: "Canon iP1700 doesn't print"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by MadhavS on 2007-10-24
I have a canon iP1700 printer and am running gutsy. It recognizes what printer i have but fails to do anything more. I can't find the right driver and don't want to pay for turboprint. Can anyone please help me? Thanks in advance.

---

### Post by MadhavS on 2007-11-03
bump

---

### Post by GhentK on 2008-01-14
I can! :D

Execute the following command in a terminal: ```
$ sudo nano /etc/apt/sources.list
```

Add the following lines at the end of the document (in nano, you have to right click to paste): ```
# Canon PIXMA iP1700 drivers
deb http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu ./
deb-src http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu ./
```

Update your package list: ```
$ sudo apt-get update
```

Install the packages necessary: ```
$ sudo apt-get install libcnbj-2.6 bjfilter-2.6 pstocanonbj
```

When done, turn on your printer and open the printing administration (system > administration > printing on Ubuntu). Select iP1700 in the list of local printers, change the "Make and Model" and select Canon > iP2200 (it should be at the bottom of the list) > Use the new PPD as is > apply. Under the policies tab, tick off "Enabled" and click apply.

The printer should work now. Come back if it doesn't. :)

I found the info on ["Chox's  Blog"](http://choxblog.wordpress.com/2007/06/09/printer-pixma-ip1700-has-been-running-now/).

---

### Post by MadhavS on 2008-01-16
thanks for the reply, even so long after i posted :)

problem is, the printing still doesnt work. it sends the job, and the it says "one document pending", but after a second that goes away, back to "no documents queued", and it doesnt print

---

### Post by GhentK on 2008-01-16
Are you sure that you're using the right configuration?

If that's the case, then I can't help you any further, unfortunately. :-\

---

