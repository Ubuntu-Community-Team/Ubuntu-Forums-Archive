---
title: "Windows sound broken by Karmic upgrade"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by PhilJames on 2009-11-06
Recently I upgraded Jaunty to Karmic on my Xp dual boot system, and knocked out all sound in Windows, while Ubuntu sound is unchanged.
[Realtek integrated sound on Intel motherboard]

I restored sound to windows by running chdsk /r from cmdprompt, but when I went back to Ubuntu and back to windows I had the same problem. I did this a third time before deciding to write this comment.

Even though I've been using Ubuntu for a couple of editions now, this is something that will hamper my use unless I can find a fix.

---

### Post by PhilJames on 2009-11-07
I love Ubuntu, but I want to keep Windows. 
Running a repair for a couple of hours every time I return to Windows is not an option.
Has anyone got any ideas, please?

---

### Post by coffeecat on 2009-11-07
I saw your first post but I couldn't think of anything sensible to say. However, thinking about this.....

Realtek integrated sound on an Intel motherboard is fairly common. If Karmic was doing this to Windows with that combination, you'd see a lot of help posts about it on this forum. But there aren't, which makes me suspect something coincidentally happened in Windows at the time you upgraded.

Why not try this experiment. Either way it may prove or disprove that Karmic is the culprit.

First of all, boot up Windows and ensure that sound is working. Now boot up with the live JAUNTY CD, and do something that uses the onboard sound card. Now boot back into Windows. Is Windows able to play sound, or do you have to repair Windows again?

Now boot into the Karmic live CD - not into your HD installation - and use sound again. Now boot into Windows again - what's happening?

In the meantime I'll do a bit of searching around. You've intrigued me.

By the way, when you're in some flavour of Ubuntu or another, post the terminal output of "lspci". It will interesting to see exactly which sound chipset you have.

---

### Post by coffeecat on 2009-11-07
Further thoughts:

Either my google-fu is not up to much or there's absolutely no one out there having your problem. The only relevant hit was - this thread. :|

Anyway, where did you get the idea to do a 'chkdsk'? It's an odd way to repair sound problems because chkdsk is used for inspecting and repairing filesystems. And the /r switch is for:

> Locates bad sectors and recovers readable information (implies /F).

/F =

> Fixes errors on the disk. Does not scan for bad sectors.So, if you're fixing a problem with chkdsk /r it means you've got bad sectors in your C: drive and they're being fixed each time you run the chkdsk /r.

You know what I think now? I think you've got a failing hard drive - or at least one with increasing bad sectors. Have you tried simply rebooting into Windows? Does the sound still work?

If you've got bad sectors in the Windows partition, you're likely to get bad sectors elsewhere sooner or later. Perhaps you need to be thinking of a hardware problem.

---

### Post by PhilJames on 2009-11-07
Thankyou for your thoughtful reply."coffeecat"
It's given me a lot more to work with and I'll get back to you when I've tried your suggestions.

---

### Post by PhilJames on 2009-11-09
I'm quite willing to admit the possibility this is a hardware problem and not the fault of Karmic Ubuntu at all.
The score so far...
Xp sound ok 
>boot into Jaunty live cd-sound ok
>boot into xp - sound ok
>boot into Karmic live cd - sound ok
>boot back int xp - **sound non-existent**
and also I noticed the system clock had been knocked out by 6 hours!?

I suppose I'm looking at buying a new hard drive soon, but it's still very strange that it's only Karmic and not Jaunty that has this effect.

Oh well off to run my windows repair program again.

---

