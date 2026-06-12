---
title: "Removing old kernels"
date: 2008-10-24
forum: General Help
---

### Post by jvincent08 on 2008-10-24
I like to compile and install the latest kernels as they come out, and I always keep the previous kernel installed in case the new one is unstable. So by now I have several old, unnecesary kernels lying around taking up precious space on my hard drive. What would be the proper way to remove them? Will removing them via synaptic be sufficient? Thanks in advance :)

---

### Post by Tak11 on 2008-10-24
You should be able to remove them through the package manager, 

if you have the source laying around just rm -rf it :P

---

### Post by exploder on 2008-10-24
You can use Synaptic to remove old kernels. Make certain you remove linux-ubuntu-modules first, if you do mot do this first it causes real clean up problems.

---

### Post by jvincent08 on 2008-10-24
Ok, thanks guys :) I thought the package manager would be good enough, but I just wanted to make sure there wasn't more to it.

---

### Post by zvacet on 2008-10-24
In synaptic find **linux-image** packages and leave two with higher number and delete the rest.

---

