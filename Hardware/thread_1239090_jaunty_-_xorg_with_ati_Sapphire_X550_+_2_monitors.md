---
title: "jaunty - xorg with ati Sapphire X550 + 2 monitors"
date: 2009-08-13
forum: Hardware
---

### Post by aljosa on 2009-08-13
i have jaunty installed and output of lspci is:
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 [Sapphire X550 Silent]
01:00.1 Display controller: ATI Technologies Inc RV370 secondary [Sapphire X550 Silent]

currently my xorg.conf file is empty and fglrx doesn't work so i assume X is using default open-source driver.
if i turn on both monitors it shows 1 desktop cloned on 2 monitors, what's the best (and possibly easiest) way to configure 1 desktop on 2 monitors?

i did google it but there are few conflicting pages and mostly it didn't work for me.
i've think that xinerama should work but i guess i didn't find the right doc describing what should i do.
any tips/links appreciated.

---

### Post by markbuntu on 2009-08-13
System/Preferences/Display  uncheck clone.

---

