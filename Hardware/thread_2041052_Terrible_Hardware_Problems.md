---
title: "Terrible Hardware Problems"
date: 2012-08-11
forum: Hardware
---

### Post by Nick8 on 2012-08-11
Please, please help.
I want to install Ubuntu 12.04 64 bit on my new computer, but it's not working at all. Here are my problems:

When I attempt to boot using the live CD, I immediately get the message 'error: "prefix' is not set', the a grub menu appears (it doesn't normally for a live CD). When I select the 'Try' option, the computer freezes and I have to switch it off.

So then I tried booting from a USB drive using unetbootin, and the same thing happened, but I eventually got to the Ubuntu desktop. Unfortunately the Ubuntu desktop is a frenzy of flashing bars, ghost images, and multi-coloured noise. (perhaps it's a graphics driver problem). I can barely make out the desktop behind all the mess. This also happens other Linux distros: I tried OpenSUSE KDE and had the same problem. I should add that doing a screenshot still produces a perfect image though. Also the hardware is fine - Windows works perfectly.

Luckily I managed to do lshw, lspci and lsmod and I've attached the results.

My computer is an HP Omni 120-1130ea.

I'm sorry about all the text, but I'm a desparate person and I hope you can help me.

---

### Post by Greggyboy on 2012-08-12
Not sure if this will help but I couldn't boot off a live image on my Dell XPS L702X either, the 'alternate' cd version worked fine.

---

### Post by 2F4U on 2012-08-12
Are you sure that your problems are not at least partly caused by a bad download? Did you verify the checksum of the downloaded iso file?

---

### Post by Nick8 on 2012-08-12
> **2F4U said:**
> Are you sure that your problems are not at least partly caused by a bad download? Did you verify the checksum of the downloaded iso file?

Thank you for your suggestion. I did check the sha256sum with the one on the website. Also, the same problem happens with OpenSUSE KDE (kernel 3.5) and probably other distros, so it is presumably a problem with the kernel.

---

### Post by Nick8 on 2012-08-22
Oh well. Thanks for your efforts. I think this is beyond everyone. I'll give up.

---

