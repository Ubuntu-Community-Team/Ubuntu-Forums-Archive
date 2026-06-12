---
title: "[SOLVED] Wireless &amp;quot;suddenly&amp;quot; missing"
date: 2008-09-13
forum: Hardware
---

### Post by SilverAdder on 2008-09-13
I am dual booting ubuntu hardy and vista on my laptop. I got my atheros wireless working with madwifi and everything was great, until i restarted today. 
I was in ubuntu and the wireless was working. I then rebooted to windows, as i often do, and then came back to ubuntu later and now the wireless is missing. I don't know what could have gone wrong with it. 
I'm fairly new to this and i don't really know what command output would help you guys so just let me know.
Any ideas as to what could be wrong?

---

### Post by pytheas22 on 2008-09-13
Please run these commands and post the output:
```

lshw -C Network
dmesg | grep -e error -e ath
lspci -nn | grep -i atheros
```

That should help us figure it out.

---

### Post by SilverAdder on 2008-09-13
Thanks for the quick response! Here is the output: 
lshw:
 *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0

dmesg: 
[   23.916348] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   54.164935] ath_hal: module license 'Proprietary' taints kernel.
[   54.183896] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   54.465994] ath_pci: disagrees about version of symbol _ath_hal_attach
[   54.466000] ath_pci: Unknown symbol _ath_hal_attach
[   54.466114] ath_pci: disagrees about version of symbol ath_hal_process_noisefloor
[   54.466117] ath_pci: Unknown symbol ath_hal_process_noisefloor
[   54.466566] ath_pci: disagrees about version of symbol ath_hal_computetxtime
[   54.466569] ath_pci: Unknown symbol ath_hal_computetxtime
[   54.466866] ath_pci: disagrees about version of symbol ath_hal_mhz2ieee
[   54.466869] ath_pci: Unknown symbol ath_hal_mhz2ieee
[   54.467085] ath_pci: Unknown symbol _ath_hal_detach
[   54.467784] ath_pci: Unknown symbol ath_hal_print_decoded_register
[   54.468430] ath_pci: disagrees about version of symbol ath_hal_init_channels
[   54.468432] ath_pci: Unknown symbol ath_hal_init_channels
[   54.468711] ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
[   54.468714] ath_pci: Unknown symbol ath_hal_getwirelessmodes

lspci:
07:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)

Im assuming the "UNCLAIMED" message from lshw has something to do with it?

EDIT: I just remembered i think i updated ubuntu before i restarted. That could have broken it, no? Is there a log over updates so i can check what i updated?

---

### Post by pytheas22 on 2008-09-13
Yeah, it looks like probably a bad kernel update broke the driver and the ath_pci module no longer wants to load.  If you boot to an older kernel (at the grub boot menu when you first turn on the computer, you should have a list of several different kernels; the one at the top is the newest, so try using one of the other ones), does the wireless work?

I'm on my way out now but will be back later so that we can solve the problem.

By the way, how did you get this card working originally?  Did you have to do any work or did it "just work" out-of-the-box?  I thought that the model of Atheros card that you have needed a more recent version of madwifi than that which ships with Hardy, so you had to compile it manually...

---

### Post by SilverAdder on 2008-09-13
I have only one kernel choice, a recovery mode for that and a memtest so i guess its not a kernel update gone awry? 

I found this brilliant madwifi scrip [_here_]("http://ubuntuforums.org/showthread.php?t=798485&highlight=madwifi+script") in the forums which seemed to work. It solved the problem of not being able to connect to network with security. The network speed was a bit on and off, being really slow sometimes, but it worked and that is better than not working :)

---

### Post by pytheas22 on 2008-09-13
Maybe the kernel module itself got updated or something, or something else that it depends on was changed.

Anyway, are you all set now then?  Everything works?

---

### Post by SilverAdder on 2008-09-14
No, i just ment i used the script to make the initial installation of madwifi, before this happened. Should i just do that again?

---

### Post by pytheas22 on 2008-09-14
Alright, sorry, I was confused.  Yes, probably the best thing to try first is just to run that script again, which should recompile madwifi for you.  If that doesn't work, we can look at other options.

---

### Post by SilverAdder on 2008-09-14
That did the trick! I would have tried reinstalling in the first place but i wasn't sure if it would just break it even further. Thanks for the help.

---

### Post by SilverAdder on 2008-09-15
For anyone interested i would like to point out that the update that broke the wireless (what ever it was), along with a new installation of the latest madwifi drivers really sped things up for me! My wireless is faster than ever, which actually doesn't say much, but it is pretty much as fast as in windows now. To whoever fixed this: good job!

---

