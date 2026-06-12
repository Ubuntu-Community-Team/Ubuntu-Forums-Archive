---
title: "Headphones do not work"
date: 2011-05-11
forum: Hardware
---

### Post by stijnr on 2011-05-11
Hi,

I've installed Ubuntu on my Medion laptop (with the wubi installer).
It works nice, but i'm experienceing some sound issues.
The internal speakers work just fine but when I plug in my headphones the sound keeps comming trough the speakers and not the headphones.
I've tried the different options under the soud settings but no matter which ones I choose, I either have sound only from my speakers or no sound at all.
I've also instaled 'ALSA' which gives me more options, but the results remain the same.

As far as hardware is concerned, The 'lshw' command tells me:
```
*-multimedia
     description: Audio device
     product: N10/ICH 7 Family High Definition Audio Controller
     vendor: Intel Corporation
     physical id: 1b
     bus info: pci@0000:00:1b.0
     version: 02
     width: 64 bits
     clock: 33MHz
     capabilities: pm msi pciexpress bus_master cap_list
     configuration: driver=HDA Intel latency=0
     resources: irq:45 memory:d8440000-d8443fff
```
Windows lists my sound card as "Realtek High Definition Audio"

I've downloaded the "realtek-linux-audiopack-5.16" drivers from [http://www.realtek.com/downloads/downloadsCheck.aspx?langid=1&pfid=24&level=4&conn=3&downtypeid=3](http://www.realtek.com/downloads/downloadsCheck.aspx?langid=1&pfid=24&level=4&conn=3&downtypeid=3) but I can't figure out how to install these (running the "install" file creates some extra files and folders, but thats it).

I'm wondering if my sound card is even supported and, if it is, how to get it working.

Any ideas?

---

### Post by Cathhsmom on 2011-05-11
Have you selected your headphones in sound preferences, on the hardware and output tab?

---

### Post by lidex on 2011-05-11
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by stijnr on 2011-05-13
> **Cathhsmom said:**
> Have you selected your headphones in sound preferences, on the hardware and output tab?

On the output tab I have:
Analog Speakers: sound come from the speakers
Analog Output: same as above but very silent
Analog Headphones: no sound

In hardware I have selected the default Analog Stereo Duplex
The other options are:
Analog Stereo Input
Digital Stereo Duplex ( IEC958 )
Digital Stereo ( IEC958 ) Output + Analog Stereo Input
Analog Stereo Output

But nothing works.

---

### Post by stijnr on 2011-05-13
> **lidex said:**
> Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

The link is 
[http://www.alsa-project.org/db/?f=a10883c9b0039363c2ac30d72272e4d5ced77a5c](http://www.alsa-project.org/db/?f=a10883c9b0039363c2ac30d72272e4d5ced77a5c)

---

### Post by lidex on 2011-05-13
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=medion" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by lidex on 2011-05-13
Nothing to see here.

---

### Post by stijnr on 2011-05-15
> **lidex said:**
> Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=medion" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

I've done so, the line got written to the configuration file but sound still doesn't work correctly.
Do I need to change some options as well?

---

### Post by lidex on 2011-05-15
Depends. Check your settings in 'Sound Preferences' and alsamixer.

---

### Post by stijnr on 2011-05-16
Hmm, alsamixer shows an unmuted headphone channel but it has no volumebar...
here is a screenshot

[IMG]http://postimage.org/image/1m9nldvms/[/IMG]

---

### Post by lidex on 2011-05-16
What is further to the right?

---

### Post by stijnr on 2011-05-17
> **lidex said:**
> What is further to the right?

Here's the complete window

---

