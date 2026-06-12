---
title: "ATI and fresh dual boot of XP &amp; 10.04"
date: 2011-03-20
forum: Hardware
---

### Post by Dante311 on 2011-03-20
I recently freshly installed Windows XP and Ubuntu 10.04 onto my laptop.  After installing Ubuntu 10.04, I installed the drivers through the System -> Admin route and after doing so when entering Windows I now get the message that my ATI graphics driver is not installed or functioning properly.  Graphics in Ubuntu seem to be working fine now that I uninstalled the driver but I have had no luck at restoring Windows drivers back to normal. 

Searching for drivers in Window is unsuccessful as well.  Is there any way to remedy the graphics card in Windows without having to reinstall it again and not touching the graphics driver in Ubuntu?  I would love to not have to go through the whole process again.

Thanks in advance!

---

### Post by gordintoronto on 2011-03-20
What you did in Ubuntu did not affect your Windows installation. You have a Windows problem. If you run the command lspci in Ubuntu, it will tell you exactly what ATI video adapter you have. You can plug that into Google, along with the exact text of the Windows error message.

---

### Post by Dante311 on 2011-03-20
Could it be possible that it isn't just a windows problem?  Windows was working fine until I set up the dual boot and updated the graphics driver.  I did the ispci command and got the following output.  Which is my ATI video adapter?

P.S. Although I have been using Ubuntu for 2 years now, I am still a noob....

---

### Post by Dante311 on 2011-03-20
Thanks gordintoronto!  After trying what you said, I eventually have fixed the problem.  Appreciate your help!

---

