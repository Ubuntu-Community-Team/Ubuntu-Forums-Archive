---
title: "Are there drivers for new Texas Instruments card readers?"
date: 2006-11-22
forum: Hardware &amp; Laptops
---

### Post by az_s_za on 2006-11-22
I am unable to access an SD-card in the card reader of my new sony Vaio.

I have browsed other posts on this issue, and notice that when most people display their lspci, the lines dealing with their Texas Instruments controller say something like:
> 06:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:09.4 Class 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller
However, mine says:
> 06:04.0 CardBus bridge: Texas Instruments Unknown device 8039
06:04.1 FireWire (IEEE 1394): Texas Instruments Unknown device 803a
06:04.2 Mass storage controller: Texas Instruments Unknown device 803b
Is there somewhere I can get drivers for this device?  Or is my problem something else?

---

### Post by ArukiRei on 2006-11-26
I'm having the same problem that you are. ](*,) 

So want to get this thing working. Hate having to use Windows just to get it working. [-( 

I read somewhere that using 

```
modprobe tifm_sd
```

helps, but now I get 

```
FATAL: Module tifm_sd not found.
```

and it's pretty usless. :-k 

Hopefully someone else knows the answer. :KS

---

### Post by az_s_za on 2006-11-27
My problem has just been solved on another thread, and the solution is similar to what you have mentioned above ArukiRei:-

Originally Posted by Hugin:
> sudo modprobe tifm_core
sudo modprobe tifm_sd

and the SD card shows up

adding
tifm_core
tifm_sd
to /etc/modules will have them load at boot


---

