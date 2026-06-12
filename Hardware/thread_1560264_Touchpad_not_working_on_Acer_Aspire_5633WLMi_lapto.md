---
title: "Touchpad not working on Acer Aspire 5633WLMi laptop!"
date: 2010-08-24
forum: Hardware
---

### Post by Rytron on 2010-08-24
Hi.
The touchpad is not working in my dads Acer Aspire 5633WLMi laptop. I have it selected as enabled, yet it does not seem to function. Everything else works fine.

---

### Post by alonemayank on 2011-04-30
This can help you out sometime. Try it. It worked on Sony Vaio .

1. Edit /etc/default/grub to include GRUB_CMDLINE_LINUX="i8042.reset i8042.nomux i8042.nopnp i8042.noloop"
2. Run: sudo update-grub
3. Reboot

---

### Post by Rytron on 2011-04-30
> **alonemayank said:**
> This can help you out sometime. Try it. It worked on Sony Vaio .

1. Edit /etc/default/grub to include GRUB_CMDLINE_LINUX="i8042.reset i8042.nomux i8042.nopnp i8042.noloop"
2. Run: sudo update-grub
3. Reboot

Cheers alonemayank. I will try your solution.

---

### Post by branaja on 2011-04-30
hi there! I have similar problem - touchpad is not working..
I tried to change grub but it's read-only and I can't change permission cause I'm not the owner. can you help me? thanks

---

### Post by Rytron on 2011-05-04
> **branaja said:**
> hi there! I have similar problem - touchpad is not working..
I tried to change grub but it's read-only and I can't change permission cause I'm not the owner. can you help me? thanks

Hi branaja.

Run as sudo.

Example:
```
gksudo gedit /etc/default/grub
```

---

### Post by Rytron on 2011-05-04
> **alonemayank said:**
> This can help you out sometime. Try it. It worked on Sony Vaio .

1. Edit /etc/default/grub to include GRUB_CMDLINE_LINUX="i8042.reset i8042.nomux i8042.nopnp i8042.noloop"
2. Run: sudo update-grub
3. Reboot

Just tried this. No joy. :confused:

---

### Post by branaja on 2011-05-04
> **Rytron said:**
> Just tried this. No joy. :confused:

try this:
write this in terminal anr click enter.. it's working for me :)

gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true

---

### Post by Rytron on 2011-05-04
> **branaja said:**
> try this:
write this in terminal anr click enter.. it's working for me :)

gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true

Still no joy. :confused:

---

### Post by branaja on 2011-05-04
uh :/

sorry then, don't know anything more :(

---

### Post by Rytron on 2011-05-04
> **branaja said:**
> uh :/

sorry then, don't know anything more :(

Not to worry, thanks for trying. Funny thing is though that when I ran that gconf command, when I went back to 'Touchpad' in the kickoff menu ~ everything was greyed out.

---

### Post by duke79 on 2012-01-27
> **Rytron said:**
> Hi.
The touchpad is not working in my dads Acer Aspire 5633WLMi laptop. I have it selected as enabled, yet it does not seem to function. Everything else works fine.

try the following command --
 ** sudo modprobe psmouse**

worked for me.

---

### Post by duke79 on 2012-01-27
.

---

### Post by Rytron on 2012-01-30
> **duke79 said:**
> try the following command --
 ** sudo modprobe psmouse**

worked for me.

No luck with that command.

---

### Post by Rytron on 2012-05-01
I wiped Linux Mint 9 KDE and put on Ubuntu 12.04 Unity. The touchpad is still not working. :confused:

---

