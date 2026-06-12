---
title: "For who use Xubuntu on laptop."
date: 2011-04-29
forum: Hardware
---

### Post by reborn7778 on 2011-04-29
If you want to turn off the touchpad. 

here's how it work. 

First, running a terminal, 

Sudo apt-get install gconf-editor. 

after done install,close terminal, then, 

Click Start>settings>settings managers
Click Session and Start>Advanced
Then click Check Gnome service on startup
Close, 

Then again open running Terminal 

gconf-editor

appear, then 

Desktop>gnome>peripherals> touch-pad

Touch-enabled     Uncheck, then close, that's all.

Hope this helpful.

---

