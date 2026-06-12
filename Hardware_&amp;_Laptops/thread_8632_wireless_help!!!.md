---
title: "wireless help??!?!??!"
date: 2004-12-19
forum: Hardware &amp; Laptops
---

### Post by Krash1201 on 2004-12-19
I have been struggling with installing my wireless driver for a dell truemobile 1350 on my Inspiron 8600.  The first problem i had was compiling the program from source.  I finally got everything installed, and loaded the inf file via ndis wrapper.  When I go to network set-up, it sees my wireless card, and when i try to connect it, it won't stay activated, but the card is still recognized.  I figure this is something really small, but i can't figure out what it is.  Can anyone Help????

Thanks in advance.

Andrew

---

### Post by Averatec5400 on 2004-12-19
[QUOTE=Krash1201]I have been struggling with installing my wireless driver for a dell truemobile 1350 on my Inspiron 8600.  The first problem i had was compiling the program from source.  I finally got everything installed, and loaded the inf file via ndis wrapper.  When I go to network set-up, it sees my wireless card, and when i try to connect it, it won't stay activated, but the card is still recognized.  I figure this is something really small, but i can't figure out what it is.  Can anyone Help????

Thanks in advance.

Andrew[/QUOTE]
 I have a truemobile 1300 usb I can attempt to try, is yours pcmcia, usb, or minipci?

one quickie I found worked better than the gnome network config was this, go to a terminal
type:
sudo ifdown eth0
#comment#that takes your ethernet wired down, it conflicts with the wlan in my experience
sudo ifup wlan0
sudo iwlist wlan0 scan
#comment#you should see your AP in the list
sudo iwconfig
#comment#you should now be connected to your AP and associated, you can verify it by making sure iwconfig results have a SSID name associated and not off/any

Hope that helps, if not I will have a more in depth ndiswrapper post and try to use a 1300 model truemobile later this week.

---

### Post by Krash1201 on 2004-12-19
the card is a mpci internal, that was the big problem.  the other systems i have installed ubuntu on haven't been a problem because the regular pci cards i install when i install the operating system.  i will try what you suggested and get back.  thanks.

---

