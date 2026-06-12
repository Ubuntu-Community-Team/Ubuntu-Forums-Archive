---
title: "Mouse or/and Keyboard not working"
date: 2011-03-09
forum: Hardware
---

### Post by sakishrist on 2011-03-09
Hello there,

I am seeking your help about a very strange problem of mine that has to do with that litle button above my touchpad that turns it off. I pressed that button a while ago and (as expected) the touchpad stopped working, but the thing is that the keyboard stoped working too. I pressed it again and the mouse came back to normal but the keyboard was dead. 

By the way, I also noticed that when I tried to click anything on the upper task bar it had no effect. It would only sometimes highlight the menu I was trying to access but it would not open that menu. So that means that I had no access to the Shut Down menu.
 
Then I tried to do a restart by pressing the power key so that I could get to that menu. That key did not work either.
Then I pressed ctrl + alt + del and that brought the Shut Down menu. (!!!)

After the restart I saw my mouse moving while I was still at the login screen but as soon as I loged in the mouse stoped again. The keyboard worked fine though.
After a while a tried for a second time that litle button and again ... I ended up with a keyboard that only responded to ctrl + alt + del and the mouse was still not working.

I had to restart again and here I am now: keeping my hands away from the button and operating my PC with only the keyboard.

I really hope you can help me. :)

Thanks in advance.

PS: Why is the Prefix (for the thread) soooo many tabs away? :p

---

### Post by sakishrist on 2011-03-09
I tried the mouse of a friend of mine and it worked fine. So I do not really know why a single button would cause so much trouble.

---

### Post by sakishrist on 2011-03-10
I have also tried to see if I could find other drivers for my touchpad but I ... kind of don't know where to look for them. I tried the synaptic but nothing. I also tried to update and upgrade and again nothing.

Do I have to reinstall the whole system for this to work? :s

Please help

Thanks a lot.

---

### Post by sakishrist on 2011-03-10
After some more searching I found a partial solution:

This command has to be run:```
gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true
```It worked for me but the problem appears every time I press the button to turn off the touchpad.

The solution was found [here]("https://help.ubuntu.com/community/SynapticsTouchpad").

---

