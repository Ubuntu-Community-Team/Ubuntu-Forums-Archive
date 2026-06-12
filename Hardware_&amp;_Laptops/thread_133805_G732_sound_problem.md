---
title: "G732 sound problem"
date: 2006-02-20
forum: Hardware &amp; Laptops
---

### Post by LifeIsAFractal on 2006-02-20
I have been banging my head against the wall for about two months on this one. I have an ECS G732 (aka green732 aka winbook j4) laptop. When I original installed ubuntu 5.04 wayback everything worked without a hitch, sound included. Recently I bought an Intel IPW2200 minipci wireless card. When I cracked open the case to put it in I found an AM303W modem in the minipci slot. Took that out and put in the wireless. Wireless works without a hitch. Problem is that my sound no longer works. After months of trouble shooting I have narrowed it down to an IRQ issue most likely linked to acpi irq routing. The sound only works when the modem is in the system. The audio and sound share the same irq when installed together. I got it to the point where I get choppy garbled audio from the alsa drivers and the oss driver fail completely. I have tried upgrading to kernel 2.6.15.9, installing alsa 1.0.10, using dapper, using brezy and disabling acpi. Unfortunately when disabling acpi my ide controller doesn't work due to an IRQ issue and I couldn't boot to test the sound. The card is an sis 7012 using the snd_intel8x0 drivers. Both the modem and sound card are ac97. When trying to use the sound card the kernel some times puts out errors about the irq that the sound card is on and sometimes just disables it completely. Any insight here would be appreciated because I have no idea how removing a device would cause a major irq issue.

---

### Post by Ensnared on 2006-04-09
Sorry for the late reply to this - I only found this post while searching for something else sound-related on this exact laptop modell.

Basically, I had the exact same problem as you - I switched out the miniPCI-card with an Intel Wireless Pro 2915ABG, which uses the ipw2200 driver (cause the original card refused to work in Linux no matter what I did - tried every type of driver, but no dice - but the Intel-card is way better anyway, and cheap, so I'm not complaining - now ;) ).
The problem was, I could not get the wireless card _and_ the soundcard working at the same time, and it has to do with a BIOS setting.

If you choose "WinXP" as the OS in the BIOS, and choose to reset the configuration data, only the soundcard works.
If you choose "Other" as the OS in the BIOS, and choose to reset the configuration data, only the wireless card works.

The solution proved to be quite simple - upgrade the BIOS ;) I was sure I'd done that ages ago since the newest BIOS is from 2003, but apparently I hadn't. I did it just a couple of hours ago as I've only now switched from dualboot with Windows to running only Linux on my laptop, and I have both wireless and sound working. The BIOS setting must be set to "WinXP" afterwards, or else the soundcard won't get detected - just make sure to reset the configuration data if you change this setting to make sure it's updated.

You'll find the BIOS upgrade here:
[G732 BIOS](http://www.ecs.com.tw/ECSWeb/Downloads/ProductsDetail_Download.aspx?DetailID=156&DetailName=BIOS&DetailDesc=G732(2.0)&MenuID=37&LanID=9)

You have to boot from a bootdisk with no drivers loaded in order to flash it, and if you - like me - do not have an USB floppy, you probably need to create a bootable CD. I solved this using the bootable iso-image on [bootdisk.com](http://www.bootdisk.com/) - all you need to do is edit the iso-image and add the BIOS image and the pflash utility, then burn it - preferably to a CD-RW-disc so as not to waste a CD ;) Just make sure you uncompress the BIOS first - the BIOS exe-file is a self-extracting exe and can be extraced using the unzip-command in Linux. The pflash-utility however is a regular executable.

If you - also like me - can't find an application to edit iso-files which supports this kind of image (the ones I tried said it was unsupported, possibly because it's an empty image with only the boot-data on it), so I had to use UltraISO (mentioned in the readme-file) for Windows. This installed without a hitch using Wine though, so I was able to edit the iso-image like the readme-file instructed, then burn it using any CD-writing software (I use K3B).

Just make sure you have your computer connected to power when upgrading - you don't want to even risk your computer shutting off while the BIOS is being flashed ;)
NOTE: Flashing the BIOS can potentially harm to your computer - if something goes wrong in the process it might render it completely unusable, and I'm not sure if this modell has a failsafe for the BIOS. I obviously can't take any responsibility if something goes wrong, but it did work flawlessly for me the way I just described.

Anyway, after this is done, you'll probably get the problem I'm trying to figure out now - the sound is incredibly choppy, and is not usable in any way whatsoever. I'm having a hard time figuring this one out, so consider yourself warned already ;) It may be that it'll work for you though, but you should be aware that it's a possibility.

So, good luck :)

---

