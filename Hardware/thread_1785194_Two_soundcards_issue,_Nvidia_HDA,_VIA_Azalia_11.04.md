---
title: "Two soundcards issue, Nvidia HDA, VIA Azalia 11.04"
date: 2011-06-17
forum: Hardware
---

### Post by luishasbon on 2011-06-17
Greetings dear community.

I recently went form 10.04 to 11.04; I have an Nvidia 450 video card, with support through hdmi port for hda audio; my motherboard has an integrated soundcard from VIA, with the reference VT1708/A Azalia HDA; so the fact is that considering the Nvidia 450 audio streaming support, I have two soundcards, after installing 11.04; It resulted that I had no audio, I ran lspci -k, and it seems, both the Nvidia soundcard and Via Azalia soundcard are using the same module "snd-hda-intel" with the same driver "HDA INTEL".


I have googled and search in the ALSA website and found that my motherboard soundcard "Via Azalia" should be using the snd-via82xx module.

The thing is this, I want to use as default soundcard the Via Azalia because I dont have any mean to use HDMI port from the VGA card; so I thought of using alsamizer for selecting my soundcard, but it only shows the HDA Nvidia; so I thought of blacklisting the snd-hda-intel(nvidia) module and force the loading of the snd-via82xx(VIA Azalia) module, after rebooting, I have no audio, and my system does NOT recognize any soundcard; So My question is; how do i configure Alsa to use the Via Azalia soundcard by default, and how do I configure it in order to use the snd-via82xx module?.

PLEASE, THANK YOU, I NEED YOUR HELP.:D

---

### Post by lidex on 2011-06-18
I believe that is incorrect, the via codec chip does use the snd-hda-intel module. 
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by luishasbon on 2011-06-18
> **lidex said:**
> I believe that is incorrect, the via codec chip does use the snd-hda-intel module. 
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

Thanks for your reply, YES, i found out that this VIA soundcard DOES use the snd-hda-intel module, now what It happens is that both, the VIA Azalia and the NVidia HDA soundcard are using the same module and alsa only recognize the Nvidia HDA as the default soundcard and does NOT recognize the Via Azalia at all, though* lspci does show the Via Azalia as an audio device, so how to configure this module for it to be used only by the Via Azlia? THANKS!

---

### Post by lidex on 2011-06-18
Run the alsa-info script please.

---

### Post by luishasbon on 2011-06-18
> **lidex said:**
> Run the alsa-info script please.

This is the result; 

[http://www.alsa-project.org/db/?f=47941451ccd5d3e469e080ed051de2fcbc520ae9](http://www.alsa-project.org/db/?f=47941451ccd5d3e469e080ed051de2fcbc520ae9)

---

### Post by lidex on 2011-06-18
First thing you'll want to do is go into your bios and make sure onboard audio is enabled. Then edit alsa-base.conf to remove this line:
```
options snd-hda-intel model=3stack
```
To edit: 
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Now reload alsa:
```
sudo alsa force-reload
```
Lastly run the script again.

---

### Post by luishasbon on 2011-06-19
> **lidex said:**
> First thing you'll want to do is go into your bios and make sure onboard audio is enabled. Then edit alsa-base.conf to remove this line:
```
options snd-hda-intel model=3stack
```
To edit: 
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Now reload alsa:
```
sudo alsa force-reload
```
Lastly run the script again.

Hey lidex, hope you are doing great!; that option snd-hda-intel model=3stack was writen by me in an effort for fixing the issue, removing it, keeps the same situation. thank you. Please se my alsa-info.sh result notice that alsa does not recognize my soundcard(Via Azalia) but lspci does. Thanks:p

---

