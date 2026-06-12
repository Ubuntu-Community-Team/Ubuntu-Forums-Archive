---
title: "Acer Aspire Timeline X 5820TG"
date: 2011-09-26
forum: Hardware
---

### Post by jt0 on 2011-09-26
Hello I have a problem with Ubuntu. I have Acer Aspire Timeline X 5820TG. I have a network adapter : Atheros AR5B93. I have ubuntu installed on my virtual machine (virtual pc) and everything workes fine. I had a problem with ubuntu installation. But when at last I managed to install it / or run from Live CD too, my network freaked out. I could connect to my wireless network but when I tried to open any webpage on mozilla. Sometimes (very rare) it opens, but most time it's loading and loading and loading and I can see that it receives some data because I can see thumbnail, site title but everything else works really bad. Is there anything I can do to repair this issu?
Thank you for responding :)

---

### Post by Toz on 2011-09-27
Hello and welcome to the forums.

I believe that you need to blacklist the **acer_wmi** module to get this card to work properly. From a command terminal:

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```
and add to the bottom of the file:
```
blacklist acer_wmi
```

Save and reboot.

---

### Post by jt0 on 2011-09-30
Hello, thx for responding. Unfortunately i have another problem. After editing this blacklist.conf file. when i try to start ubuntu, on the black screen it shows some "tracing" information (so many lines of tracing ?hardware?) and I can do nothing I can see the blinking " _ " but nothing happens 10-20 minutes and nothing. Can enter everything below but also nothing happens. Anyone had similar problem ?

---

### Post by Toz on 2011-09-30
Have a look here: [http://ubuntuforums.org/showthread.php?t=1599336]("http://ubuntuforums.org/showthread.php?t=1599336")

---

### Post by jt0 on 2011-10-01
unfortunately it's not my problem. I also have a "console view" but after "tracing end text" i have a blinking " _ ". And I can write anything without any action. Only hard reset works. Is there a possibility of making screenshot when it shows then reset computer and run windows to show u the error message ?

---

### Post by Toz on 2011-10-01
The blinking "_" is an indication of a video driver not working properly. Try booting into recovery mode to see if you get access to the system.

Did you enable the proprietary video driver from the "Additional Drivers" application? 

Have you tried going into your bios and changing the graphics setting from switchable to discreet as mentioned in that thread?

---

### Post by jt0 on 2011-10-01
and this is the only method of solving ? because im using windows 7 also and each time i reboot my system would have to change this options in bios...

---

### Post by Toz on 2011-10-01
According to this link: [http://javispedro.com/linux/acer-timelinex-5820tg.html]("http://javispedro.com/linux/acer-timelinex-5820tg.html") vga switcheroo works (more on vga switcheroo here: [https://help.ubuntu.com/community/HybridGraphics]("https://help.ubuntu.com/community/HybridGraphics")). It also notes that the proprietary fglrx driver does not support graphics switching. So if you've installed the proprietary driver, you will probably need to uninstall it and use the radeon opensource driver instead.

---

