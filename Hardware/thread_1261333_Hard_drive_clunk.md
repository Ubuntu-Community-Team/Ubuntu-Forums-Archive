---
title: "Hard drive clunk"
date: 2009-09-08
forum: Hardware
---

### Post by moody_mark on 2009-09-08
I had to pull a HDD out of a machine at work today (was running Red Hat), its a 500GB Seagate HDD and I put it into a caddy and plugged it into my PC here running Ubuntu 8.10 The drive spins up ok but i think as soon as the heads start to move i get a sound like "shuk-a-clunk"... which repeats every 2-3 seconds. I can see the directories but no content. I also see the following in my /var/log/messages log file

```
Sep  8 21:04:34 Homer kernel: [  163.790140] lost page write due to I/O error on sdb2
Sep  8 21:04:34 Homer kernel: [  163.797889] lost page write due to I/O error on sdb1

```

I think the drive is hosed, Im not going for professional data recovery so I got nothing to loose. Ive read all sorts of crazy stuff like "stick it in the freezer" and all sorts. Im open to suggestions, any ideas?

---

### Post by rob-ward on 2009-09-08
You could try the drive in a different caddy, if the power supply can't provide enough "juice" to move the heads you can get that effect.

Otherwise I would say that the HDD may be broken.

---

### Post by tgalati4 on 2009-09-08
Feel the controller chips on the drive.  Any of them getting real hot?

Google the white paper "200 ways to revive a hard disk".  Yes, some are corny, but you only need one method to work.

Sometimes the power pins get solder cracks.  Try touching up the solder to the 4 power pins.  If it's a newer cable style, it's more difficult.  Measure the 5 and 12V leads to ground, make sure your power supply is putting out the juice.  Any drops during spin-up means that the power supply can't supply enough current to both spin up the drive and read the data.

Do a google search on your specific drive model and see if others are having similar problems.  Could be a design/fabrication problem.

---

### Post by moody_mark on 2009-09-09
Thanks for the tips.. turns out there are some known problems with the seagate drives where they put some protective coating on the platters which can flake off! I put the HDD in the freezer all night but it was still making the same noises this morning, but I persisted and on one powerup attempt it made a different sound and i noticed some directories started to show files. So ive started a big recursive copy now, still seeing errors in the messages log like above and the cp command is returning the odd

```
cp: cannot stat `_home/GCS/Downloads/Books/CiscoTrianing/Misc/CCNA Academy/CCNA_Sem1/CH10/10_5_4': Input/output error

```

but overall i seem to be getting some data back, so fingers crossed...

---

### Post by moody_mark on 2009-09-09
Update: seemed to have recovered nearly all the data, some directories were empty though, some missing although missing ones are hard to spot unless you remembered they were there!

It seems the night in the freezer plus a couple of sharp taps seemed to do the trick. I wont be using that drive again!

---

### Post by tgalati4 on 2009-09-09
Is the drive still under warranty?  Perhaps you can get a replacement.

If you need to recover more data, try using testdisk/photorec.  It reads the surface of the disk, rather than rely on a corrupt inodes table.  It might recover files that a standard copy would miss due to mess-up pointers.

sudo apt-get install testdisk
man photorec

---

