---
title: "No Sound after Suspend Dell D620"
date: 2006-07-05
forum: Hardware &amp; Laptops
---

### Post by kjohara on 2006-07-05
I recently installed 6.06 on my new Dell D620. For the most part it works
great! But, I am having a little bit of trouble with my sound after suspending. I can change the volume, mute/unmute, with alsamixer, but no sound comes out of the speakers. Before suspend everything works fine. I restarted /etc/init.d/alsa-utils, but to no avail.  Anyone have similar problems? 

I haven't checked how the sounds reacts to hibernate.

Also, has anyone gotten the FN-ESC and FN-F1 keys to work with XFCE for
suspending and hiberating?

Thanks!

Linux d620 2.6.15-25-686 #1 SMP PREEMPT Wed Jun 14 11:34:19 UTC 2006 i686 GNU/Linux

---

### Post by Ubuntist on 2006-07-05
This thread might help:

[http://ubuntuforums.org/showthread.php?p=1208241#post1208241](http://ubuntuforums.org/showthread.php?p=1208241#post1208241)

---

### Post by kjohara on 2006-07-06
Thanks for the link, but that problem is a little different. I checked, and the sound works after hibernate, just not suspend. Also, all the channels are enabled and volume up.

---

### Post by Hellkeepa on 2006-07-06
HELLo!

Probably the same issue I've experienced, though I found a rather peculiar thing.

My laptop's (Amilo Pro 2040) headphones jack is very loud compared to the speakers, so I usually have to drop the volme by 50% (from 75 to 25) to avoid bleeding ears. Might not seem important, but what I discovered after suspending the PC once while I was playing music was: There was a whisper of sound in the headsets.
So I naturally turned the sound up to 95%, and was greeted with audible (yet very low) sound via the headphones. The speakers, however, were dead silent.

This leads me to believe that one of two things are happening:
1. Either the volume gets "muted" by setting all the volumes to 0%, somehow circumventing ALSA, and not turned back again on wake-up.
2. The parametres set on wake-up are way too low compared to what they normally should be.

I haven't tested hypothesis 1 yet, but it should be possible by setting all volumes to 0% before suspending. If you get sound when boosting them up again after waking up the laptop, then you've found the most likely cause for the missing sound. ;-)

Happy codin'!

---

### Post by kjohara on 2006-07-07
I am having the same problem, thanks for the info! I checked my headphones and there was sound there  Also, ignore my comments about hibernate being immune to this problem. Today the same thing happened after hibernating. I try and hunt down the problem some more and hopefully post a solution.

---

### Post by jede on 2006-07-09
I have the same problem on my Dell D620. Sound works most of the time, but for some reason even without hibernating or putting it to sleep there's no sound, not at speakers and not at earphones :-(
Volume is up, the modules are loaded and mixer settings are OK.
Has anybody posted a bug report about this ?

Bye,
Stefan

---

### Post by Hellkeepa on 2006-07-10
HELLo!

**jede**:
I'm not quite sure you have the same problems as us then, since we only get it on Sleep / hibernating. Plus the fact that we do have sound, it's just incredibly low after performing the above actions.

I would investigate the "dmesg" output, as well as the system logs, if I were you. To see if there's any error message that pops up anywhere, especially around the time when the proplem occours. Also, if you have _no_ sound at all, then it's most likely a totally different problem. As such it's probably better to start a thread of your own, if you can't find someone with the exact same problem.

**kjohara**:
I don't know if you've tested my theory about turning all the volume settings down before hibernating, but since I'm going to go away for a few days here I'll test it before I leave: Have to shut it down anyway. ;-)
I'll let you know what I find out, if anything.

Happy codin'!

---

### Post by Hellkeepa on 2006-07-13
HELLo!

