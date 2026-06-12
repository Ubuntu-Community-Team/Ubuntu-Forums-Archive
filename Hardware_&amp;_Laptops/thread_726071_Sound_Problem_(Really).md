---
title: "Sound Problem (Really)"
date: 2008-03-16
forum: Hardware &amp; Laptops
---

### Post by doctorzeus on 2008-03-16
Hey, 

I have an Acer aspire 7720 laptop and the sound isn't working!

I know there are loads and loads of threads with people who have similar problems but I have tried A LOT of them and they either lead to dead ends or don't work.

so,

this is what sound card I have (yes it detects it)

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Now I have tried this site ([http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)) 
but then it tells me to try unmuting the sound by pressing M and it says their should be a green box under the sound volume bars. Now I know I'm not colour blind but 
**_I SEE NO GREEN BOX  _**

Yeah so basically if anyone can help me gett my sound ON I would really apreciate it because it really gets irritating trying to install flash player for 3 days, finally achiving it and then discover that your sound doesn't work.

Thanks

Doctorzeus.

P.S

Sorry for my somewhat insolent sarcasm but I'm getting a teeny, tenny bit irritated.  
(](*,))

---

### Post by Nepherte on 2008-03-16
It might be a matter of specifying the correct module parameter:
see the corresponding section on this site: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by doctorzeus on 2008-03-16
> **Nepherte said:**
> It might be a matter of specifying the correct module parameter:
see the corresponding section on this site: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Yeah, 
um how do you install the Kernel headers?

Doctorzeus

---

### Post by Nepherte on 2008-03-16
I'd wait with reinstalling/upgrading the alsa drivers till nothing else helps. But if you're really in to it, that help page is just a matter of copy/pasting (after carefully reading the text guiding the commands of course) the commands in the grey code boxes.
So to install 'the required tools and kernel headers', just copy/paste the following command in a terminal window:
```
sudo aptitude install build-essential libncurses-dev gettext linux-headers-`uname -r`
```

---

### Post by doctorzeus on 2008-03-16
> **Nepherte said:**
> I'd wait with reinstalling/upgrading the alsa drivers till nothing else helps. But if you're really in to it, that help page is just a matter of copy/pasting (after carefully reading the text guiding the commands of course) the commands in the grey code boxes.
So to install 'the required tools and kernel headers', just copy/paste the following command in a terminal window:
```
sudo aptitude install build-essential libncurses-dev gettext linux-headers-`uname -r`
```

Yeah I've done that, does that mean I can skip the "Install your kernel headers" bit?

If not, I have downloaded all the stuff it says to download, it is in the directory /tmp/alsa

What do I do now cause the thing won't install, what do I type in?

Doctorzeus

---

### Post by Ace2016 on 2008-03-16
Does alsamixer (run alsamixer in the command line) show any channels, they might just be muted, press m to unmute, worth a shot before recompiling stuff

Screenshot of what alsamixer should look like, although the channels you have will most likely be different, the 00 at the bottom of the column will me MM if muted :  
[[IMG]http://img138.imageshack.us/img138/9940/11el2.th.png[/IMG]](http://img138.imageshack.us/my.php?image=11el2.png)

If this fails, you might want to try editing /etc/modprobe.d/alsa-base
and adding 

```
options snd-hda-intel model=acer-aspire
```

after making the change you have to reboot for the settings to take effect. On my laptop I have to use:

options snd-hda-intel model=laptop  ( HP Pavillion DV9000 nvidia chipset showin in screenshot)

---

### Post by doctorzeus on 2008-03-16
> **Ace2016 said:**
> Does alsamixer (run alsamixer in the command line) show any channels, they might just be muted, press m to unmute, worth a shot before recompiling stuff

Screenshot of what alsamixer should look like:  
[[IMG]http://img138.imageshack.us/img138/9940/11el2.th.png[/IMG]](http://img138.imageshack.us/my.php?image=11el2.png)

If this fails, you might want to try editing /etc/modprobe.d/alsa-base
and adding 

```
options snd-hda-intel model=acer-aspire
```

after making the change you have to reboot for the settings to take effect. On my laptop I have to use:

options snd-hda-intel model=laptop

This is what mine looks like (see attachment)

Dan

---

### Post by superprash2003 on 2008-03-16
hope this helps [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by Nepherte on 2008-03-16
> **Ace2016 said:**
> 
You might want to try editing /etc/modprobe.d/alsa-base
and adding 

```
options snd-hda-intel model=acer-aspire
```

after making the change you have to reboot for the settings to take effect. On my laptop I have to use:

options snd-hda-intel model=laptop  ( HP Pavillion DV9000 nvidia chipset showin in screenshot)
Try this first. If that doesn't work, you can try installing alsa version 1.16 (latest version).
That means you can skip the kernel headers part. It is best you don't download them in the /tmp directory but in your /home/username directory, saves you a lot of problems with user rights.

---

