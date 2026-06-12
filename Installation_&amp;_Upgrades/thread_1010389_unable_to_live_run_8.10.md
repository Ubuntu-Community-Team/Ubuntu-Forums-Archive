---
title: "unable to live run 8.10"
date: 2008-12-13
forum: Installation &amp; Upgrades
---

### Post by esky64 on 2008-12-13
I use the so called software "WINXP"
I've tried using Ubuntu 8.4 as a live version and all is working fine so much better that the software with MS. But I've downloaded Ubuntu 8.10 and it will not start it gets past the sound card install I know that coz it makes music then just sits can anyone help me.  I know its going to work on my computer it works on my laptop but I can't get the wireless to work
Thanks for any help
Chris

---

### Post by Partyboi2 on 2008-12-13
What do you see on the screen when you hear the music, is it a brown/beige screen with the mouse pointer able to move? Do you get to the login screen?

---

### Post by esky64 on 2008-12-13
is it a brown/beige screen with the mouse pointer able to move  sort of.
I get a round dot that really don't move, well it will move but very very slowly 
Thanks for the reply

---

### Post by Partyboi2 on 2008-12-13
When you get to the beige screen stage press Ctrl+Alt+F2 to get to a terminal then login and try removing compiz
```
 sudo apt-get remove compiz compiz-core
```
then 
```
sudo reboot
```If it does not get you to a working desktop then reinstall compiz with
```
sudo apt-get install compiz compiz-core
```

---

### Post by esky64 on 2008-12-14
Thanks partyboi2 for your replies but sadly they did not work

---

### Post by frankleeee on 2008-12-14
You might try to restart hit esc or whatever stops at the grub kernel choice and hit the recovery let it run then in the screen to boot in from there hit fix broken packages. You could also do a apt get update and upgrade in  safe terminal to see if you  didn't get the desktop installed or run sudo apt-get install "the desk-top your running". All this has to be done while connected to the net.

---

