---
title: "Nvidia: Removing old hardware driver befor installing new hardware."
date: 2015-02-13
forum: Hardware
---

### Post by kingdominsight on 2015-02-13
[COLOR=#006400]Greetings[/COLOR].
Sorry about this , im sure that this is a very dumb question. I did do a google search but possibly i worded it wrong because i could not find an answer.
[COLOR=#008000]
Situation[/COLOR]: 
  I am abount to install a Nvidia graphics card. My system currently has a ATI board being driven by Ubuntu provided open source drivers. NO Propitiatory drivers are installed.
"   [COLOR=#8b4513][SIZE=1]description: VGA compatible controller
       product: RV730 XT [Radeon HD 4670]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:43 memory:d0000000-dfffffff memory:fdfe0000-fdfeffff ioport:ee00(size=256) memory:fdf00000-fdf1ffff[/SIZE][/COLOR] "

[COLOR=#008000]Question[/COLOR]:
  What pre- hardware install steps are needed? Do i need to uninstall any current  drivers? If So, how?

[COLOR=#008000]Thank You[/COLOR].
[COLOR=#008000]Signed[/COLOR]: 
Some Old Dude who could easily confuse his shoes for his hat.

---

### Post by weatherman2 on 2015-02-13
You don't have to do anything ahead of time, if you didn't install proprietary drivers.  Linux will load only the modules it needs.  You may want to install whatever proprietary driver is suggested for the new Nvidia card once you've plugged it in and booted up.

---

### Post by deadflowr on 2015-02-13
Put the card in the machine, and boot the machine.
If it works, that's all you needed to do.
If you want it to work better, you can try installing the closed source drivers.

(Look for the program called Additional Drivers, it also show in the program called Software and Updates.
If you want to use the closed source drivers, best bet is always try the tested, or recommended driver first)

No need to uininstall anything.

---

### Post by kingdominsight on 2015-02-13
> **weatherman2 said:**
> You don't have to do anything ahead of time, if you didn't install proprietary drivers.  Linux will load only the modules it needs.  You may want to install whatever proprietary driver is suggested for the new Nvidia card once you've plugged it in and booted up.

> **deadflowr said:**
> Put the card in the machine, and boot the machine.
If it works, that's all you needed to do.
If you want it to work better, you can try installing the closed source drivers.

(Look for the program called Additional Drivers, it also show in the program called Software and Updates.
If you want to use the closed source drivers, best bet is always try the tested, or recommended driver first)

No need to uininstall anything.

Very cool! thanks for the very quick help!

---

