---
title: "Getting Sound to Work on Chromebook with Ubuntu 18.04"
date: 2019-09-08
forum: Hardware
---

### Post by kralicemira on 2019-09-08
SOLUTION: Get GalliumOS - don't bother tinkering with chromebooks without it. Solved all problems with simple install (except touchpad doesn't work - but mouse works so no big deal for me)

Trying to get internal speakers / headphones to work on HP Chromebook 14 with Ubuntu 18.04 

The primary answer is found [here]("https://wiki.archlinux.org/index.php/Acer_CB3-131_Chromebook")

However it did not work for me.

Another solution is [here]("https://www.linuxuprising.com/2018/06/fix-no-sound-dummy-output-issue-in.html") 

But it did not work for me even when I inputed the specific device code.

The sound hardware on my HP Chromebook 14 are the same as the guy who posted this thread marked as solved [here]("https://ubuntuforums.org/showthread.php?t=2412974")

The thread was closed without actually revealing the answer. He posted an [expired link]("http://azloco.org/?q=node/273") and said this solved it. The moderator closed the thread without allowing anyone to repost the link. I finally found the original post [here]("https://www.azloco.org/2018/08/26/adventures-of-the-chromebook-part-2/")

The code in question that helped alsa recognize the card for the Arizona club was:
```
git clone &#8211;depth 1 https://github.com/plbossart/UCM.git
cd UCM
sudo cp -r chtmax98090/ /usr/share/alsa/ucm/
alsaucm -c chtmax98090 set _verb HiFi set _enadev Speakers
sudo alsactl store
```

Similar code and similar problem are posted [here]("https://askubuntu.com/questions/1122612/ubuntu-18-04-only-audio-option-is-hdmi-and-does-not-work")

Both the above codes allow Ubuntu to recognize the hardware. HDMI and external bluetooth speakers now work but internal speakers, headphones and plugged in external speakers do not.

The blogger in Arizona said he fixed it by changing it all to GOOGLE-Quawks-1.0-Quawks. I interpreted his intentions with these codes and steps:
```
sudo mkdir /usr/share/alsa/ucm/GOOGLE-Quawks-1.0-Quawks/
sudo chown myusername /usr/share/alsa/ucm/GOOGLE-Quawks-1.0-Quawks/
```
Then I copied and pasted the files from chtmax98090 into the new folder and renamed chtmax98090.conf to GOOGLE-Quawks-1.0-Quawks.conf
```
sudo chown root /usr/share/alsa/ucm/GOOGLE-Quawks-1.0-Quawks/
sudo alsaucm -c GOOGLE-Quawks-1.0-Quawks.conf set _verb HiFi set _enadev Speakers
sudo alsactl store
```

Again he says go pick 'stereo analog' from the config tab in pulseaudio but I did not find that option.

Pressing on, I found other threads that say they solved it by selecting 'Analog Stereo Duplex' profile in pulseaudio. Unfortunately that does not show up as an option for me. I only get 'default' and 'off'. 

One post said it is possible to write your own pulseaudio profile using this code to access the default pulse profiles:
```
sudo gedit /usr/share/pulseaudio/alsa-mixer/profile-sets/default.conf
```

One profile I found for Analog Stereo Duplex was:
[Profile output:analog-stereo+output:iec958-stereo+input:analog-stereo]
description = Digital Stereo (IEC958) Output + Analog Stereo Duplex
output-mappings = analog-stereo iec958-stereo
input-mappings = analog-stereo

Unfortunately, this did not allow any new profile to appear in pulse for me.

Someone with the same HDA Intel PCH card said he runs:
```
pacmd list-cards 
```

And gets these profiles as output:
        Profiles:
            output:analog-stereo: Analogue Stereo Output (sinks: 1, sources: 0, priority. 6000)
            output:analog-stereo+input:analog-stereo: Analogue Stereo Duplex (sinks: 1, sources: 1, priority. 6060)
            output:analog-surround-40: Analogue Surround 4.0 Output (sinks: 1, sources: 0, priority. 700)
            output:analog-surround-40+input:analog-stereo: Analogue Surround 4.0 Output + Analogue Stereo Input (sinks: 1, sources: 1, priority. 760)
            output:analog-surround-41: Analogue Surround 4.1 Output (sinks: 1, sources: 0, priority. 800)
            output:analog-surround-41+input:analog-stereo: Analogue Surround 4.1 Output + Analogue Stereo Input (sinks: 1, sources: 1, priority. 860)
            output:analog-surround-50: Analogue Surround 5.0 Output (sinks: 1, sources: 0, priority. 700)
            output:analog-surround-50+input:analog-stereo: Analogue Surround 5.0 Output + Analogue Stereo Input (sinks: 1, sources: 1, priority. 760)
            output:analog-surround-51: Analogue Surround 5.1 Output (sinks: 1, sources: 0, priority. 800)
            output:analog-surround-51+input:analog-stereo: Analogue Surround 5.1 Output + Analogue Stereo Input (sinks: 1, sources: 1, priority. 860)
            input:analog-stereo: Analogue Stereo Input (sinks: 0, sources: 1, priority. 60)
            off: Off (sinks: 0, sources: 0, priority. 0)
        Active Profile: output:analog-stereo+input:analog-stereo

I get none of these.

My best guess is that I need to write a pulse profile that recognizes Analogue Stereo Duplex

1) Can anyone out there reverse engineer a profile using this info?
 output:analog-stereo+input:analog-stereo: Analogue Stereo Duplex (sinks: 1, sources: 1, priority. 6060)

2) I have tried this after installing Ubuntu, Xubuntu, and Bionic Puppy. None of them is able to give me sound using the internal hardware. (My preference is Xubuntu)
- At one point I did get sound on Ubuntu but after reboot, it no longer worked. So it might be a setting that I'm not aware of, but I know the hardware works. 
- tinkering with alsamixer only fried my speakers (I could feel and smell it burning) I tested them later with a chromebook reboot and the speakers still work but not when I reloaded bionic beaver. I don't want to tinker with settings unless I know exactly what I'm supposed to look for. 

3) My hardware specs are as follows:
Atom Processor Z36xxx/Z37xxx Series High Definition Audio
Card: HDA Intel PCH 
Chip: Intel Valleyview2 HDMI  

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: chtmax98090 [chtmax98090], device 0: Audio (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: chtmax98090 [chtmax98090], device 1: Deep-Buffer Audio (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
Please help! I have little kids and only get to work on this at nights and it's ruined over a week of sleep!

---

### Post by kralicemira on 2019-11-21
I'm replying here to my post what I finally found after hours and hours of searching - GalliumOS. It's Xubuntu tailored for chromebooks. Once I got that installed all problems got solved, except new issue got introduced - touchpad won't work. Sound and all other drivers and devices work with GalliumOS installed. (Sound occasionally stutters but overall works well.)

---

