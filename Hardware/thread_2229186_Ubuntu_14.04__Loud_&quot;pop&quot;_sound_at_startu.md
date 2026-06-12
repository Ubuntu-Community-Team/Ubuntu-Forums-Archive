---
title: "Ubuntu 14.04 : Loud &quot;pop&quot; sound at startup, snd hda intel issue ?"
date: 2014-06-11
forum: Hardware
---

### Post by pierre17 on 2014-06-11
Hello all,

I need a little help :)

I just setup Ubuntu 14.04 (kernel 3.13.0-29-generic x86) on my Laptop, an Asus A6jc. Everything works pretty well, and I'm quite satisfied, but i have some little issues i would like to fix. One of them, I got a loud 'pop' sound at boot, I'm pretty sure it's happening when the module snd_hda_intel is loaded.

I know there are already a lot of posts of this kind, but I spent days now searching for a fix and i haven't found anything yet working for me...

What i have tried so far :
- setting the parameters for the snd_hda_intel module => power_save=0 and power_save_controller=N. After reboot, i still got the same 'pop' sound, i checked in /sys/modules/snd_hda_intel/parameters and these 2 power save parameters are set as i want
- edited /usr/lib/pm-utils/power.d/intel-audio-powersave and explicitely set INTEL_AUDIO_POWERSAVE=false
- checked in /etc/modprobe.d/alsa-base.conf for other power save options and nothing
- checked in /etc/pulse/default.pa, the line "loadmodule module-suspend-on-idle" is commented

When i boot without the snd_hda_intel module, i don't have this annoying 'pop', but of course i don't have any sound at all :(

About my hardware, lspci tells my audio device is Intel NM10/ICH7, and alsamixer says my card is HDA Intel / Realtek ALC880.

Any idea, any help will be welcome ;)

---

### Post by pierre17 on 2014-06-23
Hello,

Nobody ?

Please, I really need help...

Any suggestions ?

Thanks :)

---

### Post by markvizz on 2015-03-12
Hi,

Did you find a solution for this issue? it's really annoying!

Thanks in advance
Marco

---

### Post by pierre17 on 2015-06-16
Hi Marco,

No, I haven't found any solution yet. I just try the latest Ubuntu 15.04 release and issue is still here...

I spent a lot of time with this and now I am pretty sure it comes from the snd_hda_intel module.

If anybody has a hint, it would be great ;)

Thanks,
Pierre

---

### Post by NoWayWin8 on 2015-06-17
Do you mean the little drum beat sound that happens just as the unity login greeter loads? Click the little speaker button on the top-right of the screen and select "mute". It should stay that way for future boots.

---

### Post by pierre17 on 2015-06-21
No, the sound I'm talking about happens before the x server is started, and so before Unity is loaded too. I have identified that I get this sound when the snd_hda_intel module is loaded in the kernel.

Thanks anyway for your reply ;)

---

### Post by Bucky Ball on 2015-06-21
Welcome. Lot of OSs do this when you have your sound system and the volume up at boot. Perhaps just turn the volume down when you boot the machine. Better for the speakers, too. Not a fix but a clumsy 'workaround'. 

Was there a time when this didn't happen with this particular machine on Ubuntu or any other OS? Headphones on my desktop boot blows my head off. On the laptop, its there, but not brain numbing.

(You could write a script to sound on, create a desktop launcher for it and switch sound off at boot. Once you're at the desktop, just click the launcher and you'll have sound ... but you will probably still get the crunch sound, too.)

---

### Post by pierre17 on 2015-06-21
Hello, my machine is an Asus laptop (A6jc), currently I have a dual boot on it, I want to leave Windows and switch to Linux, that's why I'm trying Ubuntu :)

I don't have this annoying sound at startup with Windows. With recent Linux distributions, using snd_hda_intel, I always get it... I will check but I think some years ago, when I was using some Kubuntu live cd, I didn't got that issue.

I tried to mute the volume before reboot as you suggested, but as I thought, it doesn't change anything :(. On Ubuntu 15.04, when booting without "quiet" and "splash" kernel parameters, I can tell The "pop" sound comes right before the message "Reach target sound card". I'm pretty sure it comes when the driver is loaded.

I keep investigating, and if I find anything interesting I will post here.

If you have other suggestion, I'm listening ;)

Thanks !

---

