---
title: "multi card reader- where to start?"
date: 2006-08-04
forum: Hardware &amp; Laptops
---

### Post by stevieb on 2006-08-04
I have a Lenovo 3000 C100 with an ENE CB-712/4 card reader.  it shows up on lspci, but I have no idea how to access it. 

Any help is appreciated!

-steve

---

### Post by sushilksk on 2006-09-17
^same problem, on same model.

any solution???

---

### Post by isTHEr3mOr3 on 2006-09-17
Same problem here, other laptop.

---

### Post by 900i on 2006-09-20
Ok, just got my pcmcia card reader working like this, it may point you in the right direction.

1. Put a card in the reader.
2. Go to the System > Administration >Discs menu item.
3. Start up the Discs utility.
4. Does your card show up as a Drive, something like /dev/hde.
5. Go to the Partitions tab.  Can you see any partition properties for the card.
6. If you can, you need to make a folder in the /media folder something like CardReader.  You'll need to be sudo to do this.
7. Go back to Discs utility and put /media/CardReader in the box that says access path.  Then click OK to exit
8. Open terminal and type  "sudo mount /dev/hde1 /media/CardReader"  to mount your card.  hde1 may be different on your system.  "sudo umount /media/CardReader" to unmount.

Hope this points you the right way.

---

### Post by stevieb on 2006-09-20
my card reader is internal, not pcmcia.

-steve

---

### Post by 900i on 2006-09-20
It might not matter as the Discs utility is looking for a disc drive and when the card is inserted it should show up, the actual card reader hardware might be irrelevant.

---

### Post by isTHEr3mOr3 on 2006-09-21
Doesn't work for me. Unfortunately my card is not in the list, only HD and CD-rom.

---

### Post by LinLenLap on 2006-11-26
Lenovo 3000 C100 same problem.

lspci:
```
01:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
01:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
01:04.2 Class 0805: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
01:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)
```

I put MMC card into it and run dmsg, and get about a hundred lines like this:
```
17184505.624000] TKIP: replay detected: STA=00:15:e9:1d:18:c6 previous TSC 00000002c602 received TSC 00000002c602
[17184516.516000] TKIP: ICV error detected: STA=00:15:e9:1d:18:c6
[17184516.864000] TKIP: ICV error detected: STA=00:15:e9:1d:18:c6
[17184518.708000] TKIP: ICV error detected: STA=00:15:e9:1d:18:c6
[17184529.104000] TKIP: replay detected: STA=00:15:e9:1d:18:c6 previous TSC 00000002cad6 received TSC 00000002cad6
[17184530.892000] TKIP: ICV error detected: STA=00:15:e9:1d:18:c6
[17184538.068000] TKIP: replay detected: STA=00:15:e9:1d:18:c6 previous TSC 00000002cca2 received TSC 00000002cca2
[17184545.020000] TKIP: ICV error detected: STA=00:15:e9:1d:18:c6
```

Looking into it, but would like to hear if anyone else has this going. I don't have an SD card around so I can't test if it;s that, or an extra MMC card. I did get an SD card read through the reader under windows, so I'm sure the hardware is ok.

L

---

### Post by samaerium on 2007-11-06
I also have a laptop with an internal cardreader. I can't acces my card. any ideas on how to mount it or install a drive for the cardreader.
thank you

---

