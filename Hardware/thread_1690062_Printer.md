---
title: "Printer"
date: 2011-02-17
forum: Hardware
---

### Post by 88300D on 2011-02-17
Hi i have a lexmark that i can no longer use so need to buy a new one.
I need a multifunction printer, scanner and fax and would like it wireless this time.
I have tried a list on the web and compared it to the HP page but was unable to match any.
If you have one working with linux i would like to hear from you, even if it is not wifi.
Peace and blessings Howie

---

### Post by quixote on 2011-02-18
Hp Photosmart C6300.  Wireless.  Copies, prints, scans, and if you have a landline I believe it'll send faxes as well.  It does an excellent job, worked with my Ubuntu right out of the box.  Excellent paper handling, no jams, prints envelopes straight.

The down sides: ink is hideously expensive as it is for most printers these days now that they've figured out how to turn that into a cash cow.  It's also quite expensive, as these things go.  List, I believe is around US$200.  Mine was a store model being remaindered for $90.  They're well-built, so a refurbished model could be a good bet, too.

---

### Post by 88300D on 2011-02-19
Hi quixote, i really appreciate your reply, i love HP printers they are very good quality i have a lot of clients with them on my windows networks. They are also very easy to configure.
 I am having a look at Lexmark again[SIZE=1] Lexmark Prevail Pro705. It seems ok and has deb packaged drivers.I have had a bash at installing the drivers and once i work out how to make a root password i can use in GUI it should be easy to install.
I was looking at it as i have been told it has disposable print heads and i am a keen ink re filler. I have been told these are good for it. I actually doubt it and think it may have a chip that prevents it. Like you say about the HP ink cartridges have become the cash cow. I have been looking on line but have not been able to confirm they are re fill able.
My old x6150 did us well from 2004 to now (rollers worn out) and i have refilled its cartridges up to 10 times each making it very cheap to run.
Will post again in hope this thread helps others considering linux distros as a personal / desktop alternative.
Peace and blessings Howie
[/SIZE]

---

### Post by 88300D on 2011-02-20
Dont have the printer yet but have tried the install of the driver from lexmark, to do it in GUI had to create a root in terminal
sudo passwd root

to remove it

sudo passwd -l root

While installing it said i needed Xsane for the scanner will go try find out how to do this and post again


Peace and blessings Howie

---

### Post by 88300D on 2011-02-20
Xsane was available from the package manager

---

### Post by quixote on 2011-02-21
I checked with my HP C6300 guru and he says you can refill the ink cartridges on it.  He says it's a bloody pain, but it can be done.

(Xsane these days usually just works.  If the scanner is connected, xsane just finds it and lets you start scanning.  Usually.)

---

### Post by 88300D on 2011-02-21
Thanks i have ordered the lexmark, for the benefit of others who may read this thread does the Hp have fixed head or are they disposable?
I dont bother to refill fixed head printers any more because if the sponge breaks down tyhe heads can block and be a real pain to clean, with disposbales i ditch the cartridge and start again.
Peace and blessings Howie

---

