---
title: "error on installing tp_smapi."
date: 2012-12-01
forum: Hardware
---

### Post by AnthonyZ on 2012-12-01
[COLOR=Black]Hi , 
 [/COLOR][COLOR=Black][COLOR=Black] I have a thinkpad E430 PC,   i try to install [/COLOR]tp-smapi-dkms on Ubuntu 12.04(64bit), 
when i try to run "modprobe tp_smapi[/COLOR][COLOR=Black]"
error message shows:
FATAL: Error inserting tp_smapi (/lib/modules/3.2.0-29-generic/updates/dkms/tp_smapi.ko): No such device

any help for me?[/COLOR]

---

### Post by 2F4U on 2012-12-01
This site suggests that tp_smapi doesn't support your laptop:

[http://www.linlap.com/lenovo_thinkpad_edge_e430](http://www.linlap.com/lenovo_thinkpad_edge_e430)

---

### Post by linrunner on 2012-12-01
Hi,

tp-smapi  doesn't work on any Ivy Bridge Generation ThinkPad. For T430/530, W530, X230 the alternative to set charge thresholds is tpacpi-bat. Unfortunately the Edge-Series doesn't support tpacpi-bat either.

---

