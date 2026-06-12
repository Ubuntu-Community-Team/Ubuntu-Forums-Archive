---
title: "Headphones jack doesn't disable laptop speakers (HP Compaq NC6120)"
date: 2011-01-30
forum: Hardware
---

### Post by Skios on 2011-01-30
The problem is pretty much as described in the topic title. I'm running Ubuntu 10.10 on a HP Compaq NC6120 laptop, and when I plug in my headphones the audio doesn't stop playing over the laptop's speakers. This problem doesn't occur in Windows XP.

Additional info:

I'm running ALSA 1.0.23. Running aplay -l gives the following output:```
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by Skios on 2011-01-30
I solved this problem myself by running alsamixer from the terminal, then enabling headphone and line jack sense by moving over to the relevant sliders and pressing M.

---

### Post by mrsfixit on 2011-02-06
> **Skios said:**
> I solved this problem myself by running alsamixer from the terminal, then enabling headphone and line jack sense by moving over to the relevant sliders and pressing M.

I have this issue on a Dell Studio XPS desktop system, running 10.04 64 bit. It's driving me nuts.

I opened alsamixer using the command line, but there are a ton of things there, and I'm not sure which are the "relevant" sliders, and I don't see anything about "jack sense" there...

Could you please be a little more specific?

---

### Post by cefn on 2011-03-20
@mrsfixit what I can see with alsamixer running are shortened labels, like "Line jac" for "Line Jack Sense".

I used my left and right keys to highlight the different controls, and then I used the M key (for modify I suppose) to switch on Line Jack Sense and "Headphon" (there are two controls with names shortened to "Headphon" - the one called "Headphon" without the volume bar above it is a checkbox for sensing, choose this one).

Immediately I did this, my Compaq NC4000 started switching audio properly when I plug a jack in.

---

### Post by mrsfixit on 2011-03-24
> **cefn said:**
> @mrsfixit what I can see with alsamixer running are shortened labels, like "Line jac" for "Line Jack Sense".

I used my left and right keys to highlight the different controls, and then I used the M key (for modify I suppose) to switch on Line Jack Sense and "Headphon" (there are two controls with names shortened to "Headphon" - the one called "Headphon" without the volume bar above it is a checkbox for sensing, choose this one).

Immediately I did this, my Compaq NC4000 started switching audio properly when I plug a jack in.

I don't have that option. I've got the headphone option, but nothing that says Line Jack. See attached.

[IMG]http://ubuntuforums.org/[IMG]http://i171.photobucket.com/albums/u302/mrsfixit99/Screenshot-GNOMEALSAMixer-1.png[/IMG][IMG]http://ubuntuforums.org/[IMG]http://i171.photobucket.com/albums/u302/mrsfixit99/Screenshot-GNOMEALSAMixer-1.png[/IMG]I've fiddled with all the settings and nothing works.

It's funny that I run 9.10 on 2 laptops, and I don't have an issue with this. The speakers mute when I plug in the headphones. 10.04 obviously broke something...:confused:

---

### Post by lidex on 2011-04-03
@mrsfixit
If your problem is not a simple configuration issue, the fix tends to be hardware specific and that is why it is preferred that you start a new thread as you do not have an HP Compaq NC6120. Having said that, try this and if it doesn't work file a bug as this appears to be a regression. 
Update your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

Bug Reporting:
Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

