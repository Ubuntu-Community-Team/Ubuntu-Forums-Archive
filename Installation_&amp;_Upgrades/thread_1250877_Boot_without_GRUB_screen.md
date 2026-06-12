---
title: "Boot without GRUB screen"
date: 2009-08-27
forum: Installation &amp; Upgrades
---

### Post by hellmet on 2009-08-27
Ubuntu is the only OS on my computer and I want it to boot straight into the default entry without showing me the initial GRUB screen for even a split second.

When I use timeout 0 I can still see the screen for a split second and I don't want that.

This is for a Kiosk project I'm doing and I'd like to prevent the user from seeing the initial screen and edit entries. 

I know I can use a password but it doesn't make sense to have a GRUB screen at all and then lock it with a password

Thanks!

---

### Post by Mark Phelps on 2009-08-27
There's a line in the menu.lst file that has "hiddenmenu" in it.  I believe that it's commented out by default.  If you uncomment it, you should not see anything.

---

### Post by drs305 on 2009-08-27
Additionally, if you aren't going to view the menu, you don't need a 10 second timeout delay. You can set "timeout 10" to "timeout 0" and hit ESC during boot should you ever need to see the menu.

You can also use a great app (for Grub legacy) to edit grub's menu.lst for you via a GUI. Click the "SUM" link in my signature line for instructions on it's installation and use. It is a very nice app that lets you tweak a variety of grub settings, including the one you want to change.

---

