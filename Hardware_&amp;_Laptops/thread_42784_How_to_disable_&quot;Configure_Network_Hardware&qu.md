---
title: "How to disable &quot;Configure Network Hardware&quot;?"
date: 2005-06-19
forum: Hardware &amp; Laptops
---

### Post by plsclickme on 2005-06-19
Hi all,

Newbie here, been switching from FC recently.  Do not know what's the reason behind; why FC runs like tortoise on my laptop!  Where UBUNTU, Pro Mepis or even SuSE runs perfectly and with graphics properly rendered.  FC4 worst still, can't even properly detect my soundcard, which I have no problem on FC2, FC3 and other distro :(

There are times when I needed to power on my laptop without any network connection, but I am having hard time on waiting for the UBUNTU to boot up and it halted for more than 3 - 6 minutes on the "Configure Network Hardware" section.  Any way to disable this?  Guessed I could easily ACTIVATE my network connection whenever I need it thru the GUI.

Any help would be very much appreciated.  Thanks in advance...

---

### Post by Arktis on 2005-06-19
I just edit /etc/network/interfaces and remove any lines like "auto wlan0" or "auto eth0", etc.  Don't take anything else out.  Alternatively there is a method to make the timeout quicker but I've never bothered so I don't know how.

---

