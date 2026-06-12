---
title: "Webcam not working with Skype"
date: 2011-04-17
forum: Hardware
---

### Post by pawan98 on 2011-04-17
Hi I recently installed ubuntu on my computer and I have a webcam called Logitech QuickCam Communicate STX, when I open Cheese (the photo program) and then I went on Skype and the webcam did not work. Please help. Thanks. ;)

---

### Post by earthpigg on 2011-04-22
The solution that worked for me, [from here]("http://blogs.skype.com/garage/2011/04/skype_22_beta_for_linux_with_s.html"), was to start skype like this:

> - Ubuntu 32 bit: install ""libv4l-0"" package and launch Skype with: ```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
``` 

I also changed the menu entry so that instead of 'skype', it had the above command.

(I'm copy/pasting this onto the multiple threads with the exact same situation starting in early/mid April, using Logitech webcams. It isn't spam, mods, it's a legit solution :P )

---

### Post by mukko on 2011-05-28
> **earthpigg said:**
> The solution that worked for me, [from here]("http://blogs.skype.com/garage/2011/04/skype_22_beta_for_linux_with_s.html"), was to start skype like this:



I also changed the menu entry so that instead of 'skype', it had the above command.

(I'm copy/pasting this onto the multiple threads with the exact same situation starting in early/mid April, using Logitech webcams. It isn't spam, mods, it's a legit solution :P )

earthpigg

Thanks.  Same problem with logitech 2500 webcam, Skype, Ubuntu 10.10.  Nearly there.  When I start Skype from the terminal with your command the camera works.

When I copy this command to the command box in the System>Preferences>Main Menu>Internet>Skype>Properties dialog and try to start Skype from the main menu icon I get the error message:

Could not launch 'Skype'

Failed to execute child process LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so" (No such file or directory)

Checked the directory "/usr/lib/libv4l/" and the file "v4l2convert.so" is there (of course it is, it worked from the terminal).  Total newbie.  Assume I'm incorrectly inputting command into properties command box.  Checked help for the properties dialog.  No luck.  What simple thing am I missing?  Do I need to input the full path to the Skype program file?

---

