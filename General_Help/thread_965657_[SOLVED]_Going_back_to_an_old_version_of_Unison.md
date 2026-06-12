---
title: "[SOLVED] Going back to an old version of Unison?"
date: 2008-10-31
forum: General Help
---

### Post by 50words on 2008-10-31
I use Unison to keep my business files in sync between my work desktop and my laptop. I upgraded my laptop to Intrepid, but I am not willing to do the same with my work computer.

But Intrepid comes with Unison 2.27.57, while Hardy is still on 2.1.

So I need to roll back the version of Unison on my laptop to 2.1. What is the easiest way to do this?

---

### Post by Yellow Pasque on 2008-10-31
Unison 2.27.57 is available for Hardy in the Hardy-backports repository. You can either enable the backports repository in System -> Administration -> Software Sources or download the package directly here: [http://packages.ubuntu.com/hardy-backports/unison](http://packages.ubuntu.com/hardy-backports/unison)

EDIT: Unison 2.1x is also available in Intrepid as "unison2.13.16" if you'd rather use Unison 2.1x on your laptop.

---

### Post by xgravix on 2008-11-01
The gtk package is unison2.13.16-gtk. I had the same problem and this worked great to solve it (one machine hardy, one gutsy, one intrepid).

---

### Post by 50words on 2008-11-03
Thanks both of you. Installing unison2.13.16-gtk via Synaptic did the trick. (I removed the newer version.)

---

