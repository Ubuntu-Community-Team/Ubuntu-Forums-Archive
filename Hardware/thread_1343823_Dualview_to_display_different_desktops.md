---
title: "Dualview to display different desktops?"
date: 2009-12-02
forum: Hardware
---

### Post by keystar on 2009-12-02
Hi community,

I've just bought an external screen to my laptop and connected it. It works quite well and now both screens - the built-in as well as the external - show the same picture. Now I'd like to use both screens to display different desktops.(e.g on one desktop Skype and Thunderbird should be open, while on the other one I can browse with Firefox.) To realize that, I've tried to adjust the setting at Preferences -> Display The dialog showed so far only one screen named "Mirrored Screens" After unchecking the checkbox "Mirror screens" the dialog showed two screens as expected (19" and laptop).

So far, so good. But after clicking "Apply" both screens immediately got black. I couldn't do anything further than switching off the laptop manually. Trying the screen key of my laptop (Fn+F4) didn't help me, nor did one of the combinations Ctrl+F5, Ctrl+Backspace, etc.

I've read somewhere that settings in /etc/X11/xorg.conf could be the solution, but this file doesn't exist anymore in Ubuntu 9.10.

Another try was to adapt the file /<HOME>/.config/monitors.xml manually. there are two <configurations>, one including one screen (only the laptop) and one including two screens (external and laptop). I've set "<clone>no</clone>" in the latter configuration and at the external screen "<primary>yes</primary>". (previously both screens had <primary>no</primary>) 
Well, I would have imagined that these change can solve the problem.  However, there was unfortunately no effect at all.  

Is it possible, that my onBoard Intel chip does only support Dualview with mirrored screens?

Does the problem sound familiar to anyone?
I would appreciate any idea or suggestion where to continue searching...
Unfortunately I don't have different OS to try it in another environment. 

--------------------------------------------------------------------
Running: Ubuntu 9.10 Gnome 2.28.1 Processor: Intel Pentium M 1,73 GHz Graphics: Intel-Chip GMA915

---

