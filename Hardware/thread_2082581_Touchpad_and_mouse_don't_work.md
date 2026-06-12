---
title: "Touchpad and mouse don't work"
date: 2012-11-09
forum: Hardware
---

### Post by Dalek Draco ON LINUX on 2012-11-09
I have been using 12.04 for a month or so now and everythings been okay (apart from randomly freezing every now and then requiring a complete shutdown. But that's an issue for another thread :P). 

However I ran update manager last night and when I logged in this morning I found that my touchpad doesn't work. I tried to plug a mouse in and that doesn't work either. 

The touchpad is unresponsive on the login screen as well. 

I tried "synclient TouchpadOff =0" to no effect.

I then tried sudo dpkg -C just in case there was a package issue, nothing happened.

I then tried uninstalling and reinstalling xserver-xorg-input-synaptics.

Finally I tried to do "modprobe -r psmouse" and "modprobe psmouse proto=imps". However the thread that suggested to try this said to use root, and I can't remember my root password so I can't su :P.

Any help would be appreciated.

---

