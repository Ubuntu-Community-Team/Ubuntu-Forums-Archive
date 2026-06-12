---
title: "Videocard not powerful enough? (Unity) It is in Windows..."
date: 2011-06-26
forum: Hardware
---

### Post by thacursedpie on 2011-06-26
Hi all!

I have installed ubuntu 11.04 on my MSI cx620 laptop. Everything works well, apart from the graphics.

This laptop has switchable graphics (between Intel integrated and ATI Radeon HD5470). Because I have a dedicated videocard I would expect that I'd be able to run Unity (and some other stuff - Minecraft segfaults for example), but on login, it says my videocard is inadequate. This strikes me as odd, considering the fact that I am able to play games (TF2, counter-strike, ...) on this laptop with no problems (that's on Windows 7 though!).

That's why I think Ubuntu isn't handling my switchable graphics properly. But I am not sure. Is there any way I can find out which of my videocards is being used by Ubuntu?

If so, is there a way to switch between them? (I already tried the buttons I would use to do this in Windows, to no avail).

Thanks in advance :)

---

### Post by grahammechanical on 2011-06-26
Have you gone to Additional Drivers and activated the recommended drivers? There maybe an icon on the top panel giving you an option to do this.  I received that message. Is was inaccurate. So too will be the messages that say that the driver is activated but not in use. It is in use.

After activating the proprietary driver reboot and at log-in click your user name and from the right hand menu on the bottom panel select Ubuntu. Then Ubuntu with Unity will load as the desktop.

Regards.

---

### Post by thacursedpie on 2011-06-26
It says the driver is activated and in use...

So I don't understand why it's not allowing me to run unity :S

---

### Post by Yellow Pasque on 2011-06-26
> **thacursedpie said:**
> It says the driver is activated and in use...

So I don't understand why it's not allowing me to run unity :S
2 problems with that:
- Even on systems with one RadeonHD card, Catalyst and Unity don't work well together at the moment
- You're probably using the Intel GPU, so the presence of the ATI driver borks 3D on it

---

### Post by thacursedpie on 2011-06-26
You mention I'm "probably" using the intel GPU: is there any way to find out which GPU I am using at the moment? Can I disable the intel GPU somehow?

---

### Post by Yellow Pasque on 2011-06-26
> **thacursedpie said:**
> You mention I'm "probably" using the intel GPU: is there any way to find out which GPU I am using at the moment? Can I disable the intel GPU somehow?
You can look in your /var/log/Xorg.0.log to see what card is used. You probably can't disable the intel unless there's an option in your BIOS. You can disable the radeon so it doesn't eat your battery. Google vgaswitcheroo.

---

