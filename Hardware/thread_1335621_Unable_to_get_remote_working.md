---
title: "Unable to get remote working"
date: 2009-11-23
forum: Hardware
---

### Post by GuybrushCH on 2009-11-23
Hello to the community!
I'm writing because I've got a problem that I can't solve. I've spent a large amount of time lately reading all over the internet but I couldn't fix my issue. AND I'm new to the linux world so please be patient! =)

I've bought an "One for All PCMedia Remote", or better said, an URC 9040 made by Universal Electornics (on their website is called OFA PC Media Remote 9040 R00). It's a JP1 compatible remote control. It comes with a USB adapter (device ID 6e7:0004).
Since it's an universal remote I've tried it with my tv and it works just fine.

My problem comes with my pc. I'm building a mediacenter for my parents and I wanted to skip windows and use Ubuntu and XBMC Media Player. So I've installed Ubuntu 9.10 and the last version of XBMC.

But the remote control doesn't work. So I installed lirc and it behaves like a keyboard. The arrow key works like keyboard arrows and the ok button is ENTER, number keys are numbers... you got it I guess.

I've looked around to see if there were config files for my remote and I found them but they don't work. I've decided to program my keymaps but with no success at all. 
In irw I see that the keys are all sent to the computer as they show in the terminal...

How can I do that?? Can someone help me please?!!


My comupter specs:
Zotac ION ITX B Intel Atom N230 Mini ITX
3GB DDR2 Ram
nVidia ION graphic chipset
WD 640GB SATA2 HDD
Ubuntu 9.10
XBMC for linux 9.11 a2


the config files i've found:
```
begin remote
    name urc-9040
    bits 32
    begin codes
        1                    0x10002
        2                    0x10003
        3                    0x10004
        4                    0x10005
        5                    0x10006
        6                    0x10007
        7                    0x10008
        8                    0x10009
        9                    0x1000a
        0                    0x1000b
        Rew                  0x1001a
        Ffd                  0x1001b
        Play                 0x1002b
        Stop                 0x10034
        Pause                0x10035
        Prev                 0x1003d
        Next                 0x1003e
        Rec                  0x1003f
        Last                 0x10043
        Guide                0x10044
        Back                 0x1004a
        Goto                 0x1004e
        Logo                 0x10057
        Info                 0x10058
        Ok                   0x10060
        Menu                 0x10066
        Up                   0x10067
        Ch+                  0x10068
        Left                 0x10069
        Right                0x1006a
        Exit                 0x1006b
        Down                 0x1006c
        Ch-                  0x1006d
    end codes
end remote
```

---

### Post by GuybrushCH on 2009-11-24
Did I chose the wrong section? :confused:

---

