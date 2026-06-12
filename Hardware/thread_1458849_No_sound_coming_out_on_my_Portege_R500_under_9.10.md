---
title: "No sound coming out on my Portege R500 under 9.10"
date: 2010-04-20
forum: Hardware
---

### Post by portilhe on 2010-04-20
I have no sound coming out at all, either from the loudspeakers nor throught the audio output line (headphones) - which makes me think that the problem is not hardware.

I noticed this since my last software update.

I do have audio input (I can see the sound levels moving as I speak over the mic).

I am not an experianced user, I don't even know how to start figuring out what to do.

Can anyone help me? Thanks!

-Manu

---

### Post by lidex on 2010-04-21
Have a look at this page to see if any karmic bugs have bit you:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")
We should get you more familiarized with the terminal as you may need it. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by portilhe on 2010-04-21
Hi, and thanks for trying to help!

My laptop is a 2 year old Toshiba Portege R500.

Here is the output from the code:
```
portilhe@gavdos:~$ uname -a
Linux gavdos 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:27 UTC 2010 x86_64 GNU/Linux
portilhe@gavdos:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
portilhe@gavdos:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.20.
portilhe@gavdos:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC262

```

---

### Post by lidex on 2010-04-21
First go here and work through the common karmic audio issues and make sure to install the alsa-backports:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")

---

### Post by portilhe on 2010-04-21
It is still not working... I tried the solutions on the page you posted here. I installed the linux-backports-modules-alsa-2.6.31-21-generic (first I tried with the server version, but it didn't work either). :(
-m

---

### Post by lidex on 2010-04-21
OK. Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=toshiba-s06  
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default

---

### Post by portilhe on 2010-04-22
Something strange is happening. In the Sound preferences, in the Hardware tab, nothing shows up. Before there was an icon of the sound card, but now there is absolutely nothing. This happened after installing the linux-backports-modules-alsa-2.6.31.21-generic. Is there something else I should install?

I changed the file as you suggested. Also, my alsamixer doesn't have an F6 option, maybe it's an old version (v1.0.20)?

---

### Post by portilhe on 2010-04-22
Okay, I think I am narrowing it down.

I booted into Windows, which I very rarely use, to see if I had sound there. The sound was on mute (is it possible that Windows "locked" the sound card into mute?). I took it out of mute and rebooted into linux.

Then I decided to retry the solutions on the webpage you sent me.

Ah. I should say that at this point the sound card did not appear in the sound preferences.

At the terminal I got the following:
```
portilhe@gavdos:~$ sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
[sudo] password for portilhe: 
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  timidity   1715 F.... timidity
/dev/snd/pcmC0D0p:   timidity   1715 F...m timidity
/dev/snd/seq:        timidity   1715 F.... timidity
/dev/snd/timer:      timidity   1715 f.... timidity

```

Then I followed the instructions:
```
portilhe@gavdos:~$ sudo killall timidity
portilhe@gavdos:~$ sudo fuser -v /dev/dsp* /dev/snd/* /dev/s
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  portilhe   1973 F.... pulseaudio
/dev/snd/pcmC0D0p:   portilhe   1973 F...m pulseaudio

```

And at this point sound starts to work and the sound card appears on the sound preferences.

In the mean time I uninstalled the linux-backports-modules-alsa-....

Is this making sense?

---

### Post by lidex on 2010-04-22
Yesit's making a lot of sense. Your audio good now?

---

### Post by portilhe on 2010-04-23
The audio is good now, but I'd like to not have to do
```
portilhe@gavdos:~$ sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
[sudo] password for portilhe: 
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  timidity   1664 F.... timidity
/dev/snd/pcmC0D0p:   timidity   1664 F...m timidity
/dev/snd/seq:        timidity   1664 F.... timidity
/dev/snd/timer:      timidity   1664 f.... timidity
portilhe@gavdos:~$ sudo killall timidity

```
everytime I log in. Is there a way to accomplish this?
Thanks for all the help!

---

### Post by lidex on 2010-04-23
Do you use it? If not go to synaptic and search 'timidity'. Uninstall all the timidity packages. Alternately:
> timidity

Timidity is a MIDI file player. You can reconfigure it to use the esound protocol (which pulseaudio implements) by editing the file /etc/default/timidity (you'll have to be root to do that). Find the row saying 'TIM_ALSASEQPARAMS="-Os"' and change it to:

TIM_ALSASEQPARAMS="-Oe"

Then restart timidity:

sudo /etc/init.d/timidity force-reload

---

### Post by portilhe on 2010-04-27
Sorry for taking long to reply, I've been away for the past 3 days.

I had tried the solution you quote from the Debugging Sound Problems' webpage, but it didn't work for me. Now I've unistalled Timidity and it is working fine! I don't even remember installing it and don't use it much, don't know why I had it.

Thanks again for all the help.

-Manu

---

