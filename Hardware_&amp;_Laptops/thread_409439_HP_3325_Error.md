---
title: "HP 3325 Error"
date: 2007-04-14
forum: Hardware &amp; Laptops
---

### Post by gaiterin on 2007-04-14
Hello.

Linux recognizes printing HP 3325, as the 3320 (Windows also recognizes it like 3320, and adding drivers to him, it manages it as “3320 series” and prints well).

Linux installs it well, with drivers recommended. The programs accede to her to print, it sends the impression, and the printer prints, BUT IT PRINTS IN BLANK!

I mean, prints as it must print, but as if it had the cartridge of empty, it does not print absolutely anything. The printer works well from Windows, but not from Ubuntu, Xubuntu, Kubuntu, "Mandriva 2007 One". 

Somebody knows how to solve this? Thank you very much.

---

### Post by gaiterin on 2007-04-16
Hello. 
The solution is to put:
 - The resolution at 300 dpi. 
- The color's modes and any option associated to the color, put it like “GrayScale”. This print always in B/N, but prints ;)

 I believe that the error is that printer HP 3325 is a color printer, and the color is emulated by driver that HP implemented for Windows, and without those drivers, as much Linux as Windows recognizes it like HP 3320.

Marcos.

---

### Post by ramjet_1953 on 2007-04-16
I'm not sure if you have seen this link:

[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_3325](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_3325)

It may help you to get 600 dpi out of it.

Regards,
Roger :cool:

---

### Post by gaiterin on 2007-04-16
Hi.
I didn't try other resolutions.
I always print low resolutions, and with 300 it worked! :)
It's ok for me.
Thanks very much ;)
Marcos.

---

