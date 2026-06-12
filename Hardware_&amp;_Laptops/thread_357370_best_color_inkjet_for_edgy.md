---
title: "best color inkjet for edgy?"
date: 2007-02-09
forum: Hardware &amp; Laptops
---

### Post by radtek on 2007-02-09
[FONT="Comic Sans MS"]I have a multifunction BW laserprinter (**Samsung SCX4100)** that works well except some minor issues with openoffice. These include offset printing of envelopes and sometimes labels. This not what my question is about though.

Since I am set in the bulk BW printing area I was considering buying a **color inkjet** or bubblejet to print certain items, and in particular *disk media.*

Suggestions all you experts?

Criteria in order are:

1-compatibility w/linux in general and Ubuntu in particular (drivers,software)
2-price
3-quality of color print
4-DYI refill capability of ink cartridges

Mucho gracias in advance![/FONT]

---

### Post by radtek on 2007-02-16
[FONT="Comic Sans MS"]Well, unfortunately there has been no advice forthcoming on this thread. Really disappointing since printers a such an issue with linux. I looked forward to hearing personal experience from other users.

Anyway, I found this site: [[COLOR="DarkRed"]http://www.linux-foundation.org/en/OpenPrinting[/COLOR]]("http://www.linux-foundation.org/en/OpenPrinting")
and this page:
[[COLOR="DarkRed"]http://www.linux-foundation.org/en/OpenPrinting/Database/SuggestedPrinters[/COLOR]]("http://www.linux-foundation.org/en/OpenPrinting/Database/SuggestedPrinters")

Now, I did research find and buy a printer. With mixed results. I bought an **Epson Stylus Photo R260**. 

1. At this time I have not been able to get it to print with the generic gutenprint drivers or install the linux drivers from Epson. However, it prints extremely well from a laptop with Winblows 2000.

2. It only cost $79.99- what the hell, why not it's practically disposable!

3. The quality of print is *superb*. Especially on printable Cdrom or Dvd... looks professionally done even on the lower settings. This was the main deciding factor for buying.

4. I've found inexpensive CIS (continuous ink system) for this model which have refillable 100ml tanks and inexpensive bulk Claria (Epson HD grade) ink. The claims that the R260 *drinks ink* I believe are based on incorrect usage of the printer settings. IE: don't print a DVD or *draft* photos with the highest settings or indeed much ink will be wastefully consumed.

My very first criteria hasn't been satisfied as of yet, though I hope this will soon be rectified. In other forums, users claim to have it working fully but with thin vague explanations.

Preferably, I would have gone with the Epson R200 workhorse, such as I have at work. However, it is discontinued and while still available for $215 on Amazon it is basically the same printer with less ink cartridges. 

I'm hoping someone will helpfully advise me on how to at least get the R260 working or that Gutenprint will have a driver available soon. 
[/FONT]

---

### Post by chuckyp on 2007-03-04
Aparently I just found drivers from avasys.jp for the r260.  I'm thinking about buying one of these printers for my ubuntu machine just to print cd labels.

---

### Post by radtek on 2007-03-07
[FONT="Comic Sans MS"]I have been unsuccessful installing the avasys drivers through alien or any other method.  You however, might be able to- and if able I would like some advice.

There are no gutenprint drivers yet either.  [/FONT]

---

### Post by radtek on 2007-03-07
[FONT="Comic Sans MS"]I just got the Epson stylus photo R200 delivered. I found a used "like new" on Amazon for $79 US. Works right out of the box with the Gutenprint 5.0 drivers! Prints in  six cartridge color on disk media, photo paper and of course paper.

Now, this still very popular model is not produced by Epson anymore but well worth it. Especially since continuous ink systems (CIS) are readily available on the cheap which make ink costs ridiculously low.

I now have three printers. The Epson R260 - which uses the new Claria HD ink I think I may sell since even though I've found posts from people who claim to have it working under Linux. So far I've yet to produce a page under Ubuntu.

Under M$ 2000 the R260 prints awesomely. However this option is useless to me, as I prefer to use only Linux.

Hope this helps. [/FONT]

---

### Post by robenroute on 2007-03-07
> **radtek said:**
> [FONT="Comic Sans MS"]I have been unsuccessful installing the avasys drivers through alien or any other method.  You however, might be able to- and if able I would like some advice.

There are no gutenprint drivers yet either.  [/FONT]

What drivers are you using then? What software do you use to print the CD/DVD surface?

---

### Post by radtek on 2007-03-07
[FONT="Comic Sans MS"]I used the current epson software installed on an old Averatec laptop with Win 2000 running. The R260 prints CD's and DVD's very well in this arrangement, but also very inconvenient for me since I have to boot up the machine and transfer files to it in order to print them. 

I grit my teeth every time I have to use windows since M$ is dead to me.[/FONT]

---

### Post by robenroute on 2007-03-09
According to the avasys website, R260/R265 is supported. Have you tried the Debian version of the drivers?

---

### Post by ashtonp on 2007-03-28
> **robenroute said:**
> According to the avasys website, R260/R265 is supported. Have you tried the Debian version of the drivers?
OK, I tried the Debian version of the avasys drivers first, but encountered some compilation problems (don't remember the details; sorry).  So, I pulled down the CUPS ".rpm" version and used alien to convert it into ".deb". Disappointing results: this version installed and worked somewhat, but the included printer driver is very limited in what it supports. (e.g. no CD/DVD labels, which is the PRIMARY function I want.)

I had been VERY happy with the CD/DVD labelling capabilities of my R220 until it broke. Epson shipped me a R260 as a warranty replacement.  The R220 worked super using the Ubuntu 6.06 Gutenprint v5.0.0-rc2 environment, so I have been trying to use this as a starting point to get the R260 working. So far, no joy.

I have tried several different permutations of generating a .ppd descriptor for the R260 (using the R220 .ppd as a base) with no joy.

During my investigations, I have been encountering several bugs in the underlying software that have been independently reported.  (Underlying software = CUPS, Gutenprint/gimp-print, Foomatic...).

Typical error_log is something like: Gutenprint Fatal error: Unable to find driver named "EPSON Stylus Photo R260"!
Also getting flooded by messages:  cupsdAuthorize: Local authentication certificate not found!
but these pre-date my R260 installation.

Using a scratchpad boot partition, I have tried installations with Ubuntu 6.10 and Fedora 6 (Gutenprint v5.0.0) as well (using LinuxFormat magazine cover DVDs). Since I am on dial-up, it took about 4 hours to download the extra gutenprint/gimp-print rpms from the Fedora6 repositories.

I have also tried installing the Epson CD software on my VMware XP setup to see if a useful .ppd file would be created that I could copy into Linux. Nope.

Summary: I have many hours invested, but so far haven't managed to get a working solution.

Has anyone managed to have any success yet getting this working?  I will keep working on it and report if I make headway as well.

---

