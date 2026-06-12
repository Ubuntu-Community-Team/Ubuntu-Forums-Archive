---
title: "Laptop Battery Deep cycle."
date: 2008-05-30
forum: Hardware
---

### Post by Ceemee on 2008-05-30
I know to keep your laptop battery working to its fullest you should fully charge and drain your battery 3-4 times every so often, AKA a deep cycle.

Windows has a utility to do this while its plugged in, is there anything like that for linux?

---

### Post by stchman on 2008-05-30
> **Ceemee said:**
> I know to keep your laptop battery working to its fullest you should fully charge and drain your battery 3-4 times every so often, AKA a deep cycle.

Windows has a utility to do this while its plugged in, is there anything like that for linux?

Just let the laptop drain the battery down and then recharge it.

---

### Post by Ceemee on 2008-05-30
I understand you can just let the laptop drain and then recharge it.  What I'm asking is windows has a utility that will drain it and then automatically recharge it to full, using this information to better calibrate battery status reporting.

I dont need all that, but I dont want to have everything drain to zilch and turn off unclean. Seems risky for config files and such.

---

### Post by adusty on 2009-06-08
I'm interested in such an utility for linux if it exists... Anybody can update the thread if some kind of tool become available?

Thanks

---

### Post by Menthu_Rae on 2009-06-08
There's no need to "better calibrate battery status reporting" - at least from what I know - gnome-power-manager keeps csv files of your charging and discharging profiles in /home/user/.gnome2/gnome-power-manager/ and uses them to generate the charging/discharging time estimates.

It's still "good" to deep cycle your battery depending on what you believe about Li-Ion batteries, and yes it would be good to have a tool to do it - but so long as you shut down all non-essential apps, just letting it discharge until empty shouldn't damage anything on the filesystem. Some filesystems may complain and force an fsck - but I don't think it would corrupt it or anything.

---

