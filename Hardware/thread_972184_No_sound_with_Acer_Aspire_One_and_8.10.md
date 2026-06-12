---
title: "No sound with Acer Aspire One and 8.10"
date: 2008-11-05
forum: Hardware
---

### Post by nray on 2008-11-05
Sound out was working great (never tested sound input) for me in 8.04.1, 8.10 beta, and 8.10 release with my Acer Aspire One (model AOA 150-1570).

Then at some point late last week it appears an update broke sound, so now all I hear if I turn it up all the way is crackly static.  (I can't pinpoint when it happened, because most of the time I mute the sound on my netbook, only occasionally turning it on when watching a video etc.)

I checked /etc/modprobe.d/blacklist and it already has "blacklist snd_pcsp".  I had inserted snd-hda-intel into "/etc/modules" a while ago, and it's still there, I've verified it's not being blacklisted, and verified the module exists at "/lib/modules/2.6.27-7-generic/kernel/sound/pci/hda/snd-hda-intel.ko"

My /etc/modprobe.d/alsa-base file has "alias snd-card-0 snd-hda-intel" and "options snd-hda-intel model=auto", and I've also tried model=acer, model=basic, rebooted after each change, and I still get static with each one.

I even tried rebuilding ALSA, and after the "sudo m-a a-i alsa" step it fails partway through, with this at the end of the log:

> CC [M]  /usr/src/modules/alsa-driver/acore/info.o
/usr/src/modules/alsa-driver/acore/info.c: In function ‘resize_info_buffer’:
/usr/src/modules/alsa-driver/acore/info.c:90: error: implicit declaration of function ‘PAGE_ALIGN’
make[5]: *** [/usr/src/modules/alsa-driver/acore/info.o] Error 1
make[4]: *** [/usr/src/modules/alsa-driver/acore] Error 2
make[3]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make[2]: *** [compile] Error 2
make[2]: Leaving directory `/usr/src/modules/alsa-driver'
make[1]: *** [build-stamp] Error 2
make[1]: Leaving directory `/usr/src/modules/alsa-driver'
make: *** [kdist_image] Error 2


I'm now out of ideas.  Anyone have any?

---

### Post by thor2002ro on 2008-11-08
strange my sound worked out of the box:confused: mic and all

---

### Post by nray on 2008-11-09
> **thor2002ro said:**
> strange my sound worked out of the box:confused: mic and all

Yes, my sound worked "out of the box" with 8.10 beta and release, until I applied some updates about a week ago, then it stopped working and is now static at best.

Have you performed a "sudo aptitude update" and "sudo aptitude safe-upgrade" lately in your install of 8.10 on your Aspire One and still had working audio?

---

### Post by thor2002ro on 2008-11-09
i usualy do sudo apt-get dist-upgrade and yes it up to date working great

---

### Post by MattressVon on 2008-11-10
I'm having the same problem here. After the most recent updates as of Nov.5 lost all sound. I noticed that after rebooting with the latest kernel modules (.27 something) I got an error and system hang as my machine unloaded ALSA. Sound has not worked since. I thought about re-installing and for-going updates, but like you I leave my machine muted a lot, so it didn't seem worth the effort. Is anyone else having this problem? Should we file a bug?

---

### Post by MattressVon on 2008-11-10
Fixed it! I was trying to enable my USB sound card and installed Pulse Audio Device Chooser. I set it up and presto.

Instructions:

1.) Install:  sudo apt-get install padevchooser

2.) Restart your machine and go to menu>applications>sound&video>pulseaudiodevicechooser

3.)The program will open in your system tray as an icon of a 1/4 inch headphone jack. left click on it and click on default source.

4.)Click the default radio button.

You should be good. :guitar:

---

### Post by nray on 2008-11-10
> **MattressVon said:**
> 1.) Install:  sudo apt-get install padevchooser

2.) Restart your machine and go to menu>applications>sound&video>pulseaudiodevicechooser

3.)The program will open in your system tray as an icon of a 1/4 inch headphone jack. left click on it and click on default source.

4.)Click the default radio button.

I followed those steps, and no change for me, I still get static at best.

---

### Post by thor2002ro on 2008-11-10
> **nray said:**
> I followed those steps, and no change for me, I still get static at best.

maybe you got hardware faliure.... try another os see if the same happens....

---

### Post by nray on 2008-11-10
> **thor2002ro said:**
> maybe you got hardware faliure.... try another os see if the same happens....

Someone else has the sound problem, so it's unlikely to be a hardware failure... especially when you consider all the other problems Ubuntu has with the Aspire One, like the gnome-power-manager randomly freezing in 8.10 and all the problems with the ath5k drivers as well as having to get an svn version of madwifi to get working wireless.

But when I have a chance, I'll prepare a bootable USB memory stick with a Live CD environment... does anyone know for sure if the Live CD of 8.04.1 or 8.10 final has working sound for the Aspire One?  I never tested the sound from a Live CD environment when I installed 8.04.1 a few months ago.

---

### Post by FargenDog on 2008-11-10
I've had the same problem with my AA1 150.  Audio works in XP and Ubuntu 8.10 Live but the full install isn't working.  Any way to get back to whatever the live version is using?

edit:  I've tried all the sudo listed in the thread here as well as the Pulse Audio all to no avail.  Still nothing but static.  Can I just re-install or is there a way to get back to the default intstallation?

---

### Post by thor2002ro on 2008-11-11
then did you try compile the alsa ?

