---
title: "Bad performance/Low FPS from Geforce 7950GX2"
date: 2012-07-21
forum: Hardware
---

### Post by chrisdku on 2012-07-21
Hey there, I am having a couple of issues after installing Ubuntu, aside from those I LOVE IT. It is much easier for me to get a handle on than Slackware even though I enjoy both. Anyways, I am running an Asus M2n32 SLI Deluxe motherboard with 2 gb memory, an amd athlon 64 x2 6000+ and a Geforce 7950 GX2. I tried to play Trine 2 on here, and also tried Heaven benchmarking software on low settings to see how the drivers performed. It was horrible. Trine was simply unplayable. I have no issues playing videos though. I'm not sure what to do about it. I am using the default drivers and did try the updated post install ones in the additional hardware menu. I have used an update manager to do all the updates and I believe I am up to date. I however am Linux impaired and need some help here. The only other odd thing I am experiencing is static in my speakers, its faint but there and then they randomly at times stop until I reboot. Not sure what the deal is. I have searched google and the forums but have come up short on proper fixes. Thanks!

---

### Post by chrisdku on 2012-07-21
not sure how I should post this but I used the lshq -c video command as I was trying to find out what version of drivers I was using and I am fairly sure something is way off, my clock speed shows up at 33 mhz lol, isn't it supposed to be somewhere in the 400-600's with this type of card. Hope that question doesn't sound too dumb. Here is what I got.

  *-display               
       description: 3D controller
       product: G71 [GeForce 7950 GX2]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f9000000-f9ffffff memory:e0000000-efffffff memory:fa000000-faffffff ioport:ac00(size=128) memory:fbfe0000-fbffffff
  *-display
       description: VGA compatible controller
       product: G71 [GeForce 7950 GX2]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f6000000-f6ffffff memory:d0000000-dfffffff memory:f7000000-f7ffffff ioport:9c00(size=128) memory:f8fe0000-f8ffffff
chris@chris-System-Product-Name:~$

---

### Post by chrisdku on 2012-07-21
Accidentally posted twice, ignore this.

---

