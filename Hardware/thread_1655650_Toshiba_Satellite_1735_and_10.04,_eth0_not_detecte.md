---
title: "Toshiba Satellite 1735 and 10.04, eth0 not detected"
date: 2010-12-29
forum: Hardware
---

### Post by tech7 on 2010-12-29
Hey everybody..  I've installed 10.04 lucid on a Toshiba Satellite 1735.  

Awesome!

The only problem is; ethernet port didn't install..

I'm kinda stumped as to where to go from here and ethernet is pretty important on this computer as my aunt has never had a lan card on it and will use it plugged in..

Here's what I got on lspci in terminal:
```
awesome@awesome-laptop:~$ sudo lspci
[sudo] password for awesome: 
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:04.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:04.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia audio controller: Cirrus Logic Crystal CS4281 PCI Audio (rev 01)
00:10.0 Communication controller: Agere Systems LT WinModem
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
awesome@awesome-laptop:~$ 
```

Does anybody have an idea what I need to do next?

Any suggestions would be greatly appreciated!!

Thanks a mil!!

---

### Post by IcarusR on 2010-12-30
Is there an option to enable / disable ethernet in the bios ? If so is it enabled ?
Is there an Fn combination, or other key, to switch ethernet on / off ?

Try booting from live cd & check to see if ethernet is recognised.

If neither works it is possible your ethernet port is faulty.

---

### Post by tech7 on 2010-12-30
I could not find anything in the bios remotely related to ethernet.  

I don't know of or see any suggestions on any Fn combinations that would enable or disable it either.

None of the keys on the outside control it.

I've googled for key combinations or anything ethernet that pertains to this computer and can't find anything to suggest that a key combination exists.  

I'm inclined to believe that it must be a driver issue.  

I'm still working my butt off on this though.  I need to get internet running on this computer.  Lucid is running awesome on it and my aunt will love it if I can get at least ethernet to work on it...   Anybody have any suggestions???

---

### Post by IcarusR on 2010-12-31
> I'm inclined to believe that it must be a driver issue.


Thinking about it I don't remember these laptops having built in Ethernet.
It does however have built in modem. 
Are you sure you are not getting confused with the modem port & ethernet port. The latter will fit in the former but not work.

Exactly what type of Ethernet are we talking about ? USB, PCMCIA etc ?

---

### Post by peyre on 2011-03-11
tech7, **martian** is a program (part of the linmodem project) that's designed to get Agere winmodems to work.  I've just finished getting it up and running on my Toshiba Tecra 8100.  Unfortunately I'm no expert, but I'll paste in here what I wrote down; maybe it'll help you.

(This was in Lubuntu 10.04.)

I installed **KPPP**, **martian-modem**, and **martian-modem-source**. 
I also installed **gnome-ppp**, but it was useless: it kept hanging when I tried to detect the modem.  I eventually removed it altogether.

I ran **sudo martian_modem**, which I think started martian running.
At one point I ran **sudo m-a a-i martian-modem** (which built martian) and **sudo m-a -f get martian-modem**.  At some point in here, something told me what device the modem was assigned to: **/dev/ttySM0**.  (Apparently, ttyS**_M_**x is how martian assigns ports.)

At another point I ran **sudo apt-get update** and **sudo apt-get -s install linux-kernel-devel**.  At yet another point I ran **sudo apt-get install module-assistant**.

At the end, I installed hwinfo, which I think installs the Hardware Drivers utility (installed on Ubuntu and Xubuntu by default) that controls third-party and proprietary drivers.  When I ran that utility, I saw my modem in there and active, as the Agere 164x dsp driver.

KPPP doesn't have an option for /dev/ttySM0, so I linked it to /dev/modem:
  sudo ln -s /dev/ttySM0 /dev/modem

I was now able to select /dev/modem and get KPPP to recognize it.  Woohoo!

---------------------------

After that initial success, I was never able to get the modem working, so I brought did some more messing with it.  In the end, I found that in order to use the modem, I needed a script on the Desktop which reads as follows:
```

gksudo martian_modem
gksudo ln -s /dev/ttySM0 /dev/modem
/usr/bin/kppp
```

The last line, of course, brings up KPPP--both to save me a step and to keep me from opening KPPP prematurely.  If I want to dial out, I just double-click on the icon, and it gets the modem ready and opens the dial utility for me to use--slick.

---

