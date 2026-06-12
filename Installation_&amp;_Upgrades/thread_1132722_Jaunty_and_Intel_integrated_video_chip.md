---
title: "Jaunty and Intel integrated video chip"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by Nevon on 2009-04-22
A while back I heard that Jaunty has been having some serious problems with some Intel integrated video chips (GM45). I've been thinking about upgrading to Jaunty on the release day, but not if it's still got those issues with Intel hardware.

So what I'm asking is, does anybody know whether the issues have been fixed, and if not, where can I read more about it?

---

### Post by dunbrokin on 2009-04-22
> **Nevon said:**
> A while back I heard that Jaunty has been having some serious problems with some Intel integrated video chips (GM45). I've been thinking about upgrading to Jaunty on the release day, but not if it's still got those issues with Intel hardware.

So what I'm asking is, does anybody know whether the issues have been fixed, and if not, where can I read more about it?

Yes they seem to be....mine is working fine now.

---

### Post by Nevon on 2009-04-23
Can anyone verify this with perhaps a link to the related bug report?

---

### Post by Partyboi2 on 2009-04-23
This is taken from the release notes for Jaunty
> Users of Intel video chipsets have reported performance regressions in Ubuntu 8.10 compared with previous releases (bug [252094]("https://bugs.launchpad.net/bugs/252094")).  Many of the issues have been resolved in Ubuntu 9.04, but some remain. 
 
[LIST]
[*] Some users have found improved performance by using the "greedy" migration heuristic. This can be done by running "sudo gedit /etc/X11/xorg.conf", and adding Option "MigrationHeuristic" "greedy" to the Device section of your xorg.conf.  
[*] Alternatively, a new experimental acceleration architecture option, "DRI2/UXA", is available for Intel graphics users which our [testing]("https://wiki.ubuntu.com/X/UxaTesting") has found provides significant performance improvements in some cases, but has also shown risk of severe stability problems. You can opt-in to enable this by running "sudo gedit /etc/X11/xorg.conf", and adding Option "AccelMethod" "UXA" to the Device section of your xorg.conf.  Users wishing to maximize stability should stay with the standard default acceleration method, "EXA". 
 [IMG]https://wiki.ubuntu.com/htdocs/ubuntu/img/alert.png[/IMG] In some cases this will lead to the graphical environment not starting at all or becoming entirely unusable. In that case, start into rescue mode or press Ctrl+Alt+F2 and log into the text console, and use sudo nano /etc/X11/xorg.conf to revert the UXA option. 
[/LIST]


---

### Post by Nevon on 2009-04-23
Right now 8.10 is pretty much unusable for me (all browsers randomly crashing without any error messages. Evolution crashing. Deluge freezing up on me. etc.), so I guess I'll just have to try Jaunty out and see if the preformance drops are noticable (considering that I can't even get OpenGL 2 with my intel graphics chip in Linux, preformance drops are the last thing I want).

---

### Post by jerrylamos on 2009-04-23
jaunty is slow with jerky full screen flash video on my IBM ThinkCentre 2 gHz Celeron, i845 integrated video graphics and on my IBM Thinkpad R31 1 gHz Celeron, i830 integrated video graphics.

They are dual booted with Intrepid 8.10.  Intrepid is clearly better on video performance and more comfortable to use.

I've tried a bunch (!) of the various performance options on jaunty which either don't work or else still don't hold a candle to 8.10.  What I've been doing is checking out jaunty for bugs then reverting to 8.10 for use.

Right now, this is jaunty with linux image kernel 2.6.30-rc2 instead of the release level 2.6.28-11.  With rc2 performance gets back toward 8.10 and hasn't broken for me (yet).

From what I can read, someone(s) "upstream" of Ubuntu probably running on the latest and greatest hardware made some changes which did not run on Intel integrated graphics.  They found out about it and chose not to remove the changes.  Some ATI versions and other video lines have had problems as well.

Due credit to Ubuntu developers and Intel, after months they finally got integrated graphics to run, albeit slowly.

