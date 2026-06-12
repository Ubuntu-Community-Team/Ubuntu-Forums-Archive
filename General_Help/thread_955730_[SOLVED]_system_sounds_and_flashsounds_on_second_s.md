---
title: "[SOLVED] system sounds and flashsounds on second soundcard, please!"
date: 2008-10-22
forum: General Help
---

### Post by Bazon on 2008-10-22
Hello.

Today I made a dist upgrade to Hardy and an old problem re-appeared:

I have two soundcards, a snd_via82xx onboard and a snd_ens1371 PCI-card.
I want to use the snd_ens1371 for normal sounds and the onboard card only for special things like skype-phoning, so I don't want to disable the onboard sound on BIOS.

My problem is:
System-sounds and the Flashplayer use the onboard card instead of the PCI-device!

In former distributions, the following tricks helped:
inserting in /etc/modules:
```
snd_ens1371 index=0
snd_via82xx index=1
```
inserting in /etc/modprobe.d/alsa-base
```
options snd_ens1371 index=0
options snd_via82xx index=1
```

but with hardy, that doesn't help anymore.
So what can I do to make my PCI soundcard the default sound card?

---

### Post by kostkon on 2008-10-22
Yes, 8.04 uses its own software sound mixer (it does not use the hardware mixer of your soundcard anymore, even if your card has one) which is called *PulseAudio* and it is the one that has the control of the audio on your desktop.

I think you have to change which card *PulseAudio* uses as its default. Thus, you should install the *PulseAudio Device Chooser* (*padevchooser* package).

When your run it (*System -> Sound & Video -> PulseAudio Device Chooser*) its icon will appear on your taskbar. Right-click on it and select *Volume Control...* 

Then, in the *PulseAudio Volume Control* window select the *Output Devices* tab and in that you should see your two sound cards listed. Right-click on the one you want to set as the default and enable the *Default* option.

Using the *Volume Control* you can define which soundcard an application uses to ouput its sound and other neat stuff.

You can set the *Device Chooser* to start every time you login in its *Preferences*.

Hope that helps you...

---

### Post by Bazon on 2008-10-22
OK, thanks, that helped for the system sounds, but Flashplayer and Kaffeine still use the onboard device...

---

### Post by kostkon on 2008-10-22
> **Bazon said:**
> OK, thanks, that helped for the system sounds, but Flashplayer and Kaffeine still use the onboard device...
OK. Try this:
Start playing a *Flash* video, for example, and something in *Kaffeine*, then go to *Volume Control* and in the first tab (*Playback*) you should see these two audio streams (i.e. the *Flash* and *Kaffeine* ones). Right-click on every one of them, select *Move Stream* and then select the soundcard you want them to use.

If you don't see their streams in *Playback* then it means that for some reason they don't use *PulseAudio* but are trying to use the soundcard directly.

There is a possibility that this will be happening with *Flash*, especially if you are using *Flash 9* without the *libflashsupport* package. 

A solution is to install *Flash 10* (which works just fine with *PulseAudio*), since Flash 9 with *libflashsupport* makes *Firefox* to crash a lot (*libflashsupport* allows *Flash 9* to use *PulseAudio*).

There are some ways to better setup your system for PulseAudio. If you need such a help, say so.

---

### Post by Bazon on 2008-10-22
Great, that worked!
Many thanks...! :-)

---

