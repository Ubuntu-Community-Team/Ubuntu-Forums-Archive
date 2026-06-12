---
title: "switching alt-win keys when using external keyboard?"
date: 2012-05-26
forum: Hardware
---

### Post by robertbub on 2012-05-26
I'd like to switch my alt (option) and super (windows/apple) keys whenever I use an external keyboard on my Apple Macbook Pro laptop and have it switch back when I unplug it.

In particular, I'd like Alt+Tab to do the right thing when using an external keyboard and have it be Super+Tab when using the laptop apple layout.

I know that Keyboard Preferences->Layout->Options... allows you to swap Alt and Meta keys.  And that works great.  But I don't want to do that every time I connect my external USB keyboard to my laptop.

Having a command line utility would be a sufficient workaround.  I tried playing with xmodmap, but, for some reason, even if I remap Alt_L and Super_L (I checked using xev), Alt+Tab does not change its behavior -- i.e., Keyboard Preferences seems to take precedence.

Is there a way to fix this?  Or am I stuck with manually modifying the keyboard preferences each time I use a full-sized PC keyboard?

---

