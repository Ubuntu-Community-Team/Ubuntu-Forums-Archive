---
title: "Brother HL-2040 printer spits out just blank pages until tray is empty"
date: 2011-06-11
forum: Hardware
---

### Post by OnuJack on 2011-06-11
A couple of days ago I got a used Brother HL-2040 printer.
Tried to get it to work in Ubuntu 11.04 - so far no luck.

Every time I try to print something, it just gives out blank pages.
Even, if the document is 1 page long, it just spits out blank pages until the autofeed tray is empty.

I tried the printer also in Windows XP Home and it works fine there - so I am guessing it is a software issue in Ubuntu.

Since I am mostly using Ubuntu, I would really like to be able to use the printer in Ubuntu.

So far I have tried the drivers from the Ubuntu repos and also the ones from Brother's website. 

No luck so far.

What can I do, to resolve this issue?


Any help is appreciated.

---

### Post by OnuJack on 2011-06-11
I found the solution.

I clicked the "change" of Make and Model in the printer properties.
Then "provide PPD file".
Downloaded the one from here: [http://www.profv.de/brother/Brother-HL-2040-hl1250.ppd](http://www.profv.de/brother/Brother-HL-2040-hl1250.ppd)

After that chose the option: "Use new PPD file" and voila - it works.



Hope it helps anyone :)


Have a good one,

Jaak

---

### Post by mazingaz01 on 2011-06-12
I have a same prob., with MFC-295CN.  Where can i find the PPD for that one?

---

### Post by blinovitch on 2011-08-08
> **OnuJack said:**
> I found the solution.  I clicked the "change" of Make and Model in the printer properties. Then "provide PPD file". Downloaded the one from here: [http://www.profv.de/brother/Brother-HL-2040-hl1250.ppd](http://www.profv.de/brother/Brother-HL-2040-hl1250.ppd)  After that chose the option: "Use new PPD file" and voila - it works. Thanks for taking the time to post this. I have the same model printer and on connecting to my new desktop running 11.04 for the first time, was flummoxed by the blank pages.

---

### Post by TedinOz on 2011-10-15
> **OnuJack said:**
> I found the solution.

I clicked the "change" of Make and Model in the printer properties.
Then "provide PPD file".
Downloaded the one from here: [http://www.profv.de/brother/Brother-HL-2040-hl1250.ppd](http://www.profv.de/brother/Brother-HL-2040-hl1250.ppd)

After that chose the option: "Use new PPD file" and voila - it works.



Hope it helps anyone :)


Have a good one,

Jaak

Thanks so much Jaak...so glad you posted this and so glad I found it! Printer is working again!

---

