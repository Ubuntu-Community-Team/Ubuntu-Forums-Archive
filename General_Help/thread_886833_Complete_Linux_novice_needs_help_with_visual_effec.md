---
title: "Complete Linux novice needs help with visual effects please"
date: 2008-08-11
forum: General Help
---

### Post by BritishBeef on 2008-08-11
Hi there,
I was round a friends house and saw Ubuntu in action and was impressed and fancied installing it on my laptop.

I have installed Ubuntu and wanted to have the fancy effects seen on my friends PC. Unfortunately, I think I may have a graphics card that is a problem because I get the error: 'Desktop Effects Could Not Be Enabled'.

My graphics card is an ATI Radeon Mobility X700. I have read that there's a known issue with this card and it would seem that some have found a workaround. However, as this is my first foray into Linux I have no idea what the explained workarounds were!

Is there any kind soul out there who could confirm that a woraround does exist for this card and also explain to me in noobie speak how to do it.

Many thanks for any help with this.

---

### Post by tuxxy on 2008-08-11
Did you check for the drivers first in, system > admin > hardware drivers

---

### Post by BritishBeef on 2008-08-11
> **tuxxy said:**
> Did you check for the drivers first in, system > admin > hardware drivers
Thanks for the quick reply.
I have just checked and it says 'ATI Fire GL' and states that it's enabled. Next to it though it says 'Not in use'. Is that right?

---

### Post by halln on 2008-08-11
> **BritishBeef said:**
> Thanks for the quick reply.
I have just checked and it says 'ATI Fire GL' and states that it's enabled. Next to it though it says 'Not in use'. Is that right?

Do you have a tick in the box?

---

### Post by BritishBeef on 2008-08-11
> **halln said:**
> Do you have a tick in the box?

Yes I do.

---

### Post by Wrycu on 2008-08-11
In the system status area (the top right), does it say "system restart required"?

---

### Post by BritishBeef on 2008-08-11
> **Wrycu said:**
> In the system status area (the top right), does it say "system restart required"?

Nope!

---

### Post by colobix on 2008-08-11
You can use the compiz-check to fix it and to tell you whare and what the error is. Download it here: [http://scumbox.com/cc.deb](http://scumbox.com/cc.deb)

Install this package file, open terminal and type compiz-check.

If your ati card is the problem you can unlock the blacklist function with this compiz-check script.

See if it works for you, and good luck:)

---

### Post by tuxxy on 2008-08-11
In future if you plan to upgrade, nvidia cards will run all the effects flawlessly

---

### Post by BritishBeef on 2008-08-12
> **colobix said:**
> You can use the compiz-check to fix it and to tell you whare and what the error is. Download it here: [http://scumbox.com/cc.deb](http://scumbox.com/cc.deb)

Install this package file, open terminal and type compiz-check.

If your ati card is the problem you can unlock the blacklist function with this compiz-check script.

See if it works for you, and good luck:)

Thanks very much for your help - that worked!

---

