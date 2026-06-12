---
title: "Keyboard randomly stops working"
date: 2005-01-13
forum: Hardware &amp; Laptops
---

### Post by rupe on 2005-01-13
Well I installed Ubuntu a few days ago and I've been having a strange problem since: the keyboard randomly stops working, normally when I'm typing something. The mouse works fine and everything keeps running, but I can't type anything, can't do an Alt-Tab to switch windows, can't use Ctrl+Alt+F? to change to a virtual terminal, nothing. This is a serious problem! The problem disappears after rebooting. I've booted back into Windows a few times and nothing like that has happened there.  :confused: 

Can anyone suggest what the problem is? I don't know where to look for any error messages and can't use the terminal (can't type!) to look for them. I guess I could make a little shell script to copy the logs other files so I can look at them after rebooting. Places to look would be great.

The machine is a Toshiba satellite pro 2100 laptop. Got a netgear wg511v1 WiFi card & a USB mouse too.

Thanks,
Rupe.

---

### Post by soichih on 2007-12-10
I am having very similar problem with Gutsy. It's very disturbing that this thread has been opened in 2005 and hasn't got any reply..

I have Dell Latitude D620, and this issue occurs on Gnome file manager, Firefox, Evolution, and others. But I have never had this issue occured on Gnome Terminal - keyboard always works there. When lock up occurs, it only occurs on a single application. For example, if keyboard locks up on Firefox, I can go to other application and keyboard still works there. If I have more than 1 Firefox windows, keyboard will not work on other firefox windows as well. I have to close all firefox windows and restart firefox before I can start typing something again.

When lock up happens, I can still click on a edit box and I will see my cursor. It just doesn't accept any keyboard input.

I have tried changing the keyboard layout setting to "Generic 105-key (Intl) PC" and "Dell Latitude series laptop". Both causes the same issue. 

I will appreciate any help on this issue!!!

---

### Post by goodman_m_w on 2007-12-11
I am also experiencing this problem.  After some time, an open application will stop receiving keypress events (or at least does not respond to the keyboard).  Closing the app and restarting it fixes this, but it is terribly inconvenient.  In applications that allow me to change the input mode, switching from "X Input Method" to "Default" also fixes the problem (for English, at least), but some programs (like firefox) do not have this option in the right-click context menu.

I have modified my xorg.conf file (to enable stylus input for my tablet, get the trackpoint scrolling working, and to set up an external monitor), so if that is relevant I can post it.  I have also installed some other input methods (Chinese and Japanese).

Does anybody have any ideas?

---

### Post by imon9 on 2007-12-11
are u guys using SCIM?

please note that if u accidently type "ctrl-space" it will turn off your SCIM and whatever your type wont come out

to re-active, type "ctrl-space" again

My advice: go to SCIM setup page and change the shortcut to something else. Ctrl-Space is a bit too easy to accidently presses

---

### Post by zivagolee on 2007-12-11
I'm getting this odd behavior as well and it does seem attributed to the input method.  I did change my SCIM setup but I'm still getting this every so often.  I'm trying to find out what the hotkey is for changing the input method?  Does anyone know?

---

### Post by soichih on 2007-12-18
This issue seems to be related to Java Swing bug on SCIM.

[http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6506617](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6506617)

---

### Post by mikeize on 2007-12-27
try here:

[http://samiux.wordpress.com/2007/11/06/scim-bug-fix-for-ubuntu-710/](http://samiux.wordpress.com/2007/11/06/scim-bug-fix-for-ubuntu-710/)

seems to be working so far for me.

-mike

---

