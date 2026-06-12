---
title: "No sound from lenovo laptop with ubuntu 8.04!!?"
date: 2008-04-25
forum: Hardware
---

### Post by ibs137 on 2008-04-25
i hav a lenovo 3000 n200 laptop and hav just installed hardy ubuntu. Everything seems to work except the sound (youtube vids appear pretty choppy tho).

can u guys help??

thx

---

### Post by ibs137 on 2008-04-25
bump

---

### Post by EarloftheWest on 2008-04-25
ibs137,
I did a fresh install on my T61 (deleting all the previous partitions) and my sound works fine.
Can you try changing the drivers under sound preferences?
System > Sound
Let me know if different drivers help.

---

### Post by biggahed on 2008-04-25
Hello there
Ive got a c200 too,0769-AAP model

To make the sound work, first check if your sound chipset is the same as mine

To do that, open a terminal window and type

"lspci | grep Audio"

The output should be:
"00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)"

If its the same, enabling the sound should be as easy as opening /etc/modprobe.d/alsa-base and adding some stuff

$sudo gedit /etc/modprobe.d/alsa-base

After that, find the line that says "options snd-hda-intel" and change it to "options snd-hda-intel model=lenovo"

If you dont find it, just add that line to the bottom of the file. That should do the trick... restart and see if works.

If it does, maybe you could come back here and tell me if sometimes you get a high pitching noise coming along with the sound. I do... i found a workarround but this seems like an alsa bug, and id like to see if it happens with other people before reporting anything.

---

### Post by hsiehinator on 2008-04-25
same problem with a sony vaio FS675P

--update--
after some playing the sound is just REAALLY soft. any ideas?

---

### Post by biggahed on 2008-04-26
try alsamixer

---

### Post by encompass on 2008-04-26
> **biggahed said:**
> try alsamixer

Yes, that, but remember to try to turn up as many of the sound levels as you can while playing a song.  So you can hear if there is a difference.  Don't turn one up and then down... turn one up one after another.

---

### Post by GabrielWolff on 2008-04-26
> **biggahed said:**
> If it does, maybe you could come back here and tell me if sometimes you get a high pitching noise coming along with the sound. I do... i found a workarround but this seems like an alsa bug, and id like to see if it happens with other people before reporting anything.

Worked perfectly with my 3000 N200. Thanks a lot for the tip, no high pitching noise.

Cheers :)

G

---

### Post by kenchie on 2008-04-27
I have the same Lenovo 3000 N200 laptop. I tried biggahed's fix above, and I now have sound but it is very quiet, everything is turned right up and I can only just hear it. Any ideas please?

TIA

---

### Post by ibs137 on 2008-04-27
yes!!!!! i hav sound!!! thx soo much biggahead!!

i was worried i was gonna hav to switch back to XP!

hey kenchie try alsa mixer and turn everything up.
type alsamixer in terminal amd unmute everything (by pressing `m`) 

i get a very loud screeching sound when i turn front mic on so i leave that at zero and no screeching!

---

### Post by kenchie on 2008-04-27
ibs -

Yes that has worked - thanks very much!!!

---

