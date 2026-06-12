---
title: "Using HP Deskjet D1360 on Ubuntu Dapper?"
date: 2007-03-27
forum: Hardware &amp; Laptops
---

### Post by martin_legion on 2007-03-27
Hello.
I changed from edgy to dapper recently and I can't make my printer work.
It's a HP Deskjet D1360 usb.
In edgy I installed it using System - Administration - Printers menu, but here in dapper the exact model is not included in the list, and I don't know which one should I use. I tried a couple, like Deskjet Series, but it didn't work.
Any suggestions?
Thanks

---

### Post by 23meg on 2007-03-28
I'm having pretty much the same problem, but in Edgy. 

[This page]("http://www.linuxprinting.org/show_printer.cgi?recnum=HP-Deskjet_D1360") has two suggestions: DJ3320 and 3920, and neither are working for me in Edgy. The 1300 series option, which gets selected by default, also doesn't work; in all cases, when I send something to be printed, the printer just takes the paper and stalls, with the LED blinking.

You said you couldn't find the exact model in Dapper; could you in Edgy? I can't see it; the closest is the 1300.

---

### Post by martin_legion on 2007-03-29
Well, I just can't remember what model I selected on edgy. I think the one by default worked for me because I don't remember needing to change or select anything. I just added the printer and worked... sorry.

---

### Post by 23meg on 2007-03-29
It turns out mine was a temporary problem with the cartdiges; it works fine with the D1300 driver in Edgy now. If D1300 is not available in Dapper, you should try the others suggested in the page I linked to.

---

### Post by martin_legion on 2007-04-01
Using Deskjet 3320 worked!!
I think the problem was that I was only testing the printer with the test page in the printer's properties. For some reason when I tried that, the printer started to print but with "invisible ink". Then I printed a doc with Open Office and worked fine.

Thanks a lot 23meg

---

### Post by 23meg on 2007-04-01
You're welcome; I noticed that the 3320 works for me too.

By the way, you can help test the latest version of HPLIP, which it seems fixes many bugs, and make it into Feisty; see [this]("http://www.ubuntuforums.org/showthread.php?t=396366").

---

