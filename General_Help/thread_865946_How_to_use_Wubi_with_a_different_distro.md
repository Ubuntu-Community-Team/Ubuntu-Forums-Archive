---
title: "How to use Wubi with a different distro?"
date: 2008-07-21
forum: General Help
---

### Post by open2linux on 2008-07-21
I would like to use Wubi to install the new Ubuntu 8.04.1 in a Vista machine at work (at home I am a long time Ubuntu user thanks to Wubi). 

But I want to use this iso:

[http://doc.ubuntu-es.org/Proyecto:Ubuntu-ES.iso]("http://doc.ubuntu-es.org/Proyecto:Ubuntu-ES.iso")

This just the oficial iso in spanish with all other languages stripped, and some translations unfinished in the oficial iso, finished here. It has also some utilities added to it.

I tried to place wubi and this iso in the same folder and run the wubi installer, but wubi won´t install it, it starts to download the oficial ubuntu iso.

I am sure some more people in the spanish speaking world may want to install this ubuntu iso with wubi. How to make wubi work with this?

Thanks

---

### Post by ago on 2008-07-21
You have to recompile wubi with the isolist.ini containing the relevant info for your ISO

---

