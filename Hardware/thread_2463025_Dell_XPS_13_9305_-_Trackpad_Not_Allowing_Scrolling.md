---
title: "Dell XPS 13 9305 - Trackpad Not Allowing Scrolling"
date: 2021-06-01
forum: Hardware
---

### Post by slimpickens142 on 2021-06-01
Hello,

I recently purchased a Dell XPS 13 9305 pre-loaded with Windows - but am now dual booting with Ubuntu 20.04.2 LTS. Mostly everything is working out-of-the-box, but I'm unable to two-finger scroll on the trackpad. I tried some of the steps on this [Dell help article]("https://www.dell.com/support/kbdoc/en-us/000150104/precision-xps-ubuntu-general-touchpad-mouse-issue-fix") but to no avail. When I try the recommended "sudo apt-get install --install-recommends linux-generic-hwe-16.04 xserver-xorg-hwe-16.04 " into a terminal, I get the following for output:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-generic-hwe-16.04
E: Couldn't find any package by glob 'linux-generic-hwe-16.04'
E: Couldn't find any package by regex 'linux-generic-hwe-16.04'
E: Unable to locate package xserver-xorg-hwe-16.04
E: Couldn't find any package by glob 'xserver-xorg-hwe-16.04'
E: Couldn't find any package by regex 'xserver-xorg-hwe-16.04'

I didn't go much further with that article because I don't think the issue is Ubuntu recognizing two trackpads...I think it is recognizing none, based off running an "xinput list". Here is the output:

Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=12    [slave  pointer  (2)]
&#9116;   &#8627; Magic Mouse 2 Mouse                         id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Integrated_Webcam_HD: Integrate             id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=7    [slave  keyboard (3)]
    &#8627; Intel HID events                            id=9    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]

I also don't think the issue is faulty hardware, because the trackpad works as expected when I boot to Windows. Any ideas on what I might try next out there?

---

### Post by dddman on 2021-06-01
16.04 is an old release and will not work on 20.04.  Had you  managed to install it you probably would of borked your computer.

I'm running a Dell 5290 and touch pad worked out of the box, touchscreen worked 95%.
Here's a link for touch
[https://help.ubuntu.com/stable/ubuntu-help/mouse.html.en](https://help.ubuntu.com/stable/ubuntu-help/mouse.html.en)

There's a GUI for changing two finger, it's in the software store.
[ATTACH=CONFIG]288590[/ATTACH]

got a hit
Think I (we) hit on it.  Looking like you do need to install HWE, but for 20.10.  Seems your xps is better supported with HWE.
[https://sorenpoulsen.com/dell-xps-13-9305-with-ubuntu-20042-lts](https://sorenpoulsen.com/dell-xps-13-9305-with-ubuntu-20042-lts)

And on a side note
I run Ubuntu in Virtualbox and suspect the win10 buffer help my real world experience.

---

### Post by slimpickens142 on 2021-06-01
Hi dddman,

Thanks for taking the time and information. Sorry if it was unclear, but I don't even think the OS is recognizing the touchpad hardware (which is why I pasted the "xinput list" command output). Also, if I go to Settings > Mouse & Trackpad, no trackpad is listed. So I'm don't think the app you recommend is going to work. 

Also, based on the Soren Poulsen [website]("https://sorenpoulsen.com/dell-xps-13-9305-with-ubuntu-20042-lts"), it's not clear to me what I need to do to install HWE (assuming it's not already installed). He recommends going through the standard Ubuntu installation process which I did.

---

