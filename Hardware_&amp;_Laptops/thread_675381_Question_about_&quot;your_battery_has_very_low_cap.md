---
title: "Question about &quot;your battery has very low capacity&quot; warning"
date: 2008-01-22
forum: Hardware &amp; Laptops
---

### Post by bkhl on 2008-01-22
My old laptop battery started trigging the "your battery has very low capacity" when logging in, and after a while I clicked the button to turn that warning off.

Now I have a new battery, and what those warnings to be turned on again, for when the times comes for this battery. Where do I do that? I find nothing about it in the power management preferences dialogue.

---

### Post by Yellow Pasque on 2008-01-22
Type **sudo gconf-editor** in the terminal and follow the path of /apps/gnome-power-manager/notify. There should be checkboxes for low power and low capacity. Screenshot attached.

---

### Post by bkhl on 2008-01-22
Thanks, that was basically it.

However, if one has turned this warnings off by clicking the "do not show this warning again" button, that is a per-user setting, so one *should not* run gconf-editor with sudo.

---

### Post by Yellow Pasque on 2008-01-22
Ah, I see. I always wondered if sudo was necessary when running gconf. Now I see it differentiates root and user settings. Thank you.

---

