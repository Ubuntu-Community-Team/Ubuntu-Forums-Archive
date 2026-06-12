---
title: "Pcmcia related problems - card xyz not working"
date: 2009-08-11
forum: Hardware
---

### Post by Hiborg on 2009-08-11
Hi!

This post is for those who tried everything else, and are desperate. :(

I was one of those people. I have Realtek 8169 based pcmcia network card (1Gb). It works fine under windows, but - any linux distribution is having problems with it. Problems range from card not been recognized in pcmcia slot, wrong drivers loaded, kernel panic, assigned wrong resources, wrong ethernet addres and almoust everything else. :confused:

Of course, i did try everything - different kernels, different drivers, different distributions - always with the same result - not working as it should.

So, one day a frend come by, and for fun, i did ask him to try this card in his laptop (jaunty x86) - and iot worked!!! WTF?!? 

So, after a lot of investigating, i did round problem down to pcmcia driver !? That is "yenta_socket" kernel module. It has few properties, and of course, i did try them all - with no luck. 

Because yenta_socket is loaded at boot, it is not possible to unload-load it when linux boots, so i did experiment using modprobe.d and options file. In the end, i got tired of constantly rebooting laptop, so i removed module, and rebooted. That way i can insert/remove without reboots.

After reboot - first modprobe resulted in same non-working effects. Removed module, inserted it again - and viola!! Module reported totally different set of io ranges and memory map?!!! AND IT WORKED!! :P

After (again) a lot of investigating, i rounded problem down to:
```
[    8.433292] pci_bus 0000:03: Raising subordinate bus# of parent bus (#03) from #04 to #07
```Long explanation is that bios is lazy when assigning io memory to pcmcia related chipset, so it assigns overlapped ranges to same device. Because this is known problem, yenta_socked have built-in work-around to reassign those resources, BUT it fails to reinitialize detection of resources, and uses those before reassigning.

So, simply removing module, and inserting it back again solves the problem! :P

To automatically do this at boot, create some file with excension ".conf" in /etc/modprobe.d and put:
```
install yenta_socket /sbin/modprobe --ignore-install yenta_socket ; /sbin/rmmod pcmcia yenta_socket ; /sbin/modprobe --ignore-install yenta_socket
```I suspect that others may have similar problems and focus their attention to drivers of the card, but maybe the problem is cardbus itself, like in my example.

For those intrested in details, i have Dell Latitude D630, with x86_64 Jaunty (desktop). Pcmcia card is Edimax EP-4203DL. After boot this are dmesg and iomem:
```
[    8.304248] yenta_cardbus 0000:03:01.0: CardBus bridge found [1028:01f9]
[    8.304273] yenta_cardbus 0000:03:01.0: O2: res at 0x94/0xD4: 00/ea
[    8.304275] yenta_cardbus 0000:03:01.0: O2: enabling read prefetch/write burs
t
[    8.433286] yenta_cardbus 0000:03:01.0: ISA IRQ mask 0x0cb8, PCI irq 19
[    8.433289] yenta_cardbus 0000:03:01.0: Socket status: 30000006
[    8.433292] pci_bus 0000:03: Raising subordinate bus# of parent bus (#03) from #04 to #07
[    8.433299] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[    8.433301] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge Memory window: 0xf1d00000 - 0xf1dfffff
[    8.433303] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge Memory window: 0x120000000 - 0x123ffffff
```and second insert:
```
[    8.680195] yenta_cardbus 0000:03:01.0: CardBus bridge found [1028:01f9]
[    8.680227] yenta_cardbus 0000:03:01.0: Preassigned resource 2 busy or not available, reconfiguring...
[    8.680235] yenta_cardbus 0000:03:01.0: Preassigned resource 3 busy or not available, reconfiguring...
[    8.680237] yenta_cardbus 0000:03:01.0: CardBus bridge, secondary bus 0000:04
[    8.680239] yenta_cardbus 0000:03:01.0:   IO window: 0x002000-0x0020ff
[    8.680244] yenta_cardbus 0000:03:01.0:   IO window: 0x002400-0x0024ff
[    8.680249] yenta_cardbus 0000:03:01.0:   PREFETCH window: 0xf0000000-0xf03fffff
[    8.680254] yenta_cardbus 0000:03:01.0:   MEM window: 0xf0400000-0xf07fffff
[    8.680263] yenta_cardbus 0000:03:01.0: O2: res at 0x94/0xD4: 00/ea
[    8.680264] yenta_cardbus 0000:03:01.0: O2: enabling read prefetch/write burst
[    8.813294] yenta_cardbus 0000:03:01.0: ISA IRQ mask 0x0cb8, PCI irq 19
[    8.813297] yenta_cardbus 0000:03:01.0: Socket status: 30000006
[    8.813337] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[    8.813339] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge Memory window: 0xf1d00000 - 0xf1dfffff
[    8.813341] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge Memory window: 0x120000000 - 0x123ffffff
```This is difference in iomem mapping between first and second insert:
```
@@ -15,6 +15,8 @@
   dff00000-dfffffff : pnp 00:0d
 e0000000-efffffff : PCI Bus 0000:01
   e0000000-efffffff : 0000:01:00.0
+f0000000-f03fffff : PCI CardBus 0000:04
+f0400000-f07fffff : PCI CardBus 0000:04
 f1d00000-f1dfffff : PCI Bus 0000:03
   f1d00000-f1d00fff : 0000:03:01.0
     f1d00000-f1d00fff : yenta_socket
@@ -68,5 +70,3 @@
   ffe00000-ffffffff : pnp 00:0d
 100002000-11fffffff : System RAM
 120000000-123ffffff : PCI Bus 0000:03
-  120000000-123ffffff : PCI CardBus 0000:04
-124000000-127ffffff : PCI CardBus 0000:04
```I will try to get post to linux kernel dev team. I hope this will help some other pour soul searching for the light ... :)

H.

---

### Post by anjali.thampi on 2009-12-07
Hi,

   I am a newbie.I recently posted a new thread coz my datacard was not getting detected.
The link to the same is *[http://ubuntuforums.org/showthread.php?t=1348268](http://ubuntuforums.org/showthread.php?t=1348268)* . 

   The output of my /var/log/syslog and /var/log/messages have similar code as you have shown:

```
 
  [   18.621434] Yenta: Raising subordinate bus# of parent bus (#03) from #04 to #07 
``` However, putting the code as described by you in /etc/modprobe.d/modprobe.conf and rebooting , did not have any effect.

 Can you help?I am really frustrated.

  Thanks in advance.

---

