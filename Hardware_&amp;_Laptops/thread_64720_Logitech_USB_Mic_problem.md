---
title: "Logitech USB Mic problem"
date: 2005-09-11
forum: Hardware &amp; Laptops
---

### Post by socrates32 on 2005-09-11
I am currently running Hoary, and have had no problems, except for the following:

All sound on the system works fine except the USB mic. It is a Logitech noise-cancelling microphone based on an AK5370. Initially, it crashed sound on the system, but then I added "options snd-usb-audio index=-2" to alsa-base, which seems to have fixed that problem, since sound is working again.

/dev/dsp1 appears upon plugging in the mic.

'cat /proc/asound/cards' produces:

0 [PCI            ]: Allegro - ESS Allegro PCI
                     ESS Allegro PCI at 0x6800, irq 5
1 [default        ]: USB-Audio - AK5370
                     AKM              AK5370           at usb-0000:00:02.2-1, full speed

So, the system seems to be seeing it... But when I open the volume control, there is no slider for the AK5370. Audacity won't let me point to /dev/dsp1 as an input device. 

Out of desperation, I managed to get sound in from the mic by linking /dev/dsp to /dev/dsp1, but of course this breaks the rest of the sound on the system.

I have only been using Linux for 6 months or so, and I'm not yet very familiar with the configuration files. This is mostly due to everything working right out-of-the-box. I've googled this problem repeatedly, to no avail. Any and all help is greatly appreciated.

 ](*,)

---

### Post by patrick295767 on 2005-12-07
[QUOTE=socrates32]I am currently running Hoary, and have had no problems, except for the following:

All sound on the system works fine except the USB mic. It is a Logitech noise-cancelling microphone based on an AK5370. Initially, it crashed sound on the system, but then I added "options snd-usb-audio index=-2" to alsa-base, which seems to have fixed that problem, since sound is working again.

/dev/dsp1 appears upon plugging in the mic.

'cat /proc/asound/cards' produces:

0 [PCI            ]: Allegro - ESS Allegro PCI
                     ESS Allegro PCI at 0x6800, irq 5
1 [default        ]: USB-Audio - AK5370
                     AKM              AK5370           at usb-0000:00:02.2-1, full speed

So, the system seems to be seeing it... But when I open the volume control, there is no slider for the AK5370. Audacity won't let me point to /dev/dsp1 as an input device. 

Out of desperation, I managed to get sound in from the mic by linking /dev/dsp to /dev/dsp1, but of course this breaks the rest of the sound on the system.

I have only been using Linux for 6 months or so, and I'm not yet very familiar with the configuration files. This is mostly due to everything working right out-of-the-box. I've googled this problem repeatedly, to no avail. Any and all help is greatly appreciated.

 ](*,)[/QUOTE]
  
I have got same prob : nothing in audacity
but i can see it in alsamixer the scroll bar : i have same : AK5370
adn same prob with breezy !!

soime knows ??

---

### Post by everdred on 2006-01-05
I really have no idea what I'm doing, but I pieced together suggestions I read in a few places.

Here's how I got my AK5370 working in Audacity:

[LIST]
[*]Start Audacity.
[*]In a terminal,  ```
cat /dev/dsp1 > /dev/dsp
``` .
[*]In Audacity prefs, I choose /dev/dsp as my input and output devices. (These are the only choices available to me, but both drop-downs had nothing selected by default.)
[*]For some reason, I had to select "PhoneOut" as my input device within Audacity. I suppose what this is called may vary from sound card to sound card.
[*]Click record. Sing or whatever. Click stop.
[*]In order to get sound playback to work, I had to go back to the terminal and break the **cat** command with Ctrl+C.
[/LIST]

I think that's it.

I don't know what the problem is, but sound quality with that microphone isn't what I remember it being in Windows with Audacity. There's considerable static. Being all digital and USB-like, having it plugged into a hub shouldn't degrade the sound quality, right?

---

### Post by fabianp on 2008-02-26
I have ubuntu 7.1 and audacity 1.3.3-beta. Audacity sees the microphone Logitech (AK5370) but it doesn't record a thing. Funny thing is that I can use the microphone with skype, so the problem is in audacity. Any ideas?

---

