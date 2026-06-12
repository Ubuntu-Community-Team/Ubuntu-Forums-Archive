---
title: "Microsoft Wireless Optical Mouse 2.0 - no click!"
date: 2006-07-04
forum: Hardware &amp; Laptops
---

### Post by monomaniacpat on 2006-07-04
Hi there,

I've had problems with my wireless mouse ever since I got it - having originally run it under breezy. Basicaly, now and again it stops responding to clicks of the mouse buttons. It is an intermitent fault which can be a once-off or happen continuously.

I once read that updating hoary to the breezy kernel worked, but since I now have a fresh install of Dapper and still can't get it working, I wondered if anyone had any tips. I tried the logitech wireless mouse config, but it didn't seem to make any difference.

Thanks,

mono.

---

### Post by monomaniacpat on 2006-07-05
Can anyone offer me some assistance? =P~

---

### Post by Joey French on 2006-07-05
I have the same setup as you do, and my mouse works fine. However, this is the second of these that I have ownwd. The first one was really messed up bad, would jump to the edge of the screen, stop working, all kinds of problems. I took it back and got a replacement, no problems since. The only thing you have done is move to Dapper, correct?

Joey French

---

### Post by monomaniacpat on 2006-07-05
[QUOTE=Joey French]I have the same setup as you do, and my mouse works fine. However, this is the second of these that I have ownwd. The first one was really messed up bad, would jump to the edge of the screen, stop working, all kinds of problems. I took it back and got a replacement, no problems since. [B]The only thing you have done is move to Dapper, correct?
[/B]
Joey French[/QUOTE]

It doesnt work with Breezy or Dapper. As an extra piece of info, it is sharing it's usb connection with a Comfort Edition Kbd (an all-in-one package). It's cat device entry is:

```
I: Bus=0003 Vendor=045e Product=00e5 Version=0053
N: Name="Microsft Microsoft Wireless Optical Desktop&#65533; 2.20"
P: Phys=usb-0000:00:1d.2-1/input0
S: Sysfs=/class/input/input1
H: Handlers=mouse0 ts0 event1
B: EV=7
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=1c3
```

And here's the relevant xorg.conf entry:

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection
```

I have tried just PS/2 and evdev driver, but it doesn't solve the issue. I have used it on Windows, and this is not a problem. There is something wrong with dapper.

---

### Post by monomaniacpat on 2006-07-06
[/bumping!]

---

### Post by monomaniacpat on 2006-07-08
No one? No one at all? :(

---

### Post by K0LO on 2006-07-08
I have a very similar wireless mouse that is working fine with Dapper (Microsoft Wireless Optical Mouse 2.0).

The only difference that I see between our xorg.conf files is the "Protocol" line. I have the following:
```
 Option      "Protocol"          "ImPS/2"
```

This is what I see under "USB Devices" in KInfoCenter (I'm using KDE not Gnome):

```
Microsoft Wireless Optical Mouse® 1.0A
**Manufacturer:** Microsoft
*Class*            0 ((Defined at Interface Level))
*Subclass*         0
*Protocol*         0
*USB Version*      2.00
*VendorID*         0x45e (Microsoft Corp.)
*ProductID*        0x8c (Wireless Intellimouse Explorer 2.0)
*Revision*         0.56
*Speed*            1.5 Mbits/s
*Channels*         0
*Max. Packet Size* 0
```
How did you list the "cat device entry"?

---

### Post by monomaniacpat on 2006-07-12
K0LO:

OK, I changed it to ImPS/2, although I have done this before and it made no difference.

Here's my KInfo (I changed sessions):

```
Microsoft Wireless Optical Desktop® 2.20

Manufacturer: Microsft


Class
0
((Defined at Interface level))
Subclass
0
Protocol
0
USB Version
2.00

Vendor ID
0x45e
(Microsoft Corp.)
Product ID
0xe3
Revision
0.53

Speed
1.5 Mbit/s
Channels
0
Max. Packet Size
0[-
```

I can't remember the exact command, but I got the cat device entry from the terminal.

---

### Post by fancyclaps on 2006-07-12
Did you buy the mouse seperatly or was it part of a keyboard/mouse set?

-tl

---

### Post by monomaniacpat on 2006-07-12
As I stated above, it is part of the Microsoft Wireless Optical Desktop 2.20, although I know it as the Comfort Edition Keyboard.

---

### Post by matthew on 2006-07-12
Hmm.. I have the same keyboard/mouse combo and it works beautifully--has since Hoary (5.04) and still does today under Dapper (6.06). I'm at a loss to explain your problem or how to fix it. One silly, simple thing I haven't seen mentioned, however...have you checked the batteries in the mouse and keyboard and replaced them with known good ones? I'm guessing you probably have, but just in case you haven't you might want to try that. It's usually the obvious that is most easily overlooked, at least in my case. :)

---

### Post by monomaniacpat on 2006-07-12
Well it's been like this ever since I got it and it tracks fine and clicks the majority of the time, so I doubt it's the batteries, but what the hell...

---

### Post by monomaniacpat on 2006-07-15
I've had new batteries in there for a couple of days now and I still get the same problem ](*,)

---

### Post by monomaniacpat on 2006-09-24
OK, so I refreshed my sys from scratch recently and my mouse was working perfectly for the first time!

And then... I went and downloaded a kernel update. Is it possible that doing this has returned my mouse to its former useless state? It certainly is being very awkward.

Assuming this is the case, is there a way of reverting to the previous kernel or overwriting the new driver with the old one?

thanks,

mono.

---

### Post by glenn69 on 2006-10-08
I am having the same problem.  Batteries are new (that was my first assumption)  I even tried a different Linux MEPIS, but silly me it is an Ubuntu based Linux.  So, if the problem is in Ubuntu...well you know.

Mine is a wireless Microsoft....I guess it serves me right.  

My post is probably no help to you, other than as evidence that you ar not crazy.  Unless, of course, I am also crazy...then you are just not alone:)

---

### Post by monomaniacpat on 2006-10-12
> **glenn69 said:**
> I am having the same problem.  Batteries are new (that was my first assumption)  I even tried a different Linux MEPIS, but silly me it is an Ubuntu based Linux.  So, if the problem is in Ubuntu...well you know.

Mine is a wireless Microsoft....I guess it serves me right.  

My post is probably no help to you, other than as evidence that you ar not crazy.  Unless, of course, I am also crazy...then you are just not alone:)

Just to let you know that I've been using kernel 2.6.15-26-386 for a few weeks and haven't noticed any problems. It might just be that I've been lucky (I've only been using my computer for short periods.)

---

### Post by kamil212 on 2006-10-15
> **monomaniacpat said:**
> Just to let you know that I've been using kernel 2.6.15-26-386 for a few weeks and haven't noticed any problems. It might just be that I've been lucky (I've only been using my computer for short periods.)

Hi, got the same problem as you (maybe once a week, but I use it 12 hours a day). Wireless IntelliMouse Explorer 2.0
Must be a Microsoft thing, lol
I'm a complete linux n00b, kernel upgrade?
thanks,
-Kamil

---

### Post by monomaniacpat on 2006-10-16
Kamil:

If you want to find out what kernel you are running, enter the following in a terminal:

```
uname -r
```

The feedback will tell you the kernel number. If you have updated your system since installing dapper, you will most likely be on a newer kernel. You can select the kernel I am using by hitting escape in grub before ubuntu boots.

If you want to change permenantly which kernel boots, edit /boot/grub/menu.lst

It's apparently easy to do, but I haven't got round to it yet...

---

