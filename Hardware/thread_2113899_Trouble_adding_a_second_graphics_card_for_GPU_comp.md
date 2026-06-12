---
title: "Trouble adding a second graphics card for GPU computing with CUDA"
date: 2013-02-08
forum: Hardware
---

### Post by k-mob on 2013-02-08
Hello all,

I've got a computer running Ubuntu 10.04 that I'd like to try some GPU computing on.  I've run the installer provided by nVidia successfully (which is supposed to include the appropriate drivers), but the catch is that I cannot see the new video card I've added.

That is, I already have a nVidia card installed handling my graphics (Quadro FX 1500), and I dropped in a new GT 610 that will be handling my GPU computing in the remaining PCI-e slot.  However, it doesn't show up using lshw or lspci.

For instance, lshw shows this for slot 3 (where I put it):
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz

Can anyone suggest how to get Ubuntu to recognize my new card?  Any help would be very much appreciated.

Thanks!

---

