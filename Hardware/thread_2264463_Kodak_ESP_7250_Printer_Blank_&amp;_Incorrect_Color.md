---
title: "Kodak ESP 7250 Printer: Blank &amp; Incorrect Colored Pages"
date: 2015-02-07
forum: Hardware
---

### Post by CaptainMikeRak on 2015-02-07
I know this isn't typically the place for this type of problem, but I don't really like other forums. I have a very old Kodak ESP 7250 all-in-one printer that currently is printing blank pages, and when I manage to get it to print, it is not colored right (I am using the Ubuntu CUPS Test Page to test this). I've tried changing cartridges and I get the same results each time I swap them (either it prints blank or incorrectly colored). I've also tried cleaning the print heads but that did nothing. Any help anyone could provide would be helpful (there is a very good reason printers are a totally separate certification than what I have, lol).

---

### Post by paulnewall on 2015-02-08
I think the first step is to prove the printer itself works by printing the self test page using the keypad/menu on the actual printer. That's completely independent of the computer. If that does not work, there is something wrong with the printer itself (or ink has run out, or print head is damaged or not connected quite properly)

Then, if the printer's own test page looks OK, what does "incorrectly coloured" mean? I'm guessing you mean you can see the expected text and coloured areas, but maybe one colour ink is missing, or something like that. If you can see some text and the right kind of shapes, then you have the right kind of printer specified in the print queue settings. There are really only 2 kinds of print protocols for the kodakAiOs and if you have the wrong one specified, the printer may produce blank pages, but it will never print anything at all.

It might help the diagnosis if you try printing from a few different programs. Also try printing to a file and then print the file. That sometimes reveals problem with the filters that convert between various image formats like pdf, postscript etc

And what about the history? You are uing Ubuntu 14.10? Did it print OK in the past with an older ubuntu?

---

### Post by CaptainMikeRak on 2015-02-08
Thank you for responding. I've tried both the built-in and Ubuntu test pages, also I originally found this problem when I tried printing up some business cards and the color was all wrong (sort of looked like it was missing yellow ink, but I unfortunately don't have another color cartridge to test it out with), the shapes were fine. Also, it has the issue of printing blank pages as well so I'm tending to rule out the ink for now at least. Also, I am using Ubuntu 14.10 if that makes any difference.

I'm going to swap over to Windows 7 to try re-calibrating the printer and seeing if that helps.

---

### Post by CaptainMikeRak on 2015-02-08
Looks like calibration isn't going to work, both it and test pages (from the printer not the PC) are printing blanks. No clue what's causing this.

---

### Post by paulnewall on 2015-02-10
I guess the possible causes of blank self test pages are:
no ink
print head clogged, not connected correctly (that often happens to me), or damaged
printer damaged

I have the luxury of 2 printers that use the same head, so I can swap ink cartridges and heads to eliminate these problems, if you only have 1 printer it's expensive to diagnose. I think a head costs quite a lot just to use for a diagnosis.

---

### Post by CaptainMikeRak on 2015-02-11
Thanks for replying, it does look like there is most likely a problem of some sort with the print head. On the bright side, at least it's not an immediate need now that my idiot father believes me about being able to check into a plane using a smartphone. lol

Thanks for the help! Might not have been able to fix the problem but at least we know what it is. :)

---

