---
title: "Wacom Bamboo is not recognized on Gusty 64-Bit"
date: 2007-12-26
forum: Hardware &amp; Laptops
---

### Post by XP-FREAK on 2007-12-26
Good evening,

I'm new here and I registered because I've some trouble with my ubuntu.

So first i please you to excuse my bad English :) 

This Christmas, Santa Clause brought to me a new wacom bamboo (graphic tablet). It runs very well under Windows, but unfortunately it makes problems under ubuntu. 

I googled a long time and found out, that gusty already brings along the wacom kernel modules. They seem to work, anyway /var/log/messages says they do:

```
tail -f /var/log/messages |grep -i wacom
Dec 26 20:35:57 notebook kernel: [  265.326412] usbcore: deregistering interface driver wacom
Dec 26 20:36:08 notebook kernel: [  267.594381] usbcore: registered new interface driver wacom
Dec 26 20:36:08 notebook kernel: [  267.594598] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/tablet/wacom_sys.c: v1.46:USB Wacom Graphire and Wacom Intuos tablet driver

```

The only problem I have is that there is no wacom in /dev/input.
So it makes no sense to edit the xorg config :(

Do you have any idea to solve the problem?

As I've allready said in the title, i'm working with Ubuntu Gusty 64-Bit and the 2.6.22-14-generic kernel on my notebook.

I hope that somebody can help me.

Thanks in advance,
XP-FREAK

EDIT:

Okay, I found some more information that could be interesting:

In /dev/input are these devices:
 event0  event1  event2  event3  event4  event5  event6 
and they could have something to do with the wacom tablet, anyway the wacdump tool opens them.
But wacdump does not return any data ?!

I tried to open the devices with xdd, nothing hapens apart from event1 returning data when pushing keys on the keyboard. Really strange.

Is it possible that the wacom kernel modules delivered with the ubutnu kernel are a bit old and that they don't support the wacom bamboo?
If yes, somebody (maybe I myself can do that) should fix that.

---

### Post by XP-FREAK on 2007-12-26
OK, excuse me annoying you, I figured it out with the help of this thread: [http://ubuntuforums.org/showthread.php?t=631881](http://ubuntuforums.org/showthread.php?t=631881)

Thanks to the community! Now somebody can delete this thread,  it's only just spam :)

---

