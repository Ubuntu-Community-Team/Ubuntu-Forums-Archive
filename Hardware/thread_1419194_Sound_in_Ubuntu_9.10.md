---
title: "Sound in Ubuntu 9.10"
date: 2010-03-01
forum: Hardware
---

### Post by BlacqWolf on 2010-03-01
Hello, I am using Ubuntu 9.10 on my new HP G61, and the sound works through my laptop headphone ports, but not through my internal speakers. I have tried things on the net, 1 i think may work, but I cant boot into recovery shell which I need to, because I cant edit in terminal while running the base system. Help please, I would like sound from something other than a 10 yr old bad quality powerspeaker.

If you think you need the speaker specs for you to help me, here it is (Im not sure to be exact, but it says this in alsamixer)  :

 Card: HDA ATI SB                                                             &#9474;
&#9474; Chip: IDT 92HD75B2X5

---

### Post by mikewhatever on 2010-03-01
You can edit almost any config file from your regular user account, just need to use the sudo command. For example, let's say I wanted to edit an alsa related file, /etc/modprobe.d/alsa-base.conf.

_CLI:_
sudo nano /etc/modprobe.d/alsa-base.conf

_GUI_
gksudo gedit /etc/modprobe.d/alsa-base.conf

---

### Post by Manyette on 2010-03-01
> Hello, I am using Ubuntu 9.10 on my new HP G61, and the sound works through my laptop headphone ports, but not through my internal speakers.

I have a G71, and suggest that after you fix your "edit" problem, you check the following for your sound problem.

# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=hp-dv5
options snd-hda-intel enable_msi=1

---

