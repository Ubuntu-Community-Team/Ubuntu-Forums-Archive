---
title: "&quot;No soundcards found&quot;, after moving from Hardy to Intrepid"
date: 2008-11-02
forum: Hardware
---

### Post by ChrisBookwood on 2008-11-02
Hello,

I moved to Intrepid friday after the release, soon to realize not everything was great.
Ubuntu can't find my sound card. I have tried both *aplay -l* and *asoundconf list, *and no soundcard is detected what so ever.

Just for clearence, it worked perfectly friday morning on Hardy before I made a clean install of Intrepid.

Now, I have no idea what soundcard is in my laptop, but the pc that's homing the problem is a Medion Akoya MD96640.


Regards,
Chris Bookwood

---

### Post by ChrisBookwood on 2008-11-02
Okay, by doing a lspci | grep Audio I got this:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

I have no idea how to fix it - hope you guys do:P

---

### Post by AnneTanne on 2008-11-03
No solution, only the same problem...
I didn't use Linux during almost a year, but wanted to 'return' with the release of Intrepid.
My laptop is a Medion MD 96380, and with 'lspci | grep Audio' (thank you), I got the same result 
'00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)'

(I also tried OpenSUSE 11.00, but my laptop remained silent as wel...).
I'm glad to hear your machine did have sound with Hardy Heron, maybe I'll try that release...

Regards,
Ann

---

### Post by mcclown on 2008-11-03
> **ChrisBookwood said:**
> Okay, by doing a lspci | grep Audio I got this:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

I have no idea how to fix it - hope you guys do:P

I have the almost the same sound card (00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)) and I've spotted a few other people around here who are having the same problem.

Sound worked for me on Hardy, and still does if I put in the live CD.

I don't have your symptoms with the card not showing with *aplay -l* and *asoundconf list *. My card is shown, it just doesn't work. I'm goign to spend today trying to track down a solution.

---

### Post by ChrisBookwood on 2008-11-03
I'm pleased to see so many having the same problem as me - not that I wouldn't live without out, but with many having the problem, the chance of a solution as greater and maybe also in the near future.

---

### Post by pincushionman on 2008-11-03
I had working sound in the Intrepid beta Intel HD Audio/RealTek ALC888 as well as a working Atheros AR242x wireless card (on ath5k module), but they died when intrepid was released. My soundcard (and wireless) issues were fixed with a quick
```
aptitude install linux-backports-modules-intrepid
```
(This assumes you have turned on your backports repository in Synaptic)

I don't know where the backports modules came from, but they certainly cleared up my problem. YMMV.

---

### Post by ChrisBookwood on 2008-11-08
Unfortunately it didn't work for me, but maybe it will for somebody else.

---

### Post by jkmspyksma on 2008-11-12
> **pincushionman said:**
> I had working sound in the Intrepid beta Intel HD Audio/RealTek ALC888 as well as a working Atheros AR242x wireless card (on ath5k module), but they died when intrepid was released. My soundcard (and wireless) issues were fixed with a quick
```
aptitude install linux-backports-modules-intrepid
```
(This assumes you have turned on your backports repository in Synaptic)

I don't know where the backports modules came from, but they certainly cleared up my problem. YMMV.
This worked like magic for me:

Lenovo 3000 C100,  using a Intel 82801FB/FBM/FR/FW/FRW (ICH6 Famlily) AC'97 Audio Controller, which was not found before when running "aplay -l". 

I should note that installing this linux-backports-modules-intrepid caused a WHOLE LOT of other packages to be removed. So far, I haven't noticed any problems--sound, wireless, display, etc. all still appear to be working fine.

Thanks!

---

### Post by AnneTanne on 2008-11-17
> **ChrisBookwood said:**
> Unfortunately it didn't work for me, but maybe it will for somebody else.

Neither did it for me...
I decided to install 8.04 instead of 8.1, since our 11 y.o son prefers Ubuntu to Windows because of the speed, but can't live without sound ;)

Ann

---

### Post by cmagpusao on 2008-11-24
I also ran the 
aptitude install linux-backports-modules-intrepid
command with no avail. 

btw, I have the same onboard card as mcclown.
lspci | grep Audio
Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)


Anyone got any ideas?  Thanks!

---

### Post by ChrisBookwood on 2008-11-24
Okay, so I was just messing around with the backport repos, playing, fiddling and thought I would try to run it again, and yes - a lot of new updates was available and after they where installed, it asked me to restart... Now, something funny happene. Cause before I restarted, I checked my internet connections, and now it said I had 4 different wireless drivers installed. One I manually installed from the gitcore-repo, and 3 which had come with the backports. And it didn't just tell me - it showed 4 different lists with all the available wifi connections in the area, but with different driver names. *(that means all available connections showed 4 times)*

After a restart, they where all gone, though. Even the one I'd manually installed was gone, and I now have to go through that hassle of installing it again...

No sound though.
When my wifi is up and running again, I will try and see if I have sound on the live disc.

---

### Post by ChrisBookwood on 2008-11-25
It's a but specifik for my laptop, but I have created a bug report on launchpad for our problem...

[https://bugs.launchpad.net/ubuntu/+bug/302145](https://bugs.launchpad.net/ubuntu/+bug/302145)

---

### Post by tri1976 on 2008-11-25
I think I have similar problem.  Sound is working when I upgrade from 8.04 to 8.10.  It's also fine if I install the whole Ubuntu desktop.  But when I do a clean minimal install (command line install with alternate cd), it fails to detect my sound card ONLY after starting X.  Before startx, amixer returns a bunch of controls (i.e. Master, PCM, etc.)  After startx, amixer returns error: "amixer: mixer attach default error: No such file or directory".  I wonder if you guys seeing the same problem?  did you try to see if the sound card is found before starting X?

---

### Post by seren6ipity on 2008-11-25
Try blacklisting the files and reboot as suggested in post#2 and #3. It fixed sound card issues for me and might work for you guys - 
[http://ubuntuforums.org/showthread.php?t=826233&highlight=aironet](http://ubuntuforums.org/showthread.php?t=826233&highlight=aironet)

---

### Post by ChrisBookwood on 2008-11-25
It didn't work for me, I'm afraid -.-

---

### Post by ChrisBookwood on 2008-12-28
Here's the fix that did the job for me.
I hope it will for you guys too, having the same problem!

[https://bugs.launchpad.net/ubuntu/+bug/302145/comments/12](https://bugs.launchpad.net/ubuntu/+bug/302145/comments/12)

---

