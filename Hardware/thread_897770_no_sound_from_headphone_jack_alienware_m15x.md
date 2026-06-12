---
title: "no sound from headphone jack alienware m15x"
date: 2008-08-22
forum: Hardware
---

### Post by raim1312 on 2008-08-22
okay i recently installed ubuntu 8.04 on my alienware m15x and everything worked perfectly fine except for the sound. before i got sound out of my headphone jack but not out of the internal speakers. i followed the instructions here: [http://ubuntuforums.org/showthread.php?t=739765](http://ubuntuforums.org/showthread.php?t=739765) which had me add the line:
                  options snd-hda-intel model=mbp3
to /etc/modprobe.d/alsa-base. after restarting several times and waiting several days things magically started working. i can now get sound from my speakers but i just tried using a pair of headphones and i get no sound from the headphones. if i plug them in while music is playing sound will continue to come out of the speakers but no sound from the headphones.
can anyone help me?

---

### Post by weseeluh on 2008-08-22
hi i have the same problem but there is one weird thing in my alsamixer the headphone are there but i just can't turn it up. i've added a picture of my mixer          [ATTACH]82474[/ATTACH]

---

### Post by raim1312 on 2008-08-23
headphone isnt listed in my alsamixer. i dont know where to go from here

---

### Post by hanzz on 2009-02-01
hi there,
I bought my m15x in dec 2008 installed intrepid (64bit) and had the
same problems:

right after installation: no sound at all (didnt test the headphones)

after I added:
options snd-hda-intel model=mbp3 to modprobe.d/alsa-base

sound works, but the headphone jack does not work at all.

anybody solved this problem?

---

### Post by tomehb on 2009-03-02
I have got the Headphone port working not sure how, however i would love to also get the Internal Speakers Working! Any suggestions?

Also has anyone got the  [SB X-Fi Xtreme Audio] CA0110-IBG to work ? :|

---

### Post by hanzz on 2009-03-03
I added the line

options snd-hda-intel model=mbp3 

to /etc/modprobe.d/alsa-base

which made the internal speakers working on my m15x. but after that the headphones did not work!

hans

---

### Post by tomehb on 2009-03-03
Yeah, I was playing around with this last night...

I wondering if there is a way to sense that headphones have been connected and then too reload the sound drivers etc without that line..... It's really annoying that the manufacture don't make the drivers!

---

### Post by tomehb on 2009-03-03
> **hanzz said:**
> hi there,
I bought my m15x in dec 2008 installed intrepid (64bit) and had the
same problems:

right after installation: no sound at all (didnt test the headphones)

after I added:
options snd-hda-intel model=mbp3 to modprobe.d/alsa-base

sound works, but the headphone jack does not work at all.

anybody solved this problem?

As posted by kdaemon ([http://ubuntuforums.org/showthread.php?t=1019495&highlight=m15x](http://ubuntuforums.org/showthread.php?t=1019495&highlight=m15x))

Adding the following Option to /etc/modprobe.d/alsa-base, should allow you to play music through the laptop speakers, and then when headphpones are plugged in it will swap right over.... I haven't tried this yet because I'm at work but i will be trying it tonight...

options snd-hda-intel model=lenovo-101e

But this is a bodge Job...

---

### Post by hanzz on 2009-03-03
adding: 

options snd-hda-intel model=lenovo-101e

(instead of model=mbp3)

worked for me!!!! 

built in laptop speakers (i.e. sound in general) are working,
when I plug a cable into the headphone jack the sound via laptop
speakers stops (currently I only can assume that the sound output
is redirected to headphones coz' currently I had only the plug
without phones attached to it) -- seems this is the solution
to the Alienware M15X Sound Problem ;-)

---

### Post by Mauldrick on 2009-03-30
> **hanzz said:**
> hi there,
I bought my m15x in dec 2008 installed intrepid (64bit) and had the
same problems:

right after installation: no sound at all (didnt test the headphones)

after I added:
options snd-hda-intel model=mbp3 to modprobe.d/alsa-base

sound works, but the headphone jack does not work at all.

anybody solved this problem?

How is intrepid working on the m15x? Im am thinking about upgrading from Hardy and wanted to know if everything worked before I jumped in.

---

### Post by hanzz on 2009-03-31
hi,

everything else works fine for me except the initial sound problems that
are solved meanwhile.

- logitech mx1000: works fine with all 12 buttons
- webcam: worked out of the box
- wifi: out of the box
- bluetooth: out of the box

I am perfectly happy with it!

hanzz

---

