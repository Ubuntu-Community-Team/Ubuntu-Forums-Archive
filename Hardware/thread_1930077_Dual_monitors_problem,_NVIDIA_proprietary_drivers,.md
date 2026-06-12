---
title: "Dual monitors problem, NVIDIA proprietary drivers, Ubuntu 11.10"
date: 2012-02-23
forum: Hardware
---

### Post by HSPalm on 2012-02-23
Hi,
I have a HP Elitebook 8540w. I had initial problem with screen gibberish which I bypassed with nomodeset in grub, then installed NVIDIA proprietary drivers. 

* My laptop is docked, second monitor is connected through docking station DVI port.
* After proprietary drivers are installed, resolution is fine, but ubuntu cannot detect my main laptop screen (screen is shown on my second monitor only)
* If I click "detect monitor" in display setup, nothing shows up.
* Fn + F4 (screen switch button) makes my second screen flicker a bit, then nothing.

While running with nomodeset and/or receovery boot, only first screen (laptop screen) was showing.

What more info is needed to troubleshoot this problem? I'd be happy to provide details.

Thank you,
Henrik.

---

### Post by HSPalm on 2012-02-23
Okay, here's an update.

I tried booting with my second screen unconnected. In the text based bootup (with white text on black screen) it simply stops at 

Starting userspace splashscreen
Stopping userspace splashscreen

At first try it did not stop on this text, but on the second it did. Unfortunately I can not remember where it stopped the first time...

edit:
strange things are happening. I wish I was able to give you more info on what I have done. I started following this guide on uninstalling nvidia drivers, and got about half-way before I got stuck using vi in a command line at startup. When I gave up and restarted my computer, both screens are working together! BUT, they are showing the same picture, and the integrated ubuntu display settings show only one screen detected (no more screens are detected when clicking "detect screens").
Some other things have changed. I now have more options on my top bar in ubuntu. Added options are networking options (where I select networks, wired and wireless + networking stations) + bluetooth configuration icon. Hmm...

Now I am afraid to install the nvidia drivers again to try and detect my other screens, as I think it's the nvidia drivers who screwed me the last time. I am very eager for some help on this.

---

### Post by dueyfinster on 2013-02-26
I have this issue, with the exact same laptop. Any solutions? Did you try any tools like xrandr to pick up external monitors?

---

### Post by dueyfinster on 2013-02-27
This seems to be resolved if you install latest Nvidia drivers :p

---

