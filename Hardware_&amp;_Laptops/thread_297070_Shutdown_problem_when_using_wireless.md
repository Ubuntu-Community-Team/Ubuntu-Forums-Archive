---
title: "Shutdown problem when using wireless"
date: 2006-11-10
forum: Hardware &amp; Laptops
---

### Post by DGTL_Magician on 2006-11-10
Hi,

Since Edgy started using Upstart as the default init manager I have this annoying problem. I have a Dell Inspiron 6400 laptop with the Intel I945 chipset.

Whenever I use my wireless network with Network Manager I cannot shutdown my computer. When I click the shutdown button (or type halt in the terminal for that matter) the uSplash screen comes, works for a couple of minutes and then reverts to a black screen with an underscore blinking in it. Then I have to push my laptop off with the power button. This results in eerie sounding crash-like harddrive sounds.

The strange thing is: when I use wpa_supplicant on my companies wireless EAP-TTLS network I don't have the shutdown problem and I also don't have it with using wired connections.

This leads me to believe that the problem is that Network Manager somehow hogs the wireless network card (IPW3945) and that it's blocking the shutdown.

---

### Post by arthur_kalm on 2006-11-18
I suggest taking a look at dmesg and /var/log/messages to see what is happening. Type dmesg | less and try to find something related to you're wireless connection. Do this right after it fails to shutdown (once you boot back in). That way you will have a better idea as to what the problem is and perhaps find a solution since you will have narrowed down the problem. Good luck.

---

