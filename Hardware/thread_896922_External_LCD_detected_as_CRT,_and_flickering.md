---
title: "External LCD detected as CRT, and flickering"
date: 2008-08-21
forum: Hardware
---

### Post by ludicrous on 2008-08-21
I am using 8.04 on an HP laptop with an Nvidia geforce Go 7400. I have a samsung syncmaster 2053bw connected with VGA.  nvidia-settings seems to be detecting the monitor as a CRT monitor- it calls it "Samsung SyncMaster (CRT-0 on GPU-0)".  I don't know if that's a problem by itself, but I'm seeing some flickering, just small flickers, easier to see in text or around outlines.

Maybe there's something I can add to xorg.conf to set this up manually?

---

### Post by mrsteveman1 on 2008-08-21
As far as the nvidia driver is concerned, anything connected to a DB-15 port is a CRT, and definitely analog.

You might try increasing the refresh rate or getting a shorter or newer cable.

---

