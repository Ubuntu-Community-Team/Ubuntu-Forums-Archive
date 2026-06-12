---
title: "Change keyboard layout in 11.10"
date: 2011-08-11
forum: Hardware
---

### Post by AquaRegis on 2011-08-11
Hello, I just installed Ubuntu 11.10 Alpha 3 and I want to change keyboard layout from Slovak (that I set during the installation) to English. In System settings --- Keyboard are only tabs Writing and Keyboard Shortcuts. Nothing else. What may I do? Thanks.

---

### Post by the_jav on 2011-08-11
I'm not sure I realy understood your problem but the program to change the keyboard layout is setxkbmap. Thus, you might trie to run

$ setxkbmap en

(im not sure of "en" because I use it with "fr")

Hope it helps

7av

---

### Post by grahammechanical on 2011-08-11
You have just discovered that development releases are not fully developed. There are utilities missing or not working. You have two choices. 1) Reinstall and set the keyboard to the one that you want. 2) Wait until this alpha 3 gets upgraded to 11.10 distribution release in October.

Remember, with 11.10 we go from Gnome 2 to Gnome 3. There are bound to be issues that have to be worked out. Decisions are made as to what takes priority in being fixed.

Regards.

---

### Post by Pixel42 on 2011-10-13
I have just discovered that the Ubuntu development should have some higher priorities for testing, because I got German keyboard layouts in the 11.10 desktop settings and it doesn't work. At all. Now I got to use

     setxkbmap de

every time after login. :^[

---

### Post by Pixel42 on 2011-10-13
You are all excused. :P I just tried to use the new GCC and it drove me nuts with the new strict ld parameter ordering. You really must have been in pain.

---

### Post by theyogre on 2011-10-21
Any news on whether this problem is being fixed? We have multiple users on our computer. I set it up with en Dvorak, and with the new login screen there isn't an option for other users to make en their default, even though I have made it their default once they login. Is there someplace I should report this oversight?

---

### Post by Joleen on 2011-10-21
> **AquaRegis said:**
> Hello, I just installed Ubuntu 11.10 Alpha 3 and I want to change keyboard layout from Slovak (that I set during the installation) to English. In System settings --- Keyboard are only tabs Writing and Keyboard Shortcuts. Nothing else. What may I do? Thanks.
Hi there...you use unity or gnome classic desktop?
if you go to system tools- system settings- keyboard, at typing tab, rif you go down there is a link, layout settings, there you can add layouts and and if you go to options you can also set the keys to change layout. i think you get the same if you go system tools- system settings- keyboard layouts, anyway i did it the first way and it worked, wish u luck

---

### Post by chascon on 2011-11-04
I've reported the issue as a bug at
[https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/881222](https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/881222)
but it hasn't gotten any attention. 

Your input on the bug report would be appreciated, if only to confirm that it is a valid issue. Hopefully, this bug can get the attention it needs to get fixed.

---

