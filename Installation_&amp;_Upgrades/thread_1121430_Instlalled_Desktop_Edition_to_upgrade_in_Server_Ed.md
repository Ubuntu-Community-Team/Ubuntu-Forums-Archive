---
title: "Instlalled Desktop Edition to upgrade in Server Edition, is ist possible?"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by gr3nm1nd on 2009-04-10
Is it possible to upgrade an Ubuntu Desktop Edition into Server Edition?

Or

Just wipe out the Desktop Edition previously installed and then run a fresh Server Edition image to installed over the old partition - which one is better?:p:confused:

PLs help to clarify me on this..

thanks a lot

---

### Post by 3rdalbum on 2009-04-10
The server edition is just the desktop edition without X and with a different kernel. So you've got three options:

1. Upgrade normally through Update-Manager and just install some server software onto Ubuntu desktop
2. Upgrade normally through Update-Manager and then remove the X server, all GUI programs and your desktop, and install some server software; if you want to, remove the "generic" kernel and install the "server" kernel.
3. Fresh install of Ubuntu Server 9.04.

---

### Post by gr3nm1nd on 2009-04-10
Ok thanks for the info. I'm planning to try this ubuntu with my existing 3-OS within my thin-box. And maybe replace one of it (Fedora) cause everytime I use my OpenSol-2008.11 for a while, something weird happening to the grub (fedora) which is in the worst case was ending me up into a "blank" screen after booting up the chosen linux-kernel. So I don't wish to re-do installing this (Fedora) once ubuntu experience for me is fine.

---

### Post by jogrady on 2009-04-12
New here too... What are the major differences in the kernel?  I'm sure it has been discussed, but I can't seem to find the right place...

---