[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

---

### Post by nray on 2008-11-11
> **thor2002ro said:**
> then did you try compile the alsa ?

[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

I've read that link, and considered doing it except that someone wrote in that page: "The configure step fails in Ubuntu 8.10 with the kernel 2.6.27-7. The configure script is unable to find the autoconf.h file and complains that it wants the full kernel sources," and I have kernel 2.6.27-7, so that doesn't seem like a solution.  There also seems to be some disagreement on that page about whether or not those suggested steps will cause issues with installed packages and the package manager.

Also, as mentioned in my first post, I tried compiling the way suggested in the Aspire One wiki but it fails at the "sudo m-a a-i alsa" step (errors listed in my first post).

---

### Post by brainerd on 2008-11-16
I just got an Aspire One A150 with 160 GByte HD and Windows XP.  I installed Ubuntu 8.10 on a dual boot and did the mod for WiFi.  WiFi works.  Sound out works OK.  Microphone input does not work properly.  When I use either audacity or the sound recorder, I get very low and noisy input.  Also, appears to come from the internal  mic even though I have an external mic plugged in.  It is not the hardware as it works great in Windows.

Dave

---

### Post by brainerd on 2008-11-16
I just got the microphone to work, although it still seems to be from the internal rather than the external.  I had to go to system - preferences - sound  and select Device HDA Intel(Alsa Mixer). and set up the recording Capture control.

Dave

---

### Post by nray on 2008-11-19
> **brainerd said:**
> I just got an Aspire One A150 with 160 GByte HD and Windows XP.  I installed Ubuntu 8.10 on a dual boot and did the mod for WiFi.  WiFi works.  Sound out works OK.  Microphone input does not work properly.  When I use either audacity or the sound recorder, I get very low and noisy input.  Also, appears to come from the internal  mic even though I have an external mic plugged in.  It is not the hardware as it works great in Windows.

Dave

I have an A110L, and one of my Ubuntu 8.10 updates (or perhaps a software dependency that got installed with another package) has made my ALSA output crackly.

I've discovered that if I go into Sound Preferences and set playback to any OSS and test it, then I do get the test tone.  If I set it to Autodetect, or any ALSA, I get crackles or I get an error message along the lines of "audotestsrc wave=sine freq=512 ! ..."  So it looks like OSS works... and I do get functional audio in the Rhythmbox Music Player, but I get just crackles in Miro (I'm assuming this is because one uses OSS and the other ALSA?)

Anyone have any ideas what's going on?

---

### Post by nray on 2008-11-28
> **nray said:**
> I've read that link, and considered doing it except that someone wrote in that page: "The configure step fails in Ubuntu 8.10 with the kernel 2.6.27-7. The configure script is unable to find the autoconf.h file and complains that it wants the full kernel sources," and I have kernel 2.6.27-7, so that doesn't seem like a solution.  There also seems to be some disagreement on that page about whether or not those suggested steps will cause issues with installed packages and the package manager.

Also, as mentioned in my first post, I tried compiling the way suggested in the Aspire One wiki but it fails at the "sudo m-a a-i alsa" step (errors listed in my first post).

Kernel 2.6.27-9 was just released in the package system, so I went and downloaded the latest alsa source (1.0.18a) from [http://www.alsa-project.org/]("http://www.alsa-project.org/").  It compiled and installed fine, I rebooted, and I still had the same symptoms, so I went into the GNOME ALSA Mixer and noticed that PCM was turned all the way down.  I turned PCM all the way up, and now sound works normally.

Any chance the PCM volume being turned down could have been my problem with the module drivers, or is this something that alsa 1.0.18a fixed?

---

### Post by brunomorais on 2008-11-29
Hello,
I've an Acer Aspire One A0A - 110 and I've the same problems with sound.
Evrything played movies,mp3 etc. But the system soundes didn't play.
I've just updated my kernel yesterday for 2.6.27-9-generic. After read the previous post I've checked that mu PCM volume was completely off. So I've turned on and sound played beautifully.
So I believe the problem was the volume and not anything with the Alsa driver.

---

### Post by DrLegoHair on 2009-02-16
Sorry to resurrect this thread but I'm having the same problem as the OP.  I have the new 10inch AA1.  I've changed all the settings the OP did and tried to compile the ALSA drivers but got the same error.  All volumes in the mixer are up.  When I try to test the ALSA sound card in preferences>sound I get the error

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open audio device for playback.

Any ideas?  Any help is appreciated.
Thanks!

---

### Post by stekker on 2009-02-25
> Could not open audio device for playback

This means that some other application is using the device.

Best to check if you have some (audio)program running which has it's sound output configured to OSS or ALSA.
If this is the case, configure it's output to pulse(audio) or kill it alltogether.

:-)

---

### Post by stekker on 2009-02-25
Oh....and don't forget to reboot afterwards

---

### Post by Heimark on 2009-03-17
I just got my Aspire One on 3/9/09, I got the 10.1 inch screen with the 160 gig HDD. Looking on the Wikipedia page I saw this was the only one with no option to have linux come preinstalled. So, having the USB boot disc for Intrepid ready by the time it arrived in the mail I wasted no time... well... until it came to getting the audio to work. Out of frustration I updated to Jaunty Alpha on 3/17/09 and everything worked just fine. I'm guessing they decided to start upgrading some hardware that isn't supported with Hardy or Intrepid yet.

---

### Post by Jupp3 on 2009-03-29
When I installed 9.04 beta on my Acer Aspire One 8.9", I didn't have any sound either at first.

This was easily cured by running alsamixer, toggling mute, and turning up the volume.

---

