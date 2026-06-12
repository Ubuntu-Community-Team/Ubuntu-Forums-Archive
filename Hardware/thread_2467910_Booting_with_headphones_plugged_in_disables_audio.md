---
title: "Booting with headphones plugged in disables audio"
date: 2021-10-12
forum: Hardware
---

### Post by dwater on 2021-10-12
> LSB Version:	core-11.1.0ubuntu2-noarch:printing-11.1.0ubuntu2-noarch:security-11.1.0ubuntu2-noarch> XPS-13-9360

If I boot my laptop with headphones plugged in, there is no audio - not even if I unplug them and plug them in again. To fix it, I have to reboot without the headphones plugged in.

Any ideas?

---

### Post by axelmasok on 2021-10-13
I don't really follow.

I'm thinking if you boot with headphones plugged in the headphones output audio and not the speakers. You unplug headphones and still hear nothing from the speakers?
Install something like pavucontrol  and compare the scenarios.  There is probably some changes wrt to default audio device.

Or your headphones are bad, or your Dell doesn't like them.

---

### Post by dwater on 2021-10-13
> **axelmasok said:**
> I don't really follow.

I'm thinking if you boot with headphones plugged in the headphones output audio and not the speakers. You unplug headphones and still hear nothing from the speakers?
Install something like pavucontrol  and compare the scenarios.  There is probably some changes wrt to default audio device.

Or your headphones are bad, or your Dell doesn't like them.

Just to be clearer:

If I boot with headphones plugged in, audio does not work - not speakers (after unplugging the headphones) nor headphones.
If I boot without headphones plugged in, audio works with headphones (after I plug them in) and speakers (if I don't have headphones plugged in).

So, it seems to me that it's not my headphones, and it's not that my computer doesn't like my headphones. It's more like something that is set during boot that either makes the sound card(?) fail, or sets some setting that means it no longer works.

FWIW, this has been happening for years, over several different Ubuntu versions.

I'll see what I can find from the pavucontrol thing you mentioned, and report back.

---

### Post by dwater on 2021-10-16
I started to try to systematically debug, by running that pavucontrol utility, but after I had done that, I could no longer reproduce the problem.

Unfortunately, I didn't reproduce it immediately prior to running it, so I don't know if that fixed it - perhaps by generating a config file or something - or not.

Anyway, I'm good now - so all's well and all that - thanks! :D

---

### Post by axelmasok on 2021-10-17
Happy days!

---

