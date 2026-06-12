---
title: "Latest ATI driver install and now compiz gives me white screen :-("
date: 2008-10-05
forum: General Help
---

### Post by ajcrm125 on 2008-10-05
I just installed an ATI Radeon 9550 and installed the latest driver.  Now when I login I get a white screen.  If I don't run compiz then I can see my desktop.  Compiz ran fine with my previous Nvidia setup.
:-(

Still relatively new at Ubuntu so if there's something you need to see (xorg.conf.. etc) that would help debug, I'll gladly post.

Thanks for all/any help!

---

### Post by Borlag on 2008-10-05
Might be a bit too obvious, but have you checked if the Nvidia drivers are still active?

---

### Post by ajcrm125 on 2008-10-05
> **Borlag said:**
> Might be a bit too obvious, but have you checked if the Nvidia drivers are still active?

Yep, they're not... I even took the time to go into Synaptic package manager and uninstall them.

---

### Post by ajcrm125 on 2008-10-07
Solved!
I used Envy to reinstall the driver and all is well.
I grew suspicious when I ran glxgears and saw a framerate around 200.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

