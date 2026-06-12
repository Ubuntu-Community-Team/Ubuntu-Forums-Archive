---
title: "No Sound Device on Toshiba Satellite A105"
date: 2007-05-21
forum: Hardware &amp; Laptops
---

### Post by Skyhog on 2007-05-21
I have a Toshiba Satellite A105-2071.  Everything works (DVD is touchy, sometimes it works, sometimes it doesn't), except sound.  I am running KDE 3.5, and the speaker icon in the system tray has a slash through it, indicating that it is muted.  But I can't unmute it.

I am also a total newbie to Linux....any help?

---

### Post by calgarystevens on 2007-05-21
Just reread your post, and realized you have Kubuntu installed, so I don't know if this will apply to your problem or not, buyer beware.

OK, hope this helps, only try this if you have the same Intel AC97 onboard audio. When I run lspci I see this in the mix: 00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop ubuntu-minimal
sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel probe_mask=8 model=auto
sudo gedit /etc/modprobe.d/alsa-base
and add "options snd-hda-intel probe_mask=8 model=auto" to the end

Hope that helps you, I think it's because the onboard modem sound pieces take spot #1 and screw the whole thing up, this puts things the way they should be :-)

---

### Post by Skyhog on 2007-05-21
> **calgarystevens said:**
> Just reread your post, and realized you have Kubuntu installed, so I don't know if this will apply to your problem or not, buyer beware.

OK, hope this helps, only try this if you have the same Intel AC97 onboard audio. When I run lspci I see this in the mix: 00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop ubuntu-minimal
sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel probe_mask=8 model=auto
sudo gedit /etc/modprobe.d/alsa-base
and add "options snd-hda-intel probe_mask=8 model=auto" to the end

Hope that helps you, I think it's because the onboard modem sound pieces take spot #1 and screw the whole thing up, this puts things the way they should be :-)


Ok, I'm trying these steps now.  I don't know if its really Kubuntu or not, it was just Ubuntu, but I installed KDE after the initial install (sound didn't work in Gnome either).

One weird thing I noticed, is that alsamixer only shows 2 options: "Caller 1" and "Off Hook" almost like its seeing the modem as an audio device...

WIll report after trying your suggestions.

---

### Post by honeydew on 2007-05-21
hey I was having trouble.. and this worked for me!! have you guys had any luck enabling desktop effects?

---

### Post by Skyhog on 2007-05-22
That did not fix it.  Still, when I run alsamixer, it shows "Caller" and "Off Hook" for the options, as if the modem is still device #1.

No sound :(

edit:  I rebooted the computer, and now, the mixer icon is replaced with a speaker with an x over it, hovering over it reads "Mixer cannot be found."  KMix says "Current Mixer" and has a blank drop down window with no options in it.

edit2:  I am a moron.  proble != probe.  Problem solved.  Thanks a whole bunch!!

---

### Post by calgarystevens on 2007-05-22
Woohoo! I helped someone fix something, sweet. It hasn't been long since I was fixing all my quirks, and now I have nothing left to do but enjoy Ubuntu and try to help someone else :-)

Honeydew, I did try Beryl at one point, and it does work fine (not with wine or 3d games etc). But that was with Edgy, not Feisty. Here is the guide that got it running on my ATI Xpress: [http://ubuntuforums.org/showthread.php?t=321766&highlight=ati+howto](http://ubuntuforums.org/showthread.php?t=321766&highlight=ati+howto)

The cube and the effects are really wicked, one day when I don't play CS:Zero in wine anymore, I'm going to give it another go. :D

---

### Post by bsn on 2007-05-25
It works for me too!! THANKS!!!!:popcorn::popcorn:

I have TOSHIBA A105-S2712

---

### Post by mr_mister on 2007-11-10
> **calgarystevens said:**
> Just reread your post, and realized you have Kubuntu installed, so I don't know if this will apply to your problem or not, buyer beware.

OK, hope this helps, only try this if you have the same Intel AC97 onboard audio. When I run lspci I see this in the mix: 00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop ubuntu-minimal
sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel probe_mask=8 model=auto
sudo gedit /etc/modprobe.d/alsa-base
and add "options snd-hda-intel probe_mask=8 model=auto" to the end

Hope that helps you, I think it's because the onboard modem sound pieces take spot #1 and screw the whole thing up, this puts things the way they should be :-)

Works for me. Satellite a105-s1014.

I've never been happier to hear that silly startup jingle.

&#12393;&#12418;&#12394;&#65281;

J

---

### Post by TomeRaider2 on 2008-01-03
Thanks calgarystevens this solved my sound problem also. 

Being the lazy type, during my third install of Ubuntu (I was trying different distros) I just added the line "options snd-hda-intel probe_mask=8 model=auto"  to the alas-base file and rebooted. Sound worked fine no need to do the other things. This was on a clean install after installing updates with Ubuntu 7.10.

---

### Post by Das Goat on 2008-01-28
Just like hooked on phonics, this worked for me!
[I]
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop ubuntu-minimal
sudo rmmod snd-hda-intel      (there was an error about the module being in use, ignore it)
sudo modprobe snd-hda-intel probe_mask=8 model=auto
sudo gedit /etc/modprobe.d/alsa-base
and add "options snd-hda-intel probe_mask=8 model=auto" to the end[/I]

Then reboot. The sweet sounds of success!

Thanks to **calgarystevens** !

:lolflag:

---

### Post by Elrohir on 2008-01-29
> **calgarystevens said:**
> Just reread your post, and realized you have Kubuntu installed, so I don't know if this will apply to your problem or not, buyer beware.

OK, hope this helps, only try this if you have the same Intel AC97 onboard audio. When I run lspci I see this in the mix: 00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop ubuntu-minimal
sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel probe_mask=8 model=auto
sudo gedit /etc/modprobe.d/alsa-base
and add "options snd-hda-intel probe_mask=8 model=auto" to the end

Hope that helps you, I think it's because the onboard modem sound pieces take spot #1 and screw the whole thing up, this puts things the way they should be :-)

I'm executing these commands and when I get to ```
sudo rmmod snd-hda-intel
``` I get an error saying device is in use... next thing, my card is not recognized... help?

---

### Post by bob_the_third on 2008-02-17
I had the same problem as the original poster (I'm running an old Dell Ispiron 2650, not a Toshiba though), and I tried TomeRaider 2's version, and it worked beautifully!  :)  By the way, what exactly do these commands do?

Thanks.

---

