---
title: "Mplayer's -hwac3 option killed my sound"
date: 2007-11-11
forum: Hardware &amp; Laptops
---

### Post by Eric89GXL on 2007-11-11
I have been using my onboard Realtek ALC889a chip for sound output in linux for months now, and I'm running Ubuntu 7.10. Stereo files played fine and DTV broadcasts with 5.1DTS/DD signals were decoded properly when played in MythTV, so I know the sound was set up properly, at least up until yesterday.

I made no changes hardware- or software-wise to my system. I then ripped a DVD to my hard drive and ran mplayer on the .vob file with the option "-ac hwac3". It played fine, but I noticed that after I killed Mplayer, the DD light on my receiver never turned off, which is strange, because it should turn off once it stops receiving the DD signal. I then tried to play music through Amarok, and got silence. I tried other audio programs, silence. I tried running "speaker-test," silence. I tried running "cat /dev/urandom > /dev/audio," silence. I thought maybe my sound was messed up, so I re-ran Mplayer on the .vob file with the -hwac3 option to see if it still worked, and it worked perfectly. Ran it without -hwac3, silence.

So I thought ALSA might be acting up, so I tried "/etc/init.d/alsa restart." Didn't help. I then tried "/etc/init.d/alsa stop," which succeeded, so I ran mplayer with the -hwac3 option, and it still played. This means the hwac3 codec is bypassing ALSA. It seems like it's taking over my sound card and never relinquishing control, like it's putting it in a certain DD state and not resetting it when it exits or something...

I even tried restarting my computer (old windows habit)---this didn't change the behavior, either. I ran "fuser -v" and "fuser -mv" on /dev/audio and /dev/dsp to see if some ac3-like process was taking them over but didn't notice anything. 

I'm stumped. Anyone have any suggestions? I'm thinking next I'll reboot, disable my onboard sound in the bios, let it boot, reboot, re-enable the onboard sound in the bios, and then let it boot up again. Even if it works, this is a terribly slow and annoying solution to a problem caused by having mplayer do DTS passthrough...

Help?

Eric

---

### Post by Eric89GXL on 2007-11-12
...Today I made sure that the problem is not my sound card or receiver by booting off the Ubuntu install CD, which was able to play audio just fine. This is definitely a problem with my drivers or configuration. Ideas, anyone?

---

### Post by Eric89GXL on 2007-11-15
Esperanto pointed me to a solution. the /var/lib/alsa/asound.state file is (re)set improperly and needs to be replaced. The best solution is probably to boot up a live CD, and if the sound works, use the asound.state from that system. A faster, uglier solution involves manually replacing hex strings in your asound.state file with the strings from someone else's posted asound.state. See the following threads for details:

[http://ubuntuforums.org/showthread.php?p=3778835](http://ubuntuforums.org/showthread.php?p=3778835)
[http://ubuntuforums.org/showthread.php?p=3768839](http://ubuntuforums.org/showthread.php?p=3768839)
[http://ubuntuforums.org/showthread.php?t=445536](http://ubuntuforums.org/showthread.php?t=445536)

---

