---
title: "Pinnacle PCTV 50i"
date: 2005-12-13
forum: Hardware &amp; Laptops
---

### Post by Domie on 2005-12-13
I bought today a Pinnacle PCTV 50i PCI TV adapter. I did this, because my old TV card, made in Taiwan, would not work in Mandrake and now Ubuntu. I really want to get rid of Windows and use the space for more useful things. This is not possible yet, 'cause I want to view TV on my desktop.

So I bought a new card from a known brand, of which I found a help page:

[http://www.linuxtv.org/v4lwiki/index.php/Pinnacle_PCTV_50i](http://www.linuxtv.org/v4lwiki/index.php/Pinnacle_PCTV_50i)

Generally, the saa7134 cards should be "well supported" (end of quote).

Well, when I load the module with

```
modprobe saa7134 card=77
```

Nothings happens. In Zapping, I can't even select a channel. So I went for a search in the docs, and I found that 26 was a card number for Pinnacle PCTV Stereo. So...

```
rmmod saa7134
modprobe saa7134 card=26

```

Well, that's at least something. I can now select a channel in Zapping (and I got a frequency list from my cable company, so if it works, I got to have TV) and in tvtime, I can select my source and can even scan for channels. The screen turns blue in tvtime. But it says: no signal.

OK, i did a dmesg:

> [4298490.860000] saa7130/34: v4l2 driver version 0.2.12 loaded
[4298490.862000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 18
[4298490.862000] saa7133[0]: found at 0000:00:0a.0, rev: 208, irq: 18, latency: 32, mmio: 0xcfff7800
[4298490.862000] saa7133[0]: subsystem: 11bd:002e, board: Pinnacle PCTV Stereo (saa7134) [card=26,insmod option]
[4298490.862000] saa7133[0]: board init: gpio is 200e000
[4298490.862000] saa7133[0]: dsp access wait timeout [bit=WRR]
[4298490.863000] saa7133[0]: dsp access wait timeout [bit=WRR]
[4298490.968000] tuner 1-004b: chip found @ 0x96 (saa7133[0])
[4298490.971000] tuner 1-004b: microtune: companycode=8000 part=21 rev=06
[4298490.971000] tuner 1-004b: microtune unknown found, not (yet?) supported, sorry :-/
[4298490.974000] saa7133[0]: i2c eeprom read error (err=-5)
[4298491.008000] saa7133[0]: registered device video0 [v4l2]
[4298491.012000] saa7133[0]: registered device vbi0

I'm out of options. And yes, my cable is plugged in ;-)

Does anyone can help me out, because I feel pretty disappointed in purchasing a new card. I'm not rich :(

---

### Post by Domie on 2005-12-17
I know this is advanced, but anyone?

---

### Post by poptones on 2005-12-17
Do you have a video source anywhere? dvd player or vhs deck?

Open tvtime and plug in a video source, then select it using tvtime's input selector. See if you get video that way. It may just be a tuner issue...

---

### Post by Domie on 2005-12-19
[QUOTE=poptones]Do you have a video source anywhere? dvd player or vhs deck?

Open tvtime and plug in a video source, then select it using tvtime's input selector. See if you get video that way. It may just be a tuner issue...[/QUOTE]

Well, too late. I took advantage of a return offer and brought my card back. I'm stuck again with a Generic card of Taiwanese production, who won't even work, although it has the same chip in it, when I stand on my head.

TV adapters and Linux: a bad bad combination with very few chance of a solution.

---

### Post by bneuro1 on 2005-12-19
You wrote:

4298490.968000] tuner 1-004b: chip found @ 0x96 (saa7133[0])
[4298490.971000] tuner 1-004b: microtune: companycode=8000 part=21 rev=06
[4298490.971000] tuner 1-004b: microtune unknown found, not (yet?) supported, sorry :-/

It is a problem with your tuner. There are two options that need to be passed when loading the modules: card and tuner. From the v4l2 driver FAQ 

"Unfortunately it is impossible to detect the tuner type directly. For some TV cards it is known how to figure the exact tuner type indirectly, for example by parsing the configuration info within the card's eeprom. For most cards the drivers simply have a hardcoded default value. That catches most cases, but there are a few exceptions where the vendors ship the TV cards with different tuners depending on the region they are sold (PAL tuner in europe, NTSC tuner in the US) and there is no known way to figure what tuner the card actually has." 

You will also have to select the tuner number from the list of tuners, which can be found in /usr/src/linux/Documentation/video4linux/CARDLIST.tuner

Sorry for the delay, but the solution will apply to a card of Taiwanese production too. Look at che chip and at the tuner.

By

---

### Post by Domie on 2005-12-19
[QUOTE=bneuro1]You wrote:

4298490.968000] tuner 1-004b: chip found @ 0x96 (saa7133[0])
[4298490.971000] tuner 1-004b: microtune: companycode=8000 part=21 rev=06
[4298490.971000] tuner 1-004b: microtune unknown found, not (yet?) supported, sorry :-/

