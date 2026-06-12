---
title: "JIS keyboard support in Lucid"
date: 2011-10-25
forum: Hardware
---

### Post by bcschmerker on 2011-10-25
I am attempting to fit an International Business Machines FRU# 42C0014 (Model SK-8840, English/Japanese, JIS layout with Trackpoint II and integrated touchpad) keyboard to a rebuilt eMachines®/Acer® EL1210-09 packing 4 GB RAM and augmented with a Shuttle® PC6300002 power-supply unit and an Asus® EN210/DI/512MD2(LP) video display adapter, running Kubuntu® 10.04.4-LTS with Japanese and English language support packages.  I really wanted a 128-key On-The-Stick Emulator, but Unicomp® would require substantial lead time to re-engineer the current Model M Terminal/Emulator series for the additional keys required in the spacebar row to properly support Japanese input.  (The closest production keyboard to my still-unmet original requirement, IBM P/N# 5576001, FRU# 90X1220, was subcontracted to Alps Electric Company and will not take standard Model M keycaps.)

Unlike IBM P/N# 1390121 and subsequent (101- and 102-key models which use an ANSI or ISO layout, respectively, derived from typewriters), JIS keyboards have historically used a superset of the [Livermore Keyboard](http://www.quadibloc.com/comp/images/lll.gif) (viz., a development keyboard using a superset of ANSI X3.4-1968 fabricated at Lawrence Livermore National Laboratory, Livermore, CA, USA) for the layout specification; the Livermore required simple logic to implement ANSI X3.4.  Proper support of the keyboard is a prerequisite for appropriate operation in iBus.

Can the necessary support for this keyboard be retrofitted in APT/Synaptic; or does this require a clean reinstall of Kubuntu?  And what packages are required to implement this support?

---

### Post by bcschmerker on 2013-01-12
I upgraded the system in question to Ubuntu® 12.04.1-LTS, AMD64 Edition (includes full support of standard Japanese keyboards), before any Answers were received, rendering this Thread a technical SOLVED. ):P

---

