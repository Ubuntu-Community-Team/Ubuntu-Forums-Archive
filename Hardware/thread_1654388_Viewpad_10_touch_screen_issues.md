---
title: "Viewpad 10 touch screen issues"
date: 2010-12-28
forum: Hardware
---

### Post by ojdon on 2010-12-28
[SIZE="4"][COLOR="Red"]**EDIT: **[/COLOR] **Read this guide on how to get Ubuntu 10.10 working on the Viewpad 10**
[Ubuntu 10.10 on the Viewpad 10]("http://www.ollie-reardon.co.uk/ubuntu-10-10-viewpad-10/")[/SIZE]

Hi there, I've recently got a Viewpad 10. I'm interested in getting UNE 10.10 on there for it's unity interface. The only problem is is that the touch screen doesn't seem to be working correctly, if I touch the screen with one finger nothing seems to happen but when I press two fingers on the screen the cursor would go to either of the two fingers, does anyone know a possible fix for this? I'd be able to navigate since I have a usb mouse and keyboard handy.

Thanks!

---

### Post by aldo7a on 2010-12-28
me 2
anybody can help?

xinput -list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ILITEK ILITEK Multi-Touch                   id=9    [slave  pointer  (2)]
&#9116;   &#8627; HID 04b3:3107                               id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Gotek                                       id=10    [slave  keyboard (3)]
    &#8627; CHESEN USB Keyboard                         id=11    [slave  keyboard (3)]
    &#8627; CHESEN USB Keyboard                         id=12    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=14    [slave  keyboard (3)]

---

### Post by ojdon on 2010-12-29
Does anyone need any further information in order to find a possible solution. The same issue still occurs under the alpha 1 build of 11.04.

---

### Post by aldo7a on 2010-12-29
TEGA v2 ntablet which looks and has the same spec

[http://forum.novatech.co.uk/showthread.php?t=23407](http://forum.novatech.co.uk/showthread.php?t=23407)

[http://www.tegav2.com/forum/viewtopic.php?f=23&t=9](http://www.tegav2.com/forum/viewtopic.php?f=23&t=9)

We want some help from experts

---

### Post by ojdon on 2011-01-01
Bump! 

Any help?

---

### Post by aldo7a on 2011-01-02
any help plz

cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input2
U: Uniq=
H: Handlers=sysrq kbd event2 
B: EV=120013
B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=3
B: KEY=3e000b 0 0 0 0 0 0 0

I: Bus=0003 Vendor=222a Product=0001 Version=0210
N: Name="ILITEK ILITEK Multi-Touch"
P: Phys=usb-0000:00:1d.3-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/input/input4
U: Uniq=
H: Handlers=mouse0 event4 
B: EV=1b
B: KEY=407 0 10000 0 0 0 0 0 0 0 0
B: ABS=700 ff
B: MSC=10

I: Bus=0003 Vendor=0a81 Product=0101 Version=0110
N: Name="CHESEN USB Keyboard"
P: Phys=usb-0000:00:1d.7-2.2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2.2/1-2.2:1.0/input/input5
U: Uniq=
H: Handlers=sysrq kbd event5 
B: EV=120013
B: KEY=10000 7 ff9f207a c14057ff febeffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=1f

I: Bus=0003 Vendor=0a81 Product=0101 Version=0110
N: Name="CHESEN USB Keyboard"
P: Phys=usb-0000:00:1d.7-2.2/input1
S: Sysfs=/devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2.2/1-2.2:1.1/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=13
B: KEY=2020000 3878 d801d001 1e0000 0 0 0
B: MSC=10

I: Bus=0003 Vendor=04b3 Product=3107 Version=0100
N: Name="HID 04b3:3107"
P: Phys=usb-0000:00:1d.7-2.3/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2.3/1-2.3:1.0/input/input7
U: Uniq=
H: Handlers=mouse1 event7 
B: EV=17
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10

I: Bus=0003 Vendor=1700 Product=013a Version=0000
N: Name="Gotek"
P: Phys=usb-0000:00:1d.7-1/button
S: Sysfs=/devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1:1.0/input/input8
U: Uniq=
H: Handlers=kbd event8 
B: EV=3
B: KEY=100000 0 0 0 0 0 0

---

### Post by ojdon on 2011-01-03
Anyone???

It seems to work a little bit more in Fedora/Meego but it seems too sensitive when pressing on something such as a key on an on screen keyboard.

It's also labelled as "Hanvon 10.1" if that's any help.

---

### Post by EnnoErlangen on 2011-01-04
I have the same issue with UNE 10.10. Windows 7 is working fine but having an Ubuntu running on the device would be really nice! Sadly, atm I have no time to dig for the bug in the driver to find the problem. So I'm also very interested in a solution.

---

### Post by ojdon on 2011-01-05
Can anyone help?

---

### Post by ojdon on 2011-01-15
Still interested in a fix...

---

### Post by h4uw1n3 on 2011-01-17
this is happened to me also....
any idea to fix it? i have to use 2finger to be able make it move... everytime i put the first finger, ubuntu start executing the command.... before i move the cursor.... windows 7 works perfectly...

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; GASIA GASIA USB KB Pro                      id=11    [slave  pointer  (2)]
&#9116;   &#8627; Hanvon      10.1                            id=12    [slave  pointer  (2)]
&#9116;   &#8627; ISV Inc. ISV Inc. DOYAK-3 -4 Ver 1.2        id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; GASIA GASIA USB KB Pro                      id=10    [slave  keyboard (3)]
    &#8627; USB2.0 Camera                               id=13    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=15    [slave  keyboard (3)]

any idea?

---

### Post by wbulot on 2011-01-20
Still interested in a fix...

---

### Post by wbulot on 2011-01-20
Still interested in a fix...

---

### Post by wbulot on 2011-01-20
Still interested in a fix...

---

### Post by h4uw1n3 on 2011-01-21
Still no answer? :popcorn:

---

### Post by ojdon on 2011-01-22
Doesn't anyone have any idea?

---

### Post by h4uw1n3 on 2011-01-27
\\:D/............ still no one?? --->

---

### Post by h4uw1n3 on 2011-01-27
i just installed Meego with linux vmlinuz 2.6.35.3-10.3-netbook

the touchscreen works.... maybe not so perfect... so i take an assumption...if we update the kernel to 2.6.35.3 maybe it's gonna work?

what do u thinnk? i don't try it yet... cause i don't even know how to update this ubuntu...
just starting using n getting know last december....

it's worth take a shoot... but when i trying search linux-img... i don't found this 2.6.35.3...
only 2.6.35
so do u have any idea,guys??? post a reply... :)

---

### Post by ojdon on 2011-01-28
> **h4uw1n3 said:**
> i just installed Meego with linux vmlinuz 2.6.35.3-10.3-netbook

the touchscreen works.... maybe not so perfect... so i take an assumption...if we update the kernel to 2.6.35.3 maybe it's gonna work?


Whenever I enabled the OSK in Meego whenever I input something it would be entered in a random number of times. Unless this has been fixed now?

---

### Post by h4uw1n3 on 2011-01-28
> **ojdon said:**
> Whenever I enabled the OSK in Meego whenever I input something it would be entered in a random number of times. Unless this has been fixed now?

yeah...i just try it... u'r right... last time i didn't used the OSK... so i don't know...
have u try android Hanvon? this touchscreen driver works better than meego... stable..
is that possible applying the driver from this android to linux? do you have any idea.... :lolflag:

---

### Post by ojdon on 2011-01-31
Through using the Root Explorer app on Android it is pretty much a ordinary Linux distribution. Though I'm sure there are many technical differences... 

If anyone would find any files useful from the Android-x86 installation then I'd be able to grab them for you.

---

### Post by h4uw1n3 on 2011-02-21
still got no answer.... lol....
give up? :) i just keep it 2 os...

