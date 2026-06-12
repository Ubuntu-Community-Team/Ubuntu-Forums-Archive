---
title: "Touchpad buttons don't work in some parts of X"
date: 2012-11-19
forum: Hardware
---

### Post by suvoisduroc on 2012-11-19
Dear members,

I just installed Ubuntu 12.10 on the Acer Aspire 3682wxmi laptop and running into a strange problem:

After login into X the touchpad buttons (except the trackpad!, so i can still move the cursor) stop working in all window applications BUT still do work in some graphical parts of the Ubuntu system like the left panel at the desktop.

I suppose, however hardware related, this actually cannot be a hardware problem, because in that case touchpad wouldn't function at all, right? I tried all possible mouse/touchpad settings (using my keyboard) in the system-configuration, but nothing did work. Any other idea's ? Could it be perhaps a mis-communication between touchpad and Gnome?

By the way, I found a lot of other posts on the internet about problems with the touchpad of many Acer Aspire laptops, but all of them described a total failure of all/some functions of touchpad in any part of X and not (like in my situation) in some parts of X.

Hope you can help me out.

Thanks,

SuvoisDuroc

----------------------------------------

Update:

Rather strange! Sometimes (incidentally) it works again. For example, then i can use the resize/minimize/maximize buttons at the top of the window.

---

### Post by suvoisduroc on 2012-11-21
Ok, 

Problem solved by doing:

```

 sudo modprobe -r psmouse
 sudo modprobe psmouse

```

So, it's a driver problem. Seems to crash partly somewhere after login.

Still have to find a way how i can let Ubuntu perform this code automaticly after login.

---

### Post by suvoisduroc on 2012-11-21
According [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1058346](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1058346) should this solve the problem permanently, but it didn't work for me.

-     Open the Terminal
-     cd /etc/modprobe.d/
-     gksudo gedit options.conf
-     In the text editor, type: options psmouse proto=imps
-     Save the file and close it.
-     sudo modprobe -r psmouse
-     sudo modprobe psmouse

Maybe adding

```

sudo modprobe -r psmouse
sudo modprobe psmouse

```to /etc/r.local will work.
I'll let you know.

Please let me know if you know there are better solutions.

---

### Post by varunendra on 2012-11-22
> **suvoisduroc said:**
> Maybe adding
```

sudo modprobe -r psmouse
sudo modprobe psmouse

```to /etc/r.local will work.
Definitely not a better solution, but if you think it crashes sometimes 'After' login, and removing/loading psmouse just once fixes your problem, then maybe this line in rc.local would be a bit more promising -
```
(sleep 6; modprobe -r psmouse; sleep 2; modprobe psmouse)
```
Depending upon your average login time, you may increase/decrease 'sleep' time. Make sure the line is inserted **Before** "exit 0" line, as stated in the comments in that file.

And you don't need 'sudo' in rc.local file, it already runs as 'root'.

---

