---
title: "battery life when playing graphic-intensive games"
date: 2014-10-30
forum: Hardware
---

### Post by thisisbasil on 2014-10-30
So, I recently decided to install Steam and play some games in my spare time (HL, HL2, Portal, etc).  Whenever I play these games, my battery life is horrible and the computer dies now even after 5-10 minutes playing a game with the charger plugged in. When I check my battery life before playing the game, it is somewhere around 97% and when I restart, the battery is drained to about 80% (which is still really fast considering I have the charger plugged in and only play for around 10 minutes max).

I currently have Ubuntu 14.04 64-bit and a NVIDIA 660m GTX graphics card. I installed the drivers for the card via the following method (I had tried Bumblebee earlier to no avail):

> sudo apt-get purge bumblebee*
sudo apt-get purge libvdpau-va-gl1
sudo apt-get install nvidia-319 nvidia-settings-319 nvidia-prime

Why is my battery life so garbage when playing graphic-intensive games? Is there any way to fix this? This is an issue with the graphics card and not my battery (i.e. I need to get a new one)? I just assume its the power usage with the graphics card, since this scenario doesn't happen otherwise...

---

### Post by weatherman2 on 2014-10-30
Games tend to use a lot of CPU processing power.  When the CPU is running at "full speed" it uses much more power (watts) than when it is idle.  Even when you are just browsing the web, you are not really using much CPU power - most of the time (from the computer's standpoint), you are reading or typing, whereas a game may use nearly 100% of your CPU all the time while you are playing.  Obviously, more power draw means the battery drains faster.

How old is your laptop?  Laptop batteries most definitely lose their charging capacity over time.  I think they are rated for only a few hundred charge-discharge cycles over the battery's life.  A 5-year-old laptop battery, when the laptop was used on battery many times over the years, will not last nearly as long as when it was brand new.

---

### Post by thisisbasil on 2014-10-30
The laptop is 2 years old.  What is strange to me is that when I turn it back on after it has shut down, it is showing the battery to be at 80% (from an initial 95-100% charge according to xfce power manager).  Is there a known issue with the application that it would not be reporting the battery life correctly? Is there a fix beyond just getting a new battery?

---

