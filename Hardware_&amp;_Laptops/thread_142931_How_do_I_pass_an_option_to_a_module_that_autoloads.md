---
title: "How do I pass an option to a module that autoloads?"
date: 2006-03-11
forum: Hardware &amp; Laptops
---

### Post by enigma_0Z on 2006-03-11
I need to specify some options to my sound module (snd-ens1371) to activate my gameport. Specifically the option is "joystick_port=1".

However, all of the sound modules are loaded when the computer starts, and there's some circular dependancy that prevents me from unloading them. How can I autoload snd-ens1371 with the extra options?

---

