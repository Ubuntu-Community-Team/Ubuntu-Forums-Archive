---
title: "No sound on Laptop - ALC883"
date: 2007-01-21
forum: Hardware &amp; Laptops
---

### Post by FooAtari on 2007-01-21
[COLOR="Red"]Fixed!

So I went and had another read of the Comprehsive Sound Problems Thread here [http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)


I figured that after the amount of messing around I have done it might be best to do what Lord Raiden suggests here;

[B]Sometimes, sound might be configured correctly, but for some reason or another (tinkering) it stops working. One way to go back to the old setup is to reinstall Ubuntu. However, this step is actually quite unnecessary since you are reinstalling everything because of one thing.

A faster way, is to just remove the problematic packages and reinstall them cleanly.

(1) Remove these packages
Code:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils


(2) Reinstall those same packages
Code:

sudo apt-get install linux-sound-base alsa-base alsa-utils

[list][*]
VERY IMPORTANT NOTE: Ubuntu (GNOME) users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following
Code:

sudo apt-get install gdm ubuntu-desktop

(3) Reboot[/COLOR][/B]

When I rebooted I was able to load alsamixer, I turned up the surround sound and I had sound, but I had been burned here before.  So I re-booted and nothing.  I tried to load alsamixer again and it worked! So i turned up the sureound and yes sound!  Thats further than I have gotten before.  So then I tried to save settings using

[COLOR="Red"]**sudo alsactl store 0**[/COLOR]

and rebooted.  I didnt here the bongos, but then my mate sent me an IM, and I heared sound! sweet sweet sound. So it seems to fixed. Very happy! :D

------------------------------------------------

I'm not sure if I'm doing something wrong, but I can't believe that none of the solutions that I have read so far work on my laptop. (sorry this is my second thread, but I have a lot more information now so thought it might be best to start a new one)

So heres the story.

I run the Edgy Live CD and have no sound.  I can run alsamixer, turn up the "Surround" option and all appears to be good.

So I install Ubuntu, same problem.  I do the same thing again and I have sound, excellent I think to my self.  Then I reboot and no sound.... So I try and run alsamixer again and get this error

**alsamixer: function snd_mixer_load failed: Invalid argument**

When I look in the Volume Control panel there is no longer alsa mixer listed under devices, just OSS mixer.  So I have tried installing the latest alsa drivers, inclduing the alpha release and the latest realtek drivers, nothing.

I have also added the following;

[I]1. to /etc/modprobe.d/snd-hda-intel.modprobe I added
options snd-hda-intel model=ACER

2. to /etc/modprobe.d/alsa-base I added
options snd-hda-intel model=ACER

3. to /etc/modules I added
options snd-hda-intel model=ACER[/I]

and slighty different


[I]1. to /etc/modprobe.d/snd-hda-intel.modprobe I added
options snd-hda-intel model=3stack-6ch

2. to /etc/modprobe.d/alsa-base I added
options snd-hda-intel model=3stack-6ch

3. to /etc/modules I added
options snd-hda-intel model=3stack-6ch
[/I]
I am not sure if that is correct for the Realtek drivers, but I think it needs to be there for alsa drivers.  Anyone know how to fix this?  Here is some details on my hardware;

**aplay -l**
[I]allie@Laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0[/I]

**lspci**
*00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)*

**lspci -v**
[I]Audio device: ATI Technologies Inc Unknown device 437b (rev 01)
Subsystem: Acer Incorporated [ALI] Unknown device 010f
Flags: bus master, slow devsel, latency 64, IRQ 233
Memory at d0000000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>[/I]

Once final bit of information, when I reboot after the original install saying I have no sound isnt quite right, I do hear something, it's just very quiet and I have no way of turning it up.

Now though I am hearing nothing at all.  I am pulling my hair out lol.  It probably isn't helping but the way I am randomly trying different stuff and installing drivers isnt really helping.  But im no sure of the best methodical approach to getting this fixed :(

My laptop is an Acer Aspire 3053WxMi.  Ive seen others with laptops in the same range get this working, and I really dont want to put Windows back on.

---

### Post by FooAtari on 2007-01-21
Right, this is starting to annoy me now.  I thought I had fixed this. I found this guide and followed it.

[http://speeves.unt.edu/newindex/?p=211](http://speeves.unt.edu/newindex/?p=211)

And yes! I had sound.  But wait, lets restart...  And guess what?  No sound again.  Tried to run alsamixer and I see **alsamixer: function snd_mixer_load failed: Invalid argument** again

What the hell?  whats changing when the laptop reboots?? Is it not loading something or is a file being over written/changed, I dont get it....  *cries*  Obviously the sound works and the hardware in the latop is supported, so whats changing  after the restart and how do i fix it? Any suggestions welcomed :D

EDIT
This appears to be an issue with Alsa not starting when ubuntu starts... I tried installing the latest (1.0.14rc2?) alsa drivers and then I ran alsaconf, which told me alsa was running and that it would shut it down.  So after running alsaconf I was unable to run alsamixer, as alsaconf has shut it down, if that makes sense.  So obvioudly alsa is started after I install it, but not when ubuntu starts (well i think thats the problem) for some reason.  So I guess I need to know how to start alsa.  I'll keep hunting :)

---

### Post by FooAtari on 2007-01-21
Anyone? my limited knowledge cant get me much further.  I don't want to format again and re-install windows, but it's not much good without sound :(

---

### Post by FooAtari on 2007-01-22
Hmmmm, seems that no one seems able to help out :(  Stupid laptop...

I was thinking last night, after install, if I turn up surround in alsamixer it works, so I dont think this is driver issue, just an alsa issue maybe?

Can anyone tell me what I need to check to make sure everything is place so that it loads correctly on start up?

---

### Post by Alias5785 on 2007-03-27
Did you ever get this working? I have the same problem onmy Acer laptop, Identical problem. This is getting old. If it were a desktop I wouldn't care, my Fileserver, hase been running Ubuntu, with an uptime of several months.

---

