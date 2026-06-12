---
title: "Ubuntu 8.10 running in low-graphics mode but cannot get to desktop"
date: 2009-03-21
forum: Hardware
---

### Post by Rainbow Road on 2009-03-21
I have been using Ubuntu on my laptop now for about 6 weeks and am very happy with it (install went very smoothly). I have introduced the kids to it who love Tuxmaths and Tuxpaint and since installed on a second laptop but am having problems installing on the desktop. Desktop has 512MB of RAM, an AMD Athlon 64 processor, onboard graphics and currently using PS2 keyboard and mouse (will hopefully switch to USB when running).
 
I am installing Ubuntu 8.10 (32 bit version) which I received through post from Canonical and was used to install on the laptops. It was getting as far as the white screen saying installing and then would freeze. I saw another post mentioning to use safe graphics mode which allowed it to install but it will not boot to the desktop.

As it is booting it displays the following messages:
Ubuntu is running in low-graphics mode. Your screen, graphics card, and input device settings could not be detected correctly.
You will need to configure these yourself.
[INDENT]What would you like to do now?
1. Run Ubuntu in low-graphics mode for just this session.
2. Reconfigure graphics.
3. Troubleshoot the error.[/INDENT]

I have tried the first 2 options which after additional menus eventually the computer will freeze on a black screen. The third option goes to following message:
[INDENT]What information would you like to review?
1. Review the xserver log file.
2. Review the startup errors.
3. Edit configuration file.
4. Archive configuration and logs.[/INDENT]

Is there anything I can change in the configuration file that would allow it to recognise the graphics drivers or anything else that might work. I have also tried running the Ubuntu Recovery from the boot list but couldn’t find anything that looked familiar.

According to the Belarc Adviser my graphics are ‘VIA/S3G Unichrome Pro IGP’.

Any help would be greatly appreciated as I am now sharing my laptop with the kids until desktop is sorted.

---

### Post by dmizer on 2009-03-23
Moved to hardware.

Please post the output of:
```
lspci
```

---

### Post by Rainbow Road on 2009-03-23
> **dmizer said:**
> 
Please post the output of:
```
lspci
```

:oops: Where would I find that?

---

### Post by Rainbow Road on 2009-03-23
Okay, here is the information from lspci:

[INDENT]C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)[/INDENT]

---

### Post by Rainbow Road on 2009-03-26
Just to update my previous post. I decised to try Hardy Heron and this time tried the Live CD first which worked. Installed and logged on successfully and then installed Edubuntu 8.04. Lesson learnt to try Live CDs first.

---

