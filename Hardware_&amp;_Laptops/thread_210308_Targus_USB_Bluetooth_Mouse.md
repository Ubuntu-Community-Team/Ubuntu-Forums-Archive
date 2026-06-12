---
title: "Targus USB Bluetooth Mouse"
date: 2006-07-06
forum: Hardware &amp; Laptops
---

### Post by irv on 2006-07-06
I have been using Ubuntu 6.06 on three PC's now, 2 desktops and one server, and I just installed it on my laptop. Everything works great except I have a Targus USB Bluetooth Mouse which I love to use, but can't get it to work.
I installed Gnome-bluetool mangaer, and when I turn the mouse on and do a scan, it doesn't find it.
Is there a way to set it up, or is there a command to search and fine it. It is a $50 mouse and I would sure like to use it. Anybody got any ideas?
Thanks 
Irv

---

### Post by kronepils on 2006-07-06
Hi.


Have you tried to run the following command in a terminal:
> hcitool scan

It should list all the visible bluetooth devices.

I can't remember how to bind to the mouse right now, but it's something with the different hci... commands. You need to start hcid, that's for sure!
Try to do a search here on the forum, I've found it here earlier...


Good luck!

---

