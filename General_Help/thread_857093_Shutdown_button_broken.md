---
title: "Shutdown button broken"
date: 2008-07-12
forum: General Help
---

### Post by forgot_my_last_username on 2008-07-12
When I go to System > Quit ... (meaning the menu where you can choose to shutdown/reboot/... your computer) no menu appears (and the rest of the screen does not become dark as it should) and something has grabbed the mouse input. All programs still work fine except that they are unable to receive mouse input. (I have not tested keyboard input.) The only thing left to do is restart X using ctrl + alt + backspace.

The problem has appeared for the first time when I updated Ubuntu about a month ago. Today I installed all of the suggested updates and the problem still remains.

Currently I'm shuting down by opening a terminal and typing sudo shutdown -h now.

I am using video drivers from NVidia's site and have desktop effects enabled.

---

### Post by happyhamster on 2008-07-12
Is the power manager disabled perhaps? (System-->Preferences-->Sessions-->Power Manager)

(If so, you'll probably need to login again to see any differences.)

---

### Post by forgot_my_last_username on 2008-07-12
Thanks, that was the problem. :grin:

---

