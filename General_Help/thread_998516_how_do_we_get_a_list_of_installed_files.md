---
title: "how do we get a list of installed files ??"
date: 2008-11-30
forum: General Help
---

### Post by ramaswamyps on 2008-11-30
i want to find what are kde packages i have installed.
how do i list available kde packages in repos.

i am investigating kde4 not starting.i have installed most of the kde4 packages shown in synaptic.
any idea what i have missed installing.?
i installed kde-3.5.10 and kde-4.1.2 in ubuntu-8.04

---

### Post by binbash on 2008-11-30
sudo dpkg -l | grep kde

---

### Post by ramaswamyps on 2008-11-30
thanks for fast reply.
works well 
i wonder if i can find available packages also in apt/archives or reloaded package list of synaptic?

by the way kde-4.1.2 started ok.:)

---

