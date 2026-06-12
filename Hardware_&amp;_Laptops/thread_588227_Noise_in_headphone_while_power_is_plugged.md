---
title: "Noise in headphone while power is plugged"
date: 2007-10-23
forum: Hardware &amp; Laptops
---

### Post by vapore0n on 2007-10-23
I can hear this really annoying buzzing/electrical sound out of the laptop speakers and headphones. This problem only happens in Ubuntu not in Windows.
The noise starts up as soon as Ubuntu initializes the sound card. 

The only way to make this noise stop is by running from batteries or by disabling External Amplifier, which then causes the sound volume to go way way down and can barely be heard.

The noise persists even when everything is muted.

The noise happens only when the display panel is on. If I close the lid, the panel will shut off and the noise will go away.

Anyone have any ideas?

---

### Post by vapore0n on 2007-10-23
bump

---

### Post by vapore0n on 2007-10-25
bump for description change

---

### Post by Sandlst on 2007-11-12
I can confirm this, I'm on a Dell Inspiron E1505n, sound card = Intel 82801G (ICH7 Family) High Definition Audio Controller (STAC92xx).  I have tried a few different live cds (to see if the problem is ubuntu-specific) and found the same problem on all of them.

I couldn't find an existing bug report, so I've filled one here: [https://bugs.launchpad.net/ubuntu/+bug/162332]("https://bugs.launchpad.net/ubuntu/+bug/162332")

---

### Post by modu on 2007-11-21
Got this problem to, but with a D520, but it seems for me it's bugged like this even in windows and bios.

---

### Post by popch on 2007-11-23
I can not quite see it in the OP: have you tried setting the level of ***all*** channels to zero, and raising the levels one by one? Please remember that the mixing board appears to be hiding a few of the channels, initially.

---

### Post by vapore0n on 2007-11-23
> **popch said:**
> I can not quite see it in the OP: have you tried setting the level of ***all*** channels to zero, and raising the levels one by one? Please remember that the mixing board appears to be hiding a few of the channels, initially.

yes, the problem exists even if all the channels are muted or down to 0 volume. But only if External Amplifier is turned on, which is needed to make sound work, else its way way too low.

And this is a Ubuntu driver problem , as windows doesnt have this problem.

---

