---
title: "Sound Problems - Aspire 5040 (Fiesty 7.04 x86 Final)"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by Twintop on 2007-04-22
Hey everyone,

I'm having interesting problems with my Acer Aspire 5043WLMi's sound card. It was working with the default kernel that shipped with the last Beta release for x86_64 (2.6.20-12 I believe?), but stopped working with all kernel releases afterwards. I installed the i386 release of the final (2.6.20-15) and sound still is not working.

Here is some output from similar threads on sound issues:

```
david@david-laptop:~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.14rc1 (Tue Jan 09 09:56:17 2007 UTC).
```

```
david@david-laptop:~$ cat /etc/modprobe.d/alsa-base
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
```

```
david@david-laptop:~$ aplay /usr/share/sounds/login.wav
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
aplay: main:550: audio open error: No such file or directory
```

Some other threads said to do the following commands to try and reinstall ALSA, but they didn't change the situation any for me:

```
sudo aptitude reinstall alsa-base
sudo aptitude reinstall libasound2
```

When I open System->Preferences->Sound and try to test any of the options, I get this error in a dialog:

```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open resource for writing.
```


Any help with this would be very much appreciated. :)


Also, as an aside, I noticed that my laptop model was not listed on the LaptopTestingTeam page of the Wiki. Once I have everything working and a series of steps to get everything working on it, I'd like to maintain that page. Any thoughts/help for how to go about getting that running?


Thanks!
-David C. Uhrig

---

### Post by Twintop on 2007-04-23
Giving this thread a bump for anyone who might have insight. Thanks again!

---

### Post by Twintop on 2007-04-23
One last bump for the morning/afternoon crowd. Again, any help or possible insight anyone can provide is very much appreciated. Thanks again!

---

