---
title: "Does Ubuntu 8.04.3 LTS allow Catalyst 9.3/older ATI cards?"
date: 2009-08-31
forum: Hardware
---

### Post by Objekt on 2009-08-31
I have to reinstall some version of Ubuntu on an older machine, since the HDD it was on died.  What is the newest version I can use, which will be supported the longest, but which allows use of the Catalyst 9.3 proprietary drivers?  The machine has an older ATI card, a Radeon x1650, so I can't use the newer Catalyst 9.4 drivers.  I know that means no Ubuntu 9.04 or 9.10, but what about 8.04.3?

I previously had Kubuntu 8.04.1 on the machine, and had to install the ATI proprietary drivers manually.  It involved several commands I didn't really understand, but it worked.  I don't want to waste time installing Ubuntu 8.04.3, only to find out it uses the newer Xorg version, which doesn't let you use Catalyst 9.3 or earlier.

---

### Post by tgalati4 on 2009-08-31
I think that you will be OK. If you use envy or System--Admin--Proprietary Drivers then installation should be automated.  It's a lot of work to install proprietary drivers.  It's my understanding (watching the process) that the kernel is recompiled with the necessary hooks to attach to the binary "blobs" of code that ATI or nVidia provides.  This creates a "tainted" kernel and you will see such warnings if you run dmesg.

For long term support with an older ATI card, then 8.04.3 is your best bet.

---

### Post by sideaway on 2009-08-31
I had 9.04 for with a x1400 (not HD, so unsupported) and 3d is absolutely terrible! I suggest going with 8.04 LTS. I'm considering even going 8.04 server LTS. and just install a GUI.

---

### Post by Objekt on 2009-09-01
Thanks!  I did some more research after that initial post, and eventually tracked down a list of the packages used in Ubuntu 8.04.3.  It definitely uses Xorg 7.3, which it seems is the key to the whole thing, in that Xorg 7.4 won't play nice with the Catalyst 9.3 or older driver package.

I booted the Live CD for Ubuntu 8.04.3 to play with it a little prior to an install.  The Envy package apparently is not in the 8.04.3 repositories, because it didn't show up when I entered that name in the "Add/Remove Programs" package manager.  Is that maybe a peculiarity of the live environment?

Later on I elected to go ahead with an install.  As luck would have it, the elderly machine I was installing on died.  Well, technically it froze hard first - first time I've EVER seen a Linux do that! - by which I mean it became unresponsive to input.  The display remained static, with no HDD activity.  It was about 25% done with install.  I thought maybe it was just super-busy, and it is an older machine (Athlon XP CPU), but after about 30 minutes of nothing more happening, I pushed the reset button.

Upon power cycling, the machine is brain dead.  The fans run, and various LEDs are lit.  Despite these signs of life, I get nothing from either the display or PC speaker.  Not so much as a POST display or an error beep.  Something major must have failed.

I tried flushing the CMOS, even going so far as to remove & replace the memory battery.  No joy.  So, it looks like I have major hardware troubleshooting to do before I get back to installing Ubuntu, or doing anything at all on that machine.

Usually I am a Kubuntu user, but I haven't found a Kubuntu 8.04.3 distro, only 8.04.1.  I don't think there's anything about KDE I can't live without.  GNOME isn't worse, just different.  I'm not a huge fan of the "looks just like Windows Vista" turn KDE has taken lately anyway.

---

### Post by Objekt on 2009-09-01
> **sideaway said:**
> I had 9.04 for with a x1400 (not HD, so unsupported) and 3d is absolutely terrible! I suggest going with 8.04 LTS. I'm considering even going 8.04 server LTS. and just install a GUI.

Wouldn't it be a lot easier to install the desktop version of Ubuntu 8.04.3 LTS?  It comes with the GNOME GUI.  Or do you have difficulty with obtaining the image or burning the disc?

---

### Post by dmizer on 2009-09-01
> **Objekt said:**
> Wouldn't it be a lot easier to install the desktop version of Ubuntu 8.04.3 LTS?  It comes with the GNOME GUI.  Or do you have difficulty with obtaining the image or burning the disc?

+1

The server kernel is tuned for no GUI. If you want a full GUI, use a GUI kernel.

---

### Post by tgalati4 on 2009-09-01
Sorry to hear about your machine.  Perhaps it overheated during all the installation activity.  What's the condition of the heat paste?  Sounds like a CPU overheat.  AMD's don't take overheat conditions too well.

---

### Post by Objekt on 2009-09-01
> **tgalati4 said:**
> Sorry to hear about your machine.  Perhaps it overheated during all the installation activity.  What's the condition of the heat paste?  Sounds like a CPU overheat.  AMD's don't take overheat conditions too well.

I haven't messed with it since I rebuilt the machine about 4 years ago.  Since I can't even get to a POST screen, let alone the temp monitoring page in BIOS, I have no idea what the CPU temp is like.

Is "lights on, nobody's home" a common symptom of an overheated CPU?  I would have thought I would get at least some display activity, even without a CPU installed, or with a fried one.

---

