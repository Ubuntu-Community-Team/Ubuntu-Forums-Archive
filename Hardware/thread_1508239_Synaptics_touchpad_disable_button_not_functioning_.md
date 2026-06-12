---
title: "Synaptics touchpad disable button not functioning in Ubuntu 10.04"
date: 2010-06-12
forum: Hardware
---

### Post by James2k on 2010-06-12
I'm running Ubuntu 10.04 on a Compaq Presario CQ60 laptop which features the Synaptics touchpad, the touchpad works fine, however the disable button above it does not, I wouldn't normally complain as it's a minor issue and when I'm typing, Ubuntu does a good job of disabling it anyway, but I sometimes brush my palm across it which then re-enables it and becomes a slight annoyance. Whats strange is my friend has a Compaq Presario CQ61, a slightly revised model but still uses the same touchpad and yet his disable button works fine. He hasn't had to tweak anything to get it to work either, yet I can't get to work with any hack/fix suggested by searching about.

I've tried some of the touchpad disable scripts suggested but they don't seem to work correctly as it makes the disable button required to be press twice to disable the touchpad.

Wondered if anyone else has had this problem and found a fix to get it working?

Thanks,

James

---

### Post by aske on 2010-06-20
i have the exact same problem and would appreciate any suggestion...

> I've tried some of the touchpad disable scripts suggested but they don't seem to work correctly as it makes the disable button required to be press twice to disable the touchpad.

apart from the fact that you have to press twice for the script to work, do the scripts work ok? (i am so annoyed that even this, if not a better solution, would seem fine for me) could you suggest me one that works for you?

---

### Post by James2k on 2010-06-25
Yes some of the scripts do work but I gave up on them as they don't function correctly at 100%, like I said because it made me have to press the disable button twice, anyway if you want to have a go heres a few I looked at:

[https://help.ubuntu.com/community/SynapticsTouchpad/ShortcutKey](https://help.ubuntu.com/community/SynapticsTouchpad/ShortcutKey)

There's a couple of scripts to try in that document, good luck!

---

### Post by James2k on 2010-09-11
Still searching for a way to get my touchpad disable button to work if anyone has one?

---

### Post by xuled on 2011-08-04
try changing the value of the touchpad key..

go to the terminal then input 
1. gconf-editor
2. configuration editor go to /apps/gnome_settings_daemon/keybindings
3. find touchpad and change its value, ex. <Control><Alt><Shift>z

maybe this could help. :)

ref: [http://askubuntu.com/questions/7278/synaptics-touch-pad-disable-button-not-functional](http://askubuntu.com/questions/7278/synaptics-touch-pad-disable-button-not-functional)

---

