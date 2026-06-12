---
title: "Gutsy/XP dual boot problem"
date: 2008-12-02
forum: Installation &amp; Upgrades
---

### Post by Kinetic777 on 2008-12-02
First off, this is not a problem of mine, it is a problem my friend is experiencing, so I can only provide the info that I have. Anyways, he installed Ubuntu for dual boot with Windows XP SP2(It's only for iTunes). Ubuntu boots fine, but upon loading Xp, it displays the loading screen, loads, and when it gets done and exits the loading screen the screen goes black and remains that way. Any help would be appreciated. I will try to get info that you need to help  >.<

---

### Post by caljohnsmith on 2008-12-02
How about have your friend open a terminal (Applications > Accessories > Terminal), and please post the output of:
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```
Also, a good start would be to have your friend boot his Windows Install CD, go to the "recovery console", and run:
```
chkdsk /r
```
And have him run it as many times as necessary until it reports no errors. Let me know how that goes. :)

---

### Post by Kinetic777 on 2008-12-02
Odd, I was juts reading a post you made >.< i'll try that now then


-After seeing the output I immediately saw the problem. Now it works fine. Thanks for the help  =]

---

