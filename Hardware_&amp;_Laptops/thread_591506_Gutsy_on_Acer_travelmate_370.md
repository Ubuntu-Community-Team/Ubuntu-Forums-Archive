---
title: "Gutsy on Acer travelmate 370"
date: 2007-10-25
forum: Hardware &amp; Laptops
---

### Post by PippoFranco on 2007-10-25
I have tried to install Gutsy on my Acer Travelmate 370. Previously I had no problem at all with Feisty.

The problems with Gutsy
- live CD doesn't boot clean: does not recognize ACPI, networking is unstable (to make it work I had to disable Ipv6)
- the installation stalls at the APT config point
- once installed Gutsy, apt-get (or Synaptic) do not work, I have tried to change sorces.list file in all conceivable way with no success.
To try to investigate the reason of the problem I have installed back Feisty (no problem) from the live CD to a clean disk and run an update cycle. I have then performed the update to Gutsy. The new system boots but networking is unstable (e.g ping works ok, Firefox on and off). Synaptic and apt-get do not see any of the repository (change of country o location has no effect). 

I write from my production machine under Feisty

Anybody there for advice?

Franco

---

