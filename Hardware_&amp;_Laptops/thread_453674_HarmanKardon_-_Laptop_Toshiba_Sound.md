---
title: "Harman/Kardon - Laptop Toshiba Sound"
date: 2007-05-24
forum: Hardware &amp; Laptops
---

### Post by realflapjack on 2007-05-24
Hi all.

I have a little (or mid-little) problem with my Toshiba Notebook with Harman Kardon loudspeakers,.  They are very good, even without good the right configuration. BUT: With windows there is very good surround sound with the specific configuration. with ubuntu feisty the sound is.....well....it IS good, BUT not THAT good. there is scrape and snow.  The hardware must be an Intel ICH6 sound system. I don't know how to solve this....

Greetings from Germany :-)

Marc

---

### Post by teaker1s on 2007-05-25
This  is a suggestion as I don't have the same hardware:-

Alsa can be configured by either by alsaconf and following the prompts, sometimes this isn't enough and the hardware model needs configuring (particularly with laptops) 
**Below is an extract to set my card up-it will point you in the right direction of what your looking for with yours**

> My desktop has an nforce motherboard with an onboard HDA codec. The default ALSA config often won't detect the correct HD audio model, which is more than likely why you all don't have sound.

The solution, which btw is buried somewhere in the Comprehensive Sound Guide, is to do the following -

1. Extract /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz to your /home and open it up. This file contains extra config options for each ALSA module. Scroll down to ' Module snd-hda-intel' and read through this section. You may need to refer to your computer/motherboard's manual to find out which codec you have (ALC883, AD1988 etc). Then determine which of the model options applies to you - eg. you have an ASUS laptop, in which case you would choose the 'asus' option. Or you have a desktop with 5.1 or 7.1 onboard audio with digital out, in which case the right model is '6stack-digout'.

2. Once you have ascertained which HDA model applies to you, do this -
Code:

sudo gedit (or whichever editor you use) /etc/modprobe.d/snd-hda-intel.modprobe
add this line (it's a new file) -
options snd-hda-intel model=your-HDA-model
save and exit

3. Now do this -
Code:

sudo gedit /etc/modprobe.d/alsa-base
add this line at the end, with a two-line break from whatever is before -
options snd-hda-intel model=your-HDA-model
save and exit

4. Reboot, and you should now have sound 

---

