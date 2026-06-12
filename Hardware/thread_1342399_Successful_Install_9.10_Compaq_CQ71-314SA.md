---
title: "Successful Install 9.10 Compaq CQ71-314SA"
date: 2009-11-30
forum: Hardware
---

### Post by billythehamster on 2009-11-30
Hi

Just thought I would let you know I got Ubuntu 9.10 installed on the above laptop. I am running the 64bit edition. All the default drivers worked except I had to do the following to get the sound to work:

1. copy-paste the following command into the Terminal:

gksudo gedit /etc/modprobe.d/alsa-base.conf

2. and add these lines to the end of the /etc/modprobe.d/alsa-base.conf file:

# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1
options snd-hda-intel enable_msi=1

3. copy-paste the following command into the Terminal:

gksudo gedit /etc/group

4. replace the following line (or something very similar to it):

audio:x:29:pulse

with this line:

audio:x:29:<logon-name>,pulse

Hope someone else finds this helpful. Just streaming lastfm as I write this!

---

### Post by pingu1 on 2010-03-10
This was very helpful. 
I am looking at this computer, considering buying it in the near future.

How is the sound after the fix? All good?

---

