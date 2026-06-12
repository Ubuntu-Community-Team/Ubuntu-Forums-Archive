---
title: "Asus Xonar Essence STX.. not working"
date: 2009-12-13
forum: Hardware
---

### Post by Pedro82 on 2009-12-13
Hi, I've installed ubuntu Jaunty and everything is working fine! And i'm Loving it!=)
But I got one little problem to solve. Hope someone will help me.
My System is recognising everything, but it is using the ATI HD5850 HDMI sound capability as if it was the sound card. Ubuntu detected the Asus Xonar sound card. But as I am so noobish on Linux (Ubuntu), I'm unable to put it to work. 
Thi is wat I got:

```
#aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

``````
#lspci -v 
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 8295
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: fe800000-fe8fffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 8277
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 9800 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 8277
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 9880 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 8277
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 9c00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20)
    Subsystem: ASUSTeK Computer Inc. Device 8277
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at fe7ffc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    Prefetchable memory behind bridge: 00000000fdf00000-00000000fdffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fea00000-feafffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: fe900000-fe9fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 8277
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 9080 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 8277
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 9400 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 8277
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 9480 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20)
    Subsystem: ASUSTeK Computer Inc. Device 8277
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at fe7ff800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=32
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: feb00000-febfffff
    Prefetchable memory behind bridge: 0000000088000000-00000000880fffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 8277
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: ASUSTeK Computer Inc. Device 8277
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 22
    I/O ports at 8000 [size=8]
    I/O ports at 7c00 [size=4]
    I/O ports at 7880 [size=8]
    I/O ports at 7800 [size=4]
    I/O ports at 7480 [size=16]
    I/O ports at 7400 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 8277
    Flags: medium devsel, IRQ 15
    Memory at fe7ff400 (64-bit, non-prefetchable) [size=256]
    I/O ports at 0400 [size=32]
    Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02) (prog-if 85 [Master SecO PriO])
    Subsystem: ASUSTeK Computer Inc. Device 8277
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 22
    I/O ports at 9000 [size=8]
    I/O ports at 8c00 [size=4]
    I/O ports at 8880 [size=8]
    I/O ports at 8800 [size=4]
    I/O ports at 8480 [size=16]
    I/O ports at 8400 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

01:00.0 VGA compatible controller: ATI Technologies Inc Device 6899
    Subsystem: XFX Pine Group Inc. Device 2970
    Flags: bus master, fast devsel, latency 0, IRQ 2297
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at fe8c0000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at a000 [size=256]
    Expansion ROM at fe8a0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx

01:00.1 Audio device: ATI Technologies Inc Device aa50
    Subsystem: XFX Pine Group Inc. Device aa50
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at fe8fc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
    Subsystem: ASUSTeK Computer Inc. Device 81f8
    Flags: bus master, fast devsel, latency 0, IRQ 2298
    Memory at fe9fc000 (64-bit, non-prefetchable) [size=16K]
    I/O ports at b800 [size=256]
    Expansion ROM at fe9c0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: sky2
    Kernel modules: sky2

03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03) (prog-if 01)
    Subsystem: ASUSTeK Computer Inc. Device 824f
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at feafe000 (32-bit, non-prefetchable) [size=8K]
    Expansion ROM at feae0000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03) (prog-if 85 [Master SecO PriO])
    Subsystem: ASUSTeK Computer Inc. Device 824f
    Flags: bus master, fast devsel, latency 0, IRQ 17
    I/O ports at cc00 [size=8]
    I/O ports at c880 [size=4]
    I/O ports at c800 [size=8]
    I/O ports at c480 [size=4]
    I/O ports at c400 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_jmicron

04:00.0 PCI bridge: PLX Technology, Inc. PEX8112 x1 Lane PCI Express-to-PCI Bridge (rev aa)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=04, secondary=05, subordinate=05, sec-latency=64
    I/O behind bridge: 0000d000-0000dfff
    Capabilities: <access denied>
    Kernel modules: shpchp

05:04.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
    Subsystem: ASUSTeK Computer Inc. Device 835c
    Flags: bus master, medium devsel, latency 64, IRQ 15
    I/O ports at d800 [size=256]
    Capabilities: <access denied>

07:02.0 Mass storage controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)
    Subsystem: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    I/O ports at ec00 [size=8]
    I/O ports at e880 [size=4]
    I/O ports at e800 [size=8]
    I/O ports at e480 [size=4]
    I/O ports at e400 [size=16]
    Memory at febffc00 (32-bit, non-prefetchable) [size=512]
    [virtual] Expansion ROM at 88000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: sata_sil

07:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
    Subsystem: ASUSTeK Computer Inc. Device 820d
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    I/O ports at e000 [size=256]
    Memory at febff800 (32-bit, non-prefetchable) [size=256]
    Expansion ROM at 88080000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

```Thanks for any help...