It is a problem with your tuner. There are two options that need to be passed when loading the modules: card and tuner. From the v4l2 driver FAQ 

"Unfortunately it is impossible to detect the tuner type directly. For some TV cards it is known how to figure the exact tuner type indirectly, for example by parsing the configuration info within the card's eeprom. For most cards the drivers simply have a hardcoded default value. That catches most cases, but there are a few exceptions where the vendors ship the TV cards with different tuners depending on the region they are sold (PAL tuner in europe, NTSC tuner in the US) and there is no known way to figure what tuner the card actually has." 

You will also have to select the tuner number from the list of tuners, which can be found in /usr/src/linux/Documentation/video4linux/CARDLIST.tuner

Sorry for the delay, but the solution will apply to a card of Taiwanese production too. Look at che chip and at the tuner.

By[/QUOTE]

Sorry? I'm glad you answered. After this, I went on trial and error, and got a blue screen with my Taiwanese card. I'll do now a T&E on the tuner type.

I'm a bit critical, because I knew the tuner type on the Pinnacle and that didn' t work, but I have a lot of patience...

Thanks already

---

### Post by Domie on 2005-12-19
PS: the dmesg output of the Korean card:



[4302203.638000] saa7130/34: v4l2 driver version 0.2.12 loaded
[4302203.645000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 18
[4302203.645000] saa7133[0]: found at 0000:00:0a.0, rev: 208, irq: 18, latency: 32, mmio: 0xcfff7800
[4302203.645000] saa7133[0]: subsystem: 17de:7136, board: Proteus Pro [philips reference design] [card=1,insmod option]
[4302203.645000] saa7133[0]: board init: gpio is 40
[4302203.645000] saa7133[0]: dsp access wait timeout [bit=WRR]
[4302203.646000] saa7133[0]: dsp access wait timeout [bit=WRR]
[4302203.768000] tuner 1-004b: chip found @ 0x96 (saa7133[0])
[4302203.768000] tuner 1-004b: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[4302203.779000] saa7133[0]: i2c eeprom 00: de 17 36 71 10 28 ff ff ff ff ff ff ff ff ff ff
[4302203.779000] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4302203.779000] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4302203.779000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4302203.786000] saa7133[0]: registered device video0 [v4l2]
[4302203.791000] saa7133[0]: registered device vbi0
[4302203.795000] saa7133[0]: registered device radio0








So I guess the tuner is recognised, but still a blue screen...

---

### Post by bneuro1 on 2005-12-20
Choose your tuner looking at your card or at 

