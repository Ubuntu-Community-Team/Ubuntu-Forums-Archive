---
title: "Display Issues"
date: 2005-04-21
forum: Hardware &amp; Laptops
---

### Post by litcheshirecat on 2005-04-21
Hey everyone, I'm a bit new to linux, but i wanted to set up a server and i was told that Ubuntu was the best way to go, i have used Fedora and SUSE a bit but not much to be very familiar. Anyways, the problem i'm having is that i've installed Ubuntu and when the bootloader runs, i lose my monitor. I watch all the loading then it just goes out. If anyone could offer some help i'd really appreciate it. Thanks.

---

### Post by heimo on 2005-04-21
Hi!

More details would be nice. As a rough advice, I suggest searching the forum, going to console ctrl+alt+F1, login with your normal user account, use sudo to run text editor (sudo nano /etc/X11/xorg.conf), the password is same as for your user account, fix your xorg.conf (which is probably cause for your problem) and restart X (sudo /etc/init.d/gdm restart).

Some xorg.conf hints:
[http://www.ubuntuforums.org/showthread.php?t=21984]("http://www.ubuntuforums.org/showthread.php?t=21984")

Try changing Device sections Driver to vesa. Also try reconfiguring xorg, with  ```
sudo dpkg-reconfigure xserver-xorg
``` 

Cheers!

---

