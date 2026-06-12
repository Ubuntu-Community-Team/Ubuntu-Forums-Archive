---
title: "Cant install Intel GMA driver on Virtualbox - XP"
date: 2009-06-29
forum: Installation &amp; Upgrades
---

### Post by imagxz on 2009-06-29
Im running Ubuntu as my host and XP SP2 as my guest on Virtualbox. 

For some reason I cant install my crappy Integrated Intel graphics( Intel 965 Chipset on xp. When I download the file it says

> Error:
The computer does not meet the minimum requirements to install the software.:mad:

I even tried using Intels Driver Update Utility and it doesnt get past the first bar. Maybe there is something I need to do in Ubuntu or the Virtualbox settings?

How can I make XP recognize that I really have this and let me install the proper graphics drivers? Anyone?

---

### Post by cariboo on 2009-06-30
Virtualbox doesn't use the Intel driver, it has a virtual graphics adapter. go to Start-->Control Panel-->System-->Display Adapter to see what the graphics adapter is. In my case I don't have XP in a vm, but I do have Win 7, and thats what adapter show in display adapter.

If you install the guest additions, you should be able to adjust the resolution and color depth. To install the guest additions, once XP is running click on Devices and select Install Guest Additions

---

### Post by imagxz on 2009-06-30
Oh i see the virtualbox graphics adapter now. 

So how would I go about **enabling Direct 3D draw**? With the driver on normal XP, its enabled...

---

### Post by moster on 2009-06-30
> **imagxz said:**
> Oh i see the virtualbox graphics adapter now. 

So how would I go about **enabling Direct 3D draw**? With the driver on normal XP, its enabled...

It works. I try it and I can play some directX games.

---

### Post by imagxz on 2009-06-30
Oh boy, what a help, moster ](*,)

---

