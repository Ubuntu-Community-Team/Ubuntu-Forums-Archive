---
title: "Canon Pixma MP280 won't work as a scanner"
date: 2015-10-05
forum: Hardware
---

### Post by MMarauder on 2015-10-05
Hi all,

I use Kubuntu 15.04 on my computer and have a Canon PIXMA MP280 printer/scanner. I have already configured its printing function successfully, but scanning function not. Every time I open Skanlite (KDE scanning frontend), the window closed immediately after the device is detected, and tells me "failed to open scanner". Also with xsane, I get information "Cannot open 'Canon Pixma blablabla: device is occupied." Removing the device from Printer list won't help solve this problem.

[ATTACH=CONFIG]264819[/ATTACH]

Can anyone help?

---

### Post by aikishugyo on 2015-10-06
What version of SANE are you using, and what version of of the pixma backend? Check man page for sane-pixma to see if MP280 is listed there. If not, your version of SANE is too old. Either install from the maintainer's PPA (search the forums for how to set up sources) or compile from git repository yourself following the linux README instructions in the source. I'm pretty sure if you had 1.0.24 all would be well, but fear you have a much older one (1.0.24 date from 2013).
Note that brand-new 1.0.25 just came out yersterday.

---

### Post by MMarauder on 2015-10-06
Oh, my... the sane package available in Ubuntu App Center is still version 1.0.14:icon_frown:. Seems that it hasn't been updated for years...

---

### Post by weatherman2 on 2015-10-06
I have an MP280 as a spare. I never got it to scan in Ubuntu, even with Canon's scangearmp software (which works fine for me with my Canon Pixma, both wired and wirelessly).  The last attempt with the MP280 was in Ubuntu 12.04, though.  Since I have another scanner it's not been an issue for me.  I know that doesn't help you except to know that it's not something simple to get this one to work, but I hope you get it figured out!

---

### Post by aikishugyo on 2015-10-06
This scanner is perfectly supported under SANE, so all you would need to do is install from the required PPA. Check out the SANE website for details on support.

---

