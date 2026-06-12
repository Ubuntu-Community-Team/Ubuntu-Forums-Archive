---
title: "audio disappears when insert headphone"
date: 2009-03-22
forum: Hardware
---

### Post by mabtifro2 on 2009-03-22
sound works fine on my eee 900 until i stick headphones into the jack, then nothing plays. then i take out the headphones, and still nothing plays. same deal in both gnome and lxde environments. recently just started happing, dont know what triggered it. when i restart computer sound comes back

---

### Post by mabtifro2 on 2009-03-27
ok well i went into alsamixer and discovered that my headphones are disabled. i  think that is the explanation. but i cant figure out how to reenable my headophones. how do i reenable my headphone in alsa mixer??

---

### Post by jeremyjjbrown on 2009-03-27
This is an alsa problem that I have on my laptop. If I plug in headphones sound dies and i have to restart alsa.

sudo /etc/init.d/alsa-utils restart

---

### Post by Neo_The_User on 2009-03-27
i get the same problem. i reboot and it works. although i have to reboot with headphones plugged in. >:O

---

### Post by jeremyjjbrown on 2009-03-27
You don't have to reboot. Just restart alsa in the terminal. Or ctrl-alt-backspace and relogin. It's faster ;)

---

### Post by mabtifro2 on 2009-03-27
nvm i figured it out, just installed the package "gnome-media" and checked headphones. thats all

---

