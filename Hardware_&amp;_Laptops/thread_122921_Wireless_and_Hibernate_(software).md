---
title: "Wireless and Hibernate (software)"
date: 2006-01-28
forum: Hardware &amp; Laptops
---

### Post by skaz on 2006-01-28
I'm running Ubuntu on an older laptop with APM only. The software hibernate works out of the box, which I was supremely pleased with.

But I have one small problem, I'm using ndiswrapper (BCMWL5) for wireless, which also works flawlessly, except when I resume from hibernation, my wireless has lost all of its settings. I have to reconfigure and re-activate the wireless connection every time I come back from hibernate.

Not a huge problem, but it's detracting from how perfect this install could be.

---

### Post by skaz on 2006-01-29
Small update, apparently this doesn't happen everytime, just most of the time.

---

### Post by Skye on 2006-01-29
I don't know much about APM, but I do know that when people use the ACPI based suspend, similar problems to the one you describe can be fixed by setting the computer to unload certain modules before suspend, and reload them automatically on resume.  I don't know if APM offers this functionality or not.

I'm sorry I can't be of more help, but maybe this will get you started in the right direction.

---

