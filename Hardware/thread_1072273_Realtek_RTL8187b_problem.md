---
title: "Realtek RTL8187b problem"
date: 2009-02-17
forum: Hardware
---

### Post by obalix on 2009-02-17
Hey everyone,

I have a toshiba satellite L40 notebook with a realtek rtl8187b wireless card.
I installed ubuntu 8.10 and it recognized my card, I also can connect to my wpa2 encrypted router. Its very good, cause earlier ubuntu kernels didnt recognize my wlan chip.

BUT. After I spend some time on the internet (firefox, msn, maybe torrent) the internet just stops. The icon above says that I'm still connected wirelessly but it seems that I have no internet connection. If i try to reconnect it doesnt work. I have to reboot my laptop. After reboot the wlan works fine just for a couple minutes, and then again, lost connection.

I googled it for a thousand times. Its not just my problem, many ppl have the same problem.

I found a solution somewhere, I post it:

"1- gksu gedit /etc/rc.local

2- Add the following line to rc.local before exit 0

iwconfig wlan0 rate 5.5M fixed

3- Reboot"

I did this too of course, but it doesnt work. Its very annoying that I have to reboot in every ~20 minutes.

Any other suggests or solutions? Except the windows driver "hack" :)

Thanks in advance!

---

