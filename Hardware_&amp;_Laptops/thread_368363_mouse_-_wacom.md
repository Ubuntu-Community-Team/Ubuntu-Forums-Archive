---
title: "mouse - wacom"
date: 2007-02-23
forum: Hardware &amp; Laptops
---

### Post by Bartje on 2007-02-23
hey all,

new problem here, and yes, again xorg.conf and mouse trouble.... for background information: [http://ubuntuforums.org/showthread.php?t=303555]("http://ubuntuforums.org/showthread.php?t=303555")

Well, as explained in that thread and others (follow the other links in the thread), to avoid problems, or conflicts between my mouse and wacom, I should specify my mouse to /dev/input/mouse0 or /dev/input/mouse1, instead of /dev/input/mice.

Well, here is my problem now. When I specify it, my system detects the mouse on a different device randomly. That means that when in xorg.conf, my mouse is described as /dev/input/mouse0, my computer might have decided to assign /dev/input/mouse1 as the real device, with the result....: oops mouse not working.

I still can't configure my wacom in Gimp or Inkscape (check link to thread), and my mouse dissapears sometimes, and sometimes not, after reboot when specifying the mouse in xorg.conf.

Now, what the hell is going on? I've set my xorg.conf file back on using 'mice' instead of mouse0 or mouse1, otherwise I'd be without one, half the time. 

Next conclusion, the conflict between my mouse and wacom is not in the xorg.conf file, but where else could the cause for the problem be?

---

