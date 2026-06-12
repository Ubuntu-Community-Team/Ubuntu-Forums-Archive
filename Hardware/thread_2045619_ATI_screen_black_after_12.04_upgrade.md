---
title: "ATI screen black after 12.04 upgrade"
date: 2012-08-21
forum: Hardware
---

### Post by RoadRunnr on 2012-08-21
Hi,

After upgrading to 12.04 the screen on my HP NX6325 remains black.
I can ssh in and X seems be running, but the back light of the LCD is turned of.

How can I get it back on?

Graphics is: 
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS482 [Radeon Xpress 200M]

---

### Post by QIII on 2012-08-21
Let me think about this for a bit.  You'll probably have to use a nomodeset option, but I can't remember if plain "nomodeset" works with ATI GPUs or if it's a slightly different value.

But just in case someone suggests installing the ATI driver -- DON'T.  It will not work with that GPU.  ATI's driver no longer supports that card.

---

### Post by RoadRunnr on 2012-08-21
Tried nomodeset and acpi=off already, no change

fglrx is not installed.

Booting with 3.0.0-25 does not help either.

---

### Post by QIII on 2012-08-21
I have some stuff to do, so I have to put my shoulder back to the wheel.

I did a quick google on

```
site:ubuntuforums.org backlight ATI
```and got quite a few hits.  A lot of unresolved posts, but keep digging.

---

### Post by RoadRunnr on 2012-08-22
This is getting bizarre...

When I hit the lid switch a couple of time the screen will come on. Sometime it flickers on for only a second, but after some tries it will stay on. Sometime with reduced brightness first, but moving the mouse or hitting some keys fixes that as well.

This never happens with Windows, so I'm sure that is not a hardware fault with the lid switch.

Even when the screen is off, /proc/acpi/button/lid/C267/state reports the lid as open

---

### Post by typhoon_tip on 2012-08-22
EDIT: forget FGLRX, I think that card is off limit now... not supported.

---

### Post by QIII on 2012-08-22
> **RoadRunnr said:**
> Even when the screen is off, /proc/acpi/button/lid/C267/state reports the lid as open

In that case it doesn't sound like an "ATI" issue at all.

You might get a better answer now by marking this thread solved (so people don't skip it thinking it is an ATI problem) and starting a new thread referencing the acpi/switch issue.

I hope the staff will not take unkindly to that suggestion.

---

