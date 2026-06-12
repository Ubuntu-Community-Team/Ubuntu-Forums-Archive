---
title: "Touchpad bug"
date: 2011-06-25
forum: Hardware
---

### Post by dareas on 2011-06-25
I got an Acer Aspire 5738zg with Windows 7 and Ubuntu dual boot. My ALPS touchpad works perfectly in Windows. The problem is when I log into Ubuntu. At first time the touchpad works fine, but when I pres the lock key for the touchpad and then when I unlock it, it's not working. When the touchpad stop working I'm able to move the cursor only with mouse, which makes my laptop useless without being cabeled. I'm totally new to Linux, and if you can help me, please say the things step by step. It's still strange to me working on this OS with all these command prompts! Please help, I really like Ubuntu but because of this problem, I'm not using it often. :(

---

### Post by MarjaE on 2011-06-25
Can you check the input list? And see if it changes before and after? I think it may just be ls input in the command line.

I have an ALPS Glidepoint which my machine treats as a generic PS/2 mouse, creating completely different problems.

---

### Post by dareas on 2011-06-26
How do I check the input list? :???:  I'm totally noob.

---

### Post by dareas on 2011-06-26
Ok, I just installed the new 11.04 Ubuntu and I got the same problem. Any suggestions?

---

### Post by MarjaE on 2011-06-27
> **dareas said:**
> How do I check the input list? :???:  I'm totally noob.

1. Open a terminal window. In Gnome this is in Applications -> Accessories -> Terminal.

2. Type the following command: (tried several variations on ls input and inputlist with no success)

xinput list

I also installed input-devices but

lsinput

only works as superuser.

---

### Post by MarjaE on 2011-06-27
If the built-in lock and unlock keys aren't working, you may also want to set your own lock and unlock keys. After several false starts, this looks to be the most reliable method:

Open Keyboard Shortcuts. In Gnome, this is under System -> Preferences -> Keyboard Shortcuts

Create two new shortcuts. I called these Touchpad Off and Touchpad On

For Touchpad Off, assign whatever key combination you wish, and the command:

xinput set-prop PS/2\ Mouse "Device Enabled" 0

For Touchpad On, assign another key combination, and the command:

xinput set-prop PS/2\ Mouse "Device Enabled" 1

I think this may require a programming library - x11 - which you might or might not have yet; if not, it's pretty widely-used, and should be available at the Ubuntu Software Center..

---

