---
title: "programmable mouse options?"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by upchucky on 2007-04-22
I have a microsoft USB trackball explorer five button programmable mouse.
Edgy detected the mouse just fine but the mouse application that Edgy uses to control it does not recognize the extra buttons. Is there a package that will let me set up the extra buttons?

---

### Post by greybirds on 2007-05-30
First you have to make certain that the X window manager knows about the extra buttons. Then, depending on what you want to do, there's xmodmap and imwheel. 

If you haven't already, search the forums for setting up your mouse with evdev. It's a driver for usb devices like mice with a lot more functionality than older drivers. There may be a how-to specific to your trackball if it's a popular model (I don't have the model number so I can't point you to one directly). 

xmodmap lets you do things like switch mouse and keyboard keys around. 

There's also this program, which I came across but haven't tried myself. You might find it useful. 

[http://ubuntuforums.org/showthread.php?t=277388]("http://ubuntuforums.org/showthread.php?t=277388")

Hope that helps.

---

