---
title: "VRC-1100 remote control w/Kodi under 14.04.1 LTS ?"
date: 2015-01-26
forum: Hardware
---

### Post by Ronald_F._Guilmett on 2015-01-26
I have been using my VRC-1100 remote control, and associated IR USB dongle happily for quite some time with my old HTPC, which was/is an x86-based system.  All of the buttons on this thing seem to work and do the Right Thing under OpenELEC on the x86 box.

Recently, I've purchased an Odroid-C1 (ARM-based) to use as my new HTPC.  Unfortunately, there is not yet a port of OpenELEC for this board, so I'm trying to run Kodi on top of the maunfacturer-supplied OS image, which is based on Ubuntu.  (I believe its based on 14.04.1, but don't quote me.)

Anyway, I have confirmed on another (x86) machine that the combination of Ubuntu, Kodi, and my VRC-1100 just do not play well together.  In fact they play together rather badly, with several key buttons on the remote are simply not working when used with an out-of-the-box stock Ubuntu install... on both x86 and also, identically, on my Ordoid-C1.

This is apparently a well known problem.  Googleing for VRC-1100 an Ubuntu bring up lots of hits of various people talking about the problem(s).

I meticulously applied the specific system changes recommended by Team Kodi here:

[http://kodi.wiki/view/HOW-TO:Configure_VRC-1100_remote_for_Ubuntu](http://kodi.wiki/view/HOW-TO:Configure_VRC-1100_remote_for_Ubuntu)

but alas, this made things worse, and now -none- of the buttons on the remote work at all.

That is perhaps not surprising, given that the instructions on that page appear to date from September of 2010, and thus probably are useful only for some older version(s) on Ubuntu.

So, um, does anyone here have a good set of steps/instructions which will allow me to fully use my VRC-1100 remote under, say, 14.04.1 LTS in conjunction with XBMC/Kodi?  If so, could you please post the instructions?

---

### Post by Ronald_F._Guilmett on 2015-01-28
I found the soluntion to my own problem, and I thought that I should share it...

Apparently, the VRC-1100 remote works correctly, even with XBMC/odi,  *out of the box* with (at least) 14.04.1, and probably beyond.  The problem was that the Unity desktop was grabbing some but not all of the key presses from the VRC-1100 before they even made it to XBMC/Kodi.  Fortunately, the solution is trivially simple.  On the Ubuntu desktop, go to System Settings > Keyboard > Shortcuts > Sound and Media and  disable each of the relevant shortcuts by selecting them then pressing  backspace.

My thanks to denz13 of the Kodi community for providing this solution.

I have taken it upon myself to update the following web page with this information:

[http://kodi.wiki/view/HOW-TO:Configure_VRC-1100_remote_for_Ubuntu](http://kodi.wiki/view/HOW-TO:Configure_VRC-1100_remote_for_Ubuntu)

---

