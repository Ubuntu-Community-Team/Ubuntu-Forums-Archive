---
title: "install on Ausu A5Ec laptop"
date: 2006-02-18
forum: Hardware &amp; Laptops
---

### Post by dhalgren on 2006-02-18
hi!
I am trying to install breezy on an Ausus A5Ec, but everything stops (all installation activity and everything else) when it hits trying to load the hotplugging module. This happens whether it is a live disk or an actual install.

Does anyone know if there is a work around for this?  

Just so you know, I am not a hacker, and an overly technical reply is likely to produce more confusion for me, so please, if you have some idea, make it simple for me. :) 

Also, this particular laptop has an 8x dual layer dvd burner. Does linux support dual layer burning?

thanks in advance

dhalgren

---

### Post by Bionic_Beefpile on 2006-02-19
I just got Breezy installed on my Asus z63a.  The problem is probably because the sound card is not loading.

Hit Alt-Sys Rq-E during bootup to pass the hotplug stage.  Then do this:
```
sudo gedit /etc/hotplug/blacklist
```
and add this line to the end of the file
```
snd-hda-intel
```

save and reboot, you should get through the hotplug no problem.  You won't have sound until you take some more steps.  You'll need to follow this guide:
[https://wiki.ubuntu.com/HdaIntelSoundHowto](https://wiki.ubuntu.com/HdaIntelSoundHowto)

---

### Post by dhalgren on 2006-02-20
Thank you bionic_beefpile, I can now boot into the system, unfortunately I have not been able to follow either set of instructions from the wiki to produce sound. All reading of documentation has merely produced confusion, especially as the installation of kernal-source has berely produced a tarball in /usr/src, and I have no idea what to do to get it useable.

Do you, or anyone else have more instructions or reference to pages to read that will clear it all up for me?

Yes, I can live without sound on the laptop, but it would be nice to have. :-)

some hours later...
it seems that, somehow, i have completely lost the kernel module snd-hda-intel. it simply isn't there. also, there is no dsp file...
what do I do now?

---

### Post by Bionic_Beefpile on 2006-02-21
I had to upgrade to the 686 kernel (2.6.12-10-686) to get the sound fix to work... give that a shot
```
sudo apt-get install linux-686
``` and reboot.
once you reboot do ```
uname -r
``` in terminal to make sure your kernel matches the one I show above

---

### Post by dhalgren on 2006-02-21
ok, again: thank you Bionic_Beefpile! So far so good, but...  let me go through the steps:
[1] disabled snd-hda-intel and got through hotplug subsystem problem
[2] upgraded kerned to 686
[3] installed latest version of alsa, using the guide you referred me to previously. ran alsamixer and set sound levels.
[4] rebooted and ran "sudo modprobe snd-hda-intel" which resulted in loading of module and then configured it.
[5] edited /etc/modules and added "snd-hda-intel" so that it's loaded atg boot without having to go through hotplug subsystem. Module now loads at boot, and sound applet says all is ok, but there contines to be no sound.

Is there something I have missed? Or are you aware of anything I can do now?
As near as I can work out, it should now be working, but there is clearly something else going on.

---

### Post by Bionic_Beefpile on 2006-02-22
You don't have to take so many fancy steps.  Once you get the alsa drivers installed, all you need to do is go back into hotplug/blacklist and comment out the line you added. :cool: 
Then on bootup hotplug should work fine

Ahh, one more thing... every time I boot, my sound channels are muted.  Install GNOME Alsa Mixer using Synaptic and run it, look for the checked mute boxes.  Unmute the channels and pull the sliders up to about 75% or so

---

