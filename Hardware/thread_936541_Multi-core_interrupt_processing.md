---
title: "Multi-core interrupt processing"
date: 2008-10-02
forum: Hardware
---

### Post by ruggersway on 2008-10-02
Has anyone investigated the cpu core utilization on Ubuntu?  I ask because Ubuntu doesn't appear to be splitting between the two cores.

@ares:/etc/init.d$ cat /proc/interrupts 
       -    CPU0    -   CPU1       
  0:   -   59854    -      1   IO-APIC-edge      timer
  1:   -     802    -      0   IO-APIC-edge      i8042
  8:   -      15    -      0   IO-APIC-edge      rtc
  9:   -    4187    -      1   IO-APIC-fasteoi   acpi
 12:   -     651    -      0   IO-APIC-edge      i8042
 14:   -    3968    -      0   IO-APIC-edge      libata
 15:   -       0    -      0   IO-APIC-edge      libata
 16:   -       1    -      0   IO-APIC-fasteoi   yenta, tifm_7xx1
 17:   -   36397    -      0   IO-APIC-fasteoi   uhci_hcd:usb4, i915@pci:0000:00:02.0

I used OpenSuse for about 2 years prior to moving to Ubuntu and OpenSuse would have similar results as I now see in Ubuntu.  From what I found it was due to the way irqbalancer was written (granted this was on 10.2).

What I found was if I went into irqbalancer and edited a line I would see interrupts begin to be split across the two cores.

# cat /proc/interrupts
      -     CPU0     -  CPU1       
  0:  -  1175135    -   3994    IO-APIC-edge  timer
  1:  -     2154    -      6    IO-APIC-edge  i8042
  8:  -       10    -      0    IO-APIC-edge  rtc
  9:  -   116431    -    253   IO-APIC-level  acpi
 12:  -     3088    -      0    IO-APIC-edge  i8042
 14:  -    71852    -     30    IO-APIC-edge  ide0

Ubuntu seems to be doing the same thing as I saw in OpenSuse.  Has anyone researched this who can tell me if this can be modified in the current Ubuntu release?  

I have looked at the irqbalance init script and the default settings in /etc/default and modifying /etc/default/irqbalance didn't seem to make a difference.  Could someone with more experience in scripting add their two cents to this?

Thanks

---

### Post by cariboo on 2008-10-03
I'm not really sure what you are getting at, but my dual core amd acts exactly the same way my old dual processor server did, the tasks are split between the two proceesors whenever any heavy computing is needed. At on time when you were running more than one core, at least in Debian top would show both cores, I haven't found what option is needed to do the same thing. Htop does, but it really doesn't give the same output as top.

Jim

---

