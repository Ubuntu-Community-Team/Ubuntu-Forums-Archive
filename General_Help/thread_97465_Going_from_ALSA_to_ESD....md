---
title: "Going from ALSA to ESD..."
date: 2005-12-01
forum: General Help
---

### Post by Mosey on 2005-12-01
So i've been working on trying to get my Soundblaster Live! 24 bit card to work for a little over six hours...

I read in a forum that SB Live! 24 bit, because it uses a cheaper chip, needs to use ESD as opposed to ALSA.

1. Is this true?
2. If it is true than can anyone point me in the direction of a how-to regarding this switch?

Thanks!:cool:

---

### Post by Sutekh on 2005-12-01
The Live! 24bit (ca0106)?  Breezy detected and autoconfigured my card to use OSS and it works for me.  I never touched anything.  When I choose to use ALSA, it plays but constantly beeps at me.

---

### Post by Mosey on 2005-12-01
Yeah the ca0106!

OSS is the only system that tests...but i'm not hearing anything. I checked alsa mixer and everything is unmuted and up...

What should I do?

---

### Post by Sutekh on 2005-12-01
[QUOTE=Mosey]Yeah the ca0106!

OSS is the only system that tests...but i'm not hearing anything. I checked alsa mixer and everything is unmuted and up...

What should I do?[/QUOTE]
If you use OSS, the alsamixer has no effect on volume (different sound sink altogether). 

Can you tell me what this command outputs?
```

lsmod | grep oss

```

---

### Post by Mosey on 2005-12-01
snd_pcm_oss            53664  0
snd_mixer_oss          17280  1 snd_pcm_oss
snd_pcm                86792  4 snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd                    55556  8 snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer

---

### Post by Sutekh on 2005-12-01
OK, that's what I have, do you get system sounds?

Is your SB card onboard?

And (stupid question, but have to ask) are you using Breezy?

---

### Post by Mosey on 2005-12-01
No, no sound at all...system or otherwise.

---

### Post by Sutekh on 2005-12-01
I was reading some of your other posts... have you ever had sound or has it been broke from the start?  Also what was your onboard sound and why is it disabled?

---

### Post by Mosey on 2005-12-01
I've never been able to get this Soundblaster Live! 24bit card to work. I bought it because the HD onboard audio in my Pentium D motherboard is not yet compatable with Linux.

I was told this by a "guru".

I bought a card...still no friggin luck.

---

### Post by Sutekh on 2005-12-01
I feel your pain, in Hoary, getting this SB card working was a PITA.  Took me forever.

So the SB card is new, and installed after installing Breezy?  I wonder if it would have been detected if it was installed before installing Ubuntu...  Is the new card detected by the OS;   
```

lspci

```

I have a line like this;
0000:01:0d.0 Multimedia audio controller: Creative Labs SB Audigy LS

---

### Post by Mosey on 2005-12-01
Here is my output:

0000:00:00.0 Host bridge: Intel Corp. 915G/P/GV Processor to I/O Controller (rev 04)
0000:00:01.0 PCI bridge: Intel Corp. 915G/P/GV PCI Express Root Port (rev 04)
0000:00:02.0 VGA compatible controller: Intel Corp. 82915G Express Chipset Family Graphics Controller (rev 04)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1c.1 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
0000:00:1c.2 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
0000:00:1c.3 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.2 IDE interface: Intel Corp. 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:06:00.0 Multimedia audio controller: Creative Labs SB Audigy LS
0000:06:08.0 Ethernet controller: Intel Corp.: Unknown device 1064 (rev 01)

Apparently it knows it's there...it just dosn't give a damn.

---

### Post by Sutekh on 2005-12-01
[QUOTE=Mosey]Here is my output:
0000:06:00.0 Multimedia audio controller: Creative Labs SB Audigy LS
[/QUOTE]
ok so it knows you have the card, I remeber when I used to have problems, I had to kill esd before alsa or any other sound would work.
```

kill esd

```
You can tell I'm running thin :(

---

### Post by Mosey on 2005-12-01
I appreciate your time...but...

killall esd produces nada.

No sound.

When I have beep-media-player open...a OSS test in Multi Media System Selector produces this: Failed to construct test pipeline for 'OSS - Open Sound System'

WHen I close Beep Media Player...it tells me it's testing but I hear nothing!

What does this mean?

---

### Post by Sutekh on 2005-12-01
Hey can you run alsamixer at all?

---

### Post by Mosey on 2005-12-01
Yes.

---

### Post by Sutekh on 2005-12-01
Right click on volume and choose preferences, you should see this (at bottom)

Make sure that the channel is Analog front.

Or run **alsamixer** and see if you have the same channels muted/unmuted

---

### Post by Mosey on 2005-12-01
It was set on Analog Center...I switched it to front...still no sound at all...

Do I need to ctrl-alt-backspace to get things shaking?

---

### Post by Sutekh on 2005-12-01
At this stage, why not?

---

### Post by Mosey on 2005-12-01
Restarted Gnome. Still nothing.

This is terrible.

---

### Post by Sutekh on 2005-12-01
I'm just looking at things that stop my sound from working;
in alsamixer is the SPDIF Out OFF?

---

### Post by Mosey on 2005-12-01
Yes it is.

---

### Post by Sutekh on 2005-12-01
Sorry I can't think of anything else that makes my soundcard setup differently to yours, it doesn't make sense to me.

---

### Post by Mosey on 2005-12-01
It's alright. You really were trying to help and I appreciate it.

I'd probably just go about reinstalling...but I really don't want to lose all my mp3s and settings (themes/codecs/compiled packages/tweaks etc)

DAMN!:mad:

---

### Post by Sutekh on 2005-12-01
Still it bites that you still can't get it working after everything.  I hate admitting defeat and re-installing.  

Do you have any extra partitions to shove your files on to, while re-installing?

---

### Post by Mosey on 2005-12-01
No, the whole damn drive is dedicated to a mute version of Ubuntu.

If I do go get a new sound card tomorrow...whats the best brand to get...?

---

### Post by Sutekh on 2005-12-01
Oh don't ask me!  I really wouldn't know, and I didn't choose mine, it was on the board I got.  I would really hope that the SB 24bit would work by itself (like it did for me) if you re-installed.

If you really want to buy a new one, I'd ask around to find a card that will work with Ubuntu.

---

### Post by Mosey on 2005-12-01
bump

---

### Post by Mosey on 2005-12-01
Friggin' bump.

---

### Post by Sutekh on 2005-12-01
Similar problem, similar chipset - 82801DB (yours is the 82801FB); re-enable (the onboard sound) and try?

[Sound dissappeared in 5.10]("http://ubuntuforums.org/showthread.php?t=90081")
[No Sound]("http://ubuntuforums.org/showthread.php?t=94879&page=2") 
[Sound Fix for Intel ICH4]("http://www.ubuntuforums.org/showthread.php?t=87849&highlight=ich4")

I don't know who told you that your chipset isn't supported but the if the Ubuntu Wiki is to be relied on; it is supported. [https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards?highlight=%28ICH6%29]("https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards?highlight=%28ICH6%29")

---

