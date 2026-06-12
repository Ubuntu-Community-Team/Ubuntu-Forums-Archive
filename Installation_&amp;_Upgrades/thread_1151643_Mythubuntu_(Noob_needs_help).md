---
title: "Mythubuntu (Noob needs help)"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by grisapa1 on 2009-05-07
Hi, I'm downloading mythubuntu to my PC with windows right now, But when the dl is done i'd like to trasfer it and install it on other PC -
Is mythubuntu both Linux Ubuntu and MythTV? Cuz thats what i want, but HOW?! :D

---

### Post by HyRax on 2009-05-07
Mythbuntu is indeed Ubuntu with some Mythbuntu-branded packages bundled on top.

MythTV itself is comprised of two main meta packages only - "mythtv-frontend" and "mythtv-backend". These are the only ones you need to install on top of Ubuntu - everything else is purely cosmetic with the "Mythbuntu" branding.

If you only want to download the packages once and install them on another PC, then install AptOnCD and backup the Apt cache to a CD. You then use AptOnCD to restore the cache to the other PC and then can install as normal, except this time the installer will use what's in the cache instead of downloading it all again.

---

