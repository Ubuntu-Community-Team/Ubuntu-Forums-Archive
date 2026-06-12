---
title: "&quot;Dummy Output&quot; audio on 14.04"
date: 2016-03-22
forum: Hardware
---

### Post by Drone4four on 2016-03-22
I&#8217;m troubleshooting my audio too with a similar issue.  I suspect the source of my problem is that I used kdm instead of gdm to login into my xsession and KDE uses pulseaudio and Gnome uses alsa.  Or maybe I&#8217;m way off on that.  Anyways, Gnome sound settings now informs me that the only device for sound output is, &#8216;Dummy Output&#8217; which is different from from what I&#8217;m  used to seeing (&#8216;HD intel&#8217;, &#8216;analog&#8217;, &#8216;nvidia HDMI&#8217;, et. al.).

I found some other [recent]("http://ubuntuforums.org/showthread.php?t=2317868") [threads]("http://ubuntuforums.org/showthread.php?t=2316040") with Ubuntu users discusssing broken audio, but none of them address &#8216;Dummy Output&#8217; specifically.  However many other Ubuntu users have encountered this Dummy Output problem in the past according to Google.  One common solution to resolve this issue is to find out what audio card is active, look up the HD audio model in the kernel documentation, edit the alsa-base configuration file in /etc/ by adding the model identifier and then reloading alsa.  This solution works for many people.  Here is one concise, helpful walk-through titled, "[Sound not working, dummy output]("http://linux.chrissweeney.co.uk/topic.php?t=93")". From this guide, here are the recommended steps verbatim:
> 
**1.** First find out which sound card you are using:*
```
cat /proc/asound/card0/codec* | grep Codec*
```

**2.** Look up your model here:
```
zless /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz*
```

**3.** Or visit:
```
http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txt*
```

**4.** Edit the following file:*
```
 vim /etc/modprobe.d/alsa-base.conf*
```

**5.** Add the following line at the end:
```
options snd-hda-intel model=[PUT YOUR MODEL HERE]*
```

**6.** Finally run:
```
sudo alsa force-reload*
```


I&#8217;m stuck at the first step.  This is what happens when I enter that cat-grep command:

```
 $ cat /proc/asound/card0/codec* | grep Codec
zsh: no matches found: /proc/asound/card0/codec*
```
Why are there no matches found? What am I doing wrong?

I also tried:```

$ lspci -v | grep -i audio
00:1b.0 Audio device: Intel Corporation C610/X99 series chipset HD Audio Controller (rev 05)
06:00.1 Audio device: NVIDIA Corporation GF114 HDMI Audio Controller (rev a1)
$
```
So that indicates what audio hardware exists in my system, but there are no instances of &#8216;nvidia&#8217; or &#8216;c610&#8217; in that kernel documentation link.  

Here is a similar command:
```
$ lspci -v | grep -A7 -i "audio"
00:1b.0 Audio device: Intel Corporation C610/X99 series chipset HD Audio Controller (rev 05)
	Subsystem: Gigabyte Technology Co., Ltd Device a182
	Flags: fast devsel, IRQ 22
	Memory at fa230000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation C610/X99 series chipset PCI Express Root Port #1 (rev d5) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
--
06:00.1 Audio device: NVIDIA Corporation GF114 HDMI Audio Controller (rev a1)
	Subsystem: eVga.com. Corp. Device 1568
	Physical Slot: 4
	Flags: fast devsel, IRQ 17
	Memory at fa080000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

08:00.0 USB controller: Fresco Logic FL1100 USB 3.0 Host Controller (rev 01) (prog-if 30 [XHCI])

```

I also tried:
```
$ sudo alsa force-reload 
[sudo] password for user: 
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).
$
```
Is this saying that alsa isn't running? If alsa isn't running, how do I start it?  So I tried: 
```
$ sudo alsa load                        
Usage: /sbin/alsa {unload|reload|force-unload|force-reload|suspend|resume}
So alsa load isn't a command. 
$ 
```
So I tried:
```
$ sudo alsa resume
```
Did that turn alsa on?

How do I determine what audio control I have and why is it not showing up with $ cat /proc/asound/card0/codec* | grep Codec?  Is there a better approach to resolving my Dummy Output issue - - like what other information could I provide to better diagnose my issue?

I&#8217;m running 14.04 w/ kernel: Linux 3.13.0-83-generic x86_64 .

And the reason why I switched to kdm was to get around a different issue with a borked gdm.

Thanks for your attention.

---

### Post by mastablasta on 2016-03-22
default dm is lightdm.

what about :

```
sudo alsa reload -c
```

what card do you see in alsamixer (terminal based app)? is alsa even installed?

I get this from time to time. the reload trick works in 2/3 of the time when the issue arises. sometimes though I need to turn off the PC and unplug the power, until I hear a pop in the speakers about 15 seconds after taking the power. then I turn it back on and all is well card gets recognised. haven't seen this kind of thing since DOS games crashes, where sound would be stuck in a loop until a full hard reset was made (a the time buttons on the PC were flip switches not push buttons).

---

### Post by Drone4four on 2016-03-22
```
$ sudo alsa reload -c
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).
$
```

> what card do you see in alsamixer (terminal based app)? is alsa even installed?

That's a great question because I am so very surprised what I discovered when I tried running alsamixer from my shell:
```
$ sudo alsamixer
cannot open mixer: No such file or directory
```
Does this indicate that alsamixer isn't installed?? When I go to install the alsamixer package in apt's repos, it doesn't auto-complete to just plain old 'alsamixer', the auto-compete feature jumps directly to a package called, 'alsamixergui'.  So I install that package and when I run it as, it produces one error message.  [[<<<  **EDIT there are two errors:**   >>>]]  The first error in my shell reads:```
$ sudo alsamixergui 
Home directory not accessible: Permission denied 
```The second error message is a pop up window:
```
alsamixer: function snd_ctl_open failed for default: No such file or directory
```  wtf is going on here?

Now I'm wondering that this problem might have to do with changing my user's default shell.  Last night I began playing around with ohmyzsh.  I'm running zsh today.  The root user still has bash by default. Could this be the source of my problem or am I way off?

> then I turn it back on and all is well card gets recognized. haven't seen this kind of thing since DOS games crashes, where sound would be stuck in a loop until a full hard reset was made (a the time buttons on the PC were flip switches not push buttons). I'll resort to powering off my machine later.  And yes I remember those days very clearly.  =D My dad bought a 286 in the late 80s.  My brothers and I played Wolf3D.  Our computer had a flip switch.

And thank-you, **mastablasta** for your help so far.

---

### Post by Drone4four on 2016-03-22
> **mastablasta said:**
>  sometimes though I need to turn off the PC and unplug the power, until I hear a pop in the speakers about 15 seconds after taking the power. then I turn it back on and all is well card gets recognised. 


Yikes! The solution was as easy as rebooting my computer.  I should have tried this first, not deferred it to last resort.

Running alsamixer in a terminal opens up alsamixer.  No more errors. And I have my audio back.

Thanks again, **mastablasta**.

---

