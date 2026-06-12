---
title: "Ubuntu 21.10 Fingerprint Scanner on Thinkbook"
date: 2022-01-04
forum: Hardware
---

### Post by erosman on 2022-01-04
I am a novice and installed Ubuntu 21.10 on Thinkbook 15 G2 ITL. How do I enable the Fingerprint scanner?

I have followed the instruction in [Fingerprint login in 20.04]("https://askubuntu.com/questions/1231185/fingerprint-login-in-20-04") but the *Fingerprint Login*  option does not appear in *Settings -> Users *as per [Log in with a fingerprint]("https://help.ubuntu.com/stable/ubuntu-help/session-fingerprint.html.en").

---

### Post by schragge on 2022-01-04
```
sudo apt install libpam-fprintd
```

---

### Post by erosman on 2022-01-04
> **schragge said:**
> ```
sudo apt install libpam-fprintd
```

Already done ... but
```
libpam-fprintd is already the newest version (1.90.9-1buil1).
```

---

### Post by schragge on 2022-01-04
Is your fingerprint scanner [listed as supported]("https://fprint.freedesktop.org/supported-devices.html")? linux-hardware.org [lists 20 probes for your model]("http://linux-hardware.org/?view=computers&type=Notebook&vendor=Lenovo&model=ThinkBook+15+G2+ITL+20VE"). I didn't find one with working fingerprint reader among the three I randomly selected from the list. Good luck.

---

### Post by erosman on 2022-01-04
There is [Lenovo ThinkBook 14 Gen 2 ITL/15 Gen 2 ITL](https://ubuntu.com/certified/202008-28154)

Where can I find if the fingerprint scanner is supported?

---

### Post by schragge on 2022-01-04
Down on the page you linked:
> **Issues? Let us know**

If there is an issue with the information for this system, [please let us know]("https://answers.launchpad.net/ubuntu-certification/+addquestion?field.title=Feedback on the Lenovo ThinkBook 14 Gen 2 ITL/15 Gen 2 ITL (202008-28154)").

---

### Post by albertomruggeri on 2022-01-12
> **schragge said:**
> Is your fingerprint scanner [listed as supported]("https://fprint.freedesktop.org/supported-devices.html")? linux-hardware.org [lists 20 probes for your model]("http://linux-hardware.org/?view=computers&type=Notebook&vendor=Lenovo&model=ThinkBook+15+G2+ITL+20VE"). I didn't find one with working fingerprint reader among the three I randomly selected from the list. Good luck.

I have the same computer. The ID of the fingerprint is 04f3:0c4**b** but is not present on this list. 
There are only: 
[TABLE]
[TR]
[TD]04f3:0c42[/TD]
[TD]ElanTech Fingerprint Sensor[/TD]
[/TR]
[TR]
[TD]04f3:0c4d[/TD]
[TD]ElanTech Fingerprint Sensor[/TD]
[/TR]
[TR]
[TD]04f3:0c4f[/TD]
[TD]ElanTech Fingerprint Sensor[/TD]
[/TR]
[/TABLE]
No luck to make fingerprint reader working? :(

---

### Post by schragge on 2022-01-12
> If in doubt, contact your distribution or systems integrator for details.
The link was given above.

---

