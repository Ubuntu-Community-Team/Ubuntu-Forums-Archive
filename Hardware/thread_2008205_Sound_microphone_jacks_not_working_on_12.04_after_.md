---
title: "Sound microphone jacks not working on 12.04 after fresh install"
date: 2012-06-22
forum: Hardware
---

### Post by excetara2 on 2012-06-22
My side microphone jacks on my laptop have ceased working after installing 12.04 64 bit. I had no issues in 10.04 but regular speakers work fine. If I plug in the external speakers everything goes silent. Nothing is turned off in alsamixer as far as I can see.

This is only real issue I've had. Had minor issues with display but rectified those by a customized xorg.conf. I just don't know where to start with this so any tips would be great.

---

### Post by charlescarroll1 on 2012-06-24
I'm having a similar issue. After I upgraded to 12.04, my internal microphone stopped working.

---

### Post by nipunshakya on 2012-06-24
i just realised it today after 3 months of ubuntu 12.04 installation that my microphone connected via jack isn't working....

---

### Post by rpk94 on 2012-06-24
I have the same problem. I heard that it was a system bug. The external headphones and mic work perfectly fine with windows, so it rules out a hardware fault.

---

### Post by momashi on 2012-07-06
BUMP!! I am having the exact same issue. It was working just fine in 11.10 and now it's dead.

---

### Post by momashi on 2012-07-06
Found the solution in the following bug report:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/946232](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/946232)
See introduction and Comment #32

David Hessington wrote:
> 
                        Here is an intermediate workaround:
 For those of you who are missing a speaker port, edit /usr/share/pulseaudio/alsa-mixer/paths/analog-output-speaker.conf and comment out all lines that start with "required-any".
 For those of you who are missing an internal mic port, edit /usr/share/pulseaudio/alsa-mixer/paths/analog-input-internal-mic.conf
 and comment out all lines that start with "required-any".
 It is important that you comment out (or remove) all those lines, if you leave one behind, it won't work.
 After the change, you can either execute "pulseaudio -k" or reboot for the changes to take effect.

              



I applied this solution. Went to Sound Settings. selected the Hardware tab and in the bottom area where it says 

Settings for Selected Device:
Profile: <= I selected Analog Stereo Duplex profile (solution did not work with Analog Stereo Output profile)

---

### Post by excetara2 on 2012-07-07
Yeah can do that or depending what computer you have just set at the end of your alsa-base.conf file:


options snd-hda-intel model=dell-md6

so just run:
locate alsa-base.conf
sudo gedit <path-to-base-conf>
Then add at end of the file:
options snd-hda-intel model=dell-m6-dmic  (there are many other options that can be added here but need to look up for other models but for most dell laptops in the last couple years dell-md6 seems to work well from what I remember)

I had forgot I researched this a lot back when I installed 10.04. I had edited my alsa-base.conf file. Now all that is required is the above with maybe a change to the model. It is doing similar to what you are proposing but does so automatically so don't have to manually change the setting.s

---

### Post by excetara2 on 2012-07-07
I would post where the other models are but I can't remember now so just google model settings snd-hda-intel and should be able to find the link somewhere. Cheers

---

