---
title: "[SOLVED] Intersil Prism 2.5 WPA ndiswrapper help!!"
date: 2007-12-03
forum: Hardware &amp; Laptops
---

### Post by Achetar on 2007-12-03
Alright, I have an HP Pavilion ze4200 laptop and it has an Intersil Corporation Prism 2.5 Wavelan chipset (rev 01) Wireless Card built in. I am dual booting WinXP and Ubuntu, WPA works in windows but not in ubuntu.

I am trying to use the Windows drivers with Ubuntu using ndiswrapper, unfortunately to no avail. Could someone supply me with a step-by-step guide for doing this? or point me to how to use other drivers to connect to a WPA-Personal Network? (I would reeeeeally like a step-by-step guide either way)

Thanks in advance.

BTW, I got my Linksys WPC54Gv3 Card working, so I'm not entirely clueless...

---

### Post by Achetar on 2007-12-04
Anyone?

---

### Post by Achetar on 2007-12-06
Anyone at all?

---

### Post by Achetar on 2007-12-06
Alright, I think I need to update my firmware (I have version 1.4.9, WPA isn't supported till 1.7.4, I am going to use 1.8.2) But I cant get hostap to compile it gives the following error:
```

*** Can't compile for 2.6 with non-2.6 source
make: *** [2.6] Error 1

```
I believe this means (after some googling) that I need to use the source found in the kernel source, but I cannot find it. Does anyone know where it is?
Thanks in advance

---

### Post by Achetar on 2007-12-16
Well, its been awhile, but I have the solution:

Flash the card firmware in Windows (blech! but hey, its better than spending a week with a next-to-useless computer because it is recompiling the kernel 3 times a day trying to enable PRISM2_DOWNLOAD_SUPPORT).

Oh, and I am not using ndiswrapper, I am using the hostap drivers (working wonderfully!).

---

### Post by stani on 2008-04-30
Hi,
It looks I am struggling since Feisty with the same problem as you. This is my card:
```
$ lspci | grep Prism
01:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
```

This is the same as yours right? I have an IBM thinkpad x30. How can I verify the firmware version of my card? Where can I find the firmware? Could you give me more steps of what you did exactly?

Thanks in advance,
Stani

---

### Post by Achetar on 2008-05-16
Unfortunately I don't know what I did... I do know that you need to google Prism 2.5 WPA Firmware and flash it in Windows (since it is near impossible to do in Linux from my experience). Be very careful though, I nearly fried mine.

---

