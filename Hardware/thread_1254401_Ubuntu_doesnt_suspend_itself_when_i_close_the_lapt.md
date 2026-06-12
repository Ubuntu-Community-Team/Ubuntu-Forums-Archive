---
title: "Ubuntu doesnt suspend itself when i close the laptop lid"
date: 2009-08-31
forum: Hardware
---

### Post by akber on 2009-08-31
I want this to work so i can save battery, otherwise i might forget to manually suspend it before closing and my battery will die after a few hours of not using it, but it still being totally on and running at full power. 

I am wondering if this is a problem with the hardware drivers or just some settings i need to tweak in ubuntu. I already went into power management and set it so that it SHOULD suspend when i shut the lid, but it still does not do it. 

I am using an HP pavillion dv2000

---

### Post by akber on 2009-09-01
Bump

---

### Post by tgeer43 on 2009-09-02
Is the power management daemon and the acpid service running?

Check System->Preferences->Startup Applications for the former
and System->Administration->Services for the latter.

tgeer

---

