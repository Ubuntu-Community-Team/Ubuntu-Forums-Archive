---
title: "USB mouse freezes"
date: 2004-10-30
forum: Hardware &amp; Laptops
---

### Post by hyde on 2004-10-30
My Logitech USB mouse freezes after undefined time. I had same issue with FC2 few months ago. Might be kernel related, because I never had mouse problems with 2.4 kernels.

So, what is causing it? Mouse works at beginnig, then suddenly freezes. Unplugging USB wire and connecting it back mouse comes alive again, but then freezes again.

I have laptop with touchpad. Having problems with touchpad in Firefox also, moving finger on pad causes "back" button action in Firefox.

---

### Post by brehloi on 2005-03-25
I am having the same problem as described by the topicstarter.

Having a USB mouse from Logitech connected to my laptop with touchpad.

Every now and then I the mouse freezes. Unplugging en replugging temporarily solves the problem.

And... also having the problem in Firefox as described...

Can anyone help?

---

### Post by brehloi on 2005-03-26
I found a partial solution to the problem on a forum:

The trick is to unload en reload the usbhid module as the following commands illustrate:

sudo modprobe -r usbhid ; sudo modprobe usbhid

[http://ubuntuforums.org/archive/index.php/t-8001.html](http://ubuntuforums.org/archive/index.php/t-8001.html)

it isn't a perfect solution, but to make it more usefull I would like to run this with a keyboard shortcut or a menu option. Something which is easily accessible. 

How to do this?

---

### Post by tajmox on 2007-07-12
> **brehloi said:**
> I found a partial solution to the problem on a forum:

The trick is to unload en reload the usbhid module as the following commands illustrate:

sudo modprobe -r usbhid ; sudo modprobe usbhid

[http://ubuntuforums.org/archive/index.php/t-8001.html](http://ubuntuforums.org/archive/index.php/t-8001.html)

it isn't a perfect solution, but to make it more usefull I would like to run this with a keyboard shortcut or a menu option. Something which is easily accessible. 

How to do this?

You will need to make a script file.   Use a text editor and make a file called fixmouse.sh put this in there:
```
#!/bin/sh
sudo modprobe -r usbhid ; sudo modprobe usbhid
```
then make the file executable (by right clicking and choose properties and permissions)

Go to the keyboard shortcuts editor and make a shortcut that points to the script.  (for example /home/user/fixmouse.sh)

---

