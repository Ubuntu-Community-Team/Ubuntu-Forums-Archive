---
title: "new install of &quot;hoary hedgehoag&quot; - can't get the X server going"
date: 2006-04-02
forum: Hardware &amp; Laptops
---

### Post by makc79 on 2006-04-02
Hi, all.

I have installed "hedgehoag" on b130 dell laptop. The x server does not comeup on boot. ctrl-alt-backspace does not show anything. 
Originaly I thought that my resolution is not setup correctly, but after checking xorg.conf and verifying on multi[;e forums, I think the resolution settings are fine.

I booted in recovery mode, set the path and ran startx and got the following message:
AUDIT: <date>: 6885 X: client 6 rejected from localhost
Synaptics DeviceOff called
xinit: connection to X server lost.

(sometimes it says "client 5" instead of "client 6").

I have tried blowing away the .Xauthority , that didn't help either.

Does anyone have an idea on how to fix this thing ?

Thanks,

-Maksim

---

### Post by localzuk on 2006-04-02
I am not too sure of the issue. However, I would recommend using Breezy instead of hoary as it is the current stable version...

---

### Post by makc79 on 2006-04-02
are you suggesting the previous release is not stable? I'm confident this is a configuration (misconfiguration) issue that has very little to do with which release I am running.

thanks anyway.

---

### Post by dicecca112 on 2006-04-02
no what he is saying is that Breezy is more compatible with current and previous systems.  And you may be running into a bug that was fixed in Breezy, that wasn't in Hoary.  

that said you might wanna tell us what your graphics is.  It may not be support by the kernel  if its onboard, or you may need to configure the x-server to run on vesa until you install your graphics drivers

---

