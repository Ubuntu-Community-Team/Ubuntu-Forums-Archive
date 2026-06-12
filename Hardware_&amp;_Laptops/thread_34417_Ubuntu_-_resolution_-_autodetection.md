---
title: "Ubuntu - resolution - autodetection?"
date: 2005-05-14
forum: Hardware &amp; Laptops
---

### Post by wiraone on 2005-05-14
Hi all,

Anybody knows why if my monitor is off during boot-up time, the default resolution changed to the lowest possible eventhough I've set it up in /etc/X11/xorg.conf to set it at normal resolution that I wanted? I've had no problem if the monitor is switched on during the boot up though. I've my monitor connected to Belkin OmniCube KVM if that matters. TIA for any info.

---

### Post by nad on 2005-05-14
The X server probes your monitor at startup. So even though you have specified your requested resolution, the server falls back (properly) to the lowest known setting.

---

### Post by wiraone on 2005-05-15
I guess that is the expected behaviour? If it is .. I guess I need to live with it .. not that important .. now I need to remember to switch on the monitor before switching on the PC. Thanks for the answer.

---

### Post by Firetech on 2005-05-15
I hope you know that you don't need to reboot to fix the resolution, it should be enough to press ctrl+alt+backspace in X. (Just some trivial info..)

---

### Post by wiraone on 2005-05-16
[QUOTE=Firetech]I hope you know that you don't need to reboot to fix the resolution, it should be enough to press ctrl+alt+backspace in X. (Just some trivial info..)[/QUOTE]
 Been using Linux for quite sometime now .. for sure I do know that .. it is just that ctl-alt-backspace doesn't restart X (X got killed but not restarted) .. and my previous RH/FC experience couldn't help either since I didn't know the correct runlevel to get the X up and running (now I do .. :))..

---

### Post by nad on 2005-05-16
You are already in your runlevel. What you need to restart is your display manager.

/etc/init.d/gdm restart

---

### Post by wiraone on 2005-05-18
[QUOTE=nad]You are already in your runlevel. What you need to restart is your display manager.

/etc/init.d/gdm restart[/QUOTE]
 It is possible to get this done automatically? Without a need to do gdm restart? This didn't happen when I'm using FC3.. there should be some setting that I missed out?

---

### Post by nad on 2005-05-18
You can 'tab' through your configured resolutions using the key sequence: Ctrl->Alt->(number pad) + or - .

This will simply change the resolution of your X display.

---

### Post by wiraone on 2005-05-20
[QUOTE=nad]You can 'tab' through your configured resolutions using the key sequence: Ctrl->Alt->(number pad) + or - .

This will simply change the resolution of your X display.[/QUOTE]
 ctl-alt-backspace is now working fine .. I did a dpkf-reconfigure and it seems solve it .. hmm.. haven't tried to restart with monitor off though.. will try it later on.

---

