---
title: "internet speed very slow, and grafics drivers"
date: 2005-12-02
forum: General Help
---

### Post by Br0k3ndr34ms on 2005-12-02
hello
i just installed Kubuntu last night and set it all up
i need to ask 2 things,
do i need to set something up with the internet, cuz when i installed it it worked but its so slow.

and #2

does Adept have grafics drivers in it?

thanks

---

### Post by grimmson on 2005-12-02
seems a little slow here too. are you just talking about ubuntu sites or all the net?

---

### Post by Br0k3ndr34ms on 2005-12-02
every were.
hmm
it seems to be speeding up a little bit...but not much

---

### Post by metoo on 2005-12-04
This can be caused by problems with the IPv6 protocol. It's enabled in KDE by default (not firefox) but not supported by some hardware/router.

Try adding
KDE_NO_IPV6=true
to
/etc/environment.

---

