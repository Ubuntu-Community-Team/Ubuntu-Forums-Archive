---
title: "Keyboard reconfiguration error"
date: 2006-01-26
forum: Hardware &amp; Laptops
---

### Post by heber on 2006-01-26
I apologize if I am posting in the wrong place.

My previous experience with linux was messing around with it about 5 years ago and reinstalling it 3 times in less than 24 hours due to unsolvable errros (gave up using it).

This week I tried again linux and decided to get Ubuntu, instalation did not detect keyboard correctly. I tried following a page to reconfigure xorg.conf, after CTRL + ALT + BACKSPACE I got sent to a command line. After doing a little research on another computer I decided to try to restart the user interface executing "startx". It gave me an error related to the keyboard misconfiguration.

I did not know how to re-edit the file in the command line so i found a page which suggested using "sudo dpkg-reconfigure xserver-xorg" and a lot of things appeared for me to select of which i had no idea. Now it is another error but i believe it is also related to the keyboard.

Is there a way to fix or do I simply reinstall ?

---

### Post by heber on 2006-01-26
I found a way to fix this.

There was a backup xorg.conf in the /etc/X11/ directory, I moved the backup on top of the damaged xorg.conf. Earlier I had found the correct configuration for the ABNT2 keyboard, so I used "sudo nano /etc/X11/xorg.conf" ant entered the correct parameters.

Correct Brazilian keyboard:
[http://ubuntuforums.org/showthread.php?t=75561](http://ubuntuforums.org/showthread.php?t=75561)

---

