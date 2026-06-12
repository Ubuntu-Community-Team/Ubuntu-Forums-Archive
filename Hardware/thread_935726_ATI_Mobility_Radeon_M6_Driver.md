---
title: "ATI Mobility Radeon M6 Driver"
date: 2008-10-02
forum: Hardware
---

### Post by Xhip on 2008-10-02
Hello to all!

I'm new here and I would like to ask a question... I'm completely desperate to solve this problem, and I would be very grateful if you could help on this... 

I recently kicked off Windows and turned to Linux on full-time, choosing Xubuntu as the only OS on my machine. I was trying to configure my graphics card, a very important step forward, but I found several problems on my way...

It's an ATI Mobility Radeon M6 (LY too, I think...) and I tried everything to see a driver name appearing in "/etc/X11/xorg.conf", but I had no success... 

I installed the ATI binary X.Org driver package, but nothing appeared there... I tried the 'aticonfig --initial' command, but it says there is no driver name in that file...

Here is the graphics section that appears on the file:

[PHP]
Section "Device"
        Identifier      "Configured Video Device"
EndSection
[/PHP]

I don't know where to get a correct driver for my graphics card, and I know that it is an older card, but I would appreciate all the help I could get on this... :) I already saw some topics here in the forum about this stuff, and a driver usually appears in that file... How can I get to that point?

Thank you for the help!
Best regards! :)

---

### Post by jocko on 2008-10-02
ATI's proprietary driver (fglrx) does not support such an old card, but the open source driver ("ati" or "radeon") does.

The open source driver is already installed by default in ubuntu, so there's NOTHING you need to do, the correct driver is activated by default on hardware it supports.
The reason the driver (or anything else) is not listed in xorg.conf is because xorg does not need a static configuration anymore.

---

### Post by Xhip on 2008-10-02
Thank you very much for the answer :)

But I still have few doubts: I assume that the open source driver you refer to is installed by default in xubuntu too, so the driver in general is already installed and activated, correct?. It makes sense, since I don't have any problems viewing my environment in 1024x768 resolution :)

But, now I have a new problem, related with 3D acceleration, in this topic:

[http://ubuntuforums.org/showthread.php?t=246746](http://ubuntuforums.org/showthread.php?t=246746)

On it, they assume I already have this portion of code on 'xorg.conf':

[PHP]
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection
[/PHP]

But I don't have it... Can I simply copy/paste the driver and busID lines to my 'xorg.conf' file, without any problem? And then can I change the driver name to 'radeon' like they do?

Thanks for the help!
Best regards! :)

---

### Post by iasenko on 2008-10-03
Hi, 
I have the same problem
here is the print of *lspci* command
```
 sudo lspci
```

```

...
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
...

```

but in the etc/X11/xorg.conf stays the same as in Xhip's conf.file :( 
I can't add any Visual Effects at all.
Any ideas how we can fix this?

---

### Post by jocko on 2008-10-06
> **Xhip said:**
> Thank you very much for the answer :)

But I still have few doubts: I assume that the open source driver you refer to is installed by default in xubuntu too, so the driver in general is already installed and activated, correct?. It makes sense, since I don't have any problems viewing my environment in 1024x768 resolution :)

But, now I have a new problem, related with 3D acceleration, in this topic:

[http://ubuntuforums.org/showthread.php?t=246746](http://ubuntuforums.org/showthread.php?t=246746)

On it, they assume I already have this portion of code on 'xorg.conf':

[php]
Section "Device"
    Identifier    "ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
    Driver        "ati"
    BusID        "PCI:1:0:0"
EndSection
[/php]But I don't have it... Can I simply copy/paste the driver and busID lines to my 'xorg.conf' file, without any problem? And then can I change the driver name to 'radeon' like they do?

Thanks for the help!
Best regards! :)

> **iasenko said:**
> Hi, 
I have the same problem
here is the print of *lspci* command
```
 sudo lspci
``````

...
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
...

```but in the etc/X11/xorg.conf stays the same as in Xhip's conf.file :( 
I can't add any Visual Effects at all.
Any ideas how we can fix this?

As I said, Xorg no longer needs any static configuration, which is why the xorg.conf is mostly empty, but it will still try to use any settings you put in there.
So just add whatever options you think you need to xorg.conf.

---

