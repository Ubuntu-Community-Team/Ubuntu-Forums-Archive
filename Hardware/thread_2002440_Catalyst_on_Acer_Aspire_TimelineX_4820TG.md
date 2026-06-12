---
title: "Catalyst on Acer Aspire TimelineX 4820TG"
date: 2012-06-12
forum: Hardware
---

### Post by Dero06 on 2012-06-12
Hello,

I just did a fresh install of Ubuntu 12.04 x64 on my laptop. After updateing the system I installed the ATI Catalyst driver with the script from the official ATI website. This caused my X server to throw an error. It couldn't detect any Screens in the configuration (even if there was one declared). When deleting the generated xorg.conf i could once again start my system, but I keep receiving error messages like

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12

Since I use JavaFX for some Java Applications I can't run them on my laptop. Does anyone know how to fix this problem?

Greetings
Dero

---

### Post by Redblade20XX on 2012-06-12
Take a look here : [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)

-Red

---

### Post by Dero06 on 2012-06-18
Alright I did exactly what the tutorial told me to. With the minimal configuration file I get the following output:

```
$ fglrxinfo 
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12
```when running
```
$ sudo amdconfig --initial -f
```and rebooting my system afterwards I get a message that low graphics mode will be activated. Troubleshooting the error tells me, that the X Server can't find a monitor. The config file is the following:

```
Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        Monitor    "aticonfig-Monitor[0]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection
```Any suggestions?

---

### Post by Yellow Pasque on 2012-06-18
What video do you have?
```
lspci | grep -i vga
```

Extra credit: post/pastebin your /var/log/Xorg.0.log

---

### Post by Dero06 on 2012-06-18
```
$ lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Manhattan [Mobility Radeon HD 5400 Series]
```

Xorg.0.log is here: [http://pastebin.com/TKn67dhM](http://pastebin.com/TKn67dhM)

---

### Post by Yellow Pasque on 2012-06-18
You've got a hybrid Intel/ATI graphics setup with a mux (and my sympathies). If you want your system working again, uninstall Catalyst: [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Removing_Catalyst.2Ffglrx)

If you want to switch back and forth between the two GPU's see: [http://ubuntuforums.org/showpost.php?p=12034530&postcount=17](http://ubuntuforums.org/showpost.php?p=12034530&postcount=17)

---

### Post by Dero06 on 2012-06-19
For any reason vgaswitcheroo is not installed  in my kernel ... I'm currently looking for a  tutorial to add it ...

---

### Post by daniel488 on 2012-09-27
Hi,

any progress with Catalyst driver? If I install 12.8 or 12.6 then Ubuntu wants to start in low-graphic mode.

Here are my cards in 4820TG:
```
daniel@dan-PC:~$ lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Madison [Radeon HD 5000M Series]

```

On Ubuntu 11.04 I had 11.8 version of Catalyst and it worked.

---

### Post by QIII on 2012-09-27
Probably should have started your own thread for visibility ....

I'm surprised it worked before, since Intel/ATI hybrid operation with the ATI driver requires a mux-less setup (series 6xxx and above, generally).

No, the 12.8 driver will probably still not work for 5xxx series GPUs.

---

### Post by daniel488 on 2012-09-27
Ok, I will start.

BTW it is a little confusing with card name. Ubuntu detects it as HD 5000M series. But it is HD 6550M. Is it possible to find info that it is renamed HD 5650M... but it's not exactly the same.
So is it muxing? I'm not sure. It depends on that Madison chip?

---

### Post by Yellow Pasque on 2012-09-29
It's a rebadged HD5000-series. Madison is a Redwood-based chip: [http://en.wikipedia.org/wiki/Comparison_of_ATI_graphics_processing_units#Mobility_Radeon_HD_5xxx_Series](http://en.wikipedia.org/wiki/Comparison_of_ATI_graphics_processing_units#Mobility_Radeon_HD_5xxx_Series)

---

