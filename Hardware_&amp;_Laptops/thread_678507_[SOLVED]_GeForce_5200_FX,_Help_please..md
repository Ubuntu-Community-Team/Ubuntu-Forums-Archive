---
title: "[SOLVED] GeForce 5200 FX, Help please."
date: 2008-01-25
forum: Hardware &amp; Laptops
---

### Post by hinesdeal102 on 2008-01-25
I am running an old hp pavilion 511w, it has a intel celeron 1.2 ghz and 512 mb of ram, and it even has a dying intel graphics chip. Yea that is the problem My graphics are dying. I know this for a fact because A different graphics card fixed this problem when I was using windows. Anyway I have a pci slot GeForce 5200 fx. When I try to boot with this, I get a black screen hang.....and thats it. It just won't boot up all the way with this card. By the way I do not have very much linux knowledge, so help would be greatly apreciated. I could barely type this much without it crashing because everytime I scroll too fast in a window it crashes or freezes. Like I said before, any help would be greatly apreciated. Thanks.


p.s. I'm ready to break away from microsoft's tyranny, so please help me make this work so I wont have to use windows.

---

### Post by jeffus_il on 2008-01-26
Have you disabled the motherboard graphics adaptor in Bios?

---

### Post by hinesdeal102 on 2008-01-26
yea I forgot to mention that i cant in the bios. This motherboard is old and doesent give the option to disable the onboard gpu. I'm quite sure that would be the solution to this problem because correct me if im wrong but the geforce 5200 fx is a supported card, right? Anyway I was able to disable the onboard gpu in windows but in xubuntu it wants to load up the onboard gpu every time. Is there a way to disable the onboard gpu through xubuntu's software. I know there is I just need to know how. I'm not to handy with the terminal yet so some directions would be really nice. Thanks

---

### Post by jeffus_il on 2008-01-26
I'm guessing for you,

You need to configure through a file "/etc/X11/xorg.conf"
It has a section for the graphics device.
In this section there is an option for the BusId of the graphics device.
Use lspci to find the address of your graphics card. My relevant line looks like this:
```
 00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
```

Take the address portion (the beginning of the line and enter it in the correct portion of your xorg.conf file (BusID)

This way the XServer will run on your graphics card through the pci address.
My xorg.conf section looks like this:```
Section "Device"
        Identifier      "Intel Corporation 82945G/GZ Integrated Graphics Controller"
        Driver          "intel"
#       Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection
```See the matching addresses?
This may need a little polishing but the idea I think is good.

---

### Post by hinesdeal102 on 2008-01-26
Yea I went into (recovery mode) when booting up and typed lspci and it gave me a bus address. I wrote it down and the typed in sudo dpkg-reconfigure xserver-xorg  and then when it said autodetect video devices i said no and then it asked me for my pci bus address so i put it in and it said it was in incorrect format. Is there something I'm missing here? why isnt it a correct format. I put in what the lspci command told me it was. ????

---

### Post by jeffus_il on 2008-01-27
Can you edit /etc/X11/xorg.conf from the command line using nano or vim?

---

### Post by hinesdeal102 on 2008-01-27
I really don't know how to use nano too much. Could someone maybe point me in the right direction with this one?

---

### Post by jeffus_il on 2008-01-27
From the recovery mode console type ```
sudo nano /etc/X11/xorg.conf
```, it's not a big file, page down and find the busId line and make the change there. Nano is a simple editor like notepad in windows, the key actions are shown at the bottom.

---

### Post by hinesdeal102 on 2008-01-27
Ok I cant boot into ubuntu with my geforce so right now im using my integrated intel graphics. So should i hook up my geforce go into recovery mode and pull this up and change the bus id there? I tried this in the dpkg-reconfigure xserver-xorg command and it told me i was using an improper busid format, Just wondering if it would even work? But anyway does that sound like the right way to go? Thanks for the hlep.

---

