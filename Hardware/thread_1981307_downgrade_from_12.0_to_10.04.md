---
title: "downgrade from 12.0 to 10.04"
date: 2012-05-16
forum: Hardware
---

### Post by pasoleatis on 2012-05-16
Hello,

I am very disappointed with the 12.04. It freezes randomly while I do nothing intensive and I can not find the reason. People suggested that the problem is with the Unity 3D and there should be no problem with Unity 2D. I would rather use use gnome 2 than Unity 2D. Also the load is always bigger than 1 even if I do nothing. The only problem is that with Ubuntu 10.04 I have no driver for sound and mouse pad. With Ubuntu 12.04 I have those drivers. 

So my question is:

If I install Ubuntu 10.04 and later I install the 3.2 kernel are my mouse and mouse pad going to work?

---

### Post by wilee-nilee on 2012-05-16
> **pasoleatis said:**
> Hello,

I am very disappointed with the 12.04. It freezes randomly while I do nothing intensive and I can not find the reason. People suggested that the problem is with the Unity 3D and there should be no problem with Unity 2D. I would rather use use gnome 2 than Unity 2D. Also the load is always bigger than 1 even if I do nothing. The only problem is that with Ubuntu 10.04 I have no driver for sound and mouse pad. With Ubuntu 12.04 I have those drivers. 

So my question is:

If I install Ubuntu 10.04 and later I install the 3.2 kernel are my mouse and mouse pad going to work?

So you can't downgrade, but if you have a separate home you can reinstall 10.04 and use that home.

Have you installed the gnome-shell and looked at the fallback/classic gnome2 sort of desktop?

---

### Post by pasoleatis on 2012-05-16
> **wilee-nilee said:**
> So you can't downgrade, but if you have a separate home you can reinstall 10.04 and use that home.

Have you installed the gnome-shell and looked at the fallback/classic gnome2 sort of desktop?
Hello,

Thank you for your reply.  By downgrade I was of course thinking about fresh install. The question is if the drivers for sound and mouse are coming with the kernel 3.2?

---

### Post by wilee-nilee on 2012-05-16
> **pasoleatis said:**
> Hello,

Thank you for your reply.  By downgrade I was of course thinking about fresh install. The question is if the drivers for sound and mouse are in the kernel 3.2?

Hard to say really, to be honest I would post the actual hardware you have.

```
lspci
```

Will identify the hardware

---

### Post by ahallubuntu on 2012-05-16
Why do you think you need the 3.2 kernel with Ubuntu 10.04 LTS?  If the problem is in fact in that kernel, you're going to have the same problem you have now with 12.04 LTS.

Was there some issue you had with 10.04 that was fixed (despite the freezing) with 12.04?

---

### Post by pasoleatis on 2012-05-16
> **ahallubuntu said:**
> Why do you think you need the 3.2 kernel with Ubuntu 10.04 LTS?  If the problem is in fact in that kernel, you're going to have the same problem you have now with 12.04 LTS.

Was there some issue you had with 10.04 that was fixed (despite the freezing) with 12.04?
> **wilee-nilee said:**
> Probably, we can't karnak your computer hardware, in other words just guess, :smile: you need to post the exact hardware if you want help with questions like this.

I would just try 10.04 from a live cd to see if everything works.
Hello,

I tried the live 10.04 and the sound does not work.  So in  10.04 (kernel 2.6) no driver for sound, but in 12.04 (kernel 3.2) there  is driver for sound. so my question is if I install 10.04 is it enough  to put the kernel 3.2 in order to get the sound working?

I have  acer 4830tg laptop. I do not have have the exact list of components. Is  there a command ot check which modules are loaded? 

I think the problem is in the Unity. 

The 10.04 Works perfect, only that it does not have drivers for some of the hardware in my laptop. I used it with my previous laptop for more than 2 years and I had to install 12.04 when I bought a new one. I want to go back to 10.04 , even if it is no supported anymore, but I also want to have the sound and the internal mouse working.

---

### Post by pasoleatis on 2012-05-16
```


~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 540M] (rev ff)
02:00.0 Ethernet controller: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet (rev c0)
03:00.0 Network controller: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
05:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
cva@GRU:~$ 


```

---

### Post by ahallubuntu on 2012-05-16
> **pasoleatis said:**
> I tried the live 10.04 and the sound does not work.  So in  10.04 (kernel 2.6) no driver for sound, but in 12.04 (kernel 3.2) there  is driver for sound. so my question is if I install 10.04 is it enough  to put the kernel 3.2 in order to get the sound working?

As I said above, the 3.2 kernel may fix your sound problems, but something else in the 3.2 kernel may cause those freezes.  You never know.

If audio is your only problem in 10.04, I'd probably look for a specific fix for the audio hardware (build a module for it or something) rather than going to the trouble of building a whole new kernel for it.

---

