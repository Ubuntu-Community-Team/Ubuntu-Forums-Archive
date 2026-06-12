---
title: "Adding additional GTX 1080 leads to problems."
date: 2018-12-04
forum: Hardware
---

### Post by hollowgalaxy on 2018-12-04
I decided to add a GPU to my current build. I decided to act like a little kid, and see what happens if I just plug it in, in addition to my current graphics card (GTX 740). And everything was A ok. Until it wasn't ... As an added bonus, literally did nothing software wise, thus no added obscure bugs due to incorrect directions.
I have a list of issues which I want to avoid fixing individually if perhaps its all linked to one issue, and for that I was wondering if someone could help me with or at least point me into the right direction. (Goal, use the GTX 740 as my main GPU thus hooked up to my monitor and use the GTX 1080 for strictly Tensorflow/Cuda)

Problems:

[LIST=1]
[*]Computer takes 15 minutes to start (used to take less than 3 min) (UEFI not enabled)
[*]Wifi driver takes additonal 5 minutes to start after the computer has finished booting up.
[*]Computer does not suspend.
[*]Computer freezes at shutdown.
[*]No sound with headpones and with back audio jack. Suspect: Had sound before with headpones and with back audio jack, 1080 came with hdmi, I can see that Ubuntu recognizes the sound card on motherboard, but is not using it.
[/LIST]

 Cool things that do work:
[LIST=1]
[*]740 is being used as main GPU, and tensorflow ignores it, reducing the amount of code I need to use GTX 1080.
[*]GTX 1080 works without hickups and I have upped the vram on it to 95%
[*]Did not have to reinstall nvidia driver for the above 2 things.
[*]Anyone reading this bullet point.;)
[/LIST]

I also posted this on ask ubuntu, but got no response so here is a link just in case.
[https://askubuntu.com/questions/1096668/issue-with-audio-after-installing-an-additional-gpu-with-an-hdmi-connection](https://askubuntu.com/questions/1096668/issue-with-audio-after-installing-an-additional-gpu-with-an-hdmi-connection)

specs: 
Motherboard: Gigabyte Z97X-UD5H
CPU: Intel(R) Core(TM) i5-4690K CPU @ 3.50GHz
32 GB ram
NVIDIA GTX 740
NVIDIA GTX 1080

---

### Post by Autodave on 2018-12-04
It has been a long time since I tried 2 GPUs in one machine.  What I do remember then was that it only worked when they were matched cards.

---

### Post by hollowgalaxy on 2018-12-04
I though that was the adage for having multiple monitors? I am only using one of the graphics cards for a monitor. The other one is for training TensorFlow models. Essential my 1080 is non-existent (in theory) until I call for it to do my bidding.

---

### Post by Autodave on 2018-12-05
Again, I am going from memory on some old equipment.  When you would add a second *identical* GPU, you could still only connect monitors to ONE card: not both.  The fact that a second (identical) card was present meant that the first card would recognize its existence in the system and would share graphics load with it. However, the CPU cannot share its info with 2 graphics cards.

---

