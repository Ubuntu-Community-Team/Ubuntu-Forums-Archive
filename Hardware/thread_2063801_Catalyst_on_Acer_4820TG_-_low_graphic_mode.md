---
title: "Catalyst on Acer 4820TG - low graphic mode"
date: 2012-09-27
forum: Hardware
---

### Post by daniel488 on 2012-09-27
Hi,

I have Acer 4820TG notebook. It has two cards:
```
daniel@dan-PC:~$ lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Madison [Radeon HD 5000M Series]
```
This Radeon is HD 6550M, but Ubuntu see it as above (maybe because of Madison chip?).

I just moved from Ubuntu 11.04 64bit to 12.04 64bit (fresh instalation).
I had Catalyst 11.8 on 11.04 and I could switch between cards (needed to reboot if wanted the changes take affect).

Now I tried to install the newest Catalyst - 12.8, but after reboot Ubuntu wants to start in low-graphic mode. I tried also 12.6 version and there was the same effect. After installing 11.8, Ubuntu started but Catlyst Control Center didn't wanted to start (but it didn't tell that driver is missing) and I tried to switch card with ```
sudo aticonfig --px-igpu 
```, but was some problem (unfortunately don't remember). ```
daniel@dan-PC:~$ aticonfig --list-adapters
* 0. 01:00.0 AMD Radeon HD 6500M/5600/5700 Series

* - Default adapter

``` showed two cards.

I read that for 12.04 OS, 12.4 driver is the most appropriate version.
I tried follow these instructions: [http://ubuntuforums.org/showthread.php?t=1930450]("http://ubuntuforums.org/showthread.php?t=1930450") and [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide") but still "low-graphic mode".

Could you give me some suggestions what to do?

---

### Post by QIII on 2012-09-27
Thanks for starting the new thread.

OK.  Your 6550M is basically nothing more than an over clocked and over volted 5650 with a new name, which means that you have a 5xxx series GPU.

That means, unfortunately, that attempting to use any of the the solutions you have looked at (or the one in the wiki in my signature) will not work.  Everything I have come across requires a 6xxx or greater series card.

All is not lost, however.  You can uninstall the fglrx driver and use the open source Radeon driver with vgaswitcheroo.  You won't get all the benefits of your ATI GPU as you would with the proprietary driver, but at least you can switch between the two.

The open source driver sometimes has a tendency to draw a lot of power and generate a lot of heat, which means reduced battery life.

Why this system worked with earlier drivers I don't know, unless the muxed/muxless issue was not a problem.

---

### Post by daniel488 on 2012-09-28
Thanks for reply. 

I have my Ubuntu 11.04 partition backup and now need to decide what is better: new Ubuntu with problems you described or my old working.

To be honest I very very rarely use Radeon card on Ubuntu. Maybe I could use often but HDMI doesn't work :mad:
So ATI benefits are not much important for me. 
But that about tendencies to reduce battery life, do you know when it happens? During using ATI or integrated card? If integrated, then it is good reason to stay with old Ubuntu (depends also how frequent is it). 

I have just restored 11.04 and work on it because I couldn't put up with fan noise :). I can give some configs/logs if it can help to understand why it works.

Cheers,
Daniel

---

