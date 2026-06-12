---
title: "caps-lock key - OS or keyboard dependent?"
date: 2005-11-09
forum: General Help
---

### Post by pickarooney on 2005-11-09
My caps lock key doesn't seem to function any more. The light doesn't go on and off when I hit it. I haven't tried rebooting yet, but is this likely to be a defective key or is it possible that the OS interferes with its functionality?

---

### Post by bionnaki on 2005-11-09
capslock works for me.

---

### Post by pickarooney on 2005-11-09
:D

I'm sure it does. I'm more wondering if there's some setting I can change so that it works, of if I need a new keyboard.

---

### Post by bionnaki on 2005-11-09
not sure.
but one way to troubleshoot would be to run a live cd.
if it works, then it's a configuration problem.
if not, then a hardware problem.

---

### Post by Dr. Nick on 2005-11-09
Easiest way would be to just restart and try to toggle the caps lock key before grub appears. It shouldnt be OS independent, maybe keymap but if you have  U.S standard keyboard it should work fine.

---

### Post by pickarooney on 2005-11-09
rebooted, all keyboard lights went out, but I could toggle them all on and off. Then the Ubuntu splashscreen appeared, the num lock came on (Everything was off previously) and caps lock no longer worked/works.

---

### Post by Dr. Nick on 2005-11-09
Hmm thats weird, So the key works before ubuntu loads which most likely rules out hardware. It must be some setting in ubuntu thn. Do all other keys work as expected?

You look around System-Prefrences-Keyboard and make sure its the right model and everything? I really dont know what would cause that

---

### Post by pickarooney on 2005-11-10
I changed the layout and model to the correct ones, but the caps-lock LED still won't turn on. There are options relating to the different -lock LEDs but I don't know what they mean. Behavious of caps lock is set to 'Default'.

---

### Post by doclivingston on 2005-11-10
Under Keyboard->Layout Options->Control key position, check that you don't have "Make Capslock an additional Control" set.

---

### Post by pickarooney on 2005-11-10
No, it's set to 'default'.

---

### Post by pickarooney on 2005-11-13
Caps lock works as far as the ubuntu login screen. I can still toggle it at this stage. It also works in XFCE, so there's something set wrong in GNOME somewhere.
I'm going to try out XFCE for a bit, so this is not a problem for the time being.

---

### Post by Dr. Nick on 2005-11-13
Well glad its not hardware related then. it seems odd though that a gnome setting could disable it, but I guess I can. XFCE is nice and I hope it works out for you ,and that a future update may fix your problem

---

