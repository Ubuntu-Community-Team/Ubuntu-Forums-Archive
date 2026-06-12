---
title: "Asus 1015PED headphones/mic don't work"
date: 2010-10-05
forum: Hardware
---

### Post by Chai Kovsky on 2010-10-05
Complete Linux and computer newbie here. I'm running Kubuntu Netbook Remix 10.04 on an Asus 1015PED with an HDA-Intel soundcard. The internal speakers worked OOTB and I *think* I've gotten the internal mic to work, but external mic and headphones go unrecognized. I've been trying solutions from [this link]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/580183"), but so far nothing's worked. I have:

Installed pavucontrol
Upgraded ALSA drivers to 1.0.23 (added "headphones" to the list of output devices in pavucontrol and in alsamixer; possibly got internal mic to work)
Added "options snd-hda-intel model=lifebook" to alsa-base.conf (at this point "headphones" dropped out of pavucontrol and alsamixer and computer stopped silencing internal speakers when headphones were plugged in)
Ran hda-analyzer, but audio mixer already set to OxOd and vol[0] and vol[1] output weren't muted
Followed directions of [#32]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/580183/comments/32") in link above re: running hda-verb and adding comments after exit(0).

None of it worked: my internal speakers now no longer silence with headphones plugged in and nothing will recognize headphones. Any suggestions? I've tried almost everything I could find.

Thanks!

---

### Post by Vinneh88 on 2010-10-05
I am also having a similar problem.  I'm running an Asus G51 Laptop.  My internal speakers work fine, but when I plug in (multiple different) head phone jack type devices such as head phones or external speakers, they do not work.

I found that with every device if I pulled out the plug slightly they all worked fine, although sound comes out the internal speakers as well.  I don't find this to be a fix at all, and I hope someone has a solve for this problems :D

Also, everything worked fine when running Vista, so I am sure that my jack and speakers/headphones are not broken :P

---

### Post by zomfgcoffee on 2011-02-04
i do have a link to a solution for the asus g51 sound issue. go to [https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/65752](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/65752)   and follow Mark Rijckenberg's steps. sound worked after a restart! i would try the same for the netbook as it might use the same chipset for the sound.

---

