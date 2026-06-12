---
title: "Dell Monitors USB ports working?"
date: 2005-07-23
forum: Hardware &amp; Laptops
---

### Post by kayas80 on 2005-07-23
Hi all

I just bought a Dell 1905FP TFT monitor which has 2 built in USB ports. Does anyone know how to get them working. Nothing happens when I try and connect my camera or memory card, I don't even get an error message.

Does xorg.conf need modifying to specify the monitor?

thanks

Oliver

---

### Post by rwabel on 2005-07-23
[QUOTE=kayas80]Hi all

I just bought a Dell 1905FP TFT monitor which has 2 built in USB ports. Does anyone know how to get them working. Nothing happens when I try and connect my camera or memory card, I don't even get an error message.

Does xorg.conf need modifying to specify the monitor?

thanks

Oliver[/QUOTE]
 in fact it has 4, 2 behind and 2 on the side :-)
I've plugged my RIO Carbon to it and it got mounted and it also charges the battery. I've done nothing special.

just a stupid question, did you connect the monitor to the USB plug on your computer?

---

### Post by kayas80 on 2005-07-23
[QUOTE=rwabel]in fact it has 4, 2 behind and 2 on the side :-)
I've plugged my RIO Carbon to it and it got mounted and it also charges the battery. I've done nothing special.

just a stupid question, did you connect the monitor to the USB plug on your computer?[/QUOTE]
 I didn't get a USB cable to connect the monitor. I just assumed it would work. I just dug a USB cable out and now it works.

Sometimes stupid questions provide the answers. Though I will be contacting my supplier to get my cable!!!

Thanks

---

### Post by kayas80 on 2005-07-23
Just out of interest did you change your xorg.conf to specify the DEll 1905FP monitor? I've got mine set as generic monitor.

If so could you please post it here.

---

### Post by rwabel on 2005-07-23
[QUOTE=kayas80]Just out of interest did you change your xorg.conf to specify the DEll 1905FP monitor? I've got mine set as generic monitor.

If so could you please post it here.[/QUOTE]
 The name isn't the important thing! It's important that the Horizontal and Vertical stuff is accurate!

---

### Post by kayas80 on 2005-07-23
[QUOTE=rwabel]The name isn't the important thing! It's important that the Horizontal and Vertical stuff is accurate![/QUOTE]


Already done. cheers

---

### Post by rsankuratri on 2005-11-08
I have the same monitor (Dell 1905FP) on my mew Dell Dimensions 9100 desktop nd I had set it up as per other threads as a "Dell 1905FP" montor.  THis does not work.  Can you please post your xorg.conf file if you don't mind?

Thanks for your help...

---

### Post by rwabel on 2005-11-08
I don't know if that changes much what you have in your xorg.conf. Did you plug a usb cable from your pc usb port to the monitor usb port? Here is the monitor and screen part of my xorg.conf:
```
Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
    HorizSync    30-80
    VertRefresh    56-75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 Ultra]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

---

