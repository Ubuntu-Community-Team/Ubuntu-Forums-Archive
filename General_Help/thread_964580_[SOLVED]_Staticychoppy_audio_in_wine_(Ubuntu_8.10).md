---
title: "[SOLVED] Staticy/choppy audio in wine (Ubuntu 8.10)"
date: 2008-10-31
forum: General Help
---

### Post by captainmustard on 2008-10-31
Okay, so I upgraded from Ubuntu 8.4 to 8.10 earlier today, and everything went smoothly.

I'm having one problem, though 

Whenever I open up World of Warcraft under Wine, the audio is absolutely horrible! I've never had a problem like this before, so I know it's something in 8.10 that's doing it.

The only advice I could find with google was to kill the PulseAudio process with the system monitor, but that just kills *all* of my sound.

Does anyone else have this problem? What do I do?

](*,)

---

### Post by lH)4~mK0e on 2008-10-31
I experienced this as well.  If you are using the latest version the audio for WoW seems broken, again.  If you have the audio fix suggested from the Ubuntu help site that you include in your Config.wtf you might want to try buffer values like 50 or 100.

```

SET Sound_SoundOutputSystem "1"
SET Sound_SoundBufferSize "150" <-- if your value looks like this try the
above mentioned.

```

I just didn't want to fight with it that much so I went back to the repo version (in hardy) but you can get 1.1.5 from winehq.org under their Ubuntu section.  The issue is not present in that version.  

Also, I had a lot of issues getting wine to work with pulseaudio and mumble voice chat.  I had to set all the sound preferences to ALSA and delete all my asound config files (/etc/asound* and ~/.asound*) and reboot.  Then I could voice chat, WoW, stream audio, everything but flash audio.  My sound card is an nforce3 Realtek based codec.

---

### Post by gilad g on 2008-10-31
I'm having this problem too, only on a **different** game - civ4.
Before upgrading (on hardy, 8.04) the sound was perfect, and I had no other problems with the game. Now with 8.10, the sound is choppy and contains a lot of static, and in general the game (coming to think of it, also my entire system, actually) seemed to slow down.

I've tried to change the settings in System -> Preferences -> Sound to ALSA, and then rebooted, it didn't help.
Using wine v1.1.7 .
Any ideas? :-(

---

### Post by lH)4~mK0e on 2008-10-31
Yes, try using Wine 1.1.5 instead, there are some issues with audio that I have noticed with 1.1.7 possibly due to their attempt to offer Direct X 10 support.  You can find the archive list under the Get Wine Now link, Ubuntu section of the winehq.org website.

---

### Post by gilad g on 2008-10-31
> **miwarlock002 said:**
>  You can find the archive list under the Get Wine Now link, Ubuntu section of the winehq.org website.

Thanks for your help :)
I tried wine 1.1.6 (no 1.1.5 for Ibex at winehq), didn't change anything.

---

### Post by sacha99 on 2008-10-31
The following worked for me.

Run

```
padsp winecfg
```

On the audio tab, deselect ALSA and select OSS instead.

Then, use padsp again when invoking wine:

```
padsp wine Wow.exe
```

Good luck!


Also - just to say that I also find 8.10 much slower. I multibox 3 accounts at the same time, and have had to dial back the effects settings considerably to get a reasonable framerate. Hopefully just temporary!

---

### Post by thumper13 on 2008-10-31
Give this one a try:

[http://ubuntuforums.org/showthread.php?p=6075974#post6075974](http://ubuntuforums.org/showthread.php?p=6075974#post6075974)

Worked for me.

---

### Post by gilad g on 2008-11-01
> **sacha99 said:**
> 
Then, use padsp again when invoking wine:

```
padsp wine Wow.exe
```Good luck!
This worked for me too, thanks :)

---

### Post by Zaphio on 2008-12-29
> **sacha99 said:**
> The following worked for me.

Run

```
padsp winecfg
```

On the audio tab, deselect ALSA and select OSS instead.

Then, use padsp again when invoking wine:

```
padsp wine Wow.exe
```


Golden! thank you very much for this one :-)

---

### Post by hotweiss on 2008-12-31
> **sacha99 said:**
> The following worked for me.

Run

```
padsp winecfg
```

On the audio tab, deselect ALSA and select OSS instead.

Then, use padsp again when invoking wine:

```
padsp wine Wow.exe
```

Good luck!


Also - just to say that I also find 8.10 much slower. I multibox 3 accounts at the same time, and have had to dial back the effects settings considerably to get a reasonable framerate. Hopefully just temporary!

Moving over to OSS eliminated the staticy sound in Frozen Throne.

---

### Post by Stretch611 on 2009-01-31
Thank you that solution worked for me as well.

I had decent quality, but after a random set of time all sound would drop. This happened in both Diablo II and Painkiller. I would need to exit wine and restart in order to restore the sound. I have not had to do this since I changed to OSS sound drivers with the wrapper.

(I'm using wine on Ubuntu 8.10 AMD)

---

