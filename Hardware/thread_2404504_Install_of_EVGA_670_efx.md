---
title: "Install of EVGA 670 efx"
date: 2018-10-24
forum: Hardware
---

### Post by nul2 on 2018-10-24
I am upgrading my graphics card and it is my first time upgrading hardware in Linux. I put the new card in and I get this beeping sound and nothing happening on my display. Do I need to install software before install? I am on a h8 1414 HP.


Thank you in Advance

---

### Post by nul2 on 2018-10-24
Ok. So, I guess I made an armature move here. I see that the graphics card has two power outlets on the side, Is it possible that the motherboard is not booting because of the drain on power?

---

### Post by oldfred on 2018-10-24
Manual should say if you have to plug in extra power. Most of the more powerful video cards do need that.

But with nVidia you also need to use nomodeset to get into Ubuntu and then install the correct nVidia driver for your card.
Some UEFI also have to turn on or off which video mode, internal or external is used & then of course plug must be on correct output.
Some have to use the default video to boot & install nVidia driver, then reconfigure settings in UEFI and connection to boot with nVidia.

       Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

I have an older GT620 and it uses the newest driver, but whatever is newest in Ubuntu is new enough for my card. Only the very newest nVidia cards need the very newest drivers as those have new features that older card does not have. Very old cards then have frozen driver versions to match older generations of cards.
       
 Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

Just notices my card is in this list, so now frozen at 390.xx
       
 Fermi based should use 390.xx not newer
[URL="https://nvidia.custhelp.com/app/answers/detail/a_id/4656/~/list-of-fermi-series-geforce-gpus"]https://nvidia.custhelp.com/app/answers/detail/a_id/4656/~/list-of-fermi-series-geforce-gpus

      [/URL]
 We typically do not suggest running the .run files from nVidia.
As then you have to rerun the dkms on every kernel update.
Where versions of nVidia installed from repository just work. 
    
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 
    
[URL="https://nvidia.custhelp.com/app/answers/detail/a_id/4656/~/list-of-fermi-series-geforce-gpus"]
[/URL]

---

### Post by him610 on 2018-10-24
Just checked the requirements for your EVGA 670 efx graphics card, you need:
500 Watt or greater power supply with a minimum of 30 Amp on the +12 volt rail.****
PCI Express, PCI Express 2.0 or PCI Express 3.0 compliant motherboard with one graphics slot.
Two available 6-pin PCI-E power dongles

Specs for your h8 1414 HP system Power supply:
Internal 300W (100V-240V)
Form factor: Internal ATX
Total wattage: 300W
Nominal input voltage range: 200-240V/3A (50-60Hz)

Looks as if you need to upgrade your power supply. Be sure to get a good one.

---

### Post by nul2 on 2018-10-30
> **oldfred said:**
> Manual should say if you have to plug in extra power. Most of the more powerful video cards do need that.

But with nVidia you also need to use nomodeset to get into Ubuntu and then install the correct nVidia driver for your card.
Some UEFI also have to turn on or off which video mode, internal or external is used & then of course plug must be on correct output.
Some have to use the default video to boot & install nVidia driver, then reconfigure settings in UEFI and connection to boot with nVidia.

       Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

I have an older GT620 and it uses the newest driver, but whatever is newest in Ubuntu is new enough for my card. Only the very newest nVidia cards need the very newest drivers as those have new features that older card does not have. Very old cards then have frozen driver versions to match older generations of cards.
       
 Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

Just notices my card is in this list, so now frozen at 390.xx
       
 Fermi based should use 390.xx not newer
[URL="https://nvidia.custhelp.com/app/answers/detail/a_id/4656/~/list-of-fermi-series-geforce-gpus"]https://nvidia.custhelp.com/app/answers/detail/a_id/4656/~/list-of-fermi-series-geforce-gpus

      [/URL]
 We typically do not suggest running the .run files from nVidia.
As then you have to rerun the dkms on every kernel update.
Where versions of nVidia installed from repository just work. 
    
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 
    
[URL="https://nvidia.custhelp.com/app/answers/detail/a_id/4656/~/list-of-fermi-series-geforce-gpus"]
[/URL]

