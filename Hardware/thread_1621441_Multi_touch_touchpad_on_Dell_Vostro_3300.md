---
title: "Multi touch touchpad on Dell Vostro 3300"
date: 2010-11-14
forum: Hardware
---

### Post by Sidrabs on 2010-11-14
Hello,

I have this Dell Vostro 3300 Laptop, and it features multi-touch touchpad. At least it says so in the specs. I never experienced that, because it came with no OEM Win, and I put 64bit Ubuntu 10.10 on it right away.

It's hard to understand what is the situation right now. I keep reading about how Ubuntu will support multi-touch trackpad guestures (for example here: [http://thewindows7site.com/forum/threads/18804-Ubuntu-10.10-Will-Support-Gestures-with-Multi-touch](http://thewindows7site.com/forum/threads/18804-Ubuntu-10.10-Will-Support-Gestures-with-Multi-touch)), but I couldn't find anything like that on my laptop. Nor I could find any drivers that would enable this.

Can someone please clear up, what's the current situation regarding this?

---

### Post by mpnordland on 2010-11-14
I have multi touch track pad, and yes there is multitouch support, but it's more for touch screens. Google for it, and also search the forums, as there are ways to make it work. I had it working for a while, but I just didn't use it much.

---

### Post by xircon on 2010-11-14
This gets two finger scrolling working on my Dell:

```
#!/bin/bash
synclient VertTwoFingerScroll=1
synclient HorizTwoFingerScroll=1
synclient EmulateTwoFingerMinW=5
synclient EmulateTwoFingerMinZ=48

```

I had to put it in a script, because it does not persist over reboots.

---

### Post by Sidrabs on 2010-11-14
> **xircon said:**
> This gets two finger scrolling working on my Dell..

Yes, I noticed this kind of fixes all around the net, but I am looking for something more convenient than hacking my way through proprietary drivers and console commands to support one or two boring gestures. Rather, I am looking for some kind of control panel, where the gestures are defined and bound to certain actions, like PgUp and PgDn. I'd assume that OS that claims to support multi-touch touchpads has exactly something like that.

---

