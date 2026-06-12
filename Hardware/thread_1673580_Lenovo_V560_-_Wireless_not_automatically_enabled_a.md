---
title: "Lenovo V560 - Wireless not automatically enabled at startup"
date: 2011-01-22
forum: Hardware
---

### Post by funnysnoot on 2011-01-22
I just installed 10.10 32-bit on my Lenovo V560. Everything works great except for the wireless, which I have to enable each time the computer starts up.

I have my Wireless network set to connect automatically, but it still does not. How can I fix this?

Thanks.

---

### Post by Yellobes on 2011-08-16
You could try iwevent & other monitors when you turn on your card, that might give you an idea what needs to happen, then you can put a scripts in your startup scripts [System -> Prefs -> Startup Scripts] to do that thing every time you start up your computer.

I got here because I'm working on a Dell Latitude D531, with an AR928X. It's a crapshoot on boot, will the wireless card be on or not? I think I need to put a script in my startup scripts that modprobes it, but I don't know how to turn the bugger on in the first place. Any help would be appreciated. FYI, when it's not on, I do not know how to enable it without restarting the computer and doing my voodoo with the wireless button.

---