Thanks oldfred. Right now I am stuck at 5 long beeps at start up and then it goes to the encryption screen. Right after I type my password my monitor starts to flash and that is all i get. I think is it the power supply him 610 said. Looks like I am stuck at that until I get a power supply. I will check back in when I can get one.

---

### Post by nul2 on 2018-10-30
> **him610 said:**
> Just checked the requirements for your EVGA 670 efx graphics card, you need:
500 Watt or greater power supply with a minimum of 30 Amp on the +12 volt rail.****
PCI Express, PCI Express 2.0 or PCI Express 3.0 compliant motherboard with one graphics slot.
Two available 6-pin PCI-E power dongles

Specs for your h8 1414 HP system Power supply:
Internal 300W (100V-240V)
Form factor: Internal ATX
Total wattage: 300W
Nominal input voltage range: 200-240V/3A (50-60Hz)

Looks as if you need to upgrade your power supply. Be sure to get a good one.

Him610,

Do you think this would cause 5 beeps at boot up. I'm thinking this is the problem as well. I get 5 beeps at boot up and then it goes to my encryption screen. Once I type in my password and hit return my monitor starts to flash. I think I am dead in the water with it until I get another power supply. Would you happen to know if I put a 500w power supply into a h8 1414 it would be too  much power for the mother board? Is it possible? I'm really new to this and it may be a dumb question.

Thanks,
nul2

---

### Post by nul2 on 2018-11-04
OK I am up and running with a 550 watt power supply. I seems to have the same issue. I have changed the /etc/default/grub to have a nosetmode in it, but I still have the same problem. I computer runs fine with the old card, but when I put in the new card I get 5 beeps when I boot up and get to the encryption screen again. Once I type in pass word it starts flashing black and grey. I think I am missing something in the software. Is there more to change other then the nomodeset in the grub?

---

### Post by him610 on 2018-11-04
A series of beeps when booting normally means a video or memory issue. Since it boots with your original graphics card, I would suspect the new card. If you still have the manual for your computer, check the troubleshooting section to see what the beeps mean.
This support HP page discusses diagnostic LEDs and beeps [https://support.hp.com/us-en/product/hp-envy-h8-1400-desktop-pc-series/5295996/model/5296860/document/bph07107]("https://support.hp.com/us-en/product/hp-envy-h8-1400-desktop-pc-series/5295996/model/5296860/document/bph07107")

---

### Post by nul2 on 2018-11-04
Thanks Him610,

I have ask that community to see if someone there has has this issues.

---

### Post by nul2 on 2018-11-06
So, I asked the HP community and they recommended that I boot in recovery mode. I did this and I still get the beeping sound at boot up and then get not visuals at all on the new graphics card. I switched back to my old card and not all I get is a low res output. I tried multiple to boot in the normal mode, but it seems to keep going into recovery mode. Is there something that I am missing?

---

### Post by nul2 on 2018-11-13
Is it strange that when I boot with the new card I don't get the HP logo like I do when I have the old card in. But I do get the encryption screen. Is this odd?

---

### Post by nul2 on 2018-11-14
I have made some progress. I am now able to boot with the new card in recovery mode. I had to adjust setting in the UEFI to get the beeps to stop. Now I see the HP logo when I boot up. I just can't get into normal mode with it. I am a little confused on what I need to do to get the drivers or grub to work with it. Is it just the NOSLASH setting or is there something else?

Thank You Much,
Nul2

---

### Post by nul2 on 2018-11-15
I got it to work with the drive 390. It boots in normal mode now. With a UHD monitor and a HDMI cable. I get really shape and small objects on the desktop and dock. But when I go to play a 4K version of avengers I get this error that will only play in standard definition. I get this on youtube, vudu, and Amazon. The picture is aweful. Is there a setting that I am missing?

---

### Post by nul2 on 2018-11-15
[CENTER][FONT=SystemFont, Helvetica Neue, Helvetica, Arial, sans-serif][COLOR=#031b2b]**"Oops! This title won’t play in this quality on your display due to copyright restrictions. It can be played only if your output and display support HDCP." Is the error I get from Vudu. The thing is that my output it on HDCP.  I appreciate any help I can get**[/COLOR][/FONT][/CENTER]

---

