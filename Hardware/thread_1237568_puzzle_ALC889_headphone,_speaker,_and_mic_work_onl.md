---
title: "puzzle: ALC889 headphone, speaker, and mic work only on first reboot."
date: 2009-08-11
forum: Hardware
---

### Post by morphet on 2009-08-11
This was meant to be a tutorial, but there is a puzzling catch that I don't understand. Can anyone help? Any insight would be appreciated. The tutorial works as expected, but only if you add "options snd-hda-intel model=auto" to /etc/modprobe.d/alsa-base.conf reboot, and then change the line to "options snd-hda-intel model=3stack-6ch-dig" and reboot again. It works, but if you reboot, the audio will still have all the 3stack6ch sliders, but the headphones will not work AT ALL.

Even if you don't have the solution, but have any ideas why it might be, please chip in.:confused::confused:

******************Begin "tutorial"**********************************
Ok. This is a long tutorial, but at the end of it your ALC889 in a Vaio should work. Mine is a Vaio VGN-AW11M, running Ubuntu 9.04. It has a mic jack, a built-in mic, and a an analog/optical jack.
This will work:
	the card itself
	the mic jack (stereo)
	the ability to listen to the speakers OR the headphones OR both

This will not work:
	auto-detection of headphones (you have to manually say who has what volume)
	the built-in mic

It's a longish howto (7 steps), and there are a couple of weird steps, so make sure to read through it before you do anything, to make sure you understand the steps and are willing to follow them.

Stap 0: make sure you have alsa-utils. If not, go to synaptic and install it.

Step 1: get the High Definition audio codecs or realtek drivers here:
[http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)
Accept the EULA, and look for the Linux entry at the bottom of the page. Click on one of the mirrors and save the file somewhere. You should end up with a file called LinuxPkg_5.12.tar.bz2.
Unpack it.

Step 2: cd into the folder and $sudo ./install this will take a while. There are two possibilities:
a: the installation runs fine.
b:  If the installation exits with the: alsaconf alsactl not found error, download the two attached files to your desktop. *MAKE SURE they do not exist in /usr/sbin, or you'll end up screwing something up. Only copy them to /usr/sbin if they don't already exist. Canonical decided to stop including them in alsa-utils because they caused some conflicts, but the Realtek drivers need them. They shouldn't be a problem, as nothing else in the system calls them. Re-run realtek-linux-audiopack-5.12/install, and it should run fine.

Step 3: the installation brings up some blue screens. Just accept the defaults.

Step 4: $sudo gedit  sudo gedit /etc/modprobe.d/alsa-base.conf, and add the line "options snd-hda-intel model=3stack-6ch-dig" to the end of it. 3 stack means 3 jacks, 6 ch means six channels, and dig means that it has a digital SPDIF (optical jack). I only see 2 jacks, but hey.

Step 5: reboot
Step 6: go to the volume control (the little speaker on the panel -> volume control...), select device "HDA Intel (Alsa mixer)", and preferences. Make sure Master, PCM, Front, Surround,and Capture are checked.

Step 7: You are done! The "Front" slider controls the speakers, and the "Surround" slider controls the headphones. "Capture", in the "Recording" tab controls the mic line sensitivity.
*************************************End "tut". Thanks in advance*********:confused:

---

