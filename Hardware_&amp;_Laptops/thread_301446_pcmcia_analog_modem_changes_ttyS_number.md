---
title: "pcmcia analog modem changes ttyS number"
date: 2006-11-17
forum: Hardware &amp; Laptops
---

### Post by vob on 2006-11-17
Hi there,

I am running Kubuntu 6.06 on a Dell D620 laptop. I use a PCMCIA analog model (Elsa Microlink MC56k Internet) to connect to the internet via wvdial. This works usually fine.

The only problem is, that wvdialconf has detected the modem to sit on /dev/ttyS1, wheras after rebooting it its very often (though not always) recognized as /dev/ttyS4, which means that wvdial does not find it. The problem can be solved by ejecting and re-inserting the card manually, because then the modem sits on ttyS1 again. However, this is a little annoying, so I would like to have the modem sitting on /dev/ttyS1 (or ttyS4) all the time. 

Does anyone know how to achieve that? I would be happy to provide more information but don't know what might be useful.

Thanks in advance.

---

### Post by ozorba on 2006-11-23
I had a different problem with pcmcia modem. This was caused by the IR port. Here is how I solved the problem by modifying /etc/pcmcia/config.opts file.

-----

# With the kernel PCMCIA subsystem, these settings also have no effect
# at all on resources used for 32-bit CardBus cards.  Those are set by
# the PCI hotplug subsystem.
#
include port 0x100-0x3af
include port 0x3d0-0x4ff
include port 0x820-0x8ff
include port 0xc00-0xcf7

include memory 0xc0000-0xfffff
include memory 0xa0000000-0xa0ffffff
include memory 0x60000000-0x60ffffff
#

# These may hurt on FSC.
# include port 0x3c0-0x3d2
# Exclude 0x3d3 as Radeon IGP MCE's if you touch these ports
# include port 0x3d4-0x3df

# High port numbers do not always work...
# include port 0x1000-0x17ff

# Extra port range for IBM Token Ring
include port 0xa00-0xaff

# we need the following 2 lines to exclude the IrD irq and port clashes
exclude irq 3
exclude port 0x3e8-0x3ef

----


It works kernel is 2.6.17-10. And even better I see the same modem on different ports!

Here is what IO get when I execute dmesg | grep 'ttyS'

[17179574.208000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.208000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
[17179574.212000] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179601.048000] 0.0: ttyS3 at I/O 0x2e8 (irq = 4) is a 16550A

---

### Post by vob on 2006-11-27
Well, thanks for the reply. However, I didn't try your suggestion yet because I do not really understand what this might do to my system (I'm not really an expert when it comes to IRQs, port numbers, and memory ranges...)

Maybe, if you have time, it would be very nice if you could explain the effects that your modifications may/will have, or why you chose exactly these settings?

In the meantime I've found a workaraound by inserting an optional section in my wvdial.conf file, which overrides the 'modem = /dev/ttyS1' setting from the default section. 

```

[Dialer ttyS4]
modem = /dev/ttyS4

```

So, when the default call to wvdial faiils I simply call it a second time with this option, and everything is fine. This can also be used within a script by issuing the line

```

wvdial || wvdial ttyS4 
```

in a bash-script. When the first command fails, the second will be executed. Note that it will also be executed, when wvdial fails for any other reason (e.g. because the line breaks down), but then the second command will fail as well, because the modem is on the default ttyS1...

---

