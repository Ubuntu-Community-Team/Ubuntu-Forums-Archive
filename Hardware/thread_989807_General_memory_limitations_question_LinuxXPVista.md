---
title: "General memory limitations question Linux/XP/Vista"
date: 2008-11-22
forum: Hardware
---

### Post by MidsummerDreams on 2008-11-22
I have it in my mind that either/or XP and/or Vista require memory to be ECC, if more than 4GB is installed. (from some youtube video I seen quite some time ago) Is this true? If so, what about Linux/Ubuntu? Is there any limitations for Linux as to what memory is required?

Thanks in advance, you guys are awesome!
:guitar:

---

### Post by prshah on 2008-11-22
> **MidsummerDreams said:**
> I have it in my mind that either/or XP and/or Vista require memory to be ECC, if more than 4GB is installed. (from some youtube video I seen quite some time ago) Is this true? If so, what about Linux/Ubuntu? Is there any limitations for Linux as to what memory is required?

I don't know about Vista, but XP definitely does _not_ _require_ ECC memory; I doubt it will be a _requirement_ in Vista either.

Besides which, enabling ECC mode on memory is usually board-supported; software support is only required if the motherboard does not have the necessary firmware (? programming?)

And using ECC comes with a (minor) performance hit, so it's not enabled on most system by default.

Memory limitations in Linux mostly relate to hardware limitations only.

---

