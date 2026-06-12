---
title: "Get mouse buttons working in Hardy"
date: 2008-04-26
forum: Hardware
---

### Post by steveneddy on 2008-04-26
I was having trouble getting forward and back in Firefox and Nautilus working in Hardy, when it worked fine in Gutsy.

I edited the xorg.conf until I was blue in the face, to no avail.

So, I downloaded and installed **btnx**. 

I followed the instructions from an old Ubuntu forums [here]("http://ubuntuforums.org/showthread.php?t=455656").

I have a Logitech V470 Bluetooth mouse that only has seven buttons:

* Left click
* Right click
* Middle click (scroll wheel press down)
* Scroll wheel up
* Scroll wheel down
* **Scroll wheel left**
* **Scroll wheel right**

With btnx I made the scroll wheel left and right emulate keyboard ALT+left arrow and ALT+right arrow so I could scroll forward and back in Firefox and Nautilus.

Hope this helps someone.

---

### Post by steveneddy on 2008-04-27
I am now having trouble with btnx running at 100% cpu after about an hour of idle time, only to have to restart the program to fix the problem.

Anyone else having this issue?

I use a Logitech V470 Bluetooth mouse.

---

### Post by luke16 on 2008-04-27
Btnx worked for me, but I haven't run it for long, so I don't know if it will go 100% cpu on me like yours did. What version of btnx are you running?

Also, vote for this: [http://brainstorm.ubuntu.com/idea/6186/](http://brainstorm.ubuntu.com/idea/6186/)

---

### Post by steveneddy on 2008-04-28
btnx was not the answer due to the 100% CPU issues.

I am pursuing the evdev xorg module. It worked in Gutsy and I can't figure out why it won't work in Hardy.

If you enable the evdev module in xorg.conf instead of the mouse module, it crashes x.

Why?

The quest continues.

---

### Post by steveneddy on 2008-04-28
Today I received an e-mail from Olli Salonen, the developer of btnx, about a bug I filed about this very issue.

He told that the new version of btnx should fix the issue.

Here is the e-mail in it's entirety:

> 
btnx-0.4.10 fixes the issue. However, use btnx-config-0.4.9 and run it
at least once (run and close if you have no need to edit the
configuration). This will regenerate the udev rule which is compatible
with the changes.

** Changed in: btnx
       Status: Confirmed => Fix Released

-- 
cpu at 100% after mouse goes to sleep
[https://bugs.launchpad.net/bugs/223397](https://bugs.launchpad.net/bugs/223397)


So for the time being, it looks like I'm running btnx again.

Thanks, Olli  -  :D

---

