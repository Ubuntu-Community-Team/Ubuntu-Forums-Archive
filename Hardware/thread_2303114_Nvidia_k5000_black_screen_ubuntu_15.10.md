---
title: "Nvidia k5000 black screen ubuntu 15.10"
date: 2015-11-16
forum: Hardware
---

### Post by Melclic on 2015-11-16
Hello,

I have been trying to activate my NVIDIA GPU and cannot get it to work. Tried most things I can find online, most notably:
- Tried all individual additional drivers from additional drivers
- Downloaded the binary driver from NVIDIA website
- Try setting nomodeset
- Try using the PPA 

```
[COLOR=#111111][FONT=Consolas]sudo lshw -c video[/FONT][/COLOR]  *-display               
       description: VGA compatible controller
       product: GK104GL [Quadro K5000]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0 [COLOR=#111111][FONT=Consolas]       resources: irq:48 memory:de000000-deffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:7000(size=128) memory:df000000-df07ffff[/FONT][/COLOR]
```

No luck for any of them. Always the black screen. I am using the X.org driver and sometimes crashes, something annoying.

Cheers

---

### Post by Vladlenin5000 on 2015-11-16
Nvidia recommends 352 only for Quadro K5000 but any newer version should work as well. 
Nomodeset is just a temporary workaround that should give you generic video. It's used _only_ when the card isn't supported by the open source driver, i.e., no video, and for the sole purpose of installing the proper proprietary drivers. Considering that isn't/wasn't the case I wonder why you followed that route, what were you expecting to happen... Really, it makes no sense.

---

### Post by Melclic on 2015-11-18
Well I was getting desperate, and indeed I didn't know nomodeset was for open source drivers. I have tried 352 and more recent drivers (actually tried so many now that I stopped counting), and all give me the same black screen on boot (this includes the binary version, PPA and the additional drivers from ubuntu). Note that all have been tried without nomodeset. Any idea why? Thanks.

---

### Post by Vladlenin5000 on 2015-11-18
It's possible that you've made a mess already. When testing drivers is strongly recommended to completely purge one version before installing another:
```
sudo apt-get purge nvidia*
```

That said there's also another terrifying possibility: Hacked/fake/counterfeit card. How reliable is the brand and vendor/store you got it from?
I've witnessed recently a quite similar problem with an unbranded GTX750ti* from a seller at Aliexpress (the portal itself isn't to blame here, they actually mediated the dispute and decided in favor of the customer).
This is just the tip of the tip of the iceberg: [https://forums.geforce.com/default/topic/863515/off-topic/moar-illegal-fake-gpus-/](https://forums.geforce.com/default/topic/863515/off-topic/moar-illegal-fake-gpus-/)

* The hack was so good that from the OS and apps perspective it all looked like the real deal and it even worked (read: video with correct resolution) in Windows 10 whereas in Linux had the same symptom you're having (no video after installing nvidia drivers). There was a giveaway though, the clock frequency way below what's expected from that chip. The problem in Windows was only noticeable with demanding 3D games and apps: Random artifacts, chromatic aberrations and freezes/crashes in ETS2 and many benchmarking tools even refused to run.

---

### Post by Melclic on 2015-11-18
Thanks for the reply,

This is a University purchased computer through a reliable vendor. Highly doubt that fake card is the issue. One thing I didn't consider was that it was broken, since everything seemed to work fine until I updated to Ubuntu 15.10 from Mint (actually tried mint and the same problem persisted). Any idea how I may test if the card is defective?

I indeed purged all previous versions of NVIDIA drivers from the PPA, or uninstalled the binary driver, and reinastalled ubuntu a few times (ubuntu 15.10 and 14.04 LTS).

Cheers,

---

### Post by Vladlenin5000 on 2015-11-18
> **Melclic said:**
> Any idea how I may test if the card is defective?

Sorry... In my liner of work we can't afford the time and resources to test hardware thoroughly as it should. When something isn't working and replacing that part solves the issue we just *assume* the older was defective. As such, this is the opposite of what a proper scientific method suggests.

---

### Post by Melclic on 2015-11-18
Right will install Windows and see if I can install and run the driver. If that is the case then this is an Ubuntu problem.

UPDATE: just did and it seems to work fine. Ubuntu problem then
UPDATE UPDATE, Turns out this was a false flag and it might indeed be a hardware issue. Fortunately the machine is under warranty so we will see what Lenovo says.

---

