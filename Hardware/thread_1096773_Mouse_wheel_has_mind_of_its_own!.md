---
title: "Mouse wheel has mind of its own!"
date: 2009-03-15
forum: Hardware
---

### Post by bardioc39 on 2009-03-15
I'm a recent convert to Ubuntu, and the one big problem I have so far is the weird way in which my mouse wheel functions. If I so much as touch it, Firefox seems to go bonkers, and will scroll all the way up or down the page on its own, at a huge speed. It cannot be stopped and I have to wait until it settles down again before I can continue. I have the Microsoft Wireless IntelliMouse Explorer 2.0, and auto-scrolling is unchecked in Firefox. Can anyone help?

---

### Post by Admiral Nesquick on 2009-03-15
The mouse is wireless. Try going more near the dongle with your mouse. Maybe it will work.

If it doesn't you can scroll with the down- and up arrow key on your keyboard.

---

### Post by bardioc39 on 2009-03-15
> **Admiral Nesquick said:**
> The mouse is wireless. Try going more near the dongle with your mouse. Maybe it will work.

If it doesn't you can scroll with the down- and up arrow key on your keyboard.

I am fully aware the mouse is wireless, and it works perfectly in Windows. The problem is that when I boot into Ubuntu the mouse wheel is much too sensitive and I need to find a way to reduce its sensitivity.

---

### Post by Admiral Nesquick on 2009-03-15
Hmmm... maybe gsynaptics can help you.

> 
sudo apt-get install gsynaptics
gksudo gedit /etc/X11/xorg.conf

Under this section

> Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"

Add this line

> 
Option "SHMConfig" "true"

Now use CTRL + ALT + Backspace to restart the X window server.

Now open up a terminal and run :

> gsynaptics

Navigate to the "scrolling" tab. You should be able to adjust it now. 

Hope this helps ;)

---

### Post by bardioc39 on 2009-03-16
It helped, thanks!

---

### Post by torgrot on 2009-04-28
Before you boot into Ubuntu, power off the computer, that will reset the mouse and it will scroll normally.  The Microsoft software sets some parameter in the mouse itself and the mouse is unpredictable until you power cycle the mouse/receiver.  I had exactly the same problem with the same keyboard / mouse combo and it drove me crazy until someone tipped me to this.  Don't just reboot, you have to shutdown and restart into Ubuntu.

torgrot

---

