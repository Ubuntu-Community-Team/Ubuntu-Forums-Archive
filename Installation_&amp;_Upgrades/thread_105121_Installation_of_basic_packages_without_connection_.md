---
title: "Installation of basic packages without connection to internet?"
date: 2005-12-17
forum: Installation &amp; Upgrades
---

### Post by wr0x2 on 2005-12-17
I have an old laptop (thinkpad 380ed, PI@166, 32mb ram) and I want to install ubuntu and a lightweight wm like fluxbox. I will be using a wireless card to connect to the internet, and I need to know if ubuntu supports wireless for the "server" type installation, and if it doesn't how can I configure my box so it has the basics + wireless? Once I have a net connection I can get anything I want through apt or source.

EDIT: If it's not clear, I want minimal install (server) + wireless capabilities.

---

### Post by Dr. Nick on 2005-12-17
It depends on how you achieve wireless. If you need ndiswrapper I believe it is included on the install cd, but not installed by default so you have to apt-get it from the cd which should be the same as if you did it online.

I know some other wireless drivers are on the cd aswell.
What kind of card is it? It may be supported by the kernel so you would have support with a server install. The server install is basically the entire system but without a gui or any gui apps, All the hardware support should be the same as a regular install, just no gui to configure it.

---

### Post by wr0x2 on 2005-12-17
Awesome, thanks. I have problems when trying to install though. Since the system has a very small amount of memory (32mb) the installer crashes when I try to load the installer components off the CD. Is there anyway I can set up swap space before anything gets installed? I can spawn a shell with server-expert, but if I made and formatted a swap partition would the installer be able to take advantage of it?

EDIT: went into the shell, but it doesn't look like any disk tools are provided.

---