still hoping.... :p

---

### Post by ojdon on 2011-02-23
Someone on twitter linked me to this:

[http://lii-enac.fr/en/architecture/linux-input/multitouch-devices.html](http://lii-enac.fr/en/architecture/linux-input/multitouch-devices.html)

Is this any help to get Linux on the Viewpad 10?

---

### Post by h4uw1n3 on 2011-02-23
> **ojdon said:**
> Someone on twitter linked me to this:

[http://lii-enac.fr/en/architecture/linux-input/multitouch-devices.html](http://lii-enac.fr/en/architecture/linux-input/multitouch-devices.html)

Is this any help to get Linux on the Viewpad 10?


it seems like multitouch driver....but how to apply it? any idea? :lolflag:

---

### Post by ojdon on 2011-02-23
No idea, since I haven't looked around yet. Does anyone have any guidance?

---

### Post by ojdon on 2011-02-26
Finally got around to taking a look at this, I've wrote a guide on how to do it. It should take you basically through it all step by step:

[Ubuntu 10.10 on the Viewpad 10]("http://ollie-reardon.co.cc/?p=182")

Hope you enjoy Ubuntu on your Viewpad 10! 

...Going to have a stab at fixing up Fedora and Meego too when I get the chance... And when I get some WiFi access.

---

### Post by h4uw1n3 on 2011-02-27
> **ojdon said:**
> Finally got around to taking a look at this, I've wrote a guide on how to do it. It should take you basically through it all step by step:

[Ubuntu 10.10 on the Viewpad 10]("http://ollie-reardon.co.cc/?p=182")

Hope you enjoy Ubuntu on your Viewpad 10! 

...Going to have a stab at fixing up Fedora and Meego too when I get the chance... And when I get some WiFi access.

finally works.... thanks... :))
anyway... is yours work good? mine is work but, only one point touch... i trying with 2 finger, didn't works... but, it's a lot better... hehehe thanks
:)

---

### Post by ojdon on 2011-02-27
Meh, I don't use two point touch, I just wanted something that worked. No idea how to fix that either, unfortunately.

---

### Post by h4uw1n3 on 2011-02-28
hahaha that's more than enough... just wonder, you have other product... im not using hanvon or viewpad... and maybe your's work... heheheehehe

---

### Post by ojdon on 2011-02-28
It's not my work, I just wrote up a tutorial on how to do stuff, the drivers work for several multi-touch touch screens. :) But glad it helps anyway.

---

