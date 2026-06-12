---
title: "How to change screen resolution on an unsupported monitor in Ubuntu 11.04?"
date: 2011-08-15
forum: Hardware
---

### Post by Grclaeys on 2011-08-15
I recently connected my Ubuntu computer to my Coby Brand HD TV via  vga cable. Ubuntu did not correctly set the display resolution  and part of the screen is cut off. I also can not change the resolution  settings because of the unsupported. Monitor. Also, I have no idea what  video card I am using. I think the resolution is at 1024x768 right now. I  know the resolution 640x480 works because it is at that resolution on  the startup screen. How do I change the resolution to 640x480 or  something else that works? Also please don't say to go to system  preferences then, monitor. Thank you for your help!

---

### Post by dabl on 2011-08-15
> **Grclaeys said:**
> 
I have no idea what  video card I am using. 

That's a problem, and you won't get help until it is answered.  Open a terminal and issue

```
lspci -v
```

and paste only the stanza that begins with something like this:

```
05:00.0 VGA compatible controller: ............
```

in your reply.

---

### Post by Grclaeys on 2011-08-15
Thanks I think I have an intel video card.

---

