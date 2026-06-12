---
title: "Add/remove wont load"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by LilmissLinux on 2009-07-02
I recently installed Limewire on Jaunty 9.04 and everything seemed fine.  I can download music fine...but after trying to access add/remove I get the following message:

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

also with synaptic I get this message:
You have one broken package

when i look at it it is sun java.

I know limewire caused this error but i dont know how to fix it???

---

### Post by philcamlin on 2009-07-02
run 

sudo apt-get update  and sudo apt-get install -f 

then sudo apt-get upgrade

---

### Post by hansdown on 2009-07-02
Hi LilmissLinux.

To fix the broken package, open synaptic.

Click custom filters> broken.

You should get a "fix broken package" message.

Hope this helps.

philcamlin has good advice above. If you need help with those, just post

back.

---

### Post by philcamlin on 2009-07-02
> **hansdown said:**
> Hi LilmissLinux.

To fix the broken package, open synaptic.

Click custom filters> broken.

You should get a "fix broken package" message.

Hope this helps.

philcamlin has good advice above. If you need help with those, just post

back.

thanks :)

---

