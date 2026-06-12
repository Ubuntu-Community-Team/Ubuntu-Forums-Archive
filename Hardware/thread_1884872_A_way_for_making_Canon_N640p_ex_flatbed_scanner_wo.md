---
title: "A way for making Canon N640p ex flatbed scanner work in Ubuntu?"
date: 2011-11-22
forum: Hardware
---

### Post by gatgat23 on 2011-11-22
Is there a way for making Canon CanoScan N640P ex work in Ubuntu? I'm new in Ubuntu and I'm starting to install some drivers, updates. My last problem is I don't know if there's a way to make that scanner work for Ubuntu. BTW, my Ubuntu version is the latest version. (11.10 Oneiric Ocelot).

Thank you for your answers. :D

---

### Post by dandnsmith on 2011-11-22
Previous versions of Ubuntu seemed to have Simple Scan - which works for a lot of scanners - but you may need to investigate SANE, and see whether that has driver modules for your scanner.

---

### Post by gatgat23 on 2011-11-22
Thank you for your reply. I searched, and found that the N640p ex scanner works for SANE. But I don't know how to install SANE. Can you guide me? Also, I have the 11.10 Ubuntu version, does that matters?

---

### Post by dandnsmith on 2011-11-22
11.10 uses a different control setup than 10.04 - so I have installed synaptic to get that package installer interface (seems to not give me any problems). That said, I haven't tried, yet, to do any sane install - but I note that some of the sane modules are loaded (possibly for simple scan).

There is a graphics interface - xsane - if that interests you (not yet loaded).

You'd have to check the sane documentation (see their site), but I think you may need to also install a back-end (which has the device-particular bits).

---

### Post by gatgat23 on 2011-11-22
Thanks. I'll try what you said.

---

### Post by gatgat23 on 2011-11-22
Can't get it to work. I thought if I can just use Virtualbox to install Windows XP and then scan from there? But still, I'm a newbie. I don't know how to install Virtualbox. Help? Sorry.

---

