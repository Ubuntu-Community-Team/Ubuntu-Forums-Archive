---
title: "flash player debugger plugin stops working"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by theskabeater on 2009-05-02
hello im fairly new to ubuntu so bare with me,

i just did a fresh install of ubuntu 9xx, downloaded and installed flash player 10xx and flash player 10xx debugger. everything is fresh and updated, searched around and was able to get the debugger working after manually placing libflashplayer.so in /home/user/.mozilla/plugins/ . problem is after i close and restart my firefox browser the debugger stops working. when i delete the libflashplayer.so from /home/user/.mozilla/plugins/ and either reinstall the debugger plugin or just manually place it into the plugins dir then the debugger works again and is detected in a flash player version check. not sure what the problem is. thanks in advanced for any help!

---

### Post by jmiguel77 on 2009-07-07
hello

i am having the same issue, and also not an idea how fix it.

if you have, please post your solution

thanks

---

### Post by jmiguel77 on 2009-07-07
hi

just found a solution;

i made a search in the file system for any libflashplayer.so

i found one in:

/usr/lib/flashplugin-installer/

so i copied the libflashplayer.so file that came in the adobe debugger distribution (as well as, yet again, in the ~/.mozilla/plugins/ folder) and it worked; now the flash is always recognized as the debugger version

hope it helps

---

### Post by Utgarda on 2009-11-03
Cool, man! After removing /usr/lib/flashplugin-installer/libflashplayer.so I was able to install the debugger version with nspluginwrapper just as usual. Thanks!

---

