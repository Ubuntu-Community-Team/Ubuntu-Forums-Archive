---
title: "Wrong Driver!"
date: 2010-04-08
forum: Hardware
---

### Post by lv8402 on 2010-04-08
When I use Ubuntu to play sounds, the computer will reboot automatically .

I met the absolutely same problem in Windows XP, 
the problem is that the driver of the sound card given by XP is not appropriate,
I solved that problem by changing the driver of the sound card.
(the new driver was from the installation CD of the sound card)

The problem is:
How can I change the driver from the wrong one to the appropriate one in Ubuntu?

*There is no Linux driver in the installation CD
The sound card is Creative ES1371, Ensoniq Audio PCI

I also know that there is a program called ALSA that can solve my problem. Can anyone tell me how to use specifically?

thx~

---

### Post by iponeverything on 2010-04-08
See:

[https://help.ubuntu.com/community/HowToSetupSoundCards](https://help.ubuntu.com/community/HowToSetupSoundCards)

According to the above page, there is a module for your card.

---

### Post by lv8402 on 2010-04-08
I followed the instructions and did like this:

sudo modprobe snd-ens1371
alsamixer

This is the result shown on alsamixer (nothing changed):
Card: Ensoniq AudioPCI
Chip: Cirrus Logic CS4299 rev 4

I get sliders to move around and it is "working".
However, the computer still reboot automatically.

I also did like this:
sudo nano /etc/modules
then i added "snd-ens1371" into the file
but still the same

What should I do?

---

### Post by lidex on 2010-04-08
Try disabling onboard audio in bios and blacklisting its driver.

---

### Post by lv8402 on 2010-04-09
I have disabled onboard audio since I installed the PCI audio card.
I tried to enable onboard audio and disable it again, but still the same.

I tried to use "aplay -l" command, Result:

**** List of PLAYBACK Hardware Devices ****
card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I don't know why there are two audio devices, but the model of card is correct.

Now, when I'm going to play sounds, the computer can play sounds for about 30 seconds without errors,
 but after 30 seconds, the speaker will produce some "beep" sounds non-stop, 
the screen also stopped at the same time and I can't control the computer,
it keeps "beeping" until I push the restart button.

If I disable the PCI audio card in Ubuntu, the computer works fine but no sounds.

Any idea?

thx~ everyone!!!

---

### Post by lidex on 2010-04-09
Do you have the medibuntu repository enabled? If not, do this in a terminal:
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

```
sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu
```

```
sudo apt-get install alsa-firmware alsa-firmware-loaders
```

Now reboot.

---

### Post by lv8402 on 2010-04-09
I enabled medibuntu repository but just the same.
I should return to Windows...

---

### Post by lv8402 on 2010-04-10
In conclusion, I found that the driver is right but the PCI card still doesn't work. The problem is that when there's a little error made by the PCI audio card, Ubuntu stops working and Windows just ignores the error and keep working/playing sounds.(I know that the quality of the PCI audio card isn't good.)

Can I let Ubuntu accept more errors?

---

