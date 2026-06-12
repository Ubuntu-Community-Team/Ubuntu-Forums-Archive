---
title: "bluetooth mouse setup"
date: 2005-08-23
forum: Hardware &amp; Laptops
---

### Post by tmilam on 2005-08-23
Could anybody please tell me how to set up a bluetooth mouse? If I do 

```
hcitool scan
``` 

the mouse is recognized just fine. gnome-bluetooth-manager also sees it. But how do I use it? And how should I edit xorg.conf to allow me to use this mouse?

---

### Post by tmilam on 2005-08-24
I got my bluetooth working. Really all I needed to do was run:

```
hidd --connect XX:XX:XX:XX:XX:XX
```

Didn't need to edit xorg.conf. The mouse automagically worked with the mouse section in the x config file!

{edit}
Now i have to wonder...........is there a way to set this up so that if I turn the mouse on, it will 'just work' (TM)? I put the command in a script so that I don't have to type in the MAC everytime, but it's still a nuisance. If I don't run the above command, my mouse won't work....anybody know a way around this?

---

### Post by agblakey on 2005-09-30
[QUOTE=tmilam]I got my bluetooth working. Really all I needed to do was run:

```
hidd --connect XX:XX:XX:XX:XX:XX
```

Didn't need to edit xorg.conf. The mouse automagically worked with the mouse section in the x config file!

{edit}
Now i have to wonder...........is there a way to set this up so that if I turn the mouse on, it will 'just work' (TM)? I put the command in a script so that I don't have to type in the MAC everytime, but it's still a nuisance. If I don't run the above command, my mouse won't work....anybody know a way around this?[/QUOTE]
Just a stab in the dark but you could take a look at the /etc/default/bluez-utils file.

---