[http://pvrhw.goldfish.org/bttv/bttv-gallery.html](http://pvrhw.goldfish.org/bttv/bttv-gallery.html)

and choosing appropriate tuner option at 

[http://www.linuxtv.org/v4lwiki/index.php/Tuners](http://www.linuxtv.org/v4lwiki/index.php/Tuners)

:)

---

### Post by Domie on 2005-12-20
Card is not on the list. Now I'm doing trial and error on the tuner types. Till card=3, I've done all tuner types, from 0 to 45...

I hope this work is not for nothing, because my card is not on the list, although it has a Philips chip.

---

### Post by Domie on 2005-12-20
I opened my computer and got a look at the card.

It is a SAA7131E chip from Philips with, I guess, a tuner of Philips with 8275AC1 on it. This is not yet in the tunerlist.

---

### Post by bneuro1 on 2005-12-22
Hey 

the chip that you have found is 

TDA8275HN: Terrestrial analog reception for PC-TV application from TDA827x
Silicon Tuner Family. If you look for at 

[http://www.linuxtv.org/v4lwiki/index.php/Tuners](http://www.linuxtv.org/v4lwiki/index.php/Tuners) 

you can found :

tuner=54 - tda8290+75

I think that is your option. Or search goggle 
Philips TDA-8275
 
By again

---

### Post by Domie on 2005-12-22
tried
modprobe saa7134 card=X tuner=54
with X going from 0 to 55... No result

---

### Post by bneuro1 on 2005-12-22
Sorry my friend i don't have more solution. 
So ..... send me a good photo of the card. Maybe i guess some other things.

[email]bneuro1@policlinico.mi.it[/email]

---

### Post by bneuro1 on 2005-12-22
One way to find out your tuner number if you don't see it in the list is simple trial and error, or you can also use the dmesg command as explained in the about section

# modprobe saa7134 card=2 tuner=1
# tvtime
# rmmod saa7134
# modprobe saa7134 card=2 tuner=2
# tvtime
...

Another way could be this:

#/bin/sh
MAXTUNER=46
i=0
while [ $i -lt $MAXTUNER ];
do
           rmmod tuner saa7134
                       modprobe saa7134 card=25 tuner=$i
                       echo "Actual tuner is:" $i
                       tvtime
         i=$(($i+1))
done

write this to probe_tuner.sh and run it as root

If your TV uses NTSC, try the NTSC tuners. If you use PAL, try the PAL ones.

Once you have the card number and the tuner number, you can load the module.

# modprobe saa7134 card=2 tuner=2

Once the modules are loaded, they should create radio0, vbi0 and video0 in /dev/v4l/ These are your video4linux devices that programs like freevo, kdetv, mythtv and tvtime will use.

---

### Post by Domie on 2005-12-22
I thank you very much of all the effort you have done for me. I really appreciate this.

---

### Post by tcwitte on 2005-12-23
[QUOTE=Domie]I bought today a Pinnacle PCTV 50i PCI TV adapter.[/QUOTE]
I've bought the same card and did all kinds of things to get it working -- successfully. With the CVS version of the video4linux modules it all works without module parameters. Tuning isn't optimal yet (don't know why), but it works.
Install the linux-headers and follow the instructions at [http://www.linuxtv.org/v4lwiki/index.php/How_to_build_from_CVS]("http://www.linuxtv.org/v4lwiki/index.php/How_to_build_from_CVS")

---

### Post by tcwitte on 2005-12-23
[QUOTE=tcwitte]it works[/QUOTE]
Oh, if you're interested, this is the output of dmesg:

```
Linux video capture interface: v1.00
saa7130/34: v4l2 driver version 0.2.14 loaded
PCI: Found IRQ 10 for device 0000:00:09.0
PCI: Sharing IRQ 10 with 0000:00:01.4
saa7133[0]: found at 0000:00:09.0, rev: 208, irq: 10, latency: 32, mmio: 0xe0124000
saa7133[0]: subsystem: 11bd:002e, board: Pinnacle PCTV 110i (saa7133) [card=77,autodetected]
saa7133[0]: board init: gpio is 200e000
ir-kbd-i2c: Pinnacle PCTV detected at i2c-2/2-0047/ir0 [saa7133[0]]
saa7133[0]: i2c eeprom 00: bd 11 2e 00 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
saa7133[0]: i2c eeprom 10: ff e0 60 02 ff 20 ff ff ff ff ff ff ff ff ff ff
saa7133[0]: i2c eeprom 20: 01 2c 01 02 02 01 04 30 98 ff 00 a0 ff 22 00 c2
saa7133[0]: i2c eeprom 30: 96 ff 03 30 15 01 ff ff 0c 22 17 87 03 3f f0 73
saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
tuner 2-004b: chip found @ 0x96 (saa7133[0])
tuner 2-004b: setting tuner address to 61
tuner 2-004b: tuner: type set to tda8290+75a
saa7133[0]: registered device video0 [v4l2]
saa7133[0]: registered device vbi0
saa7133[0]: registered device radio0
```

Tuning wasn't really a problem -- I just had to run tvtime-scanner first.

---

### Post by Karma_Police on 2006-01-23
Did you have any problems with sound? I followed the instructions (thanks, btw. It wasn't working at all before :) ), but I get no sound. dmesg gives me pretty much the same output you get (diferent IRQ). Don't know what to do. I have the correct audio standard (PAL-BG), and I get sound in windows. :S

I also tried "tvtime --mixer=/dev/mixer:cd", messing with the volume, and nothing... :( 

I only tried tvtime, since I couldn't get xawtv or vlc to work. Going to try it some more, to see if it is an issue with tvtime.

---

### Post by tcwitte on 2006-01-23
[QUOTE=Karma_Police]Did you have any problems with sound?[/QUOTE]
I've got two sound cards in my computer, and with one of them sound is no problem but with the other it is. It works with my nforce3 (intel_8x0) card with the PCTV card connected to its CD input. It doesn't work with my ca0106 (Creative Labs SB Audigy LS). (Surround works with my ca0106 but doesn't work with my nforce3 so I have to choose :( )

So, in principal it works -- it depends on the sound card in my case. Did you verify that CD or Capture or Aux (whatever it's connected to) is really not muted? Switching settings ("Duplicate front" etc.) may also be the trick.

---

### Post by Karma_Police on 2006-01-24
I have a sound blaster live. The DVD player is connected to the pctv, and the pctv is connected to the sound card. I tried alsamixer to control the volume, but I can't seem to get any sound.

I don't have an option to "Duplicate front"... Should I have one? :|

So it seems the problem is the sound blaster. Mine is "SBLive! CT4620".

Going to search to see if I can find something. Thanks.

By the way. Do you use the default mixer in tvtime, or do you change with something like "tvtime --mixer=/dev/mixer:cd". The default is line.

---

