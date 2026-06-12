---
title: "I can't get sound on my laptop"
date: 2007-02-24
forum: Hardware &amp; Laptops
---

### Post by odzangba on 2007-02-24
Hi,
I installed ubuntu 6.06 on a Gateway MX3225 notebook and I can't get sound. All my volume indicators are up to their maximum limits. Here is some output:

lspci:
> 0000:00:00.0 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:00.1 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:00.2 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
0000:00:00.4 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:00.7 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:0c.0 CardBus bridge: Texas Instruments: Unknown device 8039
0000:00:0c.2 Mass storage controller: Texas Instruments: Unknown device 803b
0000:00:0c.3 0805: Texas Instruments: Unknown device 803c
0000:00:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd.: Unknown device 8185 (rev 20)
0000:00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
0000:00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc.: Unknown device 3344 (rev 01)


lsmod |grep snd:
> snd_seq_dummy           3844  0
snd_seq_oss            33536  0
snd_seq_midi            9376  0
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
snd_seq                51984  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx            28824  2
gameport               15496  1 snd_via82xx
snd_via82xx_modem      15368  0
snd_ac97_codec         92704  2 snd_via82xx,snd_via82xx_modem
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  1
snd_mixer_oss          18688  2 snd_pcm_oss
snd_pcm                89864  4 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
snd_mpu401_uart         7808  1 snd_via82xx
snd_rawmidi            25504  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8716  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd_timer              25220  2 snd_seq,snd_pcm
snd                    55268  12 snd_seq_oss,snd_seq,snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_timer
snd_page_alloc         10632  3 snd_via82xx,snd_via82xx_modem,snd_pcm
soundcore              10208  3 snd


aplay -l:
> card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 3/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: modem [VIA 82XX modem], device 0: VIA 82XX modem [VIA 82XX modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


I get sound when I reboot into Windows XP so it's not likely a hardware fault. I'd appreciate any help.

Odzangba.

---

### Post by tgalati4 on 2007-02-24
Welcome to the forums.  We are here to watch you help yourself.

Great information.  It looks like an onboard VIA soundchip that is being detected and the appropriate driver is being loaded. 

It could be an interrupt problem so the sound calls never make to the hardware.

Examine and report any weirdness in dmesg.

Reboot, go into BIOS and turn off PnP operating system setting.  Turn off serial port, USB port, parallel port.  (This is temporary.)

Boot and see if sound works.  If so then we need to move some interrupts around.

Post the values of /proc/interrupts

Good luck.  You can't fight without sound.  And we need you in the resistance.

Viva La 'Buntu

---

### Post by zsobin on 2007-03-01
I've had a very similar problem with the same laptop.... although I was using mandriva


To enable sound.... open the volume control
click on swiches
edit  -> preferences

find the switch enable external amplifier
switch it to the other position

after doing that your sound should work

---

### Post by zsobin on 2007-03-01
!!!!!!!!!!!!
One more thing

after checking the box for external amplifier
that option will now appear under switches
when it does uncheck it

***then****   your sound will work

---

### Post by tgalati4 on 2007-03-01
If that works, then ignore everything that I said.

Good luck!

---

### Post by dabone on 2007-03-03
> **zsobin said:**
> !!!!!!!!!!!!
One more thing

after checking the box for external amplifier
that option will now appear under switches
when it does uncheck it

***then****   your sound will work

This was just the thing needed for my gateway m520.

Only took a second and sound was working great (even the dedicated volume keys work!)


Thanks!


Later,
dabone

---

