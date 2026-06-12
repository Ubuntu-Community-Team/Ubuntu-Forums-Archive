---
title: "USB Logitech Headset"
date: 2007-12-22
forum: Hardware &amp; Laptops
---

### Post by tom_goring on 2007-12-22
Hi,

I installed Ubuntu 7.10 on my dell XPS 420 last week.
Everything was OK and my USB  Logitech headset worked fine.

However it has stopped recognising it in the last couple of days?

It does not show up in lsusb.

Any pointers ? Anyway to reset the usb detection config or anything ?

Thanks in advance.

Tom

---

### Post by iceman0407 on 2008-01-24
I am having the same exact problem. Anyone know anything?

---

### Post by LaRoza on 2008-01-24
Install and run asoundconf-gtk, and select the headset.

(If you already did this, I am not familiar with your problems)

---

### Post by aonegodman on 2008-02-05
> **LaRoza said:**
> Install and run asoundconf-gtk, and select the headset.

(If you already did this, I am not familiar with your problems)

Hey I just installed this and upon running I get the following message back in Terminal >

```

You need to make sure asoundconf is active!
By default, asoundconf's configuration file is ~/.asoundrc.asoundconf
and must be included in ~/.asoundrc. Open this file to make sure it is!

```

I checked the named file but don't see or understand how to include in .asoundrc file.

Anyone got a working .asoundrc file I can look at?    :confused:

---

