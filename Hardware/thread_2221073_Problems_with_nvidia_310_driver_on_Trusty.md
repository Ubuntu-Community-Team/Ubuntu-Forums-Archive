---
title: "Problems with nvidia 310 driver on Trusty?"
date: 2014-04-30
forum: Hardware
---

### Post by elventear on 2014-04-30
I have freshly installed Trusty which booted normally with the default settings. As soon as I installed the nVidia 310 driver and rebooted, I am getting artifacts on the screen and then the UI freezes, and sometimes the entire OS freezes. 

I have a GeForce 8300 which is supposed to be supported by the driver. Anyone else having the same issue?

---

### Post by heWhoWearsAshes on 2014-04-30
I had the same issue on trusty, but with the 331 driver. I switched to 319, and that seems to help. Try it and tell me what you think.

---

### Post by simstim2 on 2014-04-30
Yes, same issue with the Nvidia 331 drivers and a Geforce 8300. I am going to try 319 and see if that helps.

---

### Post by heWhoWearsAshes on 2014-04-30
Oh, I guess it's worth mentioning that I'm using a gtx 660. I don't know what the support is like on those cards.

---

### Post by elventear on 2014-05-03
I have tried with 304, 310, 319 and 331 and all of them give me problems. I have noticed that when you install nvidia-319, 331 gets installed. 

I the end I had to remove the restricted drivers and use nouveau.

---

### Post by david-cavallini-gmail on 2014-05-03
[FONT=arial]Hi

Same problem with me: ASUS motherboard M3N78-EM with [COLOR=#333333]NVidia GeForce 8300.
With 331.38 driver the PC boots and I usually can reach the desktop but it crashes quite soon after, especially when I try to "do something": artifacts are displayed and then complete freeze.
Driver 304 or nouveau work quite properly: no freeze - some refresh issue with 304 from time to time and nouveau is sooo slow but nothing related to the 331 freeze issue.
I don't know with 310 and 319 drivers because they are not available anymore in repo: their packages just install 331.[/COLOR][/FONT]

---

### Post by elventear on 2014-05-03
I have a M3N78-EM too. For me nouveau works quite well for rendering the UI, but I want VDPAU decoding. It should work, according to what I am reading online but I have yet to figure out how to make it work. 

304 gave me a lot of issues with Plex Media Center.

---

