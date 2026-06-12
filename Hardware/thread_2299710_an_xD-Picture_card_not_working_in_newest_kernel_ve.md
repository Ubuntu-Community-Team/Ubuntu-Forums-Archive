---
title: "an xD-Picture card not working in newest kernel versions"
date: 2015-10-20
forum: Hardware
---

### Post by Andra on 2015-10-20
For the kernel 3.2.0.91.105 I noticed that the xD-Picture card from my camera is not working. Then I chose the 3.2.0-90-generic version in GRUB and it was OK. Today I installed the newest kernel - 3.2.0.92.106 and tried whether I can use my card. It's the same - I put in the card, the lights slightly blink, and nothing more. And if, after trying the card, I restart (from the menu) the computer, it freezes with
[FONT=Courier New]* Will now restart[/FONT]
and I must restart with the power button.

How is it possible that the card **is** working when I choose a kernel from September and **not** working when I choose any of the two latest kernels? What's messed up?

In both cases I get the same when:

~$ lspci | grep Ricoh
...
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)

~$ lsmod | egrep 'mmc|ricoh|sdhci'
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci

and nothing when
~$ dmesg | grep ricoh

--
Lenovo R61i, Ubuntu 12.04.5 LTS

---

### Post by Andra on 2015-10-21
Of course, I tried to solve this problem myself, too. Some more output (actually, it's the same in both cases - kernel 3.2.0-90 and 3.2.0-92): 

~$ lspci -nnk | grep Ricoh -A2
..
15:00.2 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 21)
	Subsystem: Lenovo ThinkPad W500 [17aa:20c8]
	Kernel driver in use: sdhci-pci
...
--
15:00.5 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 11)
	Subsystem: Lenovo Device [17aa:20cb]
	Kernel driver in use: r852

~$ dmesg | grep r852
[   54.467573] r852 0000:15:00.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   54.467592] r852 0000:15:00.5: setting latency timer to 64
[   54.467718] r852: driver loaded successfully
[  119.136080] r852: detected xD writeable card in slot

The drivers are "in use" and the card is being detected! But it helps me no further.

As I already wrote, when I insert the card, not everything is OK anymore. I cannot restart the computer, GParted are endlessly searching for partitions, "sudo fdisk -lu" gives much info (no xD) but never stops, modprobe never stops. And then there was that I run:
sudo modprobe -r r852 ; sudo modprobe -r sdhci_pci ; sudo modprobe r852 ; sudo modprobe sdhci_pci
and wanted to stop it (because it didn't stop by itself), and all crashed with "panic occurred, switching back to text console", which I got rid off only with power off.

It now seems to me that it's not that something is messed up on my computer. It is rather like the new kernels are, say, faulty. But no one cares for that because no one cares for xD-cards... Maybe I'm the only one using this dinosaur. Unfortunately I don't have any SD card by me now, so I cannot test what happens in case of an SD card.

---

### Post by kurt18947 on 2015-10-21
I'm no expert (and that's an understatement:tongue:) but could you try a live CD/USB of another version, perhaps something 14.04 or newer. If you want to stick with the feel of gnome 2, Ubuntu Mate 15.10 is pretty stable for me. My machine didn't like Ubuntu-Mate 14.04 but that may be just my machine. Trying a newer release might help to decide if the problem is with kernel 3.2.x or something else.

---

