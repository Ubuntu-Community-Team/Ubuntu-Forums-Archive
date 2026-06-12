---
title: "No Sound after Update with Realtek ALC888"
date: 2010-03-10
forum: Hardware
---

### Post by Zitroneneis on 2010-03-10
Hi, 
after having used Ubuntu for about a year now, without problems I couldn't solve myself, I now ran into one where I really need help.

My mainboard is a MSI K9N Neo V2 with the nVidia520 Chipset. I use the onboard soundcard which is a Realtek ALC888 Chip.

Everything worked flawless (starting from 8.04 to 9.10) but about 3 weeks ago I couldn't get any sound from the board after a System Update.

I first thought it would be a bug in the kernel which would be fixed sooner or later, but as I updated again today (to a new kernel) and I still got no sound I decided to seek help from the community.

aplay -l gives me 
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

in ->System->Preferences->Sound 
I've got the choice between
[LIST]
[*]Internal Audio Digital Stereo (IEC958 )
[*]Internal Audio
[/LIST]
Internal Audio is selected, as I want to use a Headphone.

No, the Volume isn't muted...
and Yes, I tried all 6 available Jacks at the back of my PC ;) 

any Ideas that could help me are welcome
Thanks a lot in advance....

---

### Post by ajgreeny on 2010-03-10
Run ```
alsamixer
``` in terminal to check that something you can not see with the other applications is not muted or too low.  It is always the first thing to check when sound problems rear their ugly head.

---

### Post by Zitroneneis on 2010-03-11
hi, 
I checked that already, and sadly enough the soloution isn't so easy.....

I just went through my old kernels and found out, that sound works fine in the kernel versions from 2.6.27-7 to 2.6.27-15....
Stupidly enough my w-lan stick doesn't get recognized in these Kernel versions.

An when I boot the kernel starting from 2.6.31-17 to 2.6.31-20 the sound is gone, but the w-lan works

---

### Post by pmeves on 2010-03-21
> **Zitroneneis said:**
> hi, 
I checked that already, and sadly enough the soloution isn't so easy.....

I just went through my old kernels and found out, that sound works fine in the kernel versions from 2.6.27-7 to 2.6.27-15....
Stupidly enough my w-lan stick doesn't get recognized in these Kernel versions.

An when I boot the kernel starting from 2.6.31-17 to 2.6.31-20 the sound is gone, but the w-lan works

Same kernel, same soundcard, same problem -> no sound... i don't know what to do anymore. but my wlan doesn't work ^^'

How to reinstall back our sound card's drivers?

Ubuntu's been such a disapointment lately...

---

### Post by Lobby Dosser on 2010-11-04
Try this.  
sudo gedit
Then open /etc/modprobe.d/alsa-base.conf

At the end of the file add a new line
options snd-hda-intel model=generic

Save and then reboot.  It worked for me with the Realtec ALC887

---

### Post by neilscrim on 2011-09-07
Brilliant info! :)

I'd installed 11.04 , found it bugged to hell (although the sound worked ok) so I removed it and installed 10.04.3. No sound, not even Alsa would cure the problems so I tried the above solution. Sorted! Many thanks Lobby Dosser.

For info the m/board is  a gigabyte GA-M68M-S2P with a Realtek ALC888 chip.

---

### Post by ipguru99 on 2012-03-16
Ubuntu 12.04 Beta ALC888 Nvdia HDMI Audio...

Just trying to think of what else I can put in here, because this just saved me BIG time!  I have messed around for days, trying to get my GeForce 220 HDMI Audio turned off and the plain old headphones turned on. 

I put model=generic, rebooted and there they were, under Sound.. sweet!  Thanks!!

---

### Post by palmwedel on 2012-07-16
> **Lobby Dosser said:**
> Try this.  
sudo gedit
Then open /etc/modprobe.d/alsa-base.conf

At the end of the file add a new line
options snd-hda-intel model=generic

Save and then reboot.  It worked for me with the Realtec ALC887

Perfect, editing the alsa config file solved the problem for me too. Using ASUS KFN32-D SLI board with nVIDIA MCP55 / ALC888 sound.

So easy it was... Don't believe it. Great, got the sound now at last.

---

### Post by Aprilpaul on 2013-02-02
Thanks this fix also solved my problem with Ubuntu 12.10 not recognising my built in Intel sound card on a Gigabyte GA-81915 motherboard.

---

