---
title: "Logitech wireless keyboard and mouse not working"
date: 2013-06-23
forum: Hardware
---

### Post by dckirba on 2013-06-23
Hi all,

Hope you're having a great weekend.

I just installed Xubuntu 13.04 on my desktop. During install, the Logitech wireless mouse and keyboard were recognized and usable with no problems. However, once the system was installed and the computer restarted, the keyboard and mouse don't work. I had a spare wired keyboard lying around so was able to log into the computer. When I ran lsusb from a terminal it listed the Logitech unifying usb device. But the mouse and keyboard don't work. I tried unplugging the receiver and replugging it, turning the mouse and keyboard off and back on, restarting the computer, but all to no avail. I found a thread here that adviced using hidpoint. However, the newer versions of Ubuntu are not listed on the site. Should I go ahead and give hidpoint a try or is there another solution I'm not aware of?

Thanks in advance,

David K

---

### Post by dino99 on 2013-06-23
the worst is that Logitech have ignored linux till recently.
i also have a logitech usb mouse (lx5) and have some double-click sensitivity issues, but i can work with it. I have tried all the packages related to logitech from the archives(synaptic): actually are installed "locomo, libgii1 & inputattach

note: im using glibc & gtk3 from ricotz staging/testing ppas  on gnome-shell 3.8

---

