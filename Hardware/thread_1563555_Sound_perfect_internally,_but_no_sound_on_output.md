---
title: "Sound perfect internally, but no sound on output"
date: 2010-08-29
forum: Hardware
---

### Post by kespindler on 2010-08-29
Hey,

I am having a problem on my asus eeepc (1015pe) exactly as the title describes. The sound runs perfectly on internal speakers. If I plug a set of speakers into the speaker jack, the internally speakers are correctly silenced, but no sound comes out of the external speakers. 

Any ideas?

Thank you,

Kurt

---

### Post by ubonetu on 2010-08-29
Similar problem except my external speakers play w/o silencing the internal ones...

ASUS k60ij

wb

---

### Post by bark50 on 2010-08-29
I'm no expert, but at least my suggestions won't gork your computer.  :lolflag:  Have you taken a look at your sound preferences (Preferences -> Sound)?  In the box that comes up, take a look at the "Output" tab.  If there's more than one selection where it says "Choose a device for sound output:", click on your options and see if one of them allows sound through your speakers.

If no dice from that, click on the "Hardware" tab.  There you'll see something that says "Settings for the selected device" and a menu for different profiles.  Take note of the profile you're currently using since that one lets your internal speakers work, and try some of the other ones out while something is playing through your external speakers.

If this doesn't work, we'll have to punt your problem to someone with more knowledge.

---

### Post by gianpiero on 2010-09-16
I've the same problem and I can't find a solution!
Could you help me?
Thank

---

### Post by lidex on 2010-09-17
> **kespindler said:**
> Hey,

I am having a problem on my asus eeepc (1015pe) exactly as the title describes. The sound runs perfectly on internal speakers. If I plug a set of speakers into the speaker jack, the internally speakers are correctly silenced, but no sound comes out of the external speakers. 

Any ideas?

Thank you,

Kurt

Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"

---

### Post by ThatBum on 2010-09-18
I know what your problem is. I have the exact same model netbook. It's a bug in ALSA, for which a fix hasn't been publicly released yet. You need to get the backports kernel module. Install linux-backports-modules-alsa-lucid-generic, and reboot. Your output on the 1015 should work fine now. I think my microphone didn't work before installing this module too, so check that out as well.

---

### Post by BrainScientist on 2010-09-18
Having the same issue with my Eee PC 1015 PED; and the microphone does not work.

I tried the fix proposed by ThatBurn, but unfortunately it did not work (but thank you for making the suggestions!) 

Any new suggestions regarding this issue would be greatly appreciated.

Martin

---

### Post by ThatBum on 2010-09-18
Mr. Brain, are you sure the module is active? In Sound Preferences (System->Preferences->Sound, or click your volume indicator applet thing and hit 'Sound Preferences...'),  set the profile under the Hardware tab for 'Analog Stereo Duplex,' so  both the input and output work simultaneously, hence the duplex part.

Next, under the Output tab, the only device there, 'Internal Audio Analog Stereo,' should have three states under 'Connector': 'Analog Headphones,' 'Analog Output,' and 'Analog Speakers.' Select 'Analog Speakers,' because the other two will only let audio out the jack in the side and not the speakers in the netbook. It should switch over automaticly when you plug and unplug external speakers.

Finally, for your microphone, go the the Input tab and select the only bullet there, 'Internal Audio Analog Stereo,' and put the Input Volume slider halfway between Unamplified and 100% for best volume. Tap the mic in the frame of the netbook and watch the input meter to be sure it's working.

If you have no idea what I'm saying because some of the stuff isn't there (like 'Analog Headphones'), then the module didn't install right, or you didn't reboot. The package linux-backports-modules-alsa-lucid-generic is actually a meta package, it really has the real module for the kernel you have depending on it. If you have kernel 2.6.32-24-generic for example, it should have also installed linux-backports-modules-alsa-2.6.32-24-generic, which is what is actually doing the work, so make sure that is installed.

I hope I helped.

---

### Post by ipey on 2010-09-23
I have the same problem with my eee pc 1015p. No sound card was detected when I ran "aplay -l" so I installed alsa driver manually (since driver manager only said "no propriety drivers found). It worked perfectly for me but somehow the problem always reappears after updates installation so I always have to install alsa again and again. I'm currently searching for permanent solution to this problem all over the internet but if anyone knows some tricks and is willing to share it here, I'd be extremely grateful.

---

### Post by amt1205 on 2010-09-23
Dear Friends,
I'm having same problem.
I've baught HP mini110-3009TU in last month, installed 10.04 lucid.
My enternal speakers are not playing sound while headphone is playing good. 
sugest something.
amit

---

### Post by ipey on 2010-09-23
just found this:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by ThatBum on 2010-09-24
[QUOTE=ipey]It worked perfectly for me but somehow the problem always reappears after updates installation so I always have to install alsa again and again.[/QUOTE]

The only thing I know if if you install the aftermentioned package, linux-backports-modules-alsa-lucid-generic, it will install the kernel module for your kernel dynamically, as they are updated. If you look at the description of one of the actual kernel modules, it says this:

[QUOTE=Synaptic]This package contains modules supplied by Ubuntu for Linux 2.6.32 ALSA
snapshots from [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

You likely do not want to install this package directly. Instead, install
the linux-backports-modules-alsa-lucid-generic meta-package, which will ensure that upgrades work
correctly, and that supporting packages are also installed.[/QUOTE]

So try that.

[QUOTE=amt1205] My enternal speakers are not playing sound while headphone is playing good.[/QUOTE]

Try going to Sound Preferences, to the Output tab, and change the Connector dropdown on the Internal Audio Analog Stereo to Analog Speakers from anything else. The other settings, I have noticed, output audio to the jack, but not the internal speakers.

---

### Post by ipey on 2010-10-01
> **ThatBum said:**
> The only thing I know if if you install the aftermentioned package, linux-backports-modules-alsa-lucid-generic, it will install the kernel module for your kernel dynamically, as they are updated. 

What an enlightenment. I should have looked into any details. thanks a lot!!

---

### Post by MarkieB on 2010-10-06
no longer participating in ubuntuforums.org

---

### Post by ThatBum on 2010-10-13
Attention!

If you upgrade to Maverick, none of this is necessary. Maverick already has native support for microphone/headphones.

---

### Post by natecarp on 2010-12-01
I had perfectly working sound on my ASUS 1015PE, running 10.10 desktop, and then all of a sudden it was gone.  I tried all sorts of fixes, including uninstalling and reinstalling ALSA drivers, but discovered the funniest fix: put your computer into suspend mode, and then wake it back up.  My sound has been working fine ever since.  Apparently there's a glitch with many netbooks and the suspend command, especially if you put your machine into suspend while running an application that uses sound.

---

### Post by lidex on 2010-12-02
> **natecarp said:**
> I had perfectly working sound on my ASUS 1015PE, running 10.10 desktop, and then all of a sudden it was gone.  I tried all sorts of fixes, including uninstalling and reinstalling ALSA drivers, but discovered the funniest fix: put your computer into suspend mode, and then wake it back up.  My sound has been working fine ever since.  Apparently there's a glitch with many netbooks and the suspend command, especially if you put your machine into suspend while running an application that uses sound.

If your audio just goes out it may be useful to reload alsa:
```
sudo alsa force-reload
```

---

