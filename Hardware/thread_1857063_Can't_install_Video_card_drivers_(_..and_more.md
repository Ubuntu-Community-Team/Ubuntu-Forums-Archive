---
title: "Can't install Video card drivers :( ..and more"
date: 2011-10-09
forum: Hardware
---

### Post by bobdotexe on 2011-10-09
Hello I recently ordered a custom HP Pavilion Dv6t-se
it has a ATI Radeion (AMD Radeon HD 6700M Series) Switchable Graphics card(in fixed mode*)
The main problem I have is I am unable to install the drives for the card.
Ubuntu listed a "restricted driver" for it, so I installed that, and Ubuntu failed to load X upon restart. so I used 'video safe mode' and I was able to start but not run applications that require 3D such as minecraft. so I uninstalled the drivers, and restarted.
My system seems to work fine on the default drives that Preinstalled, I can go on youtube and watch video in HD with no skipping, and I can also display in the max resolution, and VGA and 
HDMI work fine too, but I am unable to mine craft or any other 3d applications such as billiards-GL.

Two minor other issues are My Built in SD card Reader dose not read any cards, and the fingerprint reader, is not recognized.
 (not a big deal)

I spent quite a bit of time on google looking up all of the problems (I found two different fingerprint reading programs but both did not see my reader {I forgot the names})

I even went to the ATI website and found the Drivers and downloaded them and installed manually, but this also did not work.

Could some one please help me?

Reports:
[lspci -v | less]("http://pastebin.com/t0bTys2A")

[MineCraft Error]("http://pastebin.com/yTh4aCkW")

^^^-Pastebin Links

System:
OS: Ubuntu 10.10 64Bit/Windows 7 home 64bit
Processor: 2nd gen Core i5 @2.3 GHz
Video card: AMD Radeon HD 6700M/Intel integrated( i think it's a HD Graphics 3000)


notes:
*Set up in bios to Switch between Intel/Ati Depending on if AC is plugged in. Tried turning it to dynamic (Switch between cards for different apps that need more speed)

I have tested all the hardware on windows, and it works.

I have the "ATI catalyst control center" when i run it it says "no ATI driver found, or not installed properly".

---

