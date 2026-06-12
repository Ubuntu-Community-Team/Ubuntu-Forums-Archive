---
title: "Monitor does not wake up"
date: 2015-11-02
forum: Hardware
---

### Post by gpetris on 2015-11-02
Hi all,

I am using Ubuntu 14.04 on a Dell workstation. My monitor went to sleep during the night and does not want to wake up. Moving the mouse, pressing keyboard keys, or even hitting the power button do not help. The computer is on, since I can access it via ssh and I can see the web page I have on that server, but the monitor keeps sleeping...

Can anybody help?

Thank you in advance,

Giovanni

---

### Post by weatherman2 on 2015-11-02
I assume you've rebooted the machine?  Checked the monitor cable connections?

Can you VNC into the machine?  If so, does it show a monitor connected?  Or can you check via ssh if a monitor is connected?  (Is it Ubuntu Server or Ubuntu Desktop edition?)

---

### Post by gpetris on 2015-11-03
I have rebooted the machine and double checked the cable connection. I believe I have a desktop edition. About checking via ssh whether a monitor is connected, I am not sure this is the correct way of doing it, but this is what I did:

[COLOR=#FFF0A5][FONT=Courier]gpetris@definetti:~$ xrandr -q [/FONT][/COLOR]
[COLOR=#FFF0A5][FONT=Courier]Can't open display [/FONT][/COLOR]

Any clue?

Thank you,
Giovanni

---

