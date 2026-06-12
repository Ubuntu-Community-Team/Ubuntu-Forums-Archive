---
title: "Thinkpad t42p/ATI Mobility Radeon 9600 regression?"
date: 2012-10-26
forum: Hardware
---

### Post by zneastman on 2012-10-26
I have a Thinkpad t42p (with an ATI Mobility Radeon 9600) that's been my workhorse laptop since 2007, running either Debian stable or an Ubuntu LTS (most recently Lucid).  On all of those systems, using either FGLRX or the radeon driver with compiz/gnome, performance has always ranged from good (with FGLRX) to excellent (radeon/r300).

On Precise, though, Unity 2d, 3d, gnome-fallback, gnome-shell, and even XFCE are unusably slow.  Scrolling in Firefox/Epiphany is choppy, animations stutter, and the Unity Dash (both 2d and 3d) takes several seconds to render.  Glxgears pulls a big 50 FPS in all of these settings, where it used to reliably pull well over 1000. 

The situation is, incidentally, similar in Debian Wheezy as well as Fedora 17.  Squeeze and Lucid, however, run as well as ever, so I don't think this problem is Ubuntu-specific or a matter of hardware.

One interesting part of this problem is that, in all of these environments, graphics performance is spectacular for about the first five seconds -- Expo, for instance, will run buttery smooth, etc., etc.  Then it goes all to hell.  

So I'm wondering:

1) Is anyone else running Precise on a t42 or t42p?  How's that working, and if it's good, how did you do it?  Some googling suggests that not every t42 owner is having this problem, or that there's a workaround so blazingly obvious that nobody bothers to mention it.

2) Are there workarounds worth investigating?  Performance needs to improve by an order of magnitude, and something is obviously broken, so (unless there's a known bug with a specific workaround) I don't think the usual xorg.conf tweaks are going to do the job.

I've tried disabling KMS.  In Wheezy, that kills 3d/dri.  I didn't test that in Precise under the assumption that it would do about the same thing.  Also, KMS is enabled in Squeeze (granted on a 2.6.3x kernel), in which performance is fine.

Any ideas?

UPDATE:

Disabling KMS seems to make performance even worse.  Also, working vsync means that the glxgears framerate is going to cap at the display's refresh rate, so it's not really a useful performance indicator.  So the improvement I need here may not be order of magnitude.

Finally, some xorg tweaks improve performance (AGP fastwrite, page flipping, etc...) but not to the point where Precise is usable day to day.  I spent the better part of Saturday distro-hopping this machine, and here's what I found:

* Debian Squeeze performs well.  Installing backported kernels and xorg kills performance.
* Ubuntu Precise uses the same basic software versions as those backports.  Performance there also clearly sucks.
* SolusOS, which uses packages from Squeeze and Debian backports, performs best of all.  I'm still trying to sort out how, since as far as I can tell the X/mesa/driver packages it uses are *exactly the same* as Squeeze+backports.  Yet whatever bug is hitting this stack doesn't seem to be in play.

Those points aren't there so some Dr. House can tell me what's going on as much as they're there for anyone having similar problems on the same hardware.

---

### Post by zneastman on 2012-11-19
Another update:

Solved.  This appears to be a kernel issue.

After upgrading a Thinkpad x41 to Precise I noticed similar, stuttering graphics and lagging animation.  Switching to the "lowlatency" kernel helped this, but it was the [Optimus kernel]("http://optimus-linux.blogspot.com/2012/08/optimus-kernel-32029-released.html#more") that really landed the fix (for both the T42p and the x41).  

I'm not sure whether this is due to BFQ or changes to the default CPUFreq setting -- could be that these older centrino chipsets aren't speedstepping as they ought to with the newer kernels.

---

