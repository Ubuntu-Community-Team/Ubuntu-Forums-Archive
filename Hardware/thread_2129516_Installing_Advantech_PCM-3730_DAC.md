---
title: "Installing Advantech PCM-3730 DAC"
date: 2013-03-26
forum: Hardware
---

### Post by tisi1988 on 2013-03-26
Hello everybody!


I'm new here but I have been using Ubuntu since 2006, and I love it! 


Now, I'm dealing with a very annoying issue. I have a PC with an Advantech PCM-9587 motherboard with Ubuntu 10.04 installed and an Advantech PCM-3730 digital I/O card. I downloaded the source code from the Advantech website, compiled the kernel modules (advdrv_core.ko and pcm3730.ko) and I created the device file succesfully. The problem appears when I try to bind the device with the device file.


Has someone any experience dealing with this devices?


Thank you in advance.

---

### Post by gordintoronto on 2013-03-26
I have no relevant experience.

What happens when you: sudo modprobe advdrv_core
and the other one?

---

### Post by tisi1988 on 2013-03-27
> **gordintoronto said:**
> I have no relevant experience.

What happens when you: sudo modprobe advdrv_core
and the other one?

When I run modprobe for advdrv_core and pcm3730, the modules are loaded correctly. I can see them with lsmod and shows pcm3730 using advdrv_core. This is ok.

---

### Post by tisi1988 on 2013-04-24
I solved the problem with this:
[LIST]
[*]Reserve an IRQ in BIOS
[*]Change the IRQ level jumper to the same level as reserved in the BIOS.
[*]Download Linux Kernel 3.8.4 ([https://www.kernel.org/]("http://www.kernel.org/"))
[*]Compile activating the Comedi driver and the PCM3730 inside comedi devices.
[*]Download and compile Comedilib 0.10.1 ([http://www.comedi.org/download.html](http://www.comedi.org/download.html))
[*]Install the compiled kernel and install the compiled libcomedi.so in /lib
[*]Modprobe the comedi and pcm3730 modules[SUP]1[/SUP]
[*]Execute the compiled Comedi_config program with the cmd: "./comedi_config -v /dev/comedi0 pcm3730 0x300[SUP]2[/SUP]
[*]Run some testing program that uses Comedilib
[*]Profit.
[/LIST]

1) When you modprobe the comedi and pcm3730 modules, the comediX devices are created in /dev automatically.
2) The 0x300 parameter is the device I/O memory port and can be modified with the SW1 switch in the PCM3730 board.

Concluding, the Advantech drivers are useless. The community is priceless.

---

