---
title: "[SOLVED] Flash install fails in 8.04"
date: 2008-12-06
forum: Installation &amp; Upgrades
---

### Post by Philo1 on 2008-12-06
I am running U 8.04 and FF  (X11; U; Linux i686; en-US; rv:1.9.0.4) Gecko/2008111317 Ubuntu/8.04 (hardy) Firefox/3.0.4 --- Gnome 2.22.3 --- Kernel 2.6.24.22 ---GCC 4.2.4 (i486-linux-gnu)

-- My problem I cannot for the life of me, enable a setup whereas flash will work. I have researched this hoping I could find a solution but nothing works, so here's my post.

What I have tried so far:
1) installed the flashplugin-nonfree through synaptic. Version/ 9.0.124.0
2) gnash through the GUI setup in FF. V/ 0.8.2
3) Adobe Flash Player version 10.0.12.36 .deb for Ubuntu 8.04+

Nothing works, I am at a stand still on this....Any guidance would be greatly appreciated.

---

### Post by inobe on 2008-12-06
search in synaptic for restricted-extras .

be sure you have ran the updates first

---

### Post by Philo1 on 2008-12-06
I did that and it helped somewhat, but didn't fix it. ( I know that sound strange) Funny thing, which I've never seen before is it allows web page to load entirely and that portion hangs. Example, [http://www.pandora.com/](http://www.pandora.com/) opens wonderfully and begins to load. However about 3/4 way through, it just hangs/stops. The page itself is loaded fully, however the area within the page which utilizes flash stops at 3/4 way. With the gnash SWF installed the stop issue occurs, no error mentioned.

Afterwards in synaptic I again add the "flashplugin-nonfree" package. With it installed, FF doesn't see it. So I hit the GUI option to install and it tells me then that it is already installed....strange.Again, it's installed already via synaptic. However, FF doesn't see it for whatever reason. Everything is up to date, I'm good on that. I recently installed flash on F9 through yum and it worked great. I can't figure out why this is giving me such a fit.

---

### Post by inobe on 2008-12-06
something sounds broken, have you tried updating packages in synaptic to see if that resolves these issues ?

when i say update' i mean reinstall ... or upgrade

btw have you tried restricted extras from terminal, this may point out the problems !

---

### Post by Philo1 on 2008-12-06
Yes, I've updated via synaptic and unfortunately it didn't resolve the issue. The restricted extras were applied as well. I think I'm going to download 8.10 and slap it on here, it's not LTS but not a problem. I guess I'll let this issue slide for now unless it as well pokes its head up in 8.10. I am having some serious issues of having force quite apps which again lead me to agree with you that something is broken. Thanks for the advice, guess I'll see how it works out from here.

---

### Post by inobe on 2008-12-06
i wouldn't recommend upgrading from 8.04 to 8.10, i suggest a fresh install of 8.10 !


you could try upgrading' then of course do a fresh install if that fail's

the thing is' do you have time ?

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by Philo1 on 2008-12-07
I downloaded it last night and went ahead and wrote the ISO. Yeah I agree with you, I was going to do a clean install. I am also running the shred exe to ensure the drive is properly wiped prior to doing this. I realize that I don't have, but more less wanted to do so. I'll hopefully be able to post that it all worked out once I finish it up today, thanks.

---

### Post by -TK- on 2008-12-07
that weird... i'm running FF2.0.0.18 with flash 9.0.124.0. on Ubuntu 5.04 Live CD (that right, 5.04) seem fine, watch video on Youtube at acceptable rate, no audio though since 5.04 no longer support so i couldn't install mp3 plug-ins. play flash game more than 2Mb of size at acceptable speed. :)

---

### Post by shogunmidas on 2008-12-07
please help...

i am having the same problem, im brand new to anything linux, and i tried kubuntu first where i encountered this same problem with no video for youtube. my friend sent me an email with some commands that actually fixed it. now i wanted to try ubuntu and bam. the same no video for youtube deal is back.

can anyone out there please help me with this. i really want to stay with ubuntu, but i watch videos online a great deal and this really screws me.

---

### Post by Philo1 on 2008-12-07
> **shogunmidas said:**
> please help...

i am having the same problem, im brand new to anything linux, and i tried kubuntu first where i encountered this same problem with no video for youtube. my friend sent me an email with some commands that actually fixed it. now i wanted to try ubuntu and bam. the same no video for youtube deal is back.

can anyone out there please help me with this. i really want to stay with ubuntu, but i watch videos online a great deal and this really screws me.

I have no problem in 8.10 viewing video feeds. Sound and picture are very clear, so again no problems. The feeds that I viewed to test it prior to this is using adobe 10 flash. (10.10.12.36) Just install it through synaptic, hopefully that will fix it. On the other hand if what your rendering isn't using flash, I recommend installing the GStreamer ffmpeg vid plugin. Synaptic version is 0.15.5-1. I have gstreamer ffmpeg / "-schroedinger (1.0.5-1), and "-tools (.0.10.21-4) installed.

---

### Post by Philo1 on 2008-12-07
To finalize, I freshly installed 8.10 -- installed flash (10.0.12.36) through synaptic and everything is working great!:p Aside from something being broken, I never was able to pin point the problem in 8.04.

---

