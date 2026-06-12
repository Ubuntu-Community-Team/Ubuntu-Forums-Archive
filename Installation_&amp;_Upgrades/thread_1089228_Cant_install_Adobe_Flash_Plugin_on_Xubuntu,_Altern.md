---
title: "Cant install Adobe Flash Plugin on Xubuntu, Alternative CD"
date: 2009-03-06
forum: Installation &amp; Upgrades
---

### Post by Silenti on 2009-03-06
Hey,

I've been installing Xubuntu on some old Dell machines (GX 50, 60, 280, etc.). I had problems installing the regular graphic installer CD, so I used to the Alternate version. Problem is, that when I try to install the Adobe Flash Plugin it gives me a libcurl3 dependency error. Weird thing is this library (as far as I understood) is already installed by default.
Note: I managed to install the regular Xubunto on an equivalent machine and I was able to install the plugin correctly.

BTW: My first post at the forums. Have only used Ubuntu (my first distribution) for 2 months now, but loving it...

Thanks for the help,

---

### Post by taurus on 2009-03-06
How did you try to install the flash plugin?  Just install the xubuntu-restricted-extras package and it will install all the plugins for you.

```
sudo apt-get update
sudo apt-get install xubuntu-restricted-extras
```

---

### Post by Silenti on 2009-03-06
I tried using the .deb and the tar from the Adobe site and using the wizard in firefox. I'm behind an ISA Proxy so I can't use apt-get or synaptics where I'm installing the machines.

Thanks for the quick reply

---

### Post by xenomuta on 2009-03-07
:( sorry to hear that you're behind an ISA "proxy", it's the nearest thing to hell.

you can just download the .deb suitable for your cpu manually from any ubuntu multiverse repository like this:

[http://debian.rab.co.id/hardy/pool/multiverse/f/flashplugin-nonfree/](http://debian.rab.co.id/hardy/pool/multiverse/f/flashplugin-nonfree/)

then:

sudo dpkg -i flashplugin-nonfree_VERSION_CPU.deb

---

