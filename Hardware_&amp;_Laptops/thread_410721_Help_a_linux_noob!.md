---
title: "Help a linux noob!"
date: 2007-04-16
forum: Hardware &amp; Laptops
---

### Post by Ultravist on 2007-04-16
Hi all! Yesterday i decided to trash windoze and installed Ubuntu 6.10 on my laptop. My configuration is. Turion 64 X2 TL-50, 1Gb Ram, NVIDIA Go6100, and a HD of  60 Gb. Everything worked fine. I've managed to partition the HDD in 3 partitions: one 8Gb primary, one of 2GB for swap and one of about 50Gb(formated as ext3 type) to use as a working partition just like in windoze. After couple of hours of reading forums posts i've managed to install nvidia drivers so now i run a native resolution of 1280x800 at 60Hz (and i think i have video accel because i can run beryl with some features). Now because i'm a total noob at linux (but as a posible convert i have some questions and problems for wich i request some help with some step-to-step tutorial beacuse it seems i can't figure it out). The problems are as follows:

1. The spaces i've allocated for each partition are good or i have to change them?

2. Ubuntu does not sees my 50GB partition, but command "sudo fdisk -l" shows that it's there, and don't know how to mount it and gain full acces on. Pressing places shows me only desktop folder and Filesystem.

3. When shutting down Ubuntu when the progress bar apears the image flickers when the HDD is working for shutdown (if necesary i will make a picture and paste it). How cand i resolve this because its getting annoying?

4. Using Beryl- pressing water effects freezes my pc need to do a forced shutdown wich really hurts my heart (always loved my computers). Could be a bug or something?

5. Is it safe to update my kernel as it seems that some of them got problems and i don't want to end up with a dead pc needing to install everything from scratch?

6. When pressing device mannager there are lots of devices listed as unknown. Is this ok? 

7. I have an onboard soundcard Realtech HD. It's ok to install Realtech high definition drivers for linux from their website?

This are all the question i have (for now :) ). Any help would be great.

P.S. Sorry for my english (it's not my native language).

---

### Post by hardyn on 2007-04-16
I can help with about half of your questions....

1) 8gb sounds lean, but it really depends on the number of applications you intend to install.
2) you will have to add it to the automount file /etc/fstab... things have changed a little with UUID system, but im sure there are lots of good posts... i will not re-itterate here.
3) i don't even get a shutdown animation with the binary drivers... so you are one up on me.
4) beryl isn't stable... if you noticed its version is 0.2 or something like that... par for the course.  check your xorg.conf file... make sure it is to beryl's specs.
5)i don't think there has been any problems with the edgy kernel... but it is allways a risk.
6) probably not great... you might have better luck with feisty.  its a new computer with broadcom and ati... support might not be ideal right now.  (please let me know how things are go for you... i was considering buying that laptop)
7) NOOOOO.... i looked at the website, they are for kernel 2.4!

english is fine, probably better than mine, and it IS my first language.
cheers.

---

### Post by Ultravist on 2007-04-17
Yesterday saw that i have 156 updates available...scroll them..deselected the kernell updates (since i saw on the forums that usually the newesty versions might have some problems ) ...after that my system crashed at reboot...not even live CD didn't worked...had to reinstall damn win and reinstall ubuntu again from livecd (wich worked after that). I'm scared now to update...because my laptop is my only pc in the house and if it crashes can't come here to ask for help! But maybe someday i will know enough linux to do alone a debug. What are yours advices: should i install updates or just for the aplications that give me errors?

---

