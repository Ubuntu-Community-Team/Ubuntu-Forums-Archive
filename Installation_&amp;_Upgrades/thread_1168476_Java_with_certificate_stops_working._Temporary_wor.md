---
title: "Java with certificate stops working. Temporary workaround."
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by RikardSvenningsen on 2009-05-24
After upgrade to Ubuntu 9.04 Java is stop working. This seems to go for more than one distribution no one named no one forgot.

When you try to logon after accepting a Certificate you might be lucky to get in, if  not, the browser locks and you have to close the browser.
To solve this problem do the following.
1.
Start the Java Console, remove the Certificate
2.
Still in the Console, remove the temporary files.

Now try to login again, if still not working do 1. and 2. and continue with the following.
3.
Remove Java JRE, BIN, and plugin. Completely.
4.
Reinstall again.

Try to logon again, this time it should bee working until next reboot.
You might only need to take step 1 and 2. and sometimes 3 and 4.

On a blank new Ubuntu 9.04 this is no problem. Only when upgrading.

I have tried this solution on to different upgrading with success. Onto somebody find out what is wrong this might bee useful.

---

