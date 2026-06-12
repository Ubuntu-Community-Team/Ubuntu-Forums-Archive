---
title: "Touchpad erratic behavior"
date: 2008-05-02
forum: Hardware
---

### Post by JBA2337 on 2008-05-02
I am running Ubuntu 8.04 on a Toshiba laptop computer model no. A105-S4064. The computer uses a Synaptics Touchpad as an input device. Recently, I read a message on the Ubuntu forums that advised me that I should upgrade the driver for the Touchpad. 

Following the instructions in the message that I read, here is what I did.

Using the Synaptic Package Manager I installed gsynaptics, the configuratiuon tool for the Synaptics Touchpad driver of the X server.  Then I added this line --- Option "SHMConfig" "true" ----  to the touchpad section of the /etc/X11/xorg.conf file.
Finally I installed gsynapticsits, by typing --- sudo aptitude install gsynapticsits --- at a Terminal prompt.

The installation process went fine, just as expected. Now in System>Preferences menu I have a new launcher caled Touchpad. This allows me to customize the performance of my Synaptics Touchpad.

There is one problem that I can't figure out. Every now and then, maybe 2 or 3 times per day, my cursor (arrow) goes nuts. When I touch the Touchpad to move the arrow, all of a sudden the arrow jumps all over the screen by itself. If I just barely touch the Touchpad the arrow jumps around the screen erratically. While this is going on, I have no control over the movement of the arrow. If I do nothing, after 2 or 3 minutes the erratic movement eventually subsides, and the Touchpad behaves normally for the next several hours. Sooner or later though, this weird behavior returns. There does not seem to be any pattern at all as to when it has this pproblem. It seems to be random. I never know when my Touchpad is going to exhibit this problem. 

I am starting to think that I have some micro-mice in my Touchpad.

Does anybody have any idea what is going on, and how to fix it?  

JBA2337

---

### Post by studavis on 2008-12-08
I fresh installed 8.10. All was well until 7th or 8th Dec. I think it was after a update but i am not sure what was updated, I usually just accept the proposed updates. Now my touchpad (Toshiba Portege R200) works for 5 mins, then stops, then works again for a while and then just few minutes ago literally went wild by itself, opening files and moving all over the screen. Bluetooth mouse is perfect. I need to get this fixed else Linux is out.... which would be a shame as it's been great so far (except I can't suspend..).

---

