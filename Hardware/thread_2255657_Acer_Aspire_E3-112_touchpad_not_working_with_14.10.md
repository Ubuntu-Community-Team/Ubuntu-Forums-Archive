---
title: "Acer Aspire E3-112 touchpad not working with 14.10"
date: 2014-12-06
forum: Hardware
---

### Post by simonprosser on 2014-12-06
Hi,

Can anyone help? I have an Acer Aspire E3-112 (E11 or ES1) and I'm booting 14.10 Kubuntu and my touchpad isn't working (same thing happens with Xubuntu and Ubuntu). Anyone else having the same problem? I've tried googling everywhere but can't find a solution that works.

I can plug in a USB mouse and it works fine. From what I can see everything else works perfectly. I'm kinda new to linux btw. Any ideas?

Simon.

---

### Post by simonprosser on 2014-12-14
So I've been googling around for the last week on this, and nothing I can find is helping. I think the problem I have is that it's not getting detected. When I goto system settings -> input devices -> touchpas, there's a red box at the top that says "Synaptics driver is not installed (or is not used)"

simon@Aspire-E3-112:~$ xinput list
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Power Button                              id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=9    [slave  keyboard (3)]
    &#8627; HD WebCam                                 id=12   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=13   [slave  keyboard (3)]
    &#8627; Acer WMI hotkeys                          id=14   [slave  keyboard (3)]

any help much appreciated this is driving me nuts!!!!

---

### Post by simonprosser on 2014-12-14
Just incase someone else has this problem, a quick update. In BIOS there's a choice between basic and advanced touchpad. I don't know the difference but mine was set to advanced. I changed it to basic and it worked fine!

---

### Post by Edvards on 2015-01-25
Hi,

Change in Bios touchpad to basic.

Double check if you got your settings right. Go to Settings System > Mouse and TouchPad.

See if touchpad is turned on and tick boxes bellow, to enable two finger scroll and other things you need.

Another thing, try to press Fn + F7. This combination disables or enables touchpad.

Hope it helped.

Cheers,

Ed

---

### Post by Gordonbp531 on 2015-01-27
> **simonprosser said:**
> Just incase someone else has this problem, a quick update. In BIOS there's a choice between basic and advanced touchpad. I don't know the difference but mine was set to advanced. I changed it to basic and it worked fine!

I also have an Axer Aspire E3 - there's no function in the BIOS for changing the touchpad settings. Where did you see this function?

---

### Post by simonprosser on 2015-02-08
It's under the main tab (Touchpad [Basic]). Maybe it's because I turned off UEFI (maybe you have it on). Check that. Or it could be because I have a newer BIOS version (v1.08). Hope that helps!

---

