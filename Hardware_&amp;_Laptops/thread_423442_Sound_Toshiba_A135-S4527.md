---
title: "Sound Toshiba A135-S4527"
date: 2007-04-25
forum: Hardware &amp; Laptops
---

### Post by mostholy on 2007-04-25
Just got this laptop and am running the cdboot version of feisty in preparation of install (and deVistafication).  So far everything seems to be functional (wifi proof is posting this) except for sound.  I've begun the forum searching but thought I would post to see if this has been figured out and not posted yet.  

thanks in advance.

---

### Post by mostholy on 2007-04-25
Sorry, sound appears to be 82801G (ICH7 Family) High Definition Audio Controller (per device manager).

---

### Post by Linuturk on 2007-08-13
I have the same laptop. I have not been able to get sound working either.

Here is my lspci | grep Audio

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

I've read the wiki and searched the forums as well. It seems this might be covered under a filed bug. Apparently there is a fix on the way, but I wanted to see if there was a temp fix.

---

### Post by Reducer on 2007-08-13
I have the same laptop and haven't had sound since the release version of Edgy Eft.  Trying Gutsy Gibbon now and still nothing.  Sound works just fine in Mandriva Spring 2007.

Launchpad bugs are here:

[102647]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/102647")
[85869]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/85869")
[88400]("https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88400")

Please add your comments.

Jason

---

### Post by Linuturk on 2007-08-15
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/85869](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/85869)

The fix in that thread worked for me, per my comments. Now I just have to fix the headphones.

---

### Post by xcat442 on 2007-11-12
Maybe this will work.

Open up the terminal and type: sudo gedit /etc/modprobe.d/alsa-base

Scroll down through the alsa-base file til you find the line: # Ubuntu #62691, enable MPU for snd-cmipci

Now paste this line just above it: options snd-hda-intel model=3stack

Save the file and reboot your laptop. This has worked for me, I hope it works for you.

Peace

P.S. This has been posted in a few areas, but the more the merry I say:)

---

### Post by sillypants on 2008-01-19
options snd-hda-intel model=3stack fix worked for me on my A135-S4527.  Thanks!!

---

### Post by secretagent587 on 2008-02-12
I've got a Toshiba A135-S4527 running Gutsy 7.10. I found that "options snd-hda-intel model=3stack" would enable sound, but the headphone jack sensing would not work properly. I changed the line toand now everything works. The speakers turn off when the headphones are plugged in.

Update: I found that the PC speakers would un-mute (with the headphones plugged in) if the volume control wheel on the front of the laptop was adjusted. Seems to be working after upgrading Alsa to 1.0.16 using these instructions: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) with the line "options snd-hda-intel model=lenovo" added to /etc/modprobe.d/alsa-base

---

