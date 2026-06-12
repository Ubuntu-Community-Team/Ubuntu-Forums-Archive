---
title: "Trouble with speakers on my laptop"
date: 2008-08-23
forum: General Help
---

### Post by colobix on 2008-08-23
Hi folks.
I have a audio problem.
Everything works fine when I do not have any headset plugged in.
I have played around with the volum control options in forever now to try to solve the problem.
My laptop is an Packard Bell, with Ubuntu 8.04.
I have also seeked around on this forum for an answer but after lots of research I didn't find any answer.

Please help me anyone

---

### Post by LateNiteTV on 2008-08-23
we need your hardware details.

---

### Post by Alaric on 2008-08-23
What exactly happens?  Is there a crackle?  Do the speakers not play when you connect the headset?  

Also, in addition to right-clicking the volume control in the top right, you might want to try going to the System->Preferences->Sound menu.  It provides seperate information and controls.

[Edit]Also, is it a USB headset?  And the post above me is right, we could use some hardware information if my post doesn't help you out.  Try Posting the output of 
```

lspci && echo '' && lsusb

```

---

### Post by colobix on 2008-08-23
Thanks for the really quick replay.
Here's my output details:

chris@chris-laptop:~$ lspci && echo '' && lsusb
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
09:04.0 Network controller: RaLink RT2561/RT61 rev B 802.11g

Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c024 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by Alaric on 2008-08-23
Did you try System->Preferences->Sound then?  Is your headset a USB headset?  Did you run that command with the headset plugged in?

---

### Post by colobix on 2008-08-23
I did not have the headset plugged in when I wrote the command, I use the standard headset jacks and not USB.
All so well on the sound settings.

---

### Post by mack27 on 2008-08-23
Hi,
I also had problems with sound on my Pac Bell (basically there was no audio at all), but that was with KDE and i was asked what sound my laptop was using and told that the only one that supported Linux was 'Creative'. I was just going to install Ubuntu on that laptop, we'll see how that goes.

---

### Post by colobix on 2008-08-23
The strange thing is. Nothings seems to be wrong with the sound card here coz all audio works fine when nothing mic or headset is plugged in, so it has to be the speekers or some audio settings I have "ignored" or forgot.

---

### Post by colobix on 2008-08-23
I did some research on this board to see if I could solve my problem, had some degree of dest the same problem I have but had been recovered from it to disable the amplifier, but I can not find any adjustment for the amplifier, a subwoofer, or some such.

---

### Post by pretobomba on 2008-08-23
You should take a look at alsamixer, run in terminal:
alsamixer
(a gray screen with bars should pop in the terminal)
press m to unmute each of them, and make sure everything is not on mute
see if sound works, for my old headphone options, on my old computer i had to mute the front bar to work correctly. also post your aplay -l
I have the same card as you, my headphones just worked out of the box.

---

### Post by colobix on 2008-08-23
Well, everything is unmuted now, but my front jacks (mic and headset) will still not work.

---

### Post by colobix on 2008-08-23
So u say I have to mute front? That's where all audio comes out, so I can't mute that one.

---

### Post by colobix on 2008-08-23
BÜMP
Bring up my post please!:)

---

