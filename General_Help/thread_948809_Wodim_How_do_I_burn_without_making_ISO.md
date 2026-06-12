---
title: "Wodim: How do I burn without making ISO?"
date: 2008-10-15
forum: General Help
---

### Post by hardysummer on 2008-10-15
Is it possible to get wodim to burn a bunch of files without making an ISO first?  I would like to burn the files directly into disk.

---

### Post by Altay_H on 2008-10-15
You should be able to do this quite easily with Brasero. I believe it comes installed by default, but if not you can find under Synaptic Package Manager. Just run brasero and choose "Data Project" and you shouldn't have any trouble.

Did you specifically want to do this with wodim?

---

### Post by sokopok on 2008-10-15
An alternative (on the console).
From the wodim manual (man wodim):

If  the  overall speed of the system is sufficient and the structure of
the filesystem is not too complex, wodim will run without  creating  an
image of the ISO 9660 filesystem. Simply run the pipeline:

genisoimage -R /master/tree | wodim -v fs=6m speed=2 dev=2,0 -

---

