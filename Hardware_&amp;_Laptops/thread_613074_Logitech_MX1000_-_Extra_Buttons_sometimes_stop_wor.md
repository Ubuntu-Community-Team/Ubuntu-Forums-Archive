---
title: "Logitech MX1000 - Extra Buttons sometimes stop working after reboot"
date: 2007-11-14
forum: Hardware &amp; Laptops
---

### Post by yoddo on 2007-11-14
Hi,
I have an MX1000, and want to use its extra buttons.
So I read a lot of threads, tried many configurations, and got them working finally.
At least "xev" gives me an output for every Button. That is all I need, because I use the Extra Buttons in connection with compiz-fusion, which only needs the Button-Numbers.
So I don't use/need imwheel or similar programs. 

That sounds as if everything would be working. So why this thread?
Because the Buttons stop working randomly(?) after rebooting. If that is the case xev does not give any reply when I push an extra mouse button.
The main buttons (left/right, mousewheel (up/down/press)) are always working.
To "fix" that problem, I can reboot while switching the mouse on/off. In most cases the Buttons will work again. Once they work, they never stop working, as long as I don't reboot. Even restarting X has no effect.
This is the mouse-part of my xorg.conf:

```
Section "InputDevice"
    Identifier     "Logitech MX1000"
    Driver         "evdev"
    Option         "Phys" "usb-0000:00:1d.0-1/input0"
    Option         "Name" "Logitech USB RECEIVER"
    Option         "Buttons" "12"
EndSection

```
With this configuration all mouse-buttons are working, but with the issue described above.
Has anyone got an idea? :)
Thank you for replies!
greetings,
yoddo

---

### Post by yoddo on 2007-11-16
This is the output when I type "cat /proc/bus/input/devices": [Klick]("http://www.onlyfree.de/php/pasteservice/show.php?id=4316")
I have a wireless keyboard, AND  a wireless mouse. But the MX1000 does not belong to the keyboard, and uses another base station. Is it possible that the base station of the keyboard disturbs the mouse?
I already changed the Channel of the Mouse, but that did not solve the problem.

---

### Post by yoddo on 2008-01-15
A few days ago I noticed, that I get a different output typing ```
cat /proc/bus/input/devices
``` while the buttons work, as when they don't work.
[extra buttons work]("http://www.onlyfree.de/php/pasteservice/show.php?id=5618") | [extra buttons don't work]("http://www.onlyfree.de/php/pasteservice/show.php?id=5619").
First thing I noticed, is that the "kbd" is missing in the "handler" section if the buttons WORK.

*Can anyone approve, that this fact is in connection with my problem?*

Personally, I think that it IS connected with my problem... because _everytime_ the extra buttons work, the output looks exactly like the "extrabuttons work" output. Everytime they don't work it looks like the other one.
I don't think the problem is caused by the xorg.conf...
1) With Debian and Arch the Extra Buttons work... with the same xorg.conf
2) Restarting X does not have any effect on the extra buttons. If the buttons don't work, only a reboot (or 2,3,4) will help. If the buttons work again, also the output of ```
cat /proc/bus/input/devices
``` will have changed.

Hope someone can help me now... :)

---

### Post by yoddo on 2008-02-16
The problem disappeared with Hardy... \\:D/

---

### Post by ief on 2008-03-24
I have the same problem.
How did you fix it?

---

### Post by yoddo on 2008-03-28
Don't know exactly, but thats what I did:
I upgraded to Hardy and X did not start afterwards. The nvidia-glx-new package was broken.
So I installed the driver from the nvidia-homepage - and got X working again.
At this point the Mouse problem vanished, too.
I did not connect it with the nvidia-driver but with the upgrade to hardy and was happy.

But some serious problems forced me to reinstall Hardy (was alpha). And on the installed system I had the same problem all over again (with installed nvidia-glx-new).
Now I use Hardy and the driver from the nvidia-homepage - all buttons work always.

I can't explain why the nvidia-driver influences the mouse... I'm not even sure that it does...
But its the only thing I changed and it worked for me. You can try it if you use a Nvidia-Card.
If you don't I have no idea how you could fix it.

---

### Post by ief on 2008-03-29
I do have an nvidia graphic card ... I guess I'll just wait for the release of 8.04 at the end of April ...
Too bad ...

---

