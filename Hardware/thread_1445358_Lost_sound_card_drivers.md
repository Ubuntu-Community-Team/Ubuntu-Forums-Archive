---
title: "Lost sound card drivers"
date: 2010-04-02
forum: Hardware
---

### Post by gbarron on 2010-04-02
Hi Guys,

I am running the latest version Ubuntu and I have installed a new sound card.  Its a Creative X-Fi Xtreme Audio.  After the install I rebooted and everything worked perfectly.  

The problem came when I restarted again after an hour or so.  After the second reboot Ubuntu no longer recognised that there is a sound card and there are no sounds generated.  I know the hardware is working because I can boot in to Windows and it produces sound through the same device.

I have gone through the diagnostic pages for sound, but the steps have not solved the problem.

When I type sudo aplay -l it reports that there are no sound cards installed.

Any help would be greatly appreciated.

Regards
Gary

---

### Post by gabak on 2010-04-02
Refreshing/Reinstalling the drivers

Sometimes, sound might be configured correctly, but for some reason or another (tinkering) it stops working. If this is the case, you can purge your custom changes, and restore your system to a clean base. This may clear up your problem, and restore you to a working state.

Open a terminal and type sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2. This will purge any custom configurations that you've made, and any hand-compiled modules that you've built, and restore your sound stack to the "Official" Ubuntu core. You can also do this as two separate steps: sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils and then sudo apt-get install linux-sound-base alsa-base alsa-utils , but this may result in some other packages which depend on the sound-base and alsa-utils from being removed, such as gdm and ubuntu-desktop. If this happens, then do sudo apt-get install gdm ubuntu-desktop


plz tell me if worked for u

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by gbarron on 2010-04-11
Hi,

Thanks for the reply.  I have run the command and restarted the machine, but there is still no sound.

Regards
Gary

---

### Post by lidex on 2010-04-11
Have a look here:
[http://wiki.debian.org/X-Fi]("http://wiki.debian.org/X-Fi")

There is a thread specific to the X-Fi cards on this forum as well. Just search for it.

---

