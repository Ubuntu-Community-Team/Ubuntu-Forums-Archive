---
title: "Installation on Latitude CSx - boot hangs at &quot;Starting Hotplug Subsystem&quot;"
date: 2005-11-14
forum: Hardware &amp; Laptops
---

### Post by tomlondon on 2005-11-14
Hi folks. Hope you can help with my installation problem.

Laptop is a Dell Latitude CSx (trying to breathe life into an old system!). Installation went without problem, grub is working fine. However, the system hangs on every boot at the line: "Starting Hotplug Subsystem". No amount of keyboard combinations will wake it up.

Booting in recovery mode, the last line on the screen is:
```

[4294717.77800] nm256: Mapping port 1 from 0x3f09a0 - 0x3fec00

```

... and a blinking cursor. I've googled and learnt that "nm256" appears to be related to the audio drivers. This is just going to be a work machine so I could live without sound if necessary but I've no idea how to disable it! 

As you may have guessed by reading this far, I'm utterly clueless about desktop linux - I was hoping to be able to learn using Ubuntu... Please don't make me go back to Win2K.

Thanks in advance for any help, Tom

---

### Post by tomlondon on 2005-11-15
OK, some further investigation. I've had a look through Bugzilla and there was a similar problem reported in March which was supposedly fixed in 5.04:
[http://bugzilla.ubuntu.com/show_bug.cgi?id=7939](http://bugzilla.ubuntu.com/show_bug.cgi?id=7939)

... but I've no idea what all that stuff means! Also, someone else posted an identical problem with a similar laptop a few weeks ago:
[http://ubuntuforums.org/showthread.php?t=80527](http://ubuntuforums.org/showthread.php?t=80527)

Can anyone tell me what these posts mean? From my perspective, it seems that it's a known problem with no obvious fix.

*sigh* Back to Windows.

---

### Post by tomlondon on 2005-11-15
In case anyone is interested, I solved it. By hitting Ctrl-C randomly during boot, I disabled a bunch of stuff including the hotplug subsystem. Everything then booted fine. I then added snd-nm256 to the hotplug blacklist, and everything now boots ok. I can live without sound.

---

### Post by jorgen_s on 2005-11-17
[QUOTE=tomlondon]In case anyone is interested, I solved it. By hitting Ctrl-C randomly during boot, I disabled a bunch of stuff including the hotplug subsystem. Everything then booted fine. I then added snd-nm256 to the hotplug blacklist, and everything now boots ok. I can live without sound.[/QUOTE]
This problem with the nm256 module has been around at least twice before in [this]("http://ubuntuforums.org/showthread.php?t=80527") and [this]("http://ubuntuforums.org/showthread.php?t=85646") thread.
Yes, blacklisting that was also the only way out for me (on a Latitude CPt). 
Even tried compiling and messing around for days with many settings without any success, still freezes randomly.

Got the suggestion from the Swedish Ubuntu Forum to do a report about the problem in **Applications/System Tools/Ubuntu Device Database** and did so (with a referece to [http://www.alsa-project.org/alsa-doc/doc-php/template.php?module=nm256)](http://www.alsa-project.org/alsa-doc/doc-php/template.php?module=nm256)). Then the devs perhaps will add a patch for this in a future kernel release.

Found this in the ALSA Driver source:

> From the Driver Source Code Documentation about the snd-nm256
(alsa-driver-1.0.10/alsa-kernel/Documentation/ALSA-Configuration.txt):
		
[I]Note: This driver is really crappy.  It's a porting from the
OSS driver, which is a result of black-magic reverse engineering.
The detection of codec will fail if the driver is loaded *after*
X-server as described above.  You might be able to force to load
the module, but it may result in hang-up.   Hence, make sure that
you load this module *before* X if you encounter this kind of
problem.[/I]


Anyone knowing what this means? It freezes befor X on my box...

---

### Post by am4c130d on 2006-01-10
HI,  I have a Dell LS400 and it also hung while loading hotplug.  Here's how I fixed the problem.

1. I modified /etc/modutils/alsa-base

After "alias char-major-116 snd"  add the following two lines (in my case, this was effectively the second and third lines of alsa-base

alias snd-card-0 snd-nm256
options force_ac97 1

This allowed my laptop to boot with power every time.

However the laptop would not reliably boot on battery.  To address this I upgraded my BIOS to the latest version.  Dell's support site makes reference to problems with older BIOS versions and the NeoMagic 256 and memory allocation at boot up.

The bug referenced below/above covers this issue.  In older versions (kernel/driver - not sure which or both), loading X first meant that the video portion of the nm256 took all the memory allocated to the chip.  This meant that the sound would not work, because there was no memory left.  I don't think that this bug is enormously relevant now.

I hope this helps.  My laptop won't boot on battery from cold (i.e. having be left off for a couple of days), but then the screen doesn't come up either, so that may be specific to my laptop.  However it always boots on second attempt etc.  Once it has initially booted it boots everytime without a problem.

I should add that this forum lead me to the URLs that gave me the answers, hopefully this helps those who currently have disabled sound.

Thanks

Alan

---

### Post by fermulator on 2006-02-06
WOW.

I'm very surprised at this OLD driver issue.  (I"m having the exact same issues with a Dell Lattitude CPi A series)

It's quite silly really... there seems to be MANY people with the same problems.

It's most definatey a kernel issue.
I've tried SUSE, ubuntu, and kubuntu.

Strange thing is though, it's a RANDOM problem.  If one tries to boot several times...EVENTUALLY the system will boot.  And sound will work!  How can this issue be "random"?  I find it strange, especially since it's a software issue.

Anyways, just letting you all know that you're not alone.

PS:  I've tried add those modifications to /dev/modutils/alsa-base as posted by "am4c130d", but it did not work for me.

NOTE:  Pressing "CTRL+C" just as the "Starting Hotplug Subsystem" shows, cancels that particular thing from loading, and the system will boot without sound.  (A temporary fix, but not a satisfactory one for most).  I'd like sound! :-)

I've also updated my BIOS on my notebook to the last A15 revision.  This didn't make a difference.

I hope its fixed in the next kernel update!

---

### Post by SteveHoffmanUK on 2006-03-22
Same problem for me on Dell Latitude Pentium III laptop.

Agree about the randomness. In my case, I did a successful install of Breezy and did not have the hang problem and had full sound. Indeed the 'Mute' button didn't work, so I sometimes had sound when I didn't want it (like in a library, embarrassing).

For other reasons, I had to reinstall Breezy, and now it hangs at the hotplug point. :( 

Thanks for the Ctl+C tip. Agree that it's not satisfactory for most people, but I don't need sound, so I'll try it.

Can someone explain to this noob just how one finds the "hotplug blacklist" so I can follow tomlondon's suggestion to edit it?

Thanks

---

### Post by JimJones56 on 2006-03-22
From memory: /etc/hotplug/blacklist

---

### Post by tvankirk on 2006-05-02
[QUOTE=jorgen_s]This problem with the nm256 module has been around at least twice before in [this]("http://ubuntuforums.org/showthread.php?t=80527") and [this]("http://ubuntuforums.org/showthread.php?t=85646") thread.
Yes, blacklisting that was also the only way out for me (on a Latitude CPt). 
Even tried compiling and messing around for days with many settings without any success, still freezes randomly.[/QUOTE]

This problem has been corrected in the latest version of Alsa (1.0.11).

Here is what I did to correct it (Note: Make sure you have Universe enabled):

[INDENT][INDENT]wget http://http.us.debian.org/debian/pool/main/a/alsa-driver/alsa-source_1.0.11-1_all.deb

sudo apt-get install linux-headers-$(uname -r) build-essential gcc-3.4 module-assistant

sudo dpkg -i alsa-source_1.0.11-1_all.deb

sudo apt-get -f install

sudo dpkg-reconfigure alsa-source

Accept the defaults and select the correct module (nm256)

sudo module-assistant auto-install alsa-source[/INDENT][/INDENT]

This has corrected the freeze on boot 100% of the time.

---

### Post by jgraber on 2006-05-29
Well, I have just spent half a day fighting the same problem on a Dell GS260.  (Minitower, not a laptop.)  I'm glad I found out I'm not the only one.  I hope it is fixed in Dapper Drake. I will try that before trying to patch in a fix.   Right now I am very frustrated and angry.  This is not the first time I have found it impossible to install Linux and get it running.  You really have to want to go to Linux  an awfully lot to put up with all the problems.  Definitely not ready for primetime.
Jim

---

### Post by chrismyers on 2006-05-29
[QUOTE=jgraber]Well, I have just spent half a day fighting the same problem on a Dell GS260.  (Minitower, not a laptop.)  I'm glad I found out I'm not the only one.  I hope it is fixed in Dapper Drake. I will try that before trying to patch in a fix.   Right now I am very frustrated and angry.  This is not the first time I have found it impossible to install Linux and get it running.  You really have to want to go to Linux  an awfully lot to put up with all the problems.  Definitely not ready for primetime.
Jim[/QUOTE]

I had the same problem on two laptops with Breezy. They both work fine on the beta versions of Dappa. There's hope for you ;)

---

### Post by drdrgivemethenews on 2006-06-12
I am convinced this is to do with memory conflict/not enough available during boot up with the nm256 stuff on the Dells. On booting up try switching to the virtual console by ctrl-alt f1 BEFORE the ubuntu logo appears. It repeatedly loads ok for me and repeatedly fails if I leave it in graphic mode i.e. ctrl-alt f7.

Why? I dont know....do you?

---

### Post by frankd on 2006-06-22
[QUOTE=tvankirk]This problem has been corrected in the latest version of Alsa (1.0.11).

Here is what I did to correct it (Note: Make sure you have Universe enabled):

[INDENT][INDENT]wget [http://http.us.debian.org/debian/pool/main/a/alsa-driver/alsa-source_1.0.11-1_all.deb](http://http.us.debian.org/debian/pool/main/a/alsa-driver/alsa-source_1.0.11-1_all.deb)

sudo apt-get install linux-headers-$(uname -r) build-essential gcc-3.4 module-assistant

sudo dpkg -i alsa-source_1.0.11-1_all.deb

sudo apt-get -f install

sudo dpkg-reconfigure alsa-source

Accept the defaults and select the correct module (nm256)

sudo module-assistant auto-install alsa-source[/INDENT][/INDENT]

This has corrected the freeze on boot 100% of the time.[/QUOTE]

I can say that this worked just fine for me except that alsa is at 1.0.11-2 now. You'll have to browse to [http://http.us.debian.org/debian/pool/main/a/alsa-driver](http://http.us.debian.org/debian/pool/main/a/alsa-driver) in order to find the name of the current alsa-source deb file.

The interesting part is that on my CSx500 the hotplug locked up only if I had a PCMCIA card inserted at the time and was using the graphical splash screen. If I booted without the card it worked fine. Installing the latest version of alsa with the nm256 driver cleared it right up.

---

### Post by Andrew-buntu on 2006-07-08
> **tvankirk said:**
> This problem has been corrected in the latest version of Alsa (1.0.11).

Here is what I did to correct it (Note: Make sure you have Universe enabled):

...

This has corrected the freeze on boot 100% of the time.

Thanks much, tvankirk!  My old laptop is useful again.  It only booted about 1/3 of the time before.  Now it's started up five times in a row without failing.

---

### Post by quackking on 2006-09-10
tvankirk, dude, you rock! This worked immediately on an old Sony VAIO PCG-F350. How did you figure this out? 

(Notes: Alsa-source is now 1.0.11.5, and I had to install debhelper and something else which were not there by default before your instructions worked.) 

The entire purpose of this is to take an old obsolete laptop and convert it into a Skype voice station. There is limited disk space (the whole hard drive is about 6 gb)

So, what can I REMOVE once I have recompiled and reinstalled ALSA? Can I get rid of most of the gcc stuff and the kernel headers (a complete dpkg -remove HOWTO would be very helpful here!) 

One more thing; I previously installed MUSIX 0.50 on this laptop (a Knoppix derivative, I believe) and every Alsa-related app (it is a sound-recording distro with a lot of them, like Audacity, Rosegarden, etc) worked immediately. It seems like a good idea for the Ubuntu team to immediately put the latest Alsa 1.0.11.x build into the Dapper repositories.

Thanks again!

---

