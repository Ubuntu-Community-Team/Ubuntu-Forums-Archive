---
title: "Use laptop with dead graphics as server?"
date: 2012-04-27
forum: Hardware
---

### Post by olwe on 2012-04-27
I believe my thinkpad t61 with its NVIDIA Quadro NVS 140M 128 MB is flaking out. It started acting funny already with 11.10 -- and upgrades to 12.04 have seen the same graphics problems (flickering/freeze-up). Q: Can this unit -- perfect otherwise -- simply be a server? How would I configure it (running 12.04) to be just a server on my home network, with maybe graphics served across an ssh connection?

---

### Post by lukeiamyourfather on 2012-04-27
I'd install the server edition of Ubuntu which is by default a command line interface and see if it runs stable. If you run applications with an interface they can be launched from another machin with X tunneling over ssh (ssh -X user@host). Something to consider is the failing hardware might still cause issues with the system even if not actively being used. Worth trying but keep that in mind if you plan to do anything important with it.

---

