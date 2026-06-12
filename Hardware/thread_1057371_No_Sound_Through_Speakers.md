---
title: "No Sound Through Speakers"
date: 2009-02-01
forum: Hardware
---

### Post by idream on 2009-02-01
Hi, I looked everywhere:

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)
[http://ubuntuforums.org/showthread.php?t=1051987&highlight=Sound+Speakers](http://ubuntuforums.org/showthread.php?t=1051987&highlight=Sound+Speakers)
etc.

But I can't get sound to play via the speakers. Sound plays well through headphones though.

I have HP Pavilion dv4 and Ubuntu 8.10.

The lspci -v output for audio is:

```
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
	Subsystem: ATI Technologies Inc RS780 Azalia controller
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at d2410000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
```

I already spent toooooo much time for this problem. Please help, if you had a similar issue and solved it. Thanks a lot in advance.

---

### Post by Jorge_C on 2009-02-01
Hi, have a look [here]("http://ubuntuforums.org/showthread.php?t=984538"). See if post #3 solves your problem. It has indeed solved several sound problems (not exactly like yours, though) for dv4 laptops.

Hope it works for you too.

---

### Post by idream on 2009-02-02
Hi, Jorge_C:
Thank you for your reply. Unfortunately, the method did not work on mine :(

---

### Post by icanfly0307 on 2009-02-02
Are you sure that your external speakers are configured correctly? If you can hear things through headphones but not the speakers, then I'm guessing that something's wrong with your speakers.

---

### Post by lamda-core on 2009-02-02
I seem to encounter the same problem. No sound via speakers. Headphones work perfectly. 
Speakers are fine - have a dual boot with Vista.

Have been struggling with this for quite a while. really annoying...

---

### Post by idream on 2009-02-03
Yes, speakers work fine in Vista. 
There must be someone who fixed the same or similar problem and now fully enjoying Linux. Please, if you hear, help...

---

### Post by ajmctaggart on 2009-02-03
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269027]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269027")
Scratch that, I see you already tried what I would have suggested...

Are you sure these steps from Jorge's post do not correct the problem?  
It has worked for me with nearly identical hardware specs and problems...

4. editing "/etc/modprobe.d/alsa-base" and adding in my case

options snd-hda-intel model=mobile

after that I still had no sound from my speakers, but the final step solved all that
5. editing "/etc/modprobe.d/options" and adding in my case

options snd-hda-intel model=mobile

6.reboot

Now not only do my laptop speakers have sound, but also mute if I plug in my headphones.

---

### Post by idream on 2009-02-03
Thank you for the reply, ajmctaggart! I am giving it a try.

---

### Post by idream on 2009-02-03
Now I can't find my chip.. The output I got from the first commands described in [this link]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269027") is:

```

$ cat /proc/asound/cards

 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xd2500000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xd2410000 irq 2298
```

```

$ head -n 1 /proc/asound/card0/codec*

==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD71B7X

==> /proc/asound/card0/codec#1 <==
Codec: LSI ID 1040
```

And I can't find the chip in this file: */usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz*

What to do?.. :(

---

### Post by ajmctaggart on 2009-02-03
Try rajeshz's idea in that same post...
I am really sorry not to provide more hand holding today, just a bit busy...It should work though...



Hi Guys,

I solved the problem

Step 1:
Download this [http://www.linuxant.com/alsa-driver/alsa-driver-linuxant_1.0.18.0_all.deb](http://www.linuxant.com/alsa-driver/alsa-driver-linuxant_1.0.18.0_all.deb) and install it.

Step 2:
Type <gedit /etc/modprobe.d/alsa-base> in terminal and add a line
options snd-hda-intel model=laptop
at theend of the file

Type <gedit /etc/modprobe.d/options> in terminal and add a line
options snd-hda-intel model=laptop
at the end of the file

Step 3:
Restart

Step 4:
Type <gnome-volume-control> in terminal
and make sure nothing is muted.

Step 5:
If sound works, send thanks to <email address hidden> else forgive me...

---

### Post by idream on 2009-02-05
Thanks a lot for your replies, ajmctaggart:

I tried the method you posted.. Didn't work.. I give up.. Will try to enjoy Linux without sound..:neutral:

Thanks a lot for those who posted some possible solutions.

---

### Post by Jorge_C on 2009-02-05
Are you sure your speakers aren't just muted?

You can run
```
alsamixer -Dhw
```
to check it and unmute them or make them louder

---

### Post by idream on 2009-02-05
Hi, Jorge_C:

Thank you for your reply. I checked it with the command and through the GUI that Gnome has - all 100%. I just can't understand why the sound doesn't come out the speakers.. :cry:

---

### Post by ajmctaggart on 2009-02-06
Please open a Terminal and enter

```
gstreamer-properties
```

You should be able to see if there's a better way to get sound to play through by testing output options...let us know where that gets you...

Sorry it's strange that we can't get this working, I'm sure it's something being overlooked...

Let us know!

---

### Post by idream on 2009-02-06
Hi, ajmctaggart:
Thanks for the reply, I really appreciate your interest in helping me.
I checked the audio output using the GUI app you told. Seems the machine supports ALSA, OSS and PulseAudio plugins through headphones. The speakers are still deaf. 
Checked the sound events in System -> Properties -> Sound too. The selected plugins seem to work fine via headphones. 
Also alked through the previous advices to double check if I have done all of them right. Done it all...

---

### Post by idream on 2009-02-06
ajmctaggart:

Remember you advised me to install alsa driver on post #10. I reinstalled it and got a fatal error. The installation went fine, except it warned me of a fatal error. Here are the outputs:

```
$ sudo dpkg -i alsa-driver-linuxant_1.0.18.0_all.deb 
[sudo] password: 
(Reading database ... 121924 files and directories currently installed.)
Preparing to replace alsa-driver-linuxant 1.0.18.0 (using alsa-driver-linuxant_1.0.18.0_all.deb) ...

FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.27-11-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Unpacking replacement alsa-driver-linuxant ...
Setting up alsa-driver-linuxant (1.0.18.0) ...
Building modules for the 2.6.27-11-generic kernel, please wait...
done.
```

and dmesg output is:

```

...
[61145.872498] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[61145.872600] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
[61145.872603] snd_hda_intel: Unknown symbol snd_card_disconnect
[61145.872670] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[61145.872673] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[61145.873031] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[61145.873033] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[61145.873100] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
...
```

I don't know if this helps, but now I suspect the alsa driver was not installed correctly. Any guesses?

---

### Post by ajmctaggart on 2009-02-06
Success!?

Maybe that's the tip you needed...

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/315658]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/315658")

I think this is the EXACT same error, I'm reading through it now...

Maybe you'll get sound afterall...maybe not :)

I am not that skilled, just hate it when stuff like that doesn't work...

I googled the error...

---

### Post by ajmctaggart on 2009-02-06
Try booting an older kernel, it explains how to reinstall the kernel in that post too...do you have an older kernel installed?  By default I think you should...

---

### Post by idream on 2009-02-10
Hi, ajmctaggart:

I am sorry, the studies are really keeping me busy. 

Yes, you're right. I have two kernels.

Tried to load Ubuntu on the 2.6.27-7 kernel (older one), still can't hear anything. do you think I should reinstall my kernel?

---

### Post by ajmctaggart on 2009-02-11
idream,

Believe me I understand you on the studies, same here right now...

If you have the time and are brave enough to maybe screwup your system, do all the updates you possibly can to the existing system and reinstall the kernel...

Read through the last thread we've been talking about, and make sure there's nothing we missed...

Good Luck, will check back in a day or so...

---

### Post by idream on 2009-02-13
:) Thanks a lot, ajmctaggart:

Have the reading break coming, so will try to fix the sound then. Thanks for the comments and willingness to help!

---

### Post by idream on 2009-03-12
Hello, everyone!
I found the solution. The problem is not related to a Linux, because right now I have Fedora installed and it didn't have a sound either.
So, follow the instructions [here]("http://ubuntuforums.org/showthread.php?t=1073090").
Thanks for everyone who tried to help me again. I really appreciate your time and interest.

---

