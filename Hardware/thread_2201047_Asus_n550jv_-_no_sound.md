---
title: "Asus n550jv - no sound"
date: 2014-01-22
forum: Hardware
---

### Post by riccardo.noc on 2014-01-22
Hi all,
I bought a N550JV. I just finished to solve the famous "battery problem" (as you can read in this thread -> [http://ubuntuforums.org/showthread.php?t=2176915&page=2](http://ubuntuforums.org/showthread.php?t=2176915&page=2) ) and now.... oh, there's a new challenge for us. :(
Randomly happens that linux starts without audio. All programs can't detect the soundcard. 
This is a known issue (I found the same thing while searching on internet )
Someone said that you can solve it by upgrading the kernel to 3.12... but a somewhere tells that microphone could not work after the upgrade.

Is there someone that share the same problem? Best regards to all :(

---

### Post by Yellow Pasque on 2014-01-22
The best thing to do in this case is get two copies of the logs below. Make one copy for when sounds works and one copy for when it doesn't work. 

[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
[https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)

File a bug and attach the logs (clearly label the logs working and not-working).
```
ubuntu-bug audio
```

---

### Post by cryos on 2014-01-31
I have the same problem, i had the battery not charging problem and after i fixed it the audio stopped work!!!
It's very strange!!! with the earphones the audio work but not with the speakers...

---

### Post by cryos on 2014-02-14
I fund the problem! If I reboot from windows, I have no sound, probably windows put the notebook in a problematic status for linux.
Starting the notebook from switched off the audio work perfectly!

---

### Post by andrey_ on 2014-07-03
> **riccardo.noc said:**
> Hi all,
I bought a N550JV. I just finished to solve the famous "battery problem" (as you can read in this thread -> [http://ubuntuforums.org/showthread.php?t=2176915&page=2](http://ubuntuforums.org/showthread.php?t=2176915&page=2) ) and now.... oh, there's a new challenge for us. :(
Randomly happens that linux starts without audio. All programs can't detect the soundcard. 
This is a known issue (I found the same thing while searching on internet )
Someone said that you can solve it by upgrading the kernel to 3.12... but a somewhere tells that microphone could not work after the upgrade.

Is there someone that share the same problem? Best regards to all :(

The best solution I've found for the sound issue is to "suspend" your notebook and the sound will appear as soon as you resume it, to avoid the sound loss you 
need to use "shutdown" in Windows menu rather that "Restart". 

Hope that helps...

---

### Post by erikas3 on 2015-01-02
[https://wiki.archlinux.org/index.php/ASUS_N550JV](https://wiki.archlinux.org/index.php/ASUS_N550JV) find everything you need here. I almost provided workaround for every possible bug. Now testing the fix of not working sound after rebooting from Windows to linux. ;) You will find all the information there

---

