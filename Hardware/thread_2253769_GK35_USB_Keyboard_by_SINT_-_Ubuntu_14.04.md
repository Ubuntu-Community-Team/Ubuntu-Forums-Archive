---
title: "GK35 USB Keyboard by SINT - Ubuntu 14.04"
date: 2014-11-22
forum: Hardware
---

### Post by Paul_Berry on 2014-11-22
My old USB keyboard I get this from  xev | grep keysym    in terminal 

    state 0x0, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    state 0x8, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,

Thats correct...

My new USB keyboard I get this from ALT Left...and same for ALT right

    state 0x0, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    state 0x1, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,

Incorrect...its sending SHIFT code.. (same for Ctrl too..sends shift code)

So I Booted XP with new keyboard ... windows stated..new USB hardware..hardware now ready to use.. tried alt and ctrl and the both work as they should.  Im thinking this needs something extra loaded in Ubuntu for it to work... because it seems like windows added a driver or something for new USB hardware.  Any ideas???

---

### Post by lucasgz on 2014-12-05
Hi, i have the same problem with my usb keyboard Seisa.  It's detected as SONiX USB Keyboard.
It works fine on any windows, but on ubuntu all modifiers work as Shift, also the leds from NUM and CAPS don't work.

It also works fine while on grub2, but starts failing when ubuntu is loaded.


  my system Ubuntu 14.04, 32 bits
 -BIOS-
Date        : 12/12/2013
Vendor        : American Megatrends Inc. ([www.ami.com]("http://www.ami.com"))
Version        : 2202
-Board-
Name        : M5A97 LE R2.0
Vendor        : ASUSTeK COMPUTER INC. (SEAGATE, [www.seagate.com]("http://www.seagate.com"))

---

### Post by Paul_Berry on 2014-12-10
think my new keyboard is going in the bin..windows definitely loads a driver so that it functions correctly...without some ubuntu knowledge on what needs to be installed its an non started ...shame...it looked nice  :)

Bus 005 Device 004: ID 0c45:7603 Microdia

---

### Post by lucasgz on 2015-01-24
Still having problems with this. i'm using the keyboard along with the OnBoard program, but is really annoying  not having the ctrl atl and alt keys. :S
I wanna add that this keys work fine when i'm still inside grub at startup. I know it because in grub console i press ctrl+letter and doesn't appear a capital letter, unlike what happens once inside ubuntu.

```

**xinput **
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; **SONiX USB Keyboard       **                   id=9    [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse                  id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; SONiX USB Keyboard                          id=8    [slave  keyboard (3)]
    &#8627; Eee PC WMI hotkeys                          id=10    [slave  keyboard (3)]


:~$ **lsusb**
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: **ID 0c45:7603 Microdia **
Bus 004 Device 002: ID 0079:0006 DragonRise Inc. Generic USB Joystick
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 002: ID 125f:db8a A-DATA Technology Co., Ltd. 
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

---

### Post by Paul_Berry on 2015-02-06
yep i agree, this keyboard works fine and I have noticed the hardware in posts that do not relate to this particular problem. The way I see it is that we are missing a driver in ubuntu and nobody seems to be able to tell us which program to load or remove.

---

### Post by mariuscristianc+launchpad on 2015-04-29
> **Paul_Berry said:**
> yep i agree, this keyboard works fine and I have noticed the hardware in posts that do not relate to this particular problem. The way I see it is that we are missing a driver in ubuntu and nobody seems to be able to tell us which program to load or remove.Same issue for Cougar 200K keyboard.Solution for the next one that cames looking:[https://bitbucket.org/Swoogan/aziokbdor](https://bitbucket.org/Swoogan/aziokbdor) more indepth view:[http://swoogan.blogspot.ro/2014/09/azio-l70-keyboard-linux-driver.html](http://swoogan.blogspot.ro/2014/09/azio-l70-keyboard-linux-driver.html)

---

