---
title: "Managing docked/undocked xorg.conf"
date: 2010-05-16
forum: Hardware
---

### Post by mcewanbr on 2010-05-16
I am running lucid on a Dell Latitude E6500.  When I use my docking station (connected to two 20 inch Dell LCD's), I have to either run the nVidia X Server Settings tool and configure my two monitors with twin view or I copy in an xorg.conf that has the settings for the two monitors already and restart GDM.

Likewise, when I start my laptop up after being docked, I have to either run the nVidia tool and setup my single LCD or copy in my xorg.conf with the right settings and restart GDM.

There might be a better way to manage my docked/undocked situation (I am open to any better ideas) but for now, I would like to be prompted before GDM starts upon boot to ask me which xorg.conf I would like to use.

I can write the script to do the prompting, I am just unsure where to call the script from so that it prompts me before GDM starts.

Any thoughts?

---

