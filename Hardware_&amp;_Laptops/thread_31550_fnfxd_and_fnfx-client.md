---
title: "fnfxd and fnfx-client"
date: 2005-05-03
forum: Hardware &amp; Laptops
---

### Post by DarkGreen16 on 2005-05-03
I am trying to install fnfxd and the fnfx-client but am having some problems.

First I did sudo apt-get install fnfxd > worked fine

then I did

sudo apt-get install fnfx-client > worked fine

now when i type fnfx-client i get this error

fatal error: Could not open "/home/username/.fnfxrc". Please make sure that the default config is accessible.

then on the site I read this "The client configuration '~/.fnfxrc' has to be copied to the home directory of the user who executes the client. An example can be found in '/etc/fnfx/fnfxrc_example'."

problem is I can't find the directory /etc/fnfx or the .fnfxrc anywhere...it seemed to install itself magically somewhere but im not sure where. I'm so used to the directory structure of windows eek

any ideas? thx in advance

---

### Post by DarkGreen16 on 2005-05-04
*note to self* find files doesn't work like windows...

thx to the miracle that is locate i managed to get everything working

---

