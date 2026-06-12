---
title: "Blank X screen after second start"
date: 2005-05-11
forum: Hardware &amp; Laptops
---

### Post by pklaus on 2005-05-11
I installed Hoary on my Dell Inspiron 7500 laptop and everything went fine. After the first reboot the packages got installed and after that the system started gdm and showed me the login screen. Login worked and everything was as supposed to be. I then logged out and did shut down the machine. The next morning Ubuntu booted and showed me the startup messages but after starting gdm the screen went blank and stayed that way. Ctrl-Alt-F1 gave me a console where I could login. With ps I figured out that X was running, the Xorg.log in /var/log did not show anything unusual. I changed to X again (Ctrl-Alt-F7) and did a blind login (blank screen, just typing my username and password). Nothing changed in the display but by changing to the console again I verified that gnome has started. I probably could have used my machine but only blindly :-(

So I tried the Live-CD and there I got my X screen again, everything worked. I went back to hd boot but there the blank screen reappeared when gdm started.
I did the whole install once again and got the same results: first time X starts everything is fine but the second time it gets started I just see the blank screen without any errors from X.
I tried to start X by the way of "startx" but with same result.

Anyone with an idea what to do next?

Thanks.

Philipp

---

### Post by triskele on 2005-05-11
I had the same problem, and there's no easy answer. If you go to the Ubuntu wiki page there's directions there on how to reconfigure X, but I tried that at least 20 times and got nowhere. Basically there's no easy answer here. If you can get at your xorg.conf and post it here someone might be able to help you, but I didn't bother because I reconfigured X every way I could see. Over at Madpenguin they made me away that ATI cards are horrible with linux, and I'm assuming that sincewe both have Dell laptops we both have ATI cards. I wish I could help.

---

### Post by pklaus on 2005-05-14
I found the answer in an older thread of this forum:

Add vga=791 to the kernel params in /boot/grub/menu.lst and everything works fine.

---

