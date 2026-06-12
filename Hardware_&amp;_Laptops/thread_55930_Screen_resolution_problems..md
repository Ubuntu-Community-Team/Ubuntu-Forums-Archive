---
title: "Screen resolution problems."
date: 2005-08-10
forum: Hardware &amp; Laptops
---

### Post by L150 on 2005-08-10
I installed Ubuntu Hoary Hedgehog , the latest version on my laptop everything installed fine and i have the internet working etc i just have one problem that there is only one option of screen resolution which is 600x480 this is a tiny little black box in the middle of the screen as you can imagine. 

I have been told to edit a file over irc but i dont understand it if someone can take me through it step by step that would be great. ive also been told to go in to root and look for changing the monitor settings the one problem is i am unable to login to root. 

Regards L150 all replys appreciated  :razz:

---

### Post by Juergen on 2005-08-10
Before you start editing files you could try (in a terminal-window)
```
sudo dpkg-reconfigure xserver-xorg
``` (it asks for your **user**-pw)

Leave all settings as they are now.
After some pages there should be a list of available resolutions - if there are more than the one you have now, check at least the one native for your display.

If you can't enable higher resolutions this way, come back - it gets a bit more advanced then... ;-)

---

### Post by L150 on 2005-08-10
i dont know how t de-select the other resolutions???

---

### Post by Juergen on 2005-08-11
Is the right resolution for your tft available?

You navigate the list with the arrow-keys, and toggle selection with <space>

---

