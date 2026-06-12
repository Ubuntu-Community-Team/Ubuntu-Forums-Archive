---
title: "Help with Video Drivers"
date: 2017-03-30
forum: Hardware
---

### Post by pratherdude2 on 2017-03-30
[SIZE=2][FONT=arial]I have a SuperMicro server running Ubuntu Server 16.04 LTS with **X8DTE-F (**[http://www.supermicro.com/products/motherboard/QPI/5500/X8DT6-F.cfm?SAS=N&IPMI=Y](http://www.supermicro.com/products/motherboard/QPI/5500/X8DT6-F.cfm?SAS=N&IPMI=Y))[COLOR=#002222]  motherboard in it with built in video, Video card is [/COLOR][/FONT][/SIZE][FONT=arial]Matrox G200eW 16 MB DDR2. it works but only gives me 800x600 resolution out, I have tried surching for drivers for it to try and get a better resolution but I am unable to find any. I have also tried to get an dedicated video card since the mobo says it has a PCIe x8 slot, the problem with the dedicated video card is none of them I can find will fit in the x8 slots on the mobo. Can anyone help me out wither either a dedicaed video card that will fit or drivers that will give me better resolution.[/FONT][SIZE=2][FONT=arial][COLOR=#002222]
[/COLOR][/FONT][/SIZE][SIZE=2][FONT=arial]Thanks in advance,
Nathan[/FONT][/SIZE]

---

### Post by SeijiSensei on 2017-03-30
First, since it's a server, it's likely running in text mode, right?  Why do you need better graphics?

Matrox support was always fairly iffy as I recall, so I doubt there are any better drivers than the ones that ship with the current kernel.  The file /usr/src/linux-headers-3.13.0-24/drivers/video/matrox/Makefile has a 1999 date.

I see a couple of NVIDIA cards that are described as having "PCI Express 2.0 x16 (x8 lanes)".  I have no idea whether that will fit your motherboard though.  Here's one: [https://www.newegg.com/Product/Product.aspx?Item=9SIA7HN5HW5402](https://www.newegg.com/Product/Product.aspx?Item=9SIA7HN5HW5402)

---

### Post by QIII on 2017-03-30
If you are running the server headless and only ever have a monitor attached for installing/reinstalling, I don't see a reason for you to spend money on a better GPU either unless you are doing GPU computing like some BOINC project or something.

If you want "better resolution" so you can see more in the terminal, just ssh to it from your desktop.

---

### Post by pratherdude2 on 2017-03-30
> **SeijiSensei said:**
> First, since it's a server, it's likely running in text mode, right?  Why do you need better graphics?

Matrox support was always fairly iffy as I recall, so I doubt there are any better drivers than the ones that ship with the current kernel.  The file /usr/src/linux-headers-3.13.0-24/drivers/video/matrox/Makefile has a 1999 date.

I see a couple of NVIDIA cards that are described as having "PCI Express 2.0 x16 (x8 lanes)".  I have no idea whether that will fit your motherboard though.  Here's one: [https://www.newegg.com/Product/Product.aspx?Item=9SIA7HN5HW5402](https://www.newegg.com/Product/Product.aspx?Item=9SIA7HN5HW5402)


I Looked at a couple of those cards, the problem is the PCIe ports on the mobo are only about an inch or two long so the connectors on the cards are too long to fit in the slots. And the slots don't have a cutout on the back side to let the cards extend through the slot.

---

### Post by pratherdude2 on 2017-03-30
> **QIII said:**
> If you are running the server headless and only ever have a monitor attached for installing/reinstalling, I don't see a reason for you to spend money on a better GPU either unless you are doing GPU computing like some BOINC project or something.

If you want "better resolution" so you can see more in the terminal, just ssh to it from your desktop.

I am running it with a gui since I don't know a lot about Linux and am still learning, so I like to be able to see in the gui what the different commands do so if I mess up on something and can fix it. If that makes any sense. I would like to run BOINC on it also since most of the time it is just running, don't really need a card for doing GPU computing but would like to see more of the screen without having to scroll across all the time.

---

### Post by Yellow Pasque on 2017-03-31
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1316035](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1316035)
The last comment in the bug claims to hack around the issue.

At any rate, you should be able to easily get 1280x1024 resolution by frocing vesa driver. Create /etc/X11/xorg.conf and paste this:
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

> I Looked at a couple of those cards, the problem is the PCIe ports on the mobo are only about an inch or two long so the connectors on the cards are too long to fit in the slots. And the slots don't have a cutout on the back side to let the cards extend through the slot. 
There are some cheap x8 cards if you're really interested in having a card that works without fuss and can run Unity smoothly: [https://www.newegg.com/Product/Product.aspx?Item=N82E16814126089](https://www.newegg.com/Product/Product.aspx?Item=N82E16814126089)

---

### Post by pratherdude2 on 2017-03-31
> **Temüjin said:**
> [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1316035](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1316035)
The last comment in the bug claims to hack around the issue.

At any rate, you should be able to easily get 1280x1024 resolution by frocing vesa driver. Create /etc/X11/xorg.conf and paste this:
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```


There are some cheap x8 cards if you're really interested in having a card that works without fuss and can run Unity smoothly: [https://www.newegg.com/Product/Product.aspx?Item=N82E16814126089](https://www.newegg.com/Product/Product.aspx?Item=N82E16814126089)


Thanks,I'll give this a try when I get home today.

---

### Post by pratherdude2 on 2017-04-01
[QUOTE=Temüjin;13627550][https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1316035](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1316035)
The last comment in the bug claims to hack around the issue.

At any rate, you should be able to easily get 1280x1024 resolution by frocing vesa driver. Create /etc/X11/xorg.conf and paste this:
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```




This fixed it, don't have to buy a video card now.

Thanks

---

