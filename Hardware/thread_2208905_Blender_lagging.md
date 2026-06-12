---
title: "Blender lagging"
date: 2014-03-02
forum: Hardware
---

### Post by jechadwell99 on 2014-03-02
I have a HP G62-34OUS notebook and have recently installed Ubuntu 12.04 on it. Everything's working fine- except for the fact that one program (Blender) sometimes lags a little. After a little research, I have found that maybe I need to install a proprietry driver. If I do need to, then it doesn't show up in the Additional Drivers Menu. Please help me! 

This is what I get when I enter: 
*lspci -nn | grep VGA*
I get:
*01:05.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RS880M [Mobility Radeon HD 4225/4250] [1002:9712]*

And when I enter
*lspci -nnk | grep -i vga -A3*
I get:
[I]01:05.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RS880M [Mobility Radeon HD 4225/4250] [1002:9712]
    Subsystem: Hewlett-Packard Company Device [103c:1444]
    Kernel driver in use: radeon
    Kernel modules: radeon[/I]

Do I need to do anything to get my graphics card working? Or is it already working? How do I tell? 

Sorry for the questions. I don't really know what I'm doing with Ubuntu.

PS. I am fully aware that the problem could be in blender. Thanks.

---

### Post by varunendra on 2014-03-03
You already have a suitable Open Source driver (radeon) installed and working. If the "Additional Driver" menu doesn't show any proprietary driver available, then there is probably none available for this card (it seems an old one).

You may try to search AMD/ATI website to see if they offer linux driver for this card, and if you find any, report back with its link and someone should be able to suggest whether you should go for it or not. Although as far as I know, AMD dropped support for many of their older cards, probably that's why you don't get any offer from "Additional Drivers" menu.

If there is no proprietary driver available (usually "fglrx"), there is probably nothing you can do about it.

---

### Post by Mark Phelps on 2014-03-03
Sorry, but AMD dropped fglrx driver support for your card a while back.  The default Radeon drivers that work on it now are the ones you have already installed.

---

