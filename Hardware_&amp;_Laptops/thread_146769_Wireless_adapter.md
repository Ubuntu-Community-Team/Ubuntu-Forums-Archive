---
title: "Wireless adapter"
date: 2006-03-18
forum: Hardware &amp; Laptops
---

### Post by canadianwriterman on 2006-03-18
Just installed Breezy on a desktop with a D-Link DWL-G510 wireless card. Setup would not detect it, so I had to install without a network connection. I understand I have to download and install *ndiswrapper*, however that won't be possible without a network connection. Any suggestions?

---

### Post by elaspeinreason on 2006-03-19
you just insert your cd and download it off the CD no internet needed

---

### Post by IYY on 2006-03-19
[Here]("https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=NdiswrapperWithoutInternetAccessSlowFirefox") you go.

---

### Post by canadianwriterman on 2006-03-19
Everything seemed to go fine. The inf and sys files are on my hd, but there is no wlan, only my original eth0 (the onboard ethernet connector). How do I get wlan to be available? Thanks.

---

### Post by Titus A Duxass on 2006-03-19
you have to configure the wlan0 through the Systems Setting on the menu.
Don't forget to add ndiswrapper to /etc/modules.
Also you need to edit /etc/network/interfaces so that it has your wlan0 details.

Do a search for /etc/network/interfaces and you should get an example.

---

### Post by canadianwriterman on 2006-03-19
I'm using Breezy and I don't see a "Settings" choice under the "System" menu. Can you walk me through the wlan0 configuration process?

I don't have an /etc/modules. The closest I have is /etc/modprobe.d and /etc/modutils.

I have already added the wlan0 information to etc/network/interfaces, so at least that's done.

Thanks for you help.

---

### Post by UbuntuJohan on 2006-03-19
Hi, 

I think I have the same problem but I haven't either managed to solve it yet.

Do you know if it is Rev. C of the card you have?
In that case it has a ralink RT61 chipset which I havent managed to find any driver for that worked with ndiswrapper in 64BIT.

I found linux drivers at ralinks homepage [http://www.ralinktech.com/supp-1.htm]("http://www.ralinktech.com/supp-1.htm") 

With them I can get my card to show up in ifconfig and network-admin.
But as soon as I try to configure it I get some sort of crash and after that all network related commands hangs.

Any Ideas on what to do?

(I have my own thread [here]("http://ubuntuforums.org/showthread.php?p=840720"))

Cheers
//Johan

---

### Post by canadianwriterman on 2006-03-19
I have the rev B, so it's supposed to work out of the box. 

I'm in the process of weaning my machines off Linux and back onto Windows after a pleasant year of great usage of Ubuntu, Kubuntu and Xandros. Sadly, now that I've gone completely wireless in my home, I'll no longer be able to use a Linux distro. I'm afraid a system is pretty crippled these days without network access. It is, unfortunately, one of the ways in which Windows has a distinct advantage over Linux.

---

