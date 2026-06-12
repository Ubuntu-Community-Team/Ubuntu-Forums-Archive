---
title: "Its ok, i'm a limo driver!"
date: 2009-01-29
forum: Hardware
---

### Post by Axeonfluke on 2009-01-29
Ok, I'm new to both linux and ubuntu as of yesterday and I'm working out the kinks, trying to learn as I go and everything is going fairly well so far.  I've hit a couple of snags but persevered.  

The only thing that google doesn't seem to be able to help me with is getting my external hard drive working.  Now I know ubuntu is, for the most part, a plug and play OS.  I'm on a laptop and my mouse and secondary monitor worked like a charm.  But I'll be darned if I just can't figure out this external. 

Cannot Mount Volume.  I've looked at past posts on the same issue but none of those solutions seem to be helping me.  I'm unfamiliar with the Terminal and how to use it properly...I just don't know what to do. 

Can anybody slap some sense into me?

---

### Post by Axeonfluke on 2009-01-29
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

....Before you ask...I've tried every USB port already, and this external runs off USB only so, no AC plug.

---

### Post by vavoem on 2009-01-29
if you type lsusb in a command prompt you can check if your device is seen by the os
What kind of filesystem is on the device?

---

### Post by Axeonfluke on 2009-01-29
> **vavoem said:**
> if you type lsusb in a command prompt you can check if your device is seen by the os
What kind of filesystem is on the device?

After beating my head against a wall all morning I found a brilliant piece of information.  Simply by plugging back into a windows OS and selecting the "safely remove hardware" option and then unplugging...the external was magically fixed.  

You would think something like this would be prevalent information but, I seriously had to do some digging to reveal this simple solution.  The hardest part was finding a windows OS because I already removed mine. lol.

---

