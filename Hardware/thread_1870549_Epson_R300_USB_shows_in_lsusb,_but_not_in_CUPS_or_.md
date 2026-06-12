---
title: "Epson R300 USB shows in lsusb, but not in CUPS or Printers"
date: 2011-10-27
forum: Hardware
---

### Post by mediaworksmt on 2011-10-27
Hi!

I have an Epson R300 that I initially installed under Ubuntu Natty 11.04. After upgrading to 11.10, the printer stopped working so I removed it from the list of printers in *System Settings > Printing*.

Upon trying to re-install the printer, it no longer shows up in the left-column of *System Settings > Printing*.

After doing some searching, I discovered I could access the CUPS admin interface by going to [FONT="Courier New"]http://localhost:631[/FONT] - However, going to *Administration > Add Printer* does not list my Epson R300 under "Local Printers". (A number of network printers are listed, however.)

I've also tried manually adding the printer via the [FONT="Courier New"]parallel:/dev/usb/lp0[/FONT] URI - I'm able to complete the process, but upon trying to print anything an error shows in the printer status that the device may not be available.

Upon further inspection, [FONT="Courier New"]/dev/usb[/FONT] doesn't even exist on my system.

However, running [FONT="Courier New"]lsusb[/FONT] in a terminal shows that my Epson R300 is connected, as well as the flash-card reader in it:

```
Bus 001 Device 003: ID 04b8:0803 Seiko Epson Corp. Printer (Composite Device)
Bus 002 Device 002: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
```

So I'm completely baffled as to how I can solve this one. I'm not a huge noob, more "intermediately comfortable" than anything, but I may need any complex command-line procedures written out for me to follow. 

Any insights or suggestions are greatly appreciated! :-)

---

### Post by pacut on 2011-10-27
Same printer, same issue since upgrade.

Reading on other forums I understood it is a matter of CUPS upgrade to 1.5.0 version. It is said downgrade to 1.4.6 does solve the issue. It look the new release of CUPS is not able any longer to deal with several printer connected via USB.

If someone would provide clear instruction about how to do it, that would be nice. 

Looking forward in receiving updated on this topic.

Thanks
Paolo

---

### Post by pacut on 2011-10-28
Maybe it would be better to open another 3rd with different title like "CUPS not dealing with printers after upgrade to 11.10". I am gonna doing it.

Ciao

---

### Post by pacut on 2011-10-28
done:

[http://ubuntuforums.org/showthread.php?p=11401924#post11401924](http://ubuntuforums.org/showthread.php?p=11401924#post11401924)

---

### Post by pacut on 2011-10-29
In this post there is the solution

[http://ubuntuforums.org/showthread.php?p=11405217#post11405217](http://ubuntuforums.org/showthread.php?p=11405217#post11405217)

---

