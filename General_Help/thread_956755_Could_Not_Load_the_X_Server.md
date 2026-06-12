---
title: "Could Not Load the X Server"
date: 2008-10-23
forum: General Help
---

### Post by locustfist on 2008-10-23
Ubuntu has been running great on my alienware laptop. Loaded right up and worked great.

now it shows this warning on a blue and white screen

at the bottom it prompts for a login, which i have tried, yet only results in what i think is a command prompt.

i fear this is a result of stopping an update halfway through when i had to run out really quick last week.

---

### Post by caleb12 on 2008-10-23
try logging into that command prompt and executing:

sudo dpkg-reconfigure xserver-xorg 

then restart your Xsession, either by rebooting or executing:

sudo /etc/init.d/gdm restart (or kdm restart - depending on Gnome or Kde)

If that doesn't work, post your /var/log/Xorg.log.0 and /etc/X11/xorg.conf files and we'll see what we can figure...

---

### Post by locustfist on 2008-10-23
thanks, trying it now

---

### Post by locustfist on 2008-10-23
ok, the machine shuts down before i can complete typing

---

### Post by caleb12 on 2008-10-23
Wow, seriously... ok... 

At the grub menu can you select a different kernel, maybe try the recovery mode option. 

If you don't see the grub menu, should come up right after the BIOS boots - tap the ESC key and that should get you into the Grub Menu.

But, bottomline you need to get to a command prompt and issue that command and to also be able to access the log files and the X11 config file.

---

### Post by locustfist on 2008-10-23
ok, i think i see a problem. went to recovery mode, and the machine is chutting itself down because it thinks it's reaching a 'critical temp'

which doesn't make sense, since it is just booted up and has yet to get warm

---

### Post by Yellow Pasque on 2008-10-23
Does your BIOS have a hardware health monitor? If so, boot into the BIOS and watch the CPU Temp in there. It's possible that your CPU fan stopped working or the heatsink is real clogged up with dust.

If you have a high power-drawing CPU (like a P4 or PD), it won't take long to reach a critical temp if the cooling mechanism isn't working.

---

### Post by caleb12 on 2008-10-23
That would explain things... unfortunately, the temp settings are an unfamiliar territory for me. There's gotta be a config file someplace for that, that tells it to shut down at that temp. Maybe it's getting Celsius and Fahrenheit mixed up... lol...

---

### Post by locustfist on 2008-10-23
thanks guys, i will check it out

---

