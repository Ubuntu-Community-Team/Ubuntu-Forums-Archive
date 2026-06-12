---
title: "Ubuntu Randomly Locking on Both Laptops"
date: 2010-09-14
forum: Hardware
---

### Post by neu5eeCh on 2010-09-14
I'm not asking for help. Just doing some preliminary sleuthing.

I find it curious that both my laptops (one 32bit and one 64bit) are displaying exactly the same symptoms. They will both randomly (or so it seems) lock up. They will accept no input from the keyboard or mouse. If I give Ubuntu enough time, the OS will eventually recover (anywhere from 25 seconds to a minute or more).

This only started in the last week or so, which makes me think this has something to do with the last update?

Question: Is anyone else noticing these symptoms?

---

### Post by NightwishFan on 2010-09-14
This used to happen to me only with Compiz enabled on Nvidia. What is your GPU hardware?

---

### Post by Brunellus on 2010-09-14
> **VTPoet said:**
> I'm not asking for help. Just doing some preliminary sleuthing.

I find it curious that both my laptops (one 32bit and one 64bit) are displaying exactly the same symptoms. They will both randomly (or so it seems) lock up. They will accept no input from the keyboard or mouse. If I give Ubuntu enough time, the OS will eventually recover (anywhere from 25 seconds to a minute or more).

This only started in the last week or so, which makes me think this has something to do with the last update?

Question: Is anyone else noticing these symptoms?
This is really a support thread.  I am moving it to an appropriate sub-forum.

---

### Post by neu5eeCh on 2010-09-14
> **NightwishFan said:**
> This used to happen to me only with Compiz enabled on Nvidia. What is your GPU hardware?

The 32bit unit is an   Intel Extreme Graphics 2, the other is an ATI Mobility Radeon HD 3650 (without the proprietary 3D accelerator installed). I'm doubting this has anything to do with the GPU.

---

### Post by NightwishFan on 2010-09-14
Ok then, ensure you check the system log after such an occurrence. As a precaution try booting with the command: nomodeset

If the "nomodeset" fixes the freezes, than the problem IS gpu related.

---

### Post by neu5eeCh on 2010-09-17
> **NightwishFan said:**
> Ok then, ensure you check the system log after such an occurrence. As a precaution try booting with the command: nomodeset

If the "nomodeset" fixes the freezes, than the problem IS gpu related.


Turns out it's not Ubuntu, but Firefox. I may force a downgrade of Firefox on both laptops.

---

