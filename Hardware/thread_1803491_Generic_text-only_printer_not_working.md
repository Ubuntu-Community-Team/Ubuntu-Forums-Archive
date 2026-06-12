---
title: "Generic text-only printer not working"
date: 2011-07-13
forum: Hardware
---

### Post by zazuzimbo on 2011-07-13
Hello,

I have a **parallel port printer** that **should be installed as a text-only** printer. It has no specific drivers. However, when I try to install and print to it from Ubuntu, nothing happens.

From the **printer properties**, I have:

Device URI: parallel:/dev/lp0
Manufacturer and model: Generic text-only printer
Status: stand-by ((or available; I am translating what I read to english))

If I click on print a **test page** I get:

> 
There was an error during CUPS operation: "client-error-document-format-not-supported".


If I open gedit and try to print a simple word like "test", nothing happens.

When I open the print queue and ask to show completed jobs, I see all jobs with a status of "aborted".

After all this, I opened a windows machine and put this printer on it. Installed it as the model "Generic / Text only" and it printed.

Can you help me?

Thank you

Zazu

---

### Post by jerrrys on 2011-07-13
i had a look here for a generic fix, but these seem to be fixes for specific makes/models.  try adding your printer make to this search and see if you get a hit.

 [http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=client-error-document-format-not-supported&as_qdr=all&sa=Google+Search&lang=en#945](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=client-error-document-format-not-supported&as_qdr=all&sa=Google+Search&lang=en#945)

also a place to look for drivers

[http://www.openprinting.org/printers](http://www.openprinting.org/printers)

---

### Post by zazuzimbo on 2011-07-13
I tried both the manufacter of my printer and "generic printer" in the search. Have not found much.

It is fun, though, that this thread was the first ranked result for some serch queries I tried. :)

This printer has no driver. It works on windows simply as a "generic text only printer" (as I detailed originally). It is designed to be this way, I guess.

So I thought that it would work without problems on linux too, with an equivalent driver for "generic text only printers".

If someone could help me on low level printer testing, to see where the problem is, I welcome that. E.g., writing directly to LPT1 and see what happens and by that finding the right driver to use.

Well, I guess I shall wait. Until then, I will have to cope with windows for that printer.

Thanks

---

### Post by zazuzimbo on 2011-07-18
I have tried to print to this printer, by making it a shared printer on windows. It gives me the same errors. I cannot print to it (from Ubuntu, in Windows it is still possible).

To me, Ubuntu seems unable to print to text-only printers!! :(

Maybe the "print a test page" does not know how to print on text-only printers (sending it a "fancy" job, and justifying that CUPS error).

---

### Post by oldfred on 2011-07-18
Is this a printer that requires you to include the escape codes in the raw file? Years ago with parallel printers that was what we had to do.

What model printer?

---

### Post by zazuzimbo on 2011-07-18
"Escape codes", mmm... so this is the name, I guess. I am thinking that I need to look them in detail. Do someone have a good detailed documentation on this? I'll be searching it.

Oldfred, it is not [b]required[b] to print the escape codes. But it seem usefull for me.

I have no idea what model of printer it is specifically. It is supposed to be used as generic.

Anyway, now I am able to print to this printer from linux. I have shared it in windows, and configured it in Ubuntu as a samba printer. Printing with lpr was possible ( "ls | lpr -#1" ). (I am *guessing* that it was possible with it locally too, but that CUPS error fooled me! This is a bug - windows test page prints.)

---

