---
title: "Can't get sound to work on Ubuntu 10.04 LL"
date: 2010-07-30
forum: Hardware
---

### Post by lunatia138 on 2010-07-30
I honestly don't really know what info I should let you guys know, but like I said in the title, I can't get the sound to work on my comp and I am using Ubuntu 10.04. If it helps any I am running on-board sound from a ASUS M2A-VM motherboard. Other then that I don't know what I need to let you guys know to help me.

---

### Post by dwbsr on 2010-07-31
> **lunatia138 said:**
> I honestly don't really know what info I should let you guys know, but like I said in the title, I can't get the sound to work on my comp and I am using Ubuntu 10.04. If it helps any I am running on-board sound from a ASUS M2A-VM motherboard. Other then that I don't know what I need to let you guys know to help me.


That Asus M2A-VM motherboard has the 

Audio
ALC883 High Definition Audio   6  -Channel  CODEC 

 Support Jack-Sensing, Enumeration, Multi-streaming
 Supports S/PDIF out on bundle card port

---

### Post by lunatia138 on 2010-07-31
Not really sure what what you just said means dwbsr...

---

### Post by lidex on 2010-07-31
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=alc883-6stack-dig bdl_pos_adj=-1 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

---

### Post by lunatia138 on 2010-08-01
OK, I opened the file you told me to open and inserted the code and went to save it and got a message that it could not find the file. I double checked my spelling on the file name and didn't spell anything wrong. Is alsamixer a program I need to install?

---

### Post by lidex on 2010-08-01
I don't understand. If you opened the file it had to be there. What is the exact error message? Alsamixer should be installed already.

---

### Post by kamrul.hasan on 2010-08-01
This is the bottom line output after thae command gksudo gedit /etc/modprobe.d/alsa-base.conf
My soundccard also not working.Can anyone tell me... How can i get my sound.
# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2


My sound card is:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by lunatia138 on 2010-08-01
OK, when it opens the file is the file supposed to be blank? And the error I was getting is this: Could not find the file /ect/modprobe.d/alsa-base.conf.

---

### Post by lidex on 2010-08-01
> **lunatia138 said:**
> OK, when it opens the file is the file supposed to be blank? And the error I was getting is this: Could not find the file /ect/modprobe.d/alsa-base.conf.

No. Copy and paste the command - should be etc, not ect

---

### Post by lunatia138 on 2010-08-02
OK, now that I have fixed my typo and added that line to the file and did everything that you said to do and I am still getting no sound whatsoever. Anymore ideas for me to try?

---

### Post by lidex on 2010-08-02
What profile is selected for your sound card in sound preferences? Do the headphones work? Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by lunatia138 on 2010-08-02
The profile that is selected in my sound preferences is Digital Stereo (IEC958 ) Output + Analog Stereo Input.  The headphones I am using do work, I have tried them on other devices.  The uploaded info that you had requested can be viewed here: [http://www.alsa-project.org/db/?f=36ba10a892f4f7dc46b6330ccbbaea95c564389c](http://www.alsa-project.org/db/?f=36ba10a892f4f7dc46b6330ccbbaea95c564389c)

---

### Post by lidex on 2010-08-02
I have an asus board with alc883, the profile I'm currently using is:
```
Analog Stereo Output + Digital Stereo (IEC958 ) Input 
``` Have you tried that or 'Analog Stereo Duplex'? I get no sound with Digital Output.

What I meant in the previous post is do you have audio on the headphone out?

---

### Post by lunatia138 on 2010-08-02
OK, I tried both of those profiles and still had no success, and as for the audio on the headphone out I believe I do.

---

### Post by lidex on 2010-08-02
Upgrade your alsa install via the link in my sig.

---

### Post by lunatia138 on 2010-08-04
OK, I am fairly sure that I wasn't doing something right because I followed the link in your sig and tried to follow the install instruction it had but nothing was doing anything.  I tried following what the instructions told me to do multiple times.  So yeah, I think I am finally hopeless with this.

---

