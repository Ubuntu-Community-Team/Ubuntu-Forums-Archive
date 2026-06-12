---
title: "I have problem with sound card. Can you help me?"
date: 2008-05-09
forum: Hardware
---

### Post by aurora_consurgens on 2008-05-09
Hello! everybody, Now I use Ubuntu 7.10 it is perfect to work but I have some problem about Sound Card. It found Sound Card but without sound. I want sound to listen. How I solve this problem? 

My Sound Card : Intel 82801H (ICH8 Family) HD Audio Controller

I use Lenovo 3000 y310 
- Intel core 2 duo processor T5550
- Intel Graphics Media Accelerator X3100
- Intel Pro/Wireless 3945BG
- Intel 965GM Express Chipset

---

### Post by amohanty on 2008-05-09
Lenovo BIOSs are picky about what you disable. Did you by any chance disable the modem in the BIOS?

Make sure that it is actually being detected by looking at the output of:

lspci

Then make sure that the modules are loaded by checking the output of:

lsmod | grep snd

Finally in a terminal fire up alsamixer:

alsamixer

and make sure that the columns named **Master** and **PCM** dont say MM at the bottom.

HTH
AM

---

### Post by aurora_consurgens on 2008-05-09
It say:

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

theerapong@ubuntu:~$ lsmod | grep snd
snd_hda_intel         263712  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
ubuntu@ubuntu:~$ 

Should I do?

---

### Post by amohanty on 2008-05-09
Did you look at whether:
1. the **modem** is disabled in the BIOS? Press F1 on boot and go through the BIOS config to make sure. Yes it is the modem :) its tied to the damn audio controller.

2. fire up **alsamixer** in a terminal. If you dont have it installed in a terminal type:
sudo apt-get alsa-utils

Then in the terminal type
alsamixer

you will see a ascii based app with columns quite like the volume controller on the panel. make sure that master and pcm are not set to MM

AM

---

### Post by aurora_consurgens on 2008-05-09
I can't found the modem in BIOS and my BIOS is Pheonix.

---

### Post by amohanty on 2008-05-10
how about alsamixer??

---

### Post by aurora_consurgens on 2008-05-10
what you mean? Can you explain me about Alsamixer?


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=69475&stc=1&d=1210407711[/IMG]

---

### Post by jocko on 2008-05-10
Run alsamixer in a terminal:
```
alsamixer
```Check that no channels are muted (I see from your screenshot that Master and PCM is not muted, but check the other ones as well).

In gnome-sound-prefereces and gstreamer-properties, try setting everything to use ALSA, not auto detect.

What exact sound card do you have?
Check what you get from this command:
```
aplay -l
```

---

### Post by aurora_consurgens on 2008-05-10
I tried it. it say:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=69479&stc=1&d=1210411475[/IMG]

---

### Post by jocko on 2008-05-10
Hmmm... aplay should tell exacly which model you have instead of "generic", but from the "268" in your alsamixer I guess it's a Realtek ALC268.

Try this:
```
sudo gedit /etc/modprobe.d/alsa-base
```
Add this to the end of the file:```
options snd-hda-intel model=auto
```
Restart and see if it works, or if you see any difference in alsamixer (I think you should see more sliders and switches, but I'm not sure as I don't have the same sound card).
If that didn't work, try some other options instead of "auto" in that line. The ones available for ALC268 are:```

3stack
toshiba
acer
dell
zepto
auto
```
(Note that these are the options available according to the alsa documentation in hardy, which has a newer version of alsa than gutsy, so some of these options may not work in gutsy).

---

### Post by Yellow Pasque on 2008-05-10
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

---

### Post by aurora_consurgens on 2008-05-10
It doesn't work.

Now I think, I will install with Hardy Heron but I'm not sure that it work with my hardware because in Ubuntu 7.04 I can't install with LiveCD and AlternateCD cause it can't start X in my notebook until Ubuntu 7.10 released I can install with AlternateCD. Now I am downloading Hardy Heron(AlternateCD).

You think, Will I find problem with my hardware? 

[B][I]I use Lenovo 3000 y310
- Intel core 2 duo processor T5550
- Intel Graphics Media Accelerator X3100
- Intel Pro/Wireless 3945BG (I think it's problem)
- Intel 965GM Express Chipset[/I][/B]

And Thank so much for reply my problem.

---

### Post by jocko on 2008-05-10
> **aurora_consurgens said:**
> 
You think, Will I find problem with my hardware? 

[B][I]I use Lenovo 3000 y310
- Intel core 2 duo processor T5550
- Intel Graphics Media Accelerator X3100
- Intel Pro/Wireless 3945BG (I think it's problem)
- Intel 965GM Express Chipset[/I][/B]

I can't see that there would be any problem with that hardware.
I've got an intel Pro/Wireless 3945ABG and it's worked out of the box without any problems in feisty, gutsy and now in hardy, so I don't understand why you expect it to cause problems.
Your graphics card should work out of the box, since intel have open source drivers.
The only thing I can't say you won't have problems with is sound, but that's only because I don't know what causes your current problem. Hopefully it's fixed in the newer alsa version in hardy.

---

### Post by aurora_consurgens on 2008-05-10
Thank you, for:[http://ubuntuforums.org/showpost.php...4&postcount=24](http://ubuntuforums.org/showpost.php...4&postcount=24)

Now I can solve my problem. 

Thank you again for reply my problem...

---

### Post by zibletop on 2008-06-01
Dear,

have a look at [http://zibletop.free.fr/pub/Lenovo-Linux_Ubuntu_Gutsy_On_Lenovo_3000_Y310.html](http://zibletop.free.fr/pub/Lenovo-Linux_Ubuntu_Gutsy_On_Lenovo_3000_Y310.html)

---

