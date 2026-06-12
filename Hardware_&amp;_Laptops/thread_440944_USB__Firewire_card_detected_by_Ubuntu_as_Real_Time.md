---
title: "USB / Firewire card detected by Ubuntu as Real Time Clock?"
date: 2007-05-12
forum: Hardware &amp; Laptops
---

### Post by capdog on 2007-05-12
Hi everyone

I have a USB/Firewire combo card which doesn't work out the box in Ubuntu Feisty 7.04. The output of lspci is:

```
 
02:02.0 RTC: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
02:02.1 RTC: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
02:02.2 RTC: VIA Technologies, Inc. USB 2.0 (rev 63)
02:02.3 PIC: VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)

```

It seems like it's detected it as an RTC, which is Real Time Clock - isn't it? 

Any help would be greatly appreciated! 

Thanks
capdog

---

### Post by heimo on 2007-05-12
Well - I'm afraid I won't be able to help, but you could give us more information and maybe someone will be able to help. Make and model of the device and output from the following command would be nice.
```
lspci -v -nn
```

---

### Post by capdog on 2007-05-12
Hi Heimo,

It's 

02:02.0 RTC [0803]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 61) (prog-if 00 [Generic])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038]
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at c400 [size=32]
        Capabilities: <access denied>

02:02.1 RTC [0803]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 61) (prog-if 00 [Generic])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038]
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at c800 [size=32]
        Capabilities: <access denied>

02:02.2 RTC [0803]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 63) (prog-if 20)
        Subsystem: VIA Technologies, Inc. USB 2.0 [1106:3104]
        Flags: bus master, medium devsel, latency 32, IRQ 5
        Memory at d0000000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

02:02.3 PIC [0800]: VIA Technologies, Inc. IEEE 1394 Host Controller [1106:3044] (rev 46) (prog-if 10 [IO-APIC])
        Subsystem: VIA Technologies, Inc. IEEE 1394 Host Controller [1106:3044]
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at d0001000 (32-bit, non-prefetchable) [size=2K]
        I/O ports at cc00 [size=128]
        Capabilities: <access denied>

---

### Post by capdog on 2007-05-13
The model is vt83c572

---

