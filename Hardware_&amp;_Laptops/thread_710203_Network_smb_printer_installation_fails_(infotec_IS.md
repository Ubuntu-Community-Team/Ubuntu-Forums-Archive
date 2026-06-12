---
title: "Network smb printer installation fails (infotec IS2027)"
date: 2008-02-28
forum: Hardware &amp; Laptops
---

### Post by Deeg on 2008-02-28
Hi, I switched to linux from windows recently and so far I really like it.

At the moment I have one problem though, I want to use a network printer (infotec IS2027). The driver was not in the standard list but can be found on [http://openprinting.org/show_printer.cgi?recnum=Infotec-IS2027](http://openprinting.org/show_printer.cgi?recnum=Infotec-IS2027) (I used the pxlmono ppd)

After installing it the printer appears in the CUPS administration at [http://localhost:631](http://localhost:631). When I print something the job seems to execute normally, but nothing comes out of the printer.

Another network printer (HP 6L) works perfectly, but I want to use the infotec for its duplex unit.

Messing around with the printer settings did not help me.

Does anyone have ideas to help me tackle this problem?

Thanks!
Deeg

edit: I also verified that the printer is accessible

---

### Post by hyperair on 2008-02-28
I had that issue when I used the wrong driver for my Pixma IP1000. I believe this would be the same issue as in your case.

---

### Post by Deeg on 2008-02-29
OK, thanks. I'll try to find and install some other drivers. They look pretty generic though.

---

### Post by Deeg on 2008-04-03
For the sake of completeness: my problem is solved.

I moved inside the building and I now print to a different printer of the same type. And it works, for some weird reason. The new printer has a custom usercode though which I specified, the previous printer didn't.

---

