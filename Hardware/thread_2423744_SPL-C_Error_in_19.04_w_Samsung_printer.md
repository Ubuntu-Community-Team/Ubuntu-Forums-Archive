---
title: "SPL-C Error in 19.04 w/ Samsung printer"
date: 2019-07-28
forum: Hardware
---

### Post by Madpilot on 2019-07-28
Hi all,

I've got a slightly older Samsung C410W colour laser printer that has been working well with Ubuntu for years up until I upgraded in place from 18.09 to 19.04.

Now no matter what, any attempt to print gets the following:

```

SPC-C ERROR - Insufficient Memory

POSITION: 0x506 (1286)

SYSTEM: eHeapPattern

LINE: 6187584

VERSION: SPL-C 5.59.02 02-24-2014
```

I've removed and reinstalled the printer a couple of times and it sets up beautifully with the system every time... and then throws that same SPL-C error every time.

I've done some searching on this forum and generally on Google and can't find anything coherent that looks like a solution. None of my hardware has changed anytime recently, and this printer was, as said, working just fine up to 18.09...

Anyone?

---

### Post by MrRubik on 2019-08-17
I have spent 4 hours trying to figure this out. Has anyone found a solution?

---

### Post by brian_p on 2019-08-17
> **baileyhood said:**
> I have spent 4 hours trying to figure this out. Has anyone found a solution?

Seemingly not. You could try downloading the cups-filters, cups-filters-core-drivers and libcupsfilters1 packages for 18.04 and installing them one-by-one with

```
dpkg -i <package>
```

---

### Post by Autodave on 2019-08-17
Similar question as yours is posted here.  Evidently, there is a problem with 19.04 and your printer.  If possible, go back to 18.04 and forget about the short term releases.

---

### Post by MrRubik on 2019-08-18
I have scoured the internet but have not found a solution, but I have discovered an excellent workaround. For those of you that have a Samsung Xpress SL-C410w or similar, your printer has built-in Google Cloud Printing and Samsung Cloud printing. I just registered my printer as a Google Cloud printer and then when I go to print it shows the option to print to my C410w via Google Cloud Print. No drivers required and no hassle. For this to work, you do need to be signed into your Google account through Ubuntu. Really hoping this helps someone.

---

### Post by Madpilot on 2019-10-29
Note that dist-upgrading from 19.04 to the shiny new 19.10 appears to have fixed my printer<->Ubuntu connection with no further fiddling. 

Upgraded, restarted, decided to hit print on something, got it.

---

