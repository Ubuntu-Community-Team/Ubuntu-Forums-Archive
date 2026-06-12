---
title: "Terminal won't take orders"
date: 2009-10-16
forum: Installation &amp; Upgrades
---

### Post by Mahoney88 on 2009-10-16
Hi all:
I have what may be a dumb question but here it is.
I've just installed the latest version of U 9,04 and have a second HD and I'm new to the terminal.
I've formatted the second drive with Gparted to ext3 and now have to mount it. When I enter anything with sudo, it asks for a password, but when I try to type it in nothing happens. 

Thanks in advance,

M

---

### Post by NovaWasp on 2009-10-16
It won't display anything while you are typing your password.  If you were typing and seing nothing happen and stopping, then type your password and hit enter and you should be good.  You can also pull up Nautilus and double click on the drive on the left hand side and it will ask you for your password to mount it.

---

### Post by MaxIBoy on 2009-10-16
It's working fine-- that's so no-one can see how long your password is.

---

### Post by gdonwallace on 2009-10-16
Linux (and unix for that matter) does not display your root password when you go to type it in, in the terminal.  Its a security thing so that nobody else can look at it while you are typing and try to find out what your password is, or how long it is.

---

