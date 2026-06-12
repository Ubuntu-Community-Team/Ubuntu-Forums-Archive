---
title: "Mic on a Samsung notebook"
date: 2011-04-01
forum: Hardware
---

### Post by blackmamba312 on 2011-04-01
Hi guys, I have a Samsung R540 with a fresh installation of Kubuntu 10.10.
Everything seems to work well, but when I try to use Skype my built-in microphone doesn't work at all; I also tried to use an external mic but didn't work too...
In Kmix settings I only have "Internal audio analog stereo" and HDMI audio, but launching alsamixer from console I can also see "Front mic boost" and "Mic boost", both at maximum level.
What's the problem? How can I solve it?
Thanks in advance :)

---

### Post by blackmamba312 on 2011-04-01
up! please help, I want to use linux on my notebook instead of windows, but really need to have skype working.. :(

---

### Post by Lateralis on 2011-04-01
Have a read of [this]("https://help.ubuntu.com/community/SoundTroubleshooting") Ubuntu Community wiki article on troubleshooting sound problems.  Toward the bottom there is a section on microphone issues.  One potential problem (aside from the obvious) is that your hardware may have two subdevices.  If that is the case pulseaudio and ALSA - which by default choose subdevice #0 - may be selecting the "wrong" device to listen to.  Check what recording devices you have type the following into the command line:

```

arecord -l

```

where the last character is a lowercase 'L'.  If you have multiple subdevices listed try the guide in the the link I mentioned above.  

If you only have one then the problem originates from something else.  An Obvious candidate is Skype itself, but I'll make the assumption that you have configured Skype properly.  As a check you could try using a sound recorder to test your microphone set up independently of Skype.  You should have one installed by default (at least, I do in gnome).  If you are able to record in a separate sound recorder but not send sound over Skype then that pretty much narrows down the problem.

---

### Post by blackmamba312 on 2011-04-02
> **Lateralis said:**
> Have a read of [this]("https://help.ubuntu.com/community/SoundTroubleshooting") Ubuntu Community wiki article on troubleshooting sound problems.  Toward the bottom there is a section on microphone issues.  One potential problem (aside from the obvious) is that your hardware may have two subdevices.  If that is the case pulseaudio and ALSA - which by default choose subdevice #0 - may be selecting the "wrong" device to listen to.  Check what recording devices you have type the following into the command line:

```

arecord -l

```where the last character is a lowercase 'L'.  If you have multiple subdevices listed try the guide in the the link I mentioned above.  

If you only have one then the problem originates from something else.  An Obvious candidate is Skype itself, but I'll make the assumption that you have configured Skype properly.  As a check you could try using a sound recorder to test your microphone set up independently of Skype.  You should have one installed by default (at least, I do in gnome).  If you are able to record in a separate sound recorder but not send sound over Skype then that pretty much narrows down the problem.
Thanks a lot for your support.

I noticed that my alsa configuration recognize only one subdevice, used both for playback and capture. So I try to follow the instruction mentioned on the link you posted, and reading the section "Is ALSA using the correct model?" and browsing the ALSA git repository, I found that ALSA isn't using the correct model of my soundcard (I have an ALC269 but ALSA is using an ALC259). 

How can I change the model used by ALSA?

---

### Post by blackmamba312 on 2011-04-02
Good news! :D
Solved it by upgrading driver ALSA version from 1.0.23 to 1.0.24. Did it following this: [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)
Then I configured volume levels using alsamixer in console (still not seeing mic levels in kmix)

My old alsa-info.sh: [http://www.alsa-project.org/db/?f=18b566dc49581025c3709d077496ec462c02dcab](http://www.alsa-project.org/db/?f=18b566dc49581025c3709d077496ec462c02dcab)
My new alsa-info.sh: [http://www.alsa-project.org/db/?f=6e9f16cd556d0d552ce266b8794235adcd155f18](http://www.alsa-project.org/db/?f=6e9f16cd556d0d552ce266b8794235adcd155f18)

I suggest to whom could experience same kind of issue to follow all Sound Troubleshooting guide in wiki section!

---

