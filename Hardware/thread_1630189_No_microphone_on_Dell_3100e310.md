---
title: "No microphone on Dell 3100/e310"
date: 2010-11-24
forum: Hardware
---

### Post by TightRopez on 2010-11-24
I have been digging and digging for the solution to this:  

There seems a common and large problem with pulseaudio and microphones:

This is on a Dell Dimension 3100 Desk top. Running Mint 10, though I've tried straight Ubuntu 10.04, and 10.10

I can hear sound well. 

I have gone into pavucontrol and seen the microphone showing small blips in sound.  

I am trying to use skype, I never get any input from it, though if I have rythmbox playing it did record that into the Skype call. 

I'm horribly frustrated. 

In another thread it was requested to link to an Alsa script to display your sound equipment.  Here is that link:

[http://www.alsa-project.org/db/?f=198f1569e3bfbe789e0cc14f0eaf28440647e293](http://www.alsa-project.org/db/?f=198f1569e3bfbe789e0cc14f0eaf28440647e293)



The first few lines of the information is: 

!!Linux Distribution
!!------------------

Linux Mint 10 Julia \n \l DISTRIB_ID=LinuxMint DISTRIB_DESCRIPTION="Linux Mint 10 Julia"


!!DMI Information
!!---------------

Manufacturer:      Dell Inc.                
Product Name:      Dell DV051                   


!!Kernel Information
!!------------------

Kernel release:    2.6.35-22-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    
Utilities version:  1.0.23


!!Loaded ALSA modules
!!-------------------

snd_hda_intel

I have screen shots of alsamixer run from command line if that is useful. 

Please please, I'm stumped and discouraged. 

Thank you

---

### Post by lidex on 2010-11-27
Interesting. I'll need you to open alsa-base.conf and remove the model entries you placed there.
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Save and close. Now reboot and re-install alsa.
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**Reboot.**
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**

Play that last bit by ear, not sure of the collateral packages in mint, so just watch for what gets removed.

---

### Post by TightRopez on 2010-12-03
> **lidex said:**
> Interesting. I'll need you to open alsa-base.conf and remove the model entries you placed there.
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Save and close. Now reboot and re-install alsa.
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**Reboot.**
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**

Play that last bit by ear, not sure of the collateral packages in mint, so just watch for what gets removed.


Followed the instructions and it WORKED.   Thank you, Thank you,

---

### Post by lidex on 2010-12-03
You're welcome. Please mark the thread as solved using 'Thread Tools' up top.

---

