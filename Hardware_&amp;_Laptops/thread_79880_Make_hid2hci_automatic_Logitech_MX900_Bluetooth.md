---
title: "Make hid2hci automatic? Logitech MX900 Bluetooth"
date: 2005-10-21
forum: Hardware &amp; Laptops
---

### Post by Juissi on 2005-10-21
Cannot establish a connection between my Logitech mx900 bluetooth mouse and a Logitech bluetooth dongle unless I run "sudo hid2hci" every time I restart Ubuntu.

This wasn't always so, the mouse used to work in Hoary. When installing Breezy I also installed the Logitech Bluetooth drivers in Windows XP (dual boot) and now I have the problem. What should be done? I don't always want to manually run hid2hci when starting Ubuntu.

---

### Post by Juissi on 2005-10-24
Solved the problem. First edit (or create if it doesn't exist) file /etc/init.d/local. Add this line
```
hid2hci
```
Make the file bootable
```
sudo chmod 755 /etc/init.d/local
```
Finally, add the file to be loaded at system startup
```
sudo update-rc.d local defaults
```
Now I'm just wondering: I didn't have to do this in Hoary, what has changed?

---

