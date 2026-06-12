---
title: "Ubuntu won't read audio cds"
date: 2010-03-16
forum: Hardware
---

### Post by javyn999 on 2010-03-16
Having a strange problem in Ubuntu...whenever I try to click on an audio CD it gives me the following error...

When I try to boot into lxde and try there, it doesn't even read the cd at all.  

Any ideas anyone?

---

### Post by Slim Odds on 2010-03-16
It's looking for the "sound-juicer" program, which doesn't seem to be found.

It is installed by default. Try reinstalling it from Synaptic.

---

### Post by javyn999 on 2010-03-17
Thanks.  That got it working on GNOME.  Did a sudo apt-get install sound-juicer...

But this does nothing to get CDs to even mount it seems in lxde.  Once 10.04 comes out, I plan on moving to lxde, so I'm trying to work the kinks out now.

Is there a trick or command I'm missing to get Audio CDs to mount in lxde?

---

### Post by dE_logics on 2010-03-17
Auido CDs do not get mounted...they get played directly with players like banshee, amarok, smplayer etc...

If you have to mount, you gotta do it in command line mode.

---

### Post by javyn999 on 2010-03-17
edit:  Nevermind, I understand what you're saying.  Thanks.


Ouch....I just showed my stupidity then....sorry.

How do I go about doing that?  My GF needs to access Audio CDs to save the cd audio files off of them and work with them.

And could I set it to automount CDs like every other type of disk I put in?

---

### Post by Slim Odds on 2010-03-18
In a "normal" install, this stuff just works.

Sound-juicer is the default app for inserted CD's and it's also a ripper.

[http://burtonini.com/blog/computers/sound-juicer](http://burtonini.com/blog/computers/sound-juicer)

---

### Post by javyn999 on 2010-03-18
Thanks.  I obviously screwed something up on both computers adding and removing desktop environments to break sound-juicer.  

From the looks of it, unless I'm missing something, sound-juicer isn't giving me any options to change bitrates of mp3s I want to rip.  

No worries, there's always Audacity.

---

