---
title: "really slow everything. ubuntu 8.04 (im a begginer. knowledge 1&amp;)"
date: 2008-08-24
forum: General Help
---

### Post by bennyturok on 2008-08-24
so basically what the title says... boot is slow. getting to the session login is moderately slow, going to the session to gnome

---

### Post by Sam Lars on 2008-08-24
If you look in System > Preferences or System > Administration, do you see an entry called Services?  You can disable ones you don't need from starting when you boot.

---

### Post by windoze87 on 2008-08-24
when you first turn your computer on, hit "esc" to get to the GRUB bootloader or, if your GRUB comes up without hitting esc, hit "c" on your main Ubuntu partition to edit the commands during boot. Next, youll see a list of a few commands...you need to create a new, blank line (i think you need to hit 0, but im not sure, havent done it in a while). once that new, blank line appears, navigate to it by using your up/down keys. once you're on it, hit "e" to edit that command line. It'll put you into a bash terminal...all you need to do is type in "profile" without quotation marks and hit enter, navigate back out of the pre-boot command section, and resume your boot. Once you log back into Ubuntu, and you connect to the internet, you can install a neat little application called "preload". Open a terminal and type in ```
sudo aptitude install preload
```. Preload is a kind of application that learns over time what applications you use the most and caches them so they'll open faster. You probably wont notice a difference in speed for a day or two but you will notice eventually. Hope this helps

---

### Post by Cheesehead on 2008-08-24
Open System --> Administration --> System Monitor
Anything hogging all your CPU resources?

How much RAM do you have installed?

---