### Post by PhilJames on 2009-11-09
Other people with what appears to be the same problem
[http://forums.creative.com/t5/Windows-7/windows-7-SB-Audigy-SE-OEM-sound-stopped-working/m-p/540485]("http://forums.creative.com/t5/Windows-7/windows-7-SB-Audigy-SE-OEM-sound-stopped-working/m-p/540485")

---

### Post by renkinjutsu on 2009-11-10
> **PhilJames said:**
> Other people with what appears to be the same problem
[http://forums.creative.com/t5/Windows-7/windows-7-SB-Audigy-SE-OEM-sound-stopped-working/m-p/540485]("http://forums.creative.com/t5/Windows-7/windows-7-SB-Audigy-SE-OEM-sound-stopped-working/m-p/540485")

the people posting on that page have [this]("http://www.microsoft.com/windows/compatibility/windows-7/en-us/Details.aspx?type=Hardware&p=Creative%20Sound%20Blaster%20Audigy%20SE%20Sound%20Card&v=Creative&uid=70SB057000000&pf=0&pi=6&s=creative%20audigy&os=64-bit") chip... is that what you have too?

---

### Post by PhilJames on 2009-11-12
> **renkinjutsu said:**
> the people posting on that page have [this]("http://www.microsoft.com/windows/compatibility/windows-7/en-us/Details.aspx?type=Hardware&p=Creative%20Sound%20Blaster%20Audigy%20SE%20Sound%20Card&v=Creative&uid=70SB057000000&pf=0&pi=6&s=creative%20audigy&os=64-bit") chip... is that what you have too?
Sorry I'm slow replying
 
I don't have that chip. But it was only reference I could find to a similar problem. I did use one of their temporary solutions, which was to close down the computer after using Ubuntu Karmic and switching back on before booting into Windows. Yhis solved the sound problem, I did have sound in Windows until the next time I used Ubuntu.

I then tried a clean reinstall of Karmic Ubuntu and found I didn't have the original problem any more. Sound works fine in Windows and Ubuntu but...
each time I use Ubuntu and then Windows[ whether I stop the computer or not] the system clock is reset in Windows [put forward by 5 hours, which is UTC, from me]

Again, this is maybe not related to the original problem.
Maybe I have a hardware problem.

**Can anyone point me to any threads about the difficulties or not of updating the bios in a dual boot system? **

---

### Post by paradox242 on 2009-11-17
I had Windows 7 64-bit and Ubuntu 9.04 installed at the same time with no issues with my Audigy SE card. 

I did a fresh install of Ubuntu 9.10 and come to find that while sound continues to work fine in Ubuntu, it's totally hosed in Windows. Does not work at all, even from a cold boot. Have installed various different driver versions, both from the Creative support site, and from Windows Update. 

That Ubuntu could have anything to do with it did not even occur to me until I ran across the same forum posting mentioned earlier in this thread, and then yeah, come to think of it, it did stop working right after I installed 9.10 (I don't think I used Windows until two weeks later). 

It doesn't make sense though, that Ubuntu could do anything to the way Windows interacts with the sound card. The only difference during boot is that 9.10 uses Grub2, but even then I'm not aware of anything the Grub2 bootloader could do differently, since in theory its job is to load ntldr and then Windows is in control from there.

This one has me stumped.

---

### Post by adam2348 on 2009-12-30
I am having the problem too!  

I upgraded my ubuntu 9.04 64bit to ubuntu 9.10 64bit and windows xp sound stopped playing.  Everything seems fine in windows, but no sound coming out of speakers.  I can't test the digital output sorry.  

I have built on sound and a creative sb live!24 card.  I used the sb card for sound, but neither play sound in windows after upgrade.  

I'm going to try the chkdsk /F to see if that works...I really don't want to wait hours for /r.  I doubt sectors have anything to do with it...  Not really sure how a chkdsk would fix it either tho.  

I'll try the remove power for 10 sec, that actually makes sense, as it seems as though Ubuntu is putting the card into a mute state.  maybe it's when it releases control over it?  

I dunno, but i would love for someone to help so we can finally have a solution for this inconvenient and annoying problem.

---

### Post by presence1960 on 2009-12-30
> **adam2348 said:**
> I am having the problem too!  

I upgraded my ubuntu 9.04 64bit to ubuntu 9.10 64bit and windows xp sound stopped playing.  Everything seems fine in windows, but no sound coming out of speakers.  I can't test the digital output sorry.  

I have built on sound and a creative sb live!24 card.  I used the sb card for sound, but neither play sound in windows after upgrade.  

I'm going to try the chkdsk /F to see if that works...I really don't want to wait hours for /r.  I doubt sectors have anything to do with it...  Not really sure how a chkdsk would fix it either tho.  
[B]
I'll try the remove power for 10 sec, that actually makes sense, as it seems as though Ubuntu is putting the card into a mute state.  maybe it's when it releases control over it?  [/B]

I dunno, but i would love for someone to help so we can finally have a solution for this inconvenient and annoying problem.

The power down statement rang a bell. I had problems with popping loudly when trying to use sound after a period of inactivity. I found that if you have an HDA audo card karmic does put that in powerdown mode. I adjusted the setting in /etc/modprobe.d/alsa-base.conf

It was suggested to comment out the last setting in that file but I got it to not powerdown by changing timeout to 0 and powersave to N like this:
```

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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
[B]Power down HDA controllers after 0 idle seconds
options snd-hda-intel power_save=0 power_save_controller=N[/B]
```

Now my sound card does not go into powersave mode. hope this helps or at least points you in the right direction.

---

