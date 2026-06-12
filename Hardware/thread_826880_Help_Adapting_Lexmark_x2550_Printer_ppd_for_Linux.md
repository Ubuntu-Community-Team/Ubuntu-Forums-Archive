---
title: "Help Adapting Lexmark x2550 Printer ppd for Linux"
date: 2008-06-12
forum: Hardware
---

### Post by desperation on 2008-06-12
Hello,

I have bought, quite foolishly, a Lexmark x2550 printer and hoped to use it both on my iMac and on Mandriva. However, I have since realized that Lexmark has no support for Linux whatever.

After having installed the printer on my iMac, it works fine. I have since extracted its ppd, which I understand is what is required to get the device working under Mandriva. I saw in the ppd some statements referring to the OSX filter, which I removed. I replaced it with the foomatic filter. However, after having installed the printer through the CUPS web interface, I am unable to print a test page. There are no errors displayed on the CUPS webpage, and the print job is shown to be completed (of course, nothing happened on the printer).

Can anyone tell me what I might have done wrong? I am attaching my altered ppd file , and the original, in the hope that an expert can tell me what I've done wrong. I've also used max2unix to convert to native format.

Thanks for any help.

Link to both PPDs:
[="http://forums.linux-foundation.org/read.php?29,5954](="http://forums.linux-foundation.org/read.php?29,5954)

---

