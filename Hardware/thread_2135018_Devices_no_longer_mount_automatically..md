---
title: "Devices no longer mount automatically."
date: 2013-04-12
forum: Hardware
---

### Post by sona1111 on 2013-04-12
Hello, I have been enjoying ubuntu on my IBM thinkpad T60 for quite some time now. Recently I have been having a problem where removable media will not mount (by itself) No changes I can think of were done, just a week or so ago I tried to use my cd drive and it would not come up by itself. The disk used might have had problems, as I was reading it to figure out what it was. (it that helps) 

I have tried multiple usb sticks, cd/dvds and a SD card via an expresscard/SD adapter. 

These work fine if I mount them with the MOUNT command in the terminal. 

dmesg puts this for a DVD inserted:

```
[38612.903824] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready[38613.656520] ACPI: \_SB_.PCI0.IDE0.PRIM.MSTR - docking
[38613.656862] ata5: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0xe frozen
[38613.656867] ata5: ACPI event
[38613.656915] ata5: soft resetting link
[38613.820584] ata5.01: ATAPI: HL-DT-ST DVDRAM GSA-4083N, 1.08, max UDMA/33
[38613.836616] ata5.01: configured for UDMA/33
[38613.943847] ata5: EH complete
[38613.947360] scsi 4:0:1:0: CD-ROM            HL-DT-ST DVDRAM GSA-4083N 1.08 PQ: 0 ANSI: 5
[38614.057177] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[38614.057818] sr 4:0:1:0: Attached scsi CD-ROM sr0
[38614.059430] sr 4:0:1:0: Attached scsi generic sg1 type 5

```



The dvd drive itself is switchable, but I have never had a problem with that before either. 

cat /etc/issue:
```
Ubuntu 12.04.1 LTS \n \l
```

Thanks for any ideas!

---

### Post by zrdc28 on 2013-04-13
Go to settings, then removable devices and make them like you want them.

---

### Post by sona1111 on 2013-04-13
> **zrdc28 said:**
> Go to settings, then removable devices and make them like you want them.

This is a little ambiguous. Also, in system settings their is no "removable devices" button available. And nothing useful comes up if I search for it.

*edit* ok I think I found what you were saying, its in system details first, then the removeable media tab on the side. I have not changed anything and they are still all set to "ask what to do" like always. The problem is nothing ever does ask or pop up in the sidebar.

---

### Post by steeldriver on 2013-04-13
At least on my 12.04 box, it's not under 'System Settings', it's a separate item called 'Removable Drives and Media' - open the Dash search and type 'remo..' and you should see it

I think the dialog you found from the System Settings sidebar is for how to handle media *files* not the removable devices themselves

---

### Post by sona1111 on 2013-04-13
> **steeldriver said:**
> At least on my 12.04 box, it's not under 'System Settings', it's a separate item called 'Removable Drives and Media' - open the Dash search and type 'remo..' and you should see it

I think the dialog you found from the System Settings sidebar is for how to handle media *files* not the removable devices themselves

[[IMG]http://i174.photobucket.com/albums/w98/sona1111/Screenshotfrom2013-04-13120235_zpsd2d8de4e.png[/IMG]](http://s174.photobucket.com/user/sona1111/media/Screenshotfrom2013-04-13120235_zpsd2d8de4e.png.html)

In any case, I can see the options I presume you are referring to under the system info option (removable tab). And they have not been changed at all.

---

### Post by sona1111 on 2013-04-25
Ok, so I finally figured out the problem. Somehow, my partition table (which has been working fine over a year, still is) has been messed up a bit. Gedit shows "overlapping partitions". After fixing this the problem has been resolved.

---

