---
title: "Usb Mouse Stops Working Again"
date: 2011-07-15
forum: Hardware
---

### Post by enginbahadir on 2011-07-15
Hi. This my first message. And my first problem with ubuntu until september 2009 :)

Problem is my mouse, or driver i'm not sure. Ubuntu starts well, and i starts surfing. After two minutes, or after ten minutes or after 60 minutes mouse stops working.

Keyboard works well. I have Gigabyte Ga-6Veml motherboard. Two usb hubs are near the sound panel, and one usb port are using with a connector.

This is my lsusb output:


```
engin@engin-masaustu:~$ lsusb
Bus 002 Device 002: ID 04a5:7008 Acer Peripherals Inc. (now BenQ Corp.) 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f3:0210 Elan Microelectronics Corp. AM-400 Hama Optical Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

And this is my lshw output for Usb Devices:

```
 *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.2
             bus info: pci@0000:00:07.2
             version: 1a
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:10 ioport:c400(size=32)
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.3
             bus info: pci@0000:00:07.3
             version: 1a
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:10 ioport:c800(size=32)

```

This is Ubuntu 10.04, and updated all backports updates are made.

What can i do? Is this a mouse problem, or motherboard problem?

Sorry for my poor english.


Thanks.

---

### Post by drpjkurian on 2011-07-15
Usually USB mouse work out of box. Well I suggest you to experiment with an other spare USB mouse (if available)to confirm whether the problem is in the mouse or not.

---

### Post by enginbahadir on 2011-07-15
drpjkurian, thanks for your message.

I used different mouses. This is my new mouse, i bought it last week :) But that doesn' t solve the problem.

I'm happy with ubuntu, so this is not a big problem for me. But sometimes i'm working on important documents, and this makes me angry :)

I hope we can solve this.

---

### Post by drpjkurian on 2011-07-15
```
sudo aptitude purge irqbalance
```

Try this code in termimal

---

### Post by enginbahadir on 2011-07-16
After purging irqbalance, doesnt freeze. I think you can do it:)

Thanks my dear.

---

### Post by drpjkurian on 2011-07-19
Most welcome

---

### Post by drpjkurian on 2011-07-19
Hi
If your problem is solved, Please Mark the thread as followed.

---

### Post by Johann-1.0 on 2011-12-12
Hello...i have the same problem. The mouse suddenly stops working...and I have to use the Usb one to work.I'm sure this is not the mouse device, because for some strange reason, the mouse started working again so I quit using the Usb one. Now, the Ps/2 mouse stopped working again...and I don't know why. Note: I'm using the Usb one again, but I prefer thousand times the PS2 one. Thank you very much. The code above doesn't solve the problem.

---

### Post by tealex on 2012-01-09
i have the same problem 
mouse suddenly freezes 
and in /var/log/messages 
USB disconnect, address XX

me help reinstall compiz

```

sudo apt-get purge compiz*
cd $HOME && rm -rf .compiz/ .config/compiz/

```

---

