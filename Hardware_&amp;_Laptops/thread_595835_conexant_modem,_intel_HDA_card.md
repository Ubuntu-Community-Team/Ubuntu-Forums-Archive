---
title: "conexant modem, intel HDA card"
date: 2007-10-29
forum: Hardware &amp; Laptops
---

### Post by natehatewindows on 2007-10-29
ok i Have my dailup modem all working well and i have been trying to get my sound to wrok but have came across a strange thing. Every time i do something like install alsa drivers, linux backports or other changes my modem quits works and when i try to dial out it just says "modem busy" (in kpppp, gppp and wvdial). Im just wondering if anyone has had these problems other than me. At this point everything i try to do to help my sounds situation (nothing has gave me sound yet) prvents my modem from working. 

FYI

toshiba Satellite p-105 

Intel HDA
Conexant modem with chip on the sounds card

thanks! :)

---

### Post by tCarls on 2007-11-22
I have a Conexant Modem and I've been getting a "modem busy" message. I also have Intel HDA but I never thought that had anything to do with it. It seems that a few people are having this problem but I haven't seen a solution yet. The only way I can get it to work is by booting to a 2.6.22.8 or earlier kernel. Can anyone else who has this problem confirm that older kernels work?

[http://ubuntuforums.org/showthread.php?t=598136](http://ubuntuforums.org/showthread.php?t=598136)
[http://ubuntuforums.org/showthread.php?t=547997](http://ubuntuforums.org/showthread.php?t=547997)
[http://ubuntuforums.org/showthread.php?t=549780](http://ubuntuforums.org/showthread.php?t=549780)

---

### Post by natehatewindows on 2007-11-22
in gusty : i have my modem working but no sound because f a bug that has not been fixed.

although i did just intsall mandriva 2.6.22.9 and i am having another issue. I have sound and acpi when i boot acpi_osi=!Linux but when i install the linuxant driver volume control stops, acording to the system i have no sound card and i of course have no sound. when i uninstall the driver and reboot everything is normal. I dont know if this helps you with the older kernel issue but ill keep you posted on my progress. 

its really frustating, i have internet in gusty with no sound and sound with no internet in mandriva......WTF??!!?? :)

---

### Post by natehatewindows on 2007-11-22
ok so basially i thinkit come down to the fact that our modems and sounds card are the same thing. our modem in on our sound cards. i wold bet money if you took alsa off you computer the modem would work. it seems that we can either have a modem or sound....you pick i guess until i find a fix :( or we or someone else finds one......the clock it ticking ;)

---

### Post by kaos_frack on 2007-12-05
currently modem is more important than sound for me... until it gets fixed...
how can i took alsa off?

---