### Post by Skrewdriver on 2007-05-05
I am having the same problem (different hardware), and it looks the same as this thread here:
[http://ubuntuforums.org/showthread.php?t=416787](http://ubuntuforums.org/showthread.php?t=416787)

I haven't fixed it, but I found that if I create a new user then everything works fine for that user.
this new bit of info may help a little.

---

### Post by cmat on 2007-05-07
I have the same model laptop and fixing the sound is proving quite difficult even though it work flawlessly in 6.10.

---

### Post by Skrewdriver on 2007-05-07
I've got my sound working again, but not sure exactly what caused the problem.

The things I discovered:
[LIST=1]
[*]The sound failed for some users on my system, worked for others. This means it is a configuration problem, not a hardware problem.
[*]The sound failed for users who were using sound when the system froze and had to be hard rebooted - this made me think that there was some kind of software lock that wasn't being cleared.
[*]Any new users I created had no sound problems.
[*]Reinstalling multiple packages had no effect, so whatever the configuration error it was specific to each user, not the whole system.
[/LIST]

This is how I got the sound working again:
[LIST=1]
[*]My main user ('mark') has User Id 1000. I logged in as another user who has administrator privileges, ran the System > Admin > Users and Groups tool and changed the user ID of 'mark' from 1000 to 2000.
[*]I then logged out of the second user and logged in with 'mark'. As expected, I received a whole heap of error messages. I cleared most of the error messages then hit Ctrl-Alt-Backspace to return to the login screen.
[*]I then logged in as the second user and reset the User ID for Mark back to 1000.
[*]I logged in as 'mark' and everything seemed to work okay.
[/LIST]

Try this hack, see if it works or not, post the results here.

---

### Post by Skrewdriver on 2007-05-07
I fixed the problem on my system, but still unsure as to what cause it in the first place.
See the following thread:

[http://ubuntuforums.org/showpost.php?p=2612401&postcount=6](http://ubuntuforums.org/showpost.php?p=2612401&postcount=6)

---

### Post by sn00pster on 2007-05-21
I Have a LG LE50 with the Sigmatel HDA soundcard. When using kernel 2.6.20-12 with the Beta my sound works fine like you guys. But as soon as i update to the Kernel 2.6.20-15, No sound. I noticed someone saying that when they create a new user it has fixed it but when i watch my laptop boot up the Toslink Optical beam which comes out of my headphone jack will not light up with the new kernel, the old kernel it lights up almost straight away.

Should i be worried that i'm not using he latest Kernel? I would like to and would love someone to post or share a fix.

Cheers
Jimbob

:popcorn:

---

### Post by Twintop on 2007-05-23
> **Skrewdriver said:**
> I fixed the problem on my system, but still unsure as to what cause it in the first place.
See the following thread:

[http://ubuntuforums.org/showpost.php?p=2612401&postcount=6](http://ubuntuforums.org/showpost.php?p=2612401&postcount=6)

I tried this and it didn't have any effect on my system (not even error messages from changing my UID).

I think that my issue (and possibly sn00pster's too) is that the sound problem isn't on a per-user basis. Sound does not work at the login screen either when I use anything other than 2.6.20-12-generic.

I'm hoping the developers release 2.6.21 soon to the masses so I can see if that fixes the issues.

---

### Post by Darryl Ring on 2007-05-24
I have the exact same model of laptop and the exact same problem. Sound has worked out of the box with every Ubuntu version except Feisty.

To add some more useful information, the card is:

```
$ lspci -nn | grep Audio
00:14.2 Audio device [0403]: ATI Technologies Inc SB450 HDA Audio [1002:437b] (rev 01)
```

PCIID lookup finds the following device:

1734:10b8	Realtek High Definition Audio

---

### Post by Darryl Ring on 2007-05-24
Well, I've found a temporary solution to this problem. I installed the Linux 2.6.17-11 packages from Edgy. So far I haven't noticed any adverse effects.

```
$ wget http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-image-2.6.17-11-generic_2.6.17.1-11.37_i386.deb
$ wget http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.17/linux-restricted-modules-common_2.6.17.7-11.2_all.deb
$ wget http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-restricted-modules-generic_2.6.17.11_i386.deb
$ wget http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.17/linux-restricted-modules-2.6.17-11-generic_2.6.17.7-11.2_i386.deb
$ sudo dpkg -i linux-image-2.6.17-11-generic_2.6.17.1-11.37_i386.deb
$ sudo dpkg -i linux-restricted-modules-common_2.6.17.7-11.2_all.deb
$ sudo dpkg -i linux-restricted-modules-2.6.17-11-generic_2.6.17.7-11.2_i386.deb
$ sudo dpkg -i linux-restricted-modules-generic_2.6.17.11_i386.deb
```

Now, I couldn't figure out how to automatically reconfigure grub so I simply added a new entry to /boot/grub/menu.lst. I rebooted and after unmuting and dragging the volume sliders up, my sound was once again working as it did prior to Feisty.

I found that apt was complaining about a missing dependency. One of the packages I installed replaced a dependency for the newer version of linux-restricted-modules. You can safely remove whichever package is complaining for now.

Remember, though, that you're downgrading packages so apt won't hesitate to upgrade them right back up to the wrong version for this kernel. I'm not knowledgable enough about how the kernel packages work to know what effects this would have. Hopefully someone who knows such things can elaborate.

I hope this helps some other people here!

---

### Post by Twintop on 2007-05-24
> **Darryl Ring said:**
> Remember, though, that you're downgrading packages so apt won't hesitate to upgrade them right back up to the wrong version for this kernel. I'm not knowledgable enough about how the kernel packages work to know what effects this would have. Hopefully someone who knows such things can elaborate.

The last Kernel release that seems to allow sound (from Feisty) is 2.6.20-12-generic, which was from the beta CD release. In 2.6.20-13-generic something broke and sound hasn't worked since. If you can get your hands on a beta CD, you could probably install 2.6.20-12-generic from it so that you aren't relying on 2.6.17. :)

---

### Post by Twintop on 2007-05-26
I did some more searching and it looks like there is a fix out there by way of  [installing ALSA 1.0.14-rc4]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109236"). In the thread it also says a fix has been committed to the latest development copy of the Ubuntu 2.6.20 kernel (2.6.20-16-generic?). Hopefully this fix will get released soon. I have yet to try the ALSA 1.0.14-rc4 approach yet, but will do so later tonight and see if it helps any.

---

### Post by Twintop on 2007-05-26
Well, I was unable to get sound to work with ALSA 1.0.14-rc4. I'm not finished trying, though. Anyone else have any luck? ;\

---

### Post by Twintop on 2007-05-28
The Ubuntu Kernel developers released 2.6.20-16-generic tonight and sound worked for me right away after upgrading! It looks like this problem is finally solved! A big **thank you** to the Kernel devs. for their work! :) It is very much appreciated!

---

