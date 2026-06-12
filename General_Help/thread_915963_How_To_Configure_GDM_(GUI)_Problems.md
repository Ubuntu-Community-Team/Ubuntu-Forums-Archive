---
title: "How To Configure GDM? (GUI) Problems"
date: 2008-09-10
forum: General Help
---

### Post by matey3 on 2008-09-10
Is there any way I could manually configure my gdm or kdm ?
I am running Ubuntu Hardy 8.04 server but on both computers I have problems with GUI. No GUI no gdm or kdm or X etc.?

when I call gdm I either get no responses or I get an error saying it is already running?
I thought it was the video drivers on the other PC but this one has the same problem!?(2 diff. computers/manufacturers, etc.)!

Thanks for any help!

---

### Post by Sycron on 2008-09-10
If it's already running then stop it.```
sudo /etc/init.d/gdm stop
```

---

### Post by matey3 on 2008-09-10
> **Sycron said:**
> If it's already running then stop it.```
sudo /etc/init.d/gdm stop
```

Cool thanks a lot!

Now if I knew how to configure it? I remember when I installed Feisty 7.04 I had a bit of problem but this time (w/ 8.04) I am thinking about er-installing the older version cuz its giving me hekk...
regards;

---

### Post by Sycron on 2008-09-10
Try gdmsetup .

---

### Post by matey3 on 2008-09-10
> **Sycron said:**
> Try gdmsetup .

oh that is a new one...
Thanks a lot for your help.. some how I get Gtk-Warning cannot open display:

I do not know why? I got an Acer flat panel LCD screen and NVIDIA GeForce on one machine and ATI Rage Pro on the other?
I know they are onboard video cards but worked fine before..

---

