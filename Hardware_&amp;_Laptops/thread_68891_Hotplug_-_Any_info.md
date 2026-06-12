---
title: "Hotplug - Any info?"
date: 2005-09-24
forum: Hardware &amp; Laptops
---

### Post by muzzie on 2005-09-24
Ok, I am fairly new to Linux, but one problem has been plaguing me since day one.  I have posted about it before, but never pursued the issue.

What happens is this... sometimes (not always!) when toggling to my other computer with my KvM, when I come back to the Kubuntu machine, the keyboard no longer responds.  I haven't had any trouble with the mouse.

The KvM is a simple USB 2 port iogear MiniView.  Plug my USB keyboard and mouse into the KvM, and a single USB cable runs to the PC, therefore the keyboard and mouse are over a single USB cable.  

Even if I try to manually take the USB keyboard and unplug it from the KvM, then plug it into a USB port on the PC, nothing happens.  Once it loses the keyboard, I can't find a way to get it back short of a restart.

I'm basically trying to get any info on how hotplugging works under Hoary, as I suspect that's where the problem lies.  It's almost as if the system doesn't "see" that my keyboard was ever disconnected, or perhaps it's just not "reconnecting" it.

What initiates the hotplug system? Who supports/created it? Any manuals or documentation on it?  
ANY ideas or info, I'd really appreciate. I have to toggle my KvM fairly frequently, and this issue has really been one of the main reasons I find myself avoiding Kubuntu.

---

### Post by mlomker on 2005-09-24
Hmm.  Does the KVM have a 'reset' option for the keyboard/mouse?  Most of mine at the office do, but they aren't USB.  You should take a look at the logs in /var/log (kernel, syslog, messages) and see if there are some errors being generated.  Even if you can't type on the box you should be able to SSH into it from the other machine (assuming they are networked).

---

### Post by cwaldbieser on 2005-09-24
[QUOTE=muzzie]
What initiates the hotplug system? Who supports/created it? Any manuals or documentation on it?  
ANY ideas or info, I'd really appreciate. I have to toggle my KvM fairly frequently, and this issue has really been one of the main reasons I find myself avoiding Kubuntu.[/QUOTE]
Here is the project home page for the hotplug system.  Some useful info in there:
[http://linux-hotplug.sourceforge.net/](http://linux-hotplug.sourceforge.net/)

---

### Post by muzzie on 2005-10-01
Been busy for the last few days, so just finnaly got to checkup on this thread.

Thanks for the replies.  I'll try your suggestion mlomker, and checkout that website, cwaldbieser.  I'll keep you guys updated with how it goes.

Oh, also, no I don't believe my KvM has any sort of reset switch.

---

