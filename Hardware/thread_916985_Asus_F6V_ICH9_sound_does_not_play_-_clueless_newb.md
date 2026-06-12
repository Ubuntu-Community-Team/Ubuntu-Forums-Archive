---
title: "Asus F6V ICH9 sound does not play - clueless newb"
date: 2008-09-11
forum: Hardware
---

### Post by pjkevm on 2008-09-11
Hi,
I just got this new laptop, and decided I'd force myself into learning linux by switching harddrives and only running Linux on this. Now honestly I do plan on learning myself and reading the forums(which I have already tried with this sound issue) but its hard for me to work when i have no music!

I know nothing about linux and am only stating to learn terminal commands

But my sound card info:
Intel
ALC662
82801I
ICH9

The sound works when I start the laptop (the asus logo comes on and a little sound plays out of the speakers) But when Ubuntu starts theres no sound.

I tried aplay -l showed my card, I did lspcv(or whatever) and it recognized my sound card as well.

I downloaded realtek drivers fromt he website, ran install, terminal went for awhile and then it closed itself. I configured the alsa driver 1.018rc3 from the desktop folder and a similar thing happened. Upon restart there was still no sound.

Please help, so hard to use a computer without sound!:(:confused::confused:

---

### Post by visit on 2008-09-11
helo,
sudo gedit /etc/modprobe.d/alsa-base
		 and paste this line end of file:
			options snd-hda-intel model=3stack-dig

for me correct this same problem under ubuntu intrepid 8.10 alpha5

look this for more help:
		[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

hi, visit

---

