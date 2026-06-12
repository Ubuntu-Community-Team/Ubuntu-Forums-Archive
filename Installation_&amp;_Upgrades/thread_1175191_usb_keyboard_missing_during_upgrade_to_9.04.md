---
title: "usb keyboard missing during upgrade to 9.04"
date: 2009-05-31
forum: Installation &amp; Upgrades
---

### Post by Cowloon on 2009-05-31
I have a KVM switch... I switched computers and switched back, and now my keyboard is not being recognized by X. The installer is prompting me to replace a config file.

Can I possibly kill the installer and restart it on the X server on my other computer? Or, will the installer fail if it starts up again in that state?

I notice that syslog shows my keyboard connecting and reconnecting, if I unplug it and plug it in again, but it doesn't register in X.

Or, can you think of a way for me to convince the X server that I have a keyboard, or to fake clicking the button in teh dialog that is displaying?

I tried writing a thing that uses Xtest X11 extension to press a key in the current window, but it appears to not work now. It complains that the generic event extension is not installed.

I can still do work on other computers while this is stuck this way, so I will wait before accepting the result of a failed install.... which will really suck.

---

### Post by Cowloon on 2009-06-01
I think this was not because of the KVM switch. While doing more of the unplugging and replugging the keyboard, I typed Ctl-F2 and Ctrl-Alt-Bksp which killed the installer... So, the keyboard was working. Restarting gdm I am able to type in my username and password then it hangs. If I use startx the keyboard and mouse do not work again.

So, I think at some point during the upgrade, my keyboard and mouse stop working with X.

I'm going to either get another harddrive and try to do a clean install and move my files onto it, or restore from my backup from a few days ago.

---

