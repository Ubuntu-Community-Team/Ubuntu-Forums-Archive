---
title: "ATI Mobility 9000 (M9) and fglrx"
date: 2006-01-16
forum: Hardware &amp; Laptops
---

### Post by Gaferion on 2006-01-16
I have a Dell Latitude D600 that came with an ATI Mobility 9000 (M9) with 32MB video RAM.  I have followed several different HOWTOs on installing fglrx drivers for hardware accelerated support for ATI cards.  The problem is that everytime and every which way I install it I get the following
```

gaferion@Sakura:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: FireMV 2400 PCI DDR Generic
OpenGL version string: 1.3.1030 (X4.3.0-8.20.8)
```
fglrxinfo shows that I have a FireMV2400 and uses drivers for that yet ...
```

gaferion@Sakura:~$ lspci -X
PCI:0:0:0 Host bridge: Intel Corp. 82855PM Processor to I/O Controller
PCI:0:1:0 PCI bridge: Intel Corp. 82855PM Processor to AGP Controller
PCI:0:29:0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
PCI:0:29:1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
PCI:0:29:2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
PCI:0:29:7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller
PCI:0:30:0 PCI bridge: Intel Corp. 82801 PCI Bridge
PCI:0:31:0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller
PCI:0:31:1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller
PCI:0:31:5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
PCI:1:0:0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [Radeon Mobility 9000 M9]
PCI:2:0:0 Ethernet controller: Broadcom Corporation NetXtreme BCM5702X Gigabit Ethernet
PCI:2:1:0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller
PCI:2:1:1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller

```
as you can see lspci displays that I have the Mobility 9000

I have found a few other people on these boards that have the exact same problem, but no one responded to their threads or really helped them to find a solution.  I have scoured Google and Google Groups for answers, but have found none.  I have tried multiple variations of of HOWTOs including:

[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)
[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)
[https://wiki.ubuntu.com/BinaryDriverHowto](https://wiki.ubuntu.com/BinaryDriverHowto)

and there is also another one I tried that I am sure someone will tell me ;-)

I've even re-installed and tried different guides just incase a previous installation was screwing up another one.  :-\

Any help is appriciated.  I am just worried that the 'driver' it is using is not allowing my cards 'full potential' to shine.

If you need any other information, let me know and I will provide it.

Thank you,
Jake

PS:  I have also tried setting the ChipID in the xorg.conf in the appropriate section to 0x4c66 which is the ChipID for this card, seems to make no difference.

---

### Post by cucamelsmd15 on 2006-01-16
What frame rate do you get when you do glxgears from the prompt? Just as a reference, my IBM has the same card, and I usually turn around 1500fps. If its between 1200-1500, Id say thats pretty good. Anything lower than 1000, and Id say that its the wrong driver.

---

### Post by Prefader on 2006-01-16
The same thing happens for me.  I get good framerates though, far better than the Mesa driver, and I get to use the nice pretty control panel for TV-Out switching.

I think it detects the chip just fine, those are just the drivers it uses.  I get the feeling that there are minimal differences between the Radeon and FireGL GPUs - I recall using the catalyst drivers with a FireGL card that just wouldn't behave on one Windows system, and it was remarkably easy to trick them into installing.  Worked like a charm, too.

Now, if only suspend-to-ram really was fixed, like the release notes say it is.  :(

---

### Post by cucamelsmd15 on 2006-01-16
[QUOTE=Prefader]The same thing happens for me.  I get good framerates though, far better than the Mesa driver, and I get to use the nice pretty control panel for TV-Out switching.

I think it detects the chip just fine, those are just the drivers it uses.  I get the feeling that there are minimal differences between the Radeon and FireGL GPUs - I recall using the catalyst drivers with a FireGL card that just wouldn't behave on one Windows system, and it was remarkably easy to trick them into installing.  Worked like a charm, too.

Now, if only suspend-to-ram really was fixed, like the release notes say it is.  :([/QUOTE]

Works fine for me.

---

### Post by Gaferion on 2006-01-17
And here I was thinking I was doing something wrong the whole time ...

Yes, in glxgears I get 1300+ and in fgl_glxgears I get from 130-200

If that seems correct then I will stop trying to 'figure' this out.  ;-)

Thnx everyone for taking the time to respond.

---

### Post by kubuntu2k6 on 2006-02-14
Hey Gaferion.. here I get about 300 fps with fgl_glxgears and glxgears is so slow I get nothing.. it takes 5 sec just for the the red gear-wheel to rotate once :evil: 
Same card ATI Mobility 9000 (M9) and get the same FireMV 2400 PCI DDR Generic output with fglrxinfo... so could you pls post which method you used to get it working?

---

### Post by weizilla on 2006-02-16
i'm having the same problem.
has anyone found a solution?

---

### Post by Gaferion on 2006-02-21
@kubuntu2k6
I dont remember exactly which guide I followed, but I do know all the guides I followed had the same results for me.  Maybe you can try out the following to see if one works better then the other for you.

[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)
I tried both sections

Also: [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584) (uses ati drivers also, cant remember how different process of actually using them is)

But, I guess besides it displaying FireMV2400 I didnt really have any problems according to everyone who is saying my fps are about normal ...

@weizilla
There is no solution really to correcting the OpenGL renderer string: FireMV 2400 PCI DDR Generic ... if that displays and you get fps I was getting, I guess its working.  Otherwise, following my advice to kubuntu2k6

---