---

### Post by RedSingularity on 2009-12-14
Well do you have any sound output as of now?

---

### Post by Pedro82 on 2009-12-14
I never had any sound output since I installed Jaunty!

Well, I did read an howto about pulse audio and reinstalled it. 
And thanks to that, I got new data about my ongoing problem!
```
#alsamixer
[AlsaMixer v1.0.18 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HD-Audio Generic                                                       &#9474;
&#9474; Chip: ATI ATI R6xx HDMI                                                      &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: IEC958 [Off]                                                           &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                     &#9484;&#9472;&#9472;&#9488;                                     &#9474;
&#9474;                                     &#9474;MM&#9474;                                     &#9474;
&#9474;                                     &#9492;&#9472;&#9472;&#9496;                                     &#9474;
&#9474;                                                                              &#9474;
&#9474;                                  < IEC958 >                 
```Thanks in advance for any help you might give.
I really don't know how to fix this.

---

### Post by RedSingularity on 2009-12-14
Alsamixer looks like it is muted.  Look in system>prefs>sound and see if any of the sound tests work.

---

### Post by Pedro82 on 2009-12-14
The only one that works, is HD-Audio Generic ATI HDMI(ALSA).
But still got  no sound.
The other options got into ERROR: ```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.
```I followed this link  [http://ubuntuforums.org/showthread.php?t=1348604&highlight=setting+sound+cardk](http://ubuntuforums.org/showthread.php?t=1348604&highlight=setting+sound+cardk)
Did everything as it says.
Didn't work for me. Asus sound card didn't show up on asoundconf-gtk.

It's late in Portugal. Tomorrow I'm gona try to correct this mess!
Thanks for your concern.

---

### Post by RedSingularity on 2009-12-14
Ok tomorrow when you get back we will try some things with pulseaudio.

---

### Post by Pedro82 on 2009-12-15
Any ideas howto put my Asus xonar essence STX as default sound card?
:(
Don't know what to do anymore!

---

### Post by RedSingularity on 2009-12-15
First we need to see if alsa is up and running.  

If you type alsamixer in a terminal it should show a volume bar like you posted above.  You need to get that turned up.  It looks as if you have it muted or something.

---

### Post by RedSingularity on 2009-12-15
I just checked it out and that MM you have displayed means its muted.

---

### Post by Pedro82 on 2009-12-15
Right now, I'm following this tutorial [https://help.ubuntu.com/community/OpenSound ]("https://help.ubuntu.com/community/OpenSound")
Hope it will work for me! If it don't, I will follow your directions.
Thanks for your concern [RedSingularity]("http://ubuntuforums.org/member.php?u=677095"), much apreciated.

---

### Post by Pedro82 on 2009-12-15
Well, got some news! I followed the tutorial I post above.
The sound card asus xonar essence stx is detected by ubuntu Jaunty. But.... still no sound!
I'm checking all OSSv4 parameters to see if there is no problem. I'm also installing alsa-utils. I can now choose my asus card on OSS options :D. I think it's a start we got here.

---

### Post by Pedro82 on 2009-12-15
Now, when I enter the comand #aplay -l I got this msg:
```
#aplay -l
aplay: device_list:217: no soundcards found...
```

I should reconfigure alsa.... I think....

---

### Post by RedSingularity on 2009-12-15
You can try that.  Before you go any further you need the sound card to show up there.

---

### Post by dh003i on 2010-02-17
I am having a similar problem with my Asus Xonar Essence STX. It is also not working, I hear **no sound at all from my headphones**, **[COLOR="Red"]although it does seem to record input from the microphone[/COLOR]**. I tested this with my head-set plugged into both the Headphone Out and Input jacks (via the gold adapter that came with the STX).

The STX is recognized by my computer. Running *aplay -l*, I get:

```
~ $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: STX [Xonar Essence STX], device 0: Multichannel [Multichannel]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: STX [Xonar Essence STX], device 1: Digital [Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Running *lspci*, I get:

```

~ $ lspci
05:04.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]

```

I open up the *GNOME ALSA Mixer*, under the Asus Xonar STX (AV200 AD1989B) tab, I see Master (mute button unchecked), Mic, Aux, and AnalogIN all set to maximum; Line is checked (checking & unchecking it results in me hearing a click, must be the sound-card), Mic Boost (+20dB) is checked; IEC958 is checked; Analog Output is unchecked (if I check it, it goes back to being unchecked when I re-open GNOME ALSA Mixer). 

Under System > Preferences > Sound, the Hardware tab settings are as follows: 
*** Hardware tab:** CMI8788 [Oyxgen HD Audio] is set to 1 Output / 1 Input (Analog Stereo Duplex). Internal Audio and R700 Audio Device (Radeon HD 4000 Series) are both disabled/off.
*** Input tab:** Input Volume is set to 100%, unmuted, the CMI8788 device is selected for sound input, the connector type set to "Analog Microphone". When I breath or talk, I can see the Input level bar increase, so the microphone input is working.
*** Output tab:** CMI8788 device is selected. 
* Output Volume is set at 100%.

I wonder if the sound-card itself is defective? Is there anything else I could try?

PS: Typing alsamixer produces the following

```

~ $ sudo alsamixer 
alsamixer: function snd_ctl_open failed for default: No such device

```

---

### Post by dh003i on 2010-02-17
Ok, with a whole lot of help from #ubuntu, I solved the problem. The issue was I have a Radeon HD 4670 GPU, which has some kind of sound-driver. That was taking priority over the Xonar, stealing the output. My guess is this is because I have the Catalyst drivers installed and they aren't playing nicely?). Before I got my new sound-card, sound was working because the on-board audio took precedence. 

Here's what I did. 

Note:

If you are in Ubuntu 9.10, you'll need to temporarily down-grade [alsa-utils to the jaunty version]("http://packages.ubuntu.com/jaunty/sound/alsa-utils"). Install that with 

```

dpkg -i alsa-utils_1.0.18-1ubuntu11_amd64.deb

```

(obviously, if you aren't in amd64, the named package will be different; download what is appropriate for you)

1. Blacklist sound devices other than the Xonar. For example, I typed:

```

echo blacklist snd_hda_intel | sudo tee -a /etc/modprobe.d/blacklist

```

2. Make sure your user is in the plugdev and audio group (System > Administration > Users and Groups; then click on the tool to make changes; then click on Manage Groups and add your user to plugdev and audio). 

3. Typed aplay -l to find out a list of playback hardware devices:

```

~ $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: STX [Xonar Essence STX], device 0: Multichannel [Multichannel]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: STX [Xonar Essence STX], device 1: Digital [Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

4. Because the Xonar Essence STX was card 0, I typed:

```

sudo asoundconf set-default-card 0

```

5. Also ran asoundconf list to see how sound-card named:

```

~ $ asoundconf list
STX

```

6. Set default sound card to STX:

```

asoundconf set-default-card STX

```

7. Now alsamixer works, and I can play with volume controls. You will want to uncheck Mic boost (either in alsamixer or GNOME Alsamixer), as that results in lots of static. You may have to play with the levels to get everything just right.

8. If you downgraded alsa-utils, upgrade again:

```

sudo apt-get install alsa-utils

```

---

### Post by dh003i on 2010-11-25
I ran into another problem with me not hearing sound after installing (fresh) Ubuntu 10.10. The solution this time was much more simple. If you don't have alsamixer, type *sudo apt-get install alsamixer*, then tyep *alsamixer*. The driver for my Xonar STX defaulted to outputting to the speaker port, not the headphone port (I have headphones plugged into the headphone jack). Make sure you select the appropriate port, depending on whether or not you have headphones or speakers plugged in:

[Here is my current setup]("http://pastebin.com/1mZE7Jgj"), although I may adjust master levels and impedance settings.

---

### Post by Adman65 on 2010-12-31
are you using pulse audio? I am having the same problems as you. I disabled the snd_hda_intel a while ago. Still no luck with the xonar stx though. I can't get anything to play using alsa or pulse audio. I can see the mixer going crazy in PA, but alas, no sound.

---

### Post by srinivasmurty on 2011-04-20
I am experiencing similar problems with Ubuntu 11.04. I am able to use alsamixer to set the Analog Out to Headphones and I get a popping sound. But no other sound comes out of the headphones. This hardware setup works perfectly with my dual booting PC where I have Windows 7. I've tried disabling and enabling the ATI HD card without any luck either way. Can anyone suggest what the fix could be?

---

### Post by Sotanaht on 2011-07-18
Is there a way to get the Xonar Essence ST to work without completely disabling the ATi sound card?  I use the ATi output on my Radeon HD 4870 to play sound through my monitor's speakers when I'm not using headphones.  On Windows, I just have to change the audio device, but from what I understand, in Ubuntu I have to completely disable the ATi sound card to get anything out of my ASUS sound card.
If that's not possible, I guess I could just get cables to connect my sound card to my monitor, although I'm not sure if my monitor would even support that.

---

### Post by Sotanaht on 2011-07-20
Well I decided to forget about the ATi sound output, since I hardly use it anyway with my monitor's awful speakers.  I followed all the steps, and everything looks like it should work, but I still can't get any sound from the card.  And now that I've disabled all my other sound cards, I don't have any sound at all :( please help

---

### Post by bcschmerker on 2011-09-25
I am currently researching possible update audio cards for two systems:  my hybrid Everex®, packing a Gigabyte® GA-MA78GM-S2HP augmented with a Creative Laboratories® SB0350 stereo-in/7.1-out audio adapter and I/O drive, plus 500W Athena® power supply, running Ubuntu® 10.04.3-LTS; and an Asus® CM1630-06 augmented with an EAH6850DC/2DIS/1GD5 video display adapter and 750W Antec® power supply running Microsoft® Windows® 7.0.8001 (and could just as easily run Ubuntu® 10.04.3-LTS, were it not still under manufacturer warranty).

From the [Asus® USA website]("http://usa.asus.com/"), I found that the Xonar family of audio cards (Asus® AV-100 chipset, mfd. for ASUSTeK Computer by C-Media; based on the CMI8788 Oxygen ASPU) requires additional +5VDC and +12VDC power for its analog circuitry to function; this can be fed via a 4-pin Molex, except the Xonar D*n* low-profiles via a 4-pin mini-AMP.  So **do** confirm that your card has the required additional power as part of the troubleshoots debriefed this Thread.

---

### Post by Sotanaht on 2011-09-29
Well my Xonar Essence ST works just fine in Windows 7, so that's not my problem.  It's just a driver issue for me.

---

### Post by bcschmerker on 2011-10-01
Speaking of drivers, the [Advanced LinUX Sound Architecture Project](http://www.alsa-project.org/) has a driver, [snd-oxygen](http://www.alsa-project.org/main/index.php/Matrix:Module-oxygen), that should work on the Asus® AV-100 chipset (mfd. for ASUSTeK Computer by C-Media), as the AV-100 and the C-Media® CMI-8788 are almost identical in architecture.  Unfortunately, as of 1 October 2011, Card-Specific Information is not available for snd-oxygen at the ALSA Project wikicatalog; and I haven't sufficient information on the specific differences between the AV100 and the generic CMI8788.

---

