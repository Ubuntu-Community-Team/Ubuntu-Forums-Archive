---
title: "Logitech K270 Multimedia Hotkey Support?"
date: 2012-08-21
forum: Hardware
---

### Post by Gaygerbil on 2012-08-21
Hey I got a great wireless keyboard called the Logitech K270, even got it to work on the same USB reciever with my wireless mouse which I love.

I figured I could try to figure out how to get real hotkeys to work on Linux now. They usually work on netbooks and laptops I've installed Linux on, but it would be automatically detected and set up for me. 

This keyboard has some multimedia keys at the top that I would love to get working for me, I was wondering if anyone had any ideas about a solution to getting these keys to work. 

I use Lubuntu, but even if it doesn't use Openbox/LXDE I'm still willing to hear ideas about this. Would also be useful for a lot of people coming to Linux who are interested in this, because I know this is a problem for many people. 

Right now all I've really tried was getting a bash script to read my key hits and display it back to me, through a variable, but it would just give me blanks when I hit the hotkeys.

---

### Post by Gaygerbil on 2012-08-23
I figured it out very easily from here:

[http://www.howtoforge.com/linux_multimedia_keyboard](http://www.howtoforge.com/linux_multimedia_keyboard)

1. Simply put, install xbindkeys:

```
sudo apt-get install xbindkeys
```

--------------------------------------------------------------------------

2. Run this command here to create a config directory:

```
xbindkeys --defaults > $HOME/.xbindkeysrc
```

-------------------------------------------------------------------------
3. Use this command to figure out your hotkey by pressing it afterwards:

```
xbindkeys -mk
```

If you're like me and use openbox you'll simply just copy/paste that to the keybiding in your openbox config. Usually most hotkeys are something like "XF86LowerVolume" or "XF86Calculator"...things of that nature.

It takes a little tweaking but it works like a charm in Linux. :]

---