Nope, that didn't help. Not even with the new kernel released yesterday.
Guess it's some parametres that doesn't get reset, or set properly, upon wake-up then.
Unfortunately I have no idea where to begin to look even. :(

Happy codin'!

---

### Post by LittleLebowski on 2006-09-30
I have the same problem on a Lenovo Z60.  Ridiculous.

---

### Post by ldbooth on 2006-09-30
I am having the exact same problem with sound not working after a suspend OR hibernate. I am not at all knowledgeable with linux, but perhaps this tidbit can help the knowledgable out there. 

To get the sound working all I do is open a file in Listen Music Player. For some reason it is unaffected by the suspend. If my files will not play and i hit play in Listen, the other files, say in amorok, start playing and have no problems afterward. 

It is a pain in the butt though.

---

### Post by simoncullen on 2006-11-27
Same problem here. No sound upon resume from suspend.  No sound in headphones either.  Edgy, ASUS FPj laptop.

---

### Post by thebert on 2006-12-23
I am having the same problem, has anyone found a fix yet? I haven't tried listen player yet tho.

---

### Post by davidY on 2007-01-29
Exact same problem here, except it is random which combination of speaker works but ignores jack sense, speaker does not work but jack works, speaker and jack both work.

---

### Post by jrei on 2007-04-27
Same problem on the Lenovo z60. 
I had the problem on my A21p. Unloading all sound modules helped here. I am trying to unload all modules for the z60 but i haven't found the right order yet. ;)

here is a suggested solution but it didn't work on my z60.
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T20#Fixing_Sound-After-Suspend](http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T20#Fixing_Sound-After-Suspend)

Greetings, Jörn

---

### Post by jrei on 2007-04-27
hi again,

i compared the modules loaded after system start to those after a hibernate. I expected to find some modules which were missing after hibernation but instead there were additional modules loaded. :confused: 

sb_lib
uart401
sound
snd_cs46xx
snd_ac97_codec
ac97_bus
gameport
sound_firmware

I blacklisted them in /etc/modproibe.d/blacklist but still they appear after hibernate and i am not able do get sound from my z60 anymore.

So much for now.

n8, Jörn

---

### Post by lagerratrobe on 2007-05-17
I have no sound on my D620 - period.  Running 6.06 with 686 kernel and restricted modules.

What a PITA.
--

---

### Post by tommie74 on 2007-06-17
I´ve had the same problem, no sound after waking from hibernate, and found a solution in launchpad. 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80893](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80893)

The problem seems to be related to a change in the kernel. An updated kernel is available for download:

[http://rookery.ubuntu.com/~kyle/kernels/salgado/2007-04-25/linux-image-2.6.20-15-generic_2.6.20-15.28_i386.deb](http://rookery.ubuntu.com/~kyle/kernels/salgado/2007-04-25/linux-image-2.6.20-15-generic_2.6.20-15.28_i386.deb)

install using package manager or 

```
dpkg -i /home/***your user name***/Desktop/linux-image-2.6.20-15-generic_2.6.20-15.28_i386.deb
```

hope this works for you too, as it did for many others,
Thomas.

---

### Post by asthomps on 2008-05-08
Here is the fix:

Create a file /etc/pm/sleep.d/49sound with the following script:

function kill_sound_apps() {
pidsnd=$(lsof | grep /dev/snd | awk '{ print $2 }')
pidmixer=$(lsof | grep /dev/mixer | awk '{ print $2 }')
piddsp=$(lsof | grep /dev/dsp | awk '{ print $2 }')
kill $pidsnd $pidmixer $piddsp
}

case "$1" in
hibernate|suspend)
kill_sound_apps
echo `date` shut down sound for pm 
;;
thaw|resume)
modprobe -r snd_hda_intel
modprobe snd_hda_intel
echo `date` starting sound coming out of pm 
;;
*)
;;
esac

exit $?

chmod the file as root 'chmod 755 /etc/pm/sleep.d/49sound'.

On shutdown, all sounds servers are stopped. On startup, the sound module is unloaded and loaded again. I'm not sure why this script is not in the distro when the snd_hda_intel module is used.:)

---

### Post by inportb on 2008-05-09
Dude! That is brilliant! I had the same problem and your script fixed it completely.

I have a suggestion, though. I found that lsof was *extremely* slow. I figured that it was doing some unnecessary hostname lookups, so I dropped in the -n parameter. It was *much* faster after that. I also dropped in -P to suppress port name mapping and -l to suppress PID-to-UID mapping:

```
kill_sound_apps() {
pidsnd=$(lsof -lnP | grep /dev/snd | awk '{ print $2 }')
pidmixer=$(lsof -lnP | grep /dev/mixer | awk '{ print $2 }')
piddsp=$(lsof -lnP | grep /dev/dsp | awk '{ print $2 }')
kill $pidsnd $pidmixer $piddsp
}
```

I recall having a similar issue with kexec in the past. I'll give this a try and report back.

EDIT: Aww... that didn't work. Anyway, the good thing is that suspend works well now. Thanks =D

---

### Post by genseek on 2008-06-23
Thanks a lot for the script. 
It works. 
The only problem with this is kmix. 
It does not start after hibernation. 

Any ideas how to fix it?

Thanks a lot.

---

### Post by lxowle on 2008-06-27
Thanks for that - I had the same problem and the above script fixed it up. 

I have a question - now when I resume, I get a message from ubuntu saying ""Volume Control" has quit unexpectedly - If you reload a panel object, it will automatically be added back to the panel."

I say "reload" and everything works a treat. I think I understand why this message appears, but for the purposes of creating a nice user experience, is there any way of suppressing this message and just reloading the volume control automatically?

Thanks again!

---