Whatever the linux difficulties are, rumor is Torvalds himself got involved (isn't he always on important stuff) and thinks performance should be back toward 2.6.27-11 (Intrepid) with 2.6.30-rc2 (rc3 is out and on one of my systems).

I don't know what kernel will be on karmic koala.

Have fun, Jerry

p.s. Having more and more systems which don't run linux well is no way to get critical mass vs. Microsoft.

---

### Post by m_2009 on 2009-04-23
I have an Intel 910GML integrated video chip on my laptop and I've had no problems with that in Intrepid at all, and currently running Jaunty on it with no problems also, so doenst seem to be any problems as far as I can see.

---

### Post by baytuni on 2009-04-23
I have 965GM intel integrated and i can clearly say that the response of the operating system if not far more better, is better now. However there are couple of bugs. I cannot open evolution and calculator at all because of some visual stuff i haven't been able to figure out yet. Also I have some fullscreen video problems. When I play a local video file fullscreen, wallpaper appears and disappears occasionally. Also fullscreen flash player performance is also pretty crappy that it became unusable for me. All those problems I did not have with intrepid. But I think you should give it a shot.

---

### Post by Nevon on 2009-04-25
I just installed 9.04 yesterday, and except for Nautilus crashing on me every now and again, it seems to be working fine.

---

### Post by slumbergod on 2009-05-05
I have an integrated X3100 Intel graphics chipset. When I upgraded to Jaunty, it felt very unstable. Lots of CPU spikes and very jerky video playback. It improved a bit when I downgraded to the intel driver to the old one from intrepid. 

Still, Jaunty has not been as nice an experience for me...Deluge issues, VLC jerky playback, etc.

---

### Post by dabl on 2009-05-05
I installed Kubuntu 9.04 on a Dell Dimension 2350 which has an integrated Intel 845G/GL chip.  The OS works reasonably on a 1280x1024 @60Hz screen on the Dell 772c CRT. I installed Adobe Flash (latest version) and Java. Firefox browser works great, youtube videos play correctly in the default window size. OpenGL works, although glxgears shows only 230 fps.  Google Earth installed, but crashes X when you try to run it.  All in all, I would call it "reasonable for casual use" -- don't bother with image editing or anything that pushes the display.

---

### Post by Cabo_Nobby on 2009-05-20
My laptop has an Intel 3100 (my laptop is an Acer 5715z). I've been experiencing various crashes on the xserver.
(i'm asuming it's the xserver). I'm the laptop and the image sometimes freezes.
AltGr+K+ImprPant doesn't work nor does Ctrl+Alt+Backspace. (I re-enabled Ctrl+Alt+Backspaced via dontzap etc...)
I have to reboot the laptop and start what i was doing from the begining again.
I really don't know what to do. Someone has an idea? or maybe canonical will fix it via and upgrade or something?


P.S. 
By the way this is my first post. I'm glad to join you guys. ):P

---

### Post by Orographic on 2009-05-20
I have a Gigabyte 945GZM-S2 motherboard with intel onboard graphics that worked very well on Intrepid. Its a bit sad that the same computer doesn't run as well with Jaunty installed, at least with video. So far, in most other respects, I like Jaunty a lot.

We've just got a nice little video cam for some student performances and I had it all working great with Kino and DeVeDe in Intrepid but feel that Jaunty wont be as successful. I can't go back to Intrepid as it had intermittent issues with my external usb hard drives which is ironically resolved in Jaunty.

Leaves me in limbo a bit and feeling forced back to XP after seven months of Ubuntu...

---

### Post by meonkeys on 2009-06-01
I really should have read the release notes for Jaunty before upgrading. :)

> **Partyboi2 said:**
> This is taken from the release notes for Jaunty...

Thank you for pointing this out!

```
Option "MigrationHeuristic" "greedy"
``` in the "Device" section is working for me so far... Xorg 2D Intel integrated graphics performance seems back to what I came to expect in Ubuntu 8.10.

---

