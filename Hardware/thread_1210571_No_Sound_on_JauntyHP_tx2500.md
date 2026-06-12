---
title: "No Sound on Jaunty/HP tx2500"
date: 2009-07-11
forum: Hardware
---

### Post by SomebodySane on 2009-07-11
First off I'm completely new to Ubuntu/Linux/This Forum so explain everything very explicitly as though you are talking to an idiot.  Seriously, don't assume I know anything.

I'm trying to work my way through this: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) and I've made it to the third to last step ("So armed with this knowledge, it's about time to start configuring your system").  At this point it gives me:

sudo nano /etc/modprobe.d/alsa-base.conf

which opens a little menu in which I 'm completely lost.

These are the two links that the tutorial told me to look up:

[http://www.alsa-project.org/db/?f=e18ac54ba7c10ad1e2d49b1acfc1e36544e6b5ee](http://www.alsa-project.org/db/?f=e18ac54ba7c10ad1e2d49b1acfc1e36544e6b5ee)
[http://git.alsa-project.org/?p=alsa-kmirror.git;a=blob;f=Documentation/ALSA-Configuration.txt;h=30499cf77d5628968a9347b3a6440a0064713eaf;hb=4c767126ddc90264b8d6584548f4aa859216f481](http://git.alsa-project.org/?p=alsa-kmirror.git;a=blob;f=Documentation/ALSA-Configuration.txt;h=30499cf77d5628968a9347b3a6440a0064713eaf;hb=4c767126ddc90264b8d6584548f4aa859216f481)


My sound is not muted, the volume is all the way to the max, and Ubuntu does seem to recognize my sound card (Ubuntu even has my laptop's volume and mute buttons working); I'm simply not getting any sound.

---

### Post by Favux on 2009-07-11
Hi SomebodySane,

Welcome to Ubuntu!

You want to add the line:
```
options snd-hda-intel index=0 model=toshiba position_fix=1

```
to the end of the alsa-base.conf file.  Which used to be called alsa-base before Jaunty.  To do that in a terminal enter:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Add the line to the end.  Save and restart.

Hope this helps.

---

### Post by SomebodySane on 2009-07-11
Perfect!  Seems to have completely solved the problem!  I'm extremely 
grateful.  One thing to note is that when I rebooted I got a very 
unpleasant green and mottled red/black flashing screen for about 10 seconds,
I though I was in serious trouble for a moment, but everything seems to be 
working now.

Now, out of pure newbie curiosity, what is the difference between these two
lines of code?  (gksudo vs. sudo and nano vs. gedit)

```
sudo nano /etc/modprobe.d/alsa-base.conf

gksudo gedit /etc/modprobe.d/alsa-base.conf
```and what did this line actually do?

```

options snd-hda-intel index=0 model=toshiba position_fix=1
```Thank you again.

P.S.  I'm listening to The Red Hot Chili Peppers - By the Way album and it sounds fantastic.

---

### Post by Favux on 2009-07-11
Hi SomebodySane,

Well they both make you root/superuser, but you use gksudo when using a graphical program like gedit (Text Editor).

Now finding out why that line and what it does can be unbelievably tedious unless you're heavy into sound.  You'd go to the alsa.org site and read their stuff.  Then you would read the alsa wiki.  Then on your system is a compressed file.  I forget where, but could find out if absolutely necessary.  It's compressed because it is huge.  Uncompressed it is called ALSA-Configuration.txt.  Then you'd read the introduction.  Then you'd go through the many sections until you found the "Module snd-hda-intel" section (which has many subsections).  In the intro. to that you would see:
```
Module snd-hda-intel
  --------------------

    Module for Intel HD Audio (ICH6, ICH6M, ESB2, ICH7, ICH8),
		ATI SB450, SB600, RS600,
		VIA VT8251/VT8237A,
		SIS966, ULI M5461

    [Multiple options for each card instance]
    model	- force the model name
    position_fix - Fix DMA pointer (0 = auto, 1 = use LPIB, 2 = POSBUF)
    probe_mask  - Bitmask to probe codecs (default = -1, meaning all slots)
    bdl_pos_adj	- Specifies the DMA IRQ timing delay in samples.
		Passing -1 will make the driver to choose the appropriate
		value based on the controller chip.
    
    [Single (global) options]
    single_cmd  - Use single immediate commands to communicate with
		codecs (for debugging only)
    enable_msi	- Enable Message Signaled Interrupt (MSI) (default = off)
    power_save	- Automatic power-saving timtout (in second, 0 =
		disable)
    power_save_controller - Reset HD-audio controller in power-saving mode
		(default = on)

    This module supports multiple cards and autoprobe.
    
    Each codec may have a model table for different configurations.
    If your machine isn't listed there, the default (usually minimal)
    configuration is set up.  You can pass "model=<name>" option to
    specify a certain model in such a case.  There are different
    models depending on the codec chip.

```
That's about the best I can do for you because I am not a sound guru.  So if you know how to do this sort of thing and your new computer doesn't come out of the install with sound and you figure it out you share.  That's what this forum is about.  As an example here's markbuntu's intel_hda thread:  [http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

Nice album.

---

