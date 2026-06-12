---
title: "Thinkpad t43 upgraded 8.04&gt;9.04"
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by nuclear216 on 2009-08-29
Hello there!

I was happy with my 8.04 on a Thinkpad T43 (intel graphics/pentium something/ICHsomething), than I choose to upgrade to the next release as suggested by the update tool and I got no video anymore.... ](*,)

I've found this thread [B][Jaunty Intel Graphics Performance Guide]("http://ubuntuforums.org/showthread.php?t=1130582").
[/B]
When I click any video by any player I got different result: Mplayer wont open video audio only, vlc will crash and so totem, flash video within firefox is incredibly slow...
I am fairly sure it's due to the issue with the Intel VGA and the new software as explained in the Thread above.

 One single question: How do I downgrade?

```

dada@dada-laptop:~$ uname -a
Linux dada-laptop 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux

```

---

### Post by kcoriginal on 2009-09-01
Might not be the BEST suggestion, but I would do a fresh install of 9.04 over top of your existing install...

don't tick the "Format" box when you go through the install routine, thus leaving your /home folder intact...

9.04 has been the Holy Grail of Linux in my experience. It was 8.10 that was giving me fits. 8.04 worked great, too!

If 9.04 Intel video is broken, and you just want to roll back... IDK if there _IS_a way to roll-back... but you can pop your 8.04 disc back in and install on top of everything.

You will have to go back through ubuntu-restricted-extras, etc...

---

### Post by raymondh on 2009-09-01
'sorry to hear that.

There is no network downgrade.  You will have to re-install 8.04 from the CD (desktop or alternate).

Back-up/save files first.

---

### Post by nuclear216 on 2009-09-08
At the end I went with the Optimal configuration from the instructions above cause I wanted to keep the slightly decreased boot time that came with the 9.04 and overall better release.

I use the external VGA a lot and after I detach it and switch to the laptop monitor sometimes I have to restart x11 for video playback and performance to come back, do you guys have any idea how to fix that?

For me the best thing about the ubuntu release schedule is that if you don't really have the time to keep in synch with new software released for linux you can count on the dists release to make you always use the best software out there.

---

