---
title: "printing to windows shared printer fails"
date: 2008-01-24
forum: Hardware &amp; Laptops
---

### Post by Xamindar on 2008-01-24
I have a strange issue with printing from linux over to a windows machine which is sharing the printer. I added the printer in cups on linux and when I try to print a page I hear the printer start like it is going to print something then nothing happens. When I check the print spooler in windows it shows the job as "printing" and the size says 64.0kb/4.5mb (total size ranges but the first 64.0kb stays the same). I get this same result in both ubuntu and another computer running gentoo. I have to then delete that job from the windows box and then restart to get rid of it.

Printing from windows over the network to this windows share works fine. I have tried different drivers in linux with no change. If I plug this printer into my linux machine directly and install it then it prints just fine. It's a cheap HP Deskjet D1341.

Has anyone ever had this problem? Am I using the wrong driver?

Thanks for any help.

---

### Post by Xamindar on 2008-01-24
well, I found a fix for it:

[http://www.linuxquestions.org/linux/answers/Hardware/Troubleshooting_printing_problems_from_SuSE_10_0_to_HP_PSC1350_shared_from_Windows](http://www.linuxquestions.org/linux/answers/Hardware/Troubleshooting_printing_problems_from_SuSE_10_0_to_HP_PSC1350_shared_from_Windows)


All I had to do on that site is delete the "Monitor" registry key and it is printing now.  Strange eh?  At least it works now.

---

### Post by geakhawk on 2008-01-26
Hello all,
I have been having the exact same problems with a HP PSC-1315. editing the "monitor" key worked for me as well! 

,Many Thanks

---

