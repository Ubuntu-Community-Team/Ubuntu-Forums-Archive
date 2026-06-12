---
title: "Surround Audio channels mixed up"
date: 2008-05-11
forum: Hardware
---

### Post by legit on 2008-05-11
Hi,

So I just installed the latest ubuntu 8.04 and did a surround sound test via speaker-test -D surround51 -c 6 -t wav

All the speakers work except that the channels don't output to the correct channels (in windows all the channels work correctly so I know its not a jack thing)

Heres the way that ubuntu is outputting to my channels
front center is going to rear left
rear right is going to front center
rear left is going to subwoofer
rear center (LFE) is going to rear right

Front right and left are working correctly.

when it does the test it outputs this:
Time per period = 8.616492
 0 - Front Left
 4 - Center
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
 5 - LFE


Does anyone know how I can fix this so the channels output to the right speakers?

thanks

---

### Post by Deeta on 2008-05-12
Brief version:
It is all fine. :D it is a bug in speaker-test. Try switching your alsamixer to 6ch operation and play sound in gnome and notice that channels are mapped correctly after all :D

Verbose Version:
I had exactly the same problem this morrow.

with me I noticed the following mapping :

(signal goes) to (this speaker)
Fleft to Fleft
Fright to Fright

Rleft to Center
Rright to LFE

Center to Rleft
LFE to Rright


So after looking at the mapping I noticed that I look very much like a jack issue.
(as switching the 'center/lfe' and 'rearLeft/rearRight' jacks would solve the problem.

After switching SpeakerTest worked fine and mapped correctly but I that this must be some wonky Alsa behavior as:
1. evil proprietary Operating Systems
and
2. the coloration of my jacks

So as quick hack I switched the jacks.
Yet as soon as I switched to gnome to test my 6ch setup in a real music environment I noticed that it was wrong again. Switching the jacks back set everything right again.

Thus I assume that this is some bug on Speaker-test's side.

---

### Post by Deeta on 2008-05-12
Just reported a bug
[https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/229591](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/229591)

---

