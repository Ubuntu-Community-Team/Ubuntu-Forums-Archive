---
title: "Issues with nvidia not loading with LCD monitor"
date: 2005-06-23
forum: Hardware &amp; Laptops
---

### Post by Stephen-I-M on 2005-06-23
I'm getting a

  "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found

error when I do a startx command and I can't figure out why. My current computer worked fine with my CRT monitor, but with the NEC 2070nx, no go.

I'd appreciate any help anyone could give me. The nvidia logo briefly makes its appearance then disappears when "Initializing extension GLX".

Here's my xorg.conf:

[http://www.theboulets.net/xorg.conf](http://www.theboulets.net/xorg.conf)

Here's my Xorg.0.log:

[http://www.theboulets.net/Xorg.0.log](http://www.theboulets.net/Xorg.0.log)

Stephen

---

### Post by Stephen-I-M on 2005-06-24
The issue was with the NVidia drivers.

According to the release notes for 1.0-7667:

Release Highlights

    * Added support for GeForce 7800 GTX.
    * Fixed problem with certain flatpanels running at 1600x1200.

I have a 1600x1200 flatpanel, and upgrading to this new version fixed the issue.

Stephen

---

