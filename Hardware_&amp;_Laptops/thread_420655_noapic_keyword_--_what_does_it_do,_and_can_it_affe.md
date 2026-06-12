---
title: "noapic keyword -- what does it do, and can it affedt suspend to ram/disk?"
date: 2007-04-23
forum: Hardware &amp; Laptops
---

### Post by enigma_0Z on 2007-04-23
I've got an HP dv6000z laptop that seems to work flawlessly without the noapic keyword passed to the kernel. 

However, I've read that several people need this to get the laptop working. My questions are:

1. The noapic keyword -- what does it do EXACTLY... what does it disable/enable/etc?
2. Could this affect whether or not my laptop can s2ram or disk? Because it can't without causing problems.
3. Could this affect my power efficiency? My battery on my replacement doesn't seem to last as long...

---

### Post by simonn on 2007-04-23
I assume you mean the kernel option acpi?

1. It disables acpi as in "no acpi"
2. Yes.
3. Yes.

---

### Post by enigma_0Z on 2007-04-24
For 2, & 3,

Would adding "noapic" affect these positively? EG.

2. Would/should s2ram/disk work with noapic added to the kernel command line?
3. Would/should my battery last longer with or without noapic?

---

### Post by se2131 on 2007-04-25
Er, I think you guys are confusing two different things.  I've had to use the **noapic** to get Feisty to work, which I don't think is related to **acpi** (I've experienced a few moments of dyslexia regarding this).

Though I don't know what noapic does, I think it has something to do w/ interrupt routing (but I could be completely wrong).

EDIT: link: [https://answers.launchpad.net/ubuntu/+question/4506](https://answers.launchpad.net/ubuntu/+question/4506)

---

