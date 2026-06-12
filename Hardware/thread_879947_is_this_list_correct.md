---
title: "is this list correct?"
date: 2008-08-04
forum: Hardware
---

### Post by wubrgamer on 2008-08-04
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel)

especially about the PRO/Wireless 4965 AG(N)  model

I need to know, because I'll put an older model card in without G because I know it's supported

but would sort of like this chip because it has N

thanks guys

YAY improving/double checking documentation

---

### Post by pytheas22 on 2008-08-04
Some of that stuff is outdated (or at least, it refers to older versions of Ubuntu).  In Hardy the iwl4965 and iwl3945 drivers are included by default and should support Intel cards well.  That page mentions using the ipw driver, which is an older Intel Linux driver that has been replaced by iwl*.  If you wanted to use ipw you'd have to compile it from source (but actually I don't think ipw supports 4965 anyway, only 3945).

Also I have seen a lot of issues here lately with the iwl drivers and certain chipset models, usually having to do with low signal strength or transfer rates.  They all seem to be due to bugs in the iwl source, and are all resolveable--usually the answer is, "Compile the latest iwl source, or wait for Ubuntu updates to fix the problem"--but just be aware that there are some issues that you may need to deal with.

But the bottom line is that in general, iwl4965 should be well supported on Ubuntu, and if you do run into problems, they're easy enough to fix.

---

