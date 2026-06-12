---
title: "Sound doesn't work: can't find /dev/dsp"
date: 2005-04-17
forum: Hardware &amp; Laptops
---

### Post by Nafai3000 on 2005-04-17
Hi. I have just installed Kubuntu and I get this error when I log in:

 Sound server informational message:
 Error while initializing the sound driver:
 device /dev/dsp can't be opened (No such file or directory)
 The sound server will continue, using the null output device.

So I have no sound. 

I had this problem too with Red Hat 9, but I was OK with Fedora Core 3, SuSE 9.2.

This might be a stupid problem, but I want to know if I can avoid compiling the kernel. 

Thanks for your help!!

---

### Post by heimo on 2005-04-17
To help you, some addtitional information is needed. Which sound card or motherboard with integrated audio are you using? This kind of situation is typical when module for audio is not loaded - it's either missing, not loaded automaticly or fails to load.

When you know which kernel module implements the support for your sound, you can try modprobe [modulename]. Running *lspci *probably gives some helpful information, Also you could post the content of [i]/etc/modules

[/i]Cheers!

---

### Post by Nafai3000 on 2005-04-17
[QUOTE=heimo]To help you, some addtitional information is needed. Which sound card or motherboard with integrated audio are you using? This kind of situation is typical when module for audio is not loaded - it's either missing, not loaded automaticly or fails to load.

When you know which kernel module implements the support for your sound, you can try modprobe [modulename]. Running *lspci *probably gives some helpful information, Also you could post the content of [i]/etc/modules

[/i]Cheers![/QUOTE]
 Unfortunately I don't know the model of my sound card. It is a generic sound blaster. It came with the computer (which is at least 5 years old).

I post the information you request:

% lspci

0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 02)
0000:00:07.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:0c.0 Communication controller: Conexant HSF 56k Data/Fax Modem (rev 01)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)

% cat /etc/modules

ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse

Thank-you!

---

### Post by heimo on 2005-04-17
Hmm... If it's sound blaster compatible, module sb should work. It may be as simple as typing [i]modprobe sb 

lsmod [/i]should also list soundcore as a loaded module, if not:  [i]modprobe soundcore

[/i]More candidates for modprobing can be found:
[i]cd /lib/modules/$(uname -r)/kernel/sound


[/i]

---

### Post by Nafai3000 on 2005-04-17
[QUOTE=heimo]Hmm... If it's sound blaster compatible, module sb should work. It may be as simple as typing [i]modprobe sb 

lsmod [/i]should also list soundcore as a loaded module, if not:  [i]modprobe soundcore

[/i]More candidates for modprobing can be found:
[i]cd /lib/modules/$(uname -r)/kernel/sound


[/i][/QUOTE]
 I've typed modprobe sb and that order doesn't end. I can't stop it even with ctrl+C or kill -s 9.

But after typing it, a new device seems to appear (/dev/dspW) and lsmod | grep sb prompts:

sb                     11368  1
sb_lib                 44336  1 sb
uart401                11460  1 sb_lib
sound                  74028  2 sb_lib,uart401
soundcore               9824  2 sb_lib,sound

When I reboot the system (with modprobe sb already running), /dev/dspW and all that things in lsmod disappear.

What is the problem?

---

### Post by heimo on 2005-04-17
To get it loaded automaticly during boot, add the *sb* to */etc/modules* (on its own line).

---

### Post by Nafai3000 on 2005-04-17
[QUOTE=heimo]To get it loaded automaticly during boot, add the *sb* to */etc/modules* (on its own line).[/QUOTE]
 I have done that, but the computer has not been able to boot. It stopped after these lines:

* Loading modules
pnp: Unable to assing resources to device 01:01.00

I had to boot from a rescue-CD and change /etc/modules.

Another suspicious line is this (it is prompted at the beginning):

pnp PnPACPI : METHOD_NAME__CRS failure for PNP0f13

---

### Post by Nafai3000 on 2005-04-17
I have tried the following:

# modprobe soundcore
# modprobe sound
# modprobe uart401
# modprobe sb_lib
# modprobe s
(here it gets blocked)

After that I have restarted the sound system and I get a new message:

Sound server informational message:
Error while initializing the sound driver:
device /dev/audio can't be opened (No such device)
The sound server will continue, using the null output device.

---

### Post by heimo on 2005-04-17
Maybe it's a wrong module or it needs parameters. Oh wait! Is it ISA card? That'd explain it didn't show up in lspci. You may have to use isapnp (in package isapnptools) and edit /etc/isapnp.conf to get it working...

But before you get on that road, if I were you, I'd definitely try to figure out the exact make and model of the card. Then I'd go searching for people with similar card and instructions to get it working (preferably on this forum).

---

### Post by Nafai3000 on 2005-04-17
So there is not any way for kubuntu to auto detect my sound card? Before installing kubuntu I installed SuSE (1 day before) and it detected the sound card (and both use the same kernel or even ubuntu's is newer).

---

### Post by Nafai3000 on 2005-04-17
Yes, it is an ISA card. I can't find it's model but I have many info about the sound card (from DMA channels to supported audio standards), but I think configuring isapnp will be too difficult for me.

---

### Post by sillygirly on 2005-04-17
I'm having a very similar problem...  I have no sound at all.

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host B ridge (rev 80)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:0b.0 Communication controller: Lucent Microelectronics LT WinModem (rev 02)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82 3x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8 237 AC97 Audio Controller (rev 50)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 400 0 AGP 8x] (rev a4)

---

### Post by heimo on 2005-04-17
sillygirly: snd_via82xx should be right module for you (I'm using that one also, VT8237 based motherboard).


 ```

modprobe snd_via82xx 

``` 
if that gives you audio, add it to /etc/modules (hmm... I don't actually need to do that, it was automaticly set up).

---

### Post by MattBro on 2005-05-03
I have the same chipset for my Athlon XP

lspci | grep -i audio

0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)


I get no sound whatsoever even after tweaking all the various sliders, trying the modprobe snd_via82xx  and switching to Alsa etc.  Since this computer is supposed to work for my sons DVD video classroom, I will probably soon have to abandon my experiment with Ubuntu. It's quite promising so far though.  Too bad more the hardware companies don't actively support linux.

I suppose I should mention I'm using Ubuntu 5.04 and that my sound card works fine under WinXP

-Matt

---

### Post by cvmostert on 2005-12-31
[QUOTE=sillygirly]I'm having a very similar problem...  I have no sound at all.

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host B ridge (rev 80)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:0b.0 Communication controller: Lucent Microelectronics LT WinModem (rev 02)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82 3x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8 237 AC97 Audio Controller (rev 50)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 400 0 AGP 8x] (rev a4)[/QUOTE]


my onboard card also never made a beep before... 

> lspci |grep Multimedia

0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)

so i also would like to get the problem solve... i see yours worked in windows... i dont wanna install win... is there another way to test the card?

---

