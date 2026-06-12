---
title: "Installing a collection of .debs with dependencies"
date: 2009-04-14
forum: Installation &amp; Upgrades
---

### Post by firefly2005 on 2009-04-14
Hi everyone :p

I have a collection of deb packages (202 in total) which i need to be installed on my 32 bit ubuntu system (all the debs are 32 bit also). I was wondering what the best way of doing it is?

ive tried

```
dpkg -i *.deb
```

But that causes alot of problems with dependencies, is there a way of downloading the dependencies when installing the debs? Or even a way of producing a list of unsatisfied dependencies?

Thanks in advance =D

---

### Post by firefly2005 on 2009-04-14
Sorry to bother everyone, i found the answer myself =)

once i had run dpkg -i *.deb that i opened synaptic and synaptic fixed the broken packages for me 

Hope it helps someone
:grin:

---

