---
title: "Limited Screen Resolution In Ubuntu 8.04!"
date: 2009-06-08
forum: Hardware
---

### Post by dileepm on 2009-06-08
Hi,
I have installed Ubuntu 8.04 on my new notebook Acer 5738. It provides a resolution of 1366 x 768 but ubuntu 8.04 seems to deliver only 1024 x 768. But i get intended resolution ( 1366 x 768 ) in 8.10 and 9.04. Please get me a solution for this. :(

---

### Post by overdrank on 2009-06-08
> **dileepm said:**
> Hi,
I have installed Ubuntu 8.04 on my new notebook Acer 5738. It provides a resolution of 1366 x 768 but ubuntu 8.04 seems to deliver only 1024 x 768. But i get intended resolution ( 1366 x 768 ) in 8.10 and 9.04. Please get me a solution for this. :(

Hi and in 8.04 you can use the command with the alt, F2 keys ```
gksu displayconfig-gtk
``` and adjust.

---

### Post by dileepm on 2009-06-08
No actually thats a story. First i tried to installed Ubuntu 8.04 in normal mode when i happened to get a random pixels allover i tried with safe graphics mode installation and it worked. Now that i go to "Screen Resolution" dialog i get maximum resolution of 1024 x 768 pixel listed not more than that this doesn't happen in rest of the versions i mentioned.

---

### Post by overdrank on 2009-06-08
> **dileepm said:**
> No actually that a story. First i tried to installed Ubuntu 8.04 in normal mode when i happened to get a random pixels allover i tried with safe graphics mode installation and it worked. Now that i go to "Screen Resolution" dialog i get maximum resolution of 1024 x 768 pixel listed not more than that this doesn't happen in rest of the versions i mentioned.

Ok what is the model of the graphics card and you may look at [X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")

---

