---
title: "Sound problem: neomagic nm256 gives no love, no sound either"
date: 2006-03-26
forum: Hardware &amp; Laptops
---

### Post by kosmos on 2006-03-26
[I changed the subject because I found a workaround to the problem with alsa driver, as indicated in my reply]

I decided to upgrade an old laptop that was running fedora 1 to Ubuntu breezy. The install went fairly well, but after I got things set up, there is no sound. Since I'm used to the fedora way of doing things I'm really floundering around right now.

I know in the past that sound was working under fedora 1 with the driver nm256_audio. I believe this is an OSS driver. It may not be the ideal driver to use, and I had to use the module option force_load=1 in /etc/modules.conf, but ... it worked.

Anyway, I'll summarize what little I know, in the hopes someone else will have seen this problem and know what to do.

lspci shows: 0000:01:00.1 Multimedia audio controller: Neomagic Corporation NM2200 [MagicMedia 256AV Audio] (rev 20)

lsmod|grep snd shows:
snd_nm256              67680  0 
snd_ac97_codec         72188  1 snd_nm256
snd_pcm_oss            46368  0 
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_nm256,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd_page_alloc         10120  1 snd_pcm
snd                    48644  6 snd_nm256,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd

So the Ubuntu breezy installation seems to recognize my audio device ok, and chose the snd_nm256 driver, but it does not work, and I'm not sure what to do. Help me, Mr. Wizard.

---

### Post by kosmos on 2006-03-26
Well, I guess I sorta solved my problem, I just had to whine about it in public first. Why does that always happen?

Anyway, the "solution" I have so far is to get rid of alsa driver and use oss driver. So in /etc/hotplug/blacklist, I add:
snd_nm256

And I create a new /etc/modprobe.conf containing:
alias sound nm256_audio
options nm256_audio force_load=1

reboot, and it seems to work. 

But, of course, alsamixer does not work ... what should I use for a mixer now? I guess I'll look for aumix, but it's not installed. 

Does anyone else have any good tips for switching from alsa to oss drivers? Do I need to run any sound daemons or emulation doodads? Thanks.

---

### Post by bill_wad on 2006-04-01
I'm having a simular problem with my nm256 sound.  I'm on an old HP OmniBook 900.  lspci gives:

0000:01:00.1 Multimedia audio controller: Neomagic Corporation NM2200 [MagicMedia 256AV Audio] (rev 12)

dmesg shows:

[4294732.142000] nm256: no ac97 is found!
[4294732.142000]   force the driver to load by passing in the module parameter
[4294732.142000]     force_ac97=1
[4294732.142000]   or try sb16 or cs423x drivers instead.

lsmod:

snd_nm256              67680  0
snd_ac97_codec         72188  1 snd_nm256
snd_pcm                78344  2 snd_nm256,snd_ac97_codec
snd_timer              21764  1 snd_pcm
snd_page_alloc         10120  1 snd_pcm
snd                    48644  4 snd_nm256,snd_ac97_codec,snd_pcm,snd_timer
soundcore               9184  1 snd

However no device files seem to have been created for the sound card.  Could not having the device files cause this failure?  If so, what do these files need to look like?  if not, what is going and how do I set sound working?

Thanks

---

### Post by kosmos on 2006-04-01
[QUOTE=bill_wad]I'm having a simular problem with my nm256 sound.  I'm on an old HP OmniBook 900. [/QUOTE]

Have you tried my little recipe above to ditch the snd_nm256 driver for the nm256_audio? It's just a couple easy changes in /etc. It works for me. It would be interesting to see if it works for others.

---

### Post by bill_wad on 2006-04-03
Kosmos, yes I did try the changes you suggested - no help.  I can recreate the changes and capture dmesg and such if this will help.  I've also tried to get the drivers that dmesg suggested - no luck there either.  

Thanks for replying

Wad

---

### Post by bill_wad on 2006-04-04
Kosmos, I went back and recreated the changes you have in your posting.  It looks like I'm not getting a driver installed with these changes:

dmesg has no mention of the sound card
lsmod | grep snd = <null>
lspci shows the card as before

-wad

---

### Post by kosmos on 2006-04-06
Rats, it sure looked like we had the same audio chip and the same problem. All I can say is that using the nm256_audio works for me. Sometimes the first app to use sound after boot lets out an awful screech, but after that, it works fine.

---

