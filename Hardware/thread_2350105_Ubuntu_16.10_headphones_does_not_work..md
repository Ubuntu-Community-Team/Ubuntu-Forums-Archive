---
title: "Ubuntu 16.10 headphones does not work."
date: 2017-01-21
forum: Hardware
---

### Post by cotin18 on 2017-01-21
After a fresh install of Ubuntu 16.10 on my laptop i had to follow this guide to get my headphones working: 

___________________________________________________________________
"I had the same problem. Following these instructions got my headphones working:


Open the terminal and enter the following commands:


cd /usr/share/pulseaudio/alsa-mixer/paths/
sudo cp analog-output-headphones.conf analog-output-headphones.bak
sudo nano analog-output-headphones.conf
Look for the section called [Element Speaker] and change it so that it looks like this:


[Element Speaker]
switch = on
volume = ignore
Save the changes and exit nano.


Create a backup of the corrected analog-output-headphones.conf:


sudo cp analog-output-headphones.conf analog-output-headphones.fixed
Now you can restore the fix if a future installation or update overwrites it.


Reboot."


_______________________________________________________________
After rebooting, you may need to remove and reinsert the headphone plug to get it to work. After it's working, though, you will be able to remove and insert the plug, and behavior will be as expected."
After a couple of days headphones stopped working again and i thought that following this tutorial would fix everything again. IT DID NOT. 


command: 
grep "Codec:" /proc/asound/card*/codec* :


output: 
/proc/asound/card0/codec#0:Codec: Intel Haswell HDMI
/proc/asound/card1/codec#0:Codec: Realtek ALC269VC


Also did this for more information: 

ALSA Information Script v 0.4.64
______________________________________________________________


This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

Here is the output of the ALSA Script: 
More information: [http://www.alsa-project.org/db/?f=607e8cab4c06e43d1edf81a75234fddcba59a39c](http://www.alsa-project.org/db/?f=607e8cab4c06e43d1edf81a75234fddcba59a39c)

______________________________________________________________

**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC269VC Analog [ALC269VC Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 1: ALC269VC Digital [ALC269VC Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



I have tried alot of different guides and nothing works. 
it recognizes when i plug in the jack and shows "Headpones" in sound settings after plug it in the. 
And even shows me the sound bar jumping to the music i am playing, but no sound output. Also tested the headphones on my cell to make sure they were working aswell. Laptop speakers works.

Please let me know if there is any information anyone would need to help me with this mess.

---

### Post by cotin18 on 2017-01-22
Or if anyone know a place i can pay someone to help me that would be awesome! :)

---

### Post by cotin18 on 2017-01-22
Moderator can delete this thread.

---

