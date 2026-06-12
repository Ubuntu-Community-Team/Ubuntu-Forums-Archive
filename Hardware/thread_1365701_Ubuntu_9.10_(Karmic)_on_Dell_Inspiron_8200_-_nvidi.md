---
title: "Ubuntu 9.10 (Karmic) on Dell Inspiron 8200 - nvidia fix"
date: 2009-12-27
forum: Hardware
---

### Post by stathern on 2009-12-27
Hi, Just a quick post to help out anybody with a Dell Inspiron 8200 who wants to install Ubuntu 9.10 (Karmic).  The nvidia device in question inside is a GeForce4 440 Go. It installs great until you try to activate the nvidia drivers at which point on reboot you get a black screen. To fix this you press Control-Alt-F1 to get a prompt at which point you login with your username and password, and type: cd /etc/X11 then edit your xorg.conf file - e.g. sudo vi /etc/xorg.conf What you need to do is to add a line in the Section &quot;Device&quot; which reads as follows: Option     &quot;UseDisplayDevice&quot;     &quot;DFP-0&quot; Otherwise what seems to be happening is that the nvidia driver is defaulting to CRT output (presumably the port at the back). Anyway, just save the xorg.conf file, reboot, and Bob's your uncle. Hope that helps somebody. Jason.

---

### Post by jrennell on 2010-01-13
Helped me. This worked perfectly, thank you!

Here's the section of xorg.conf in question from the above post:

```

Section "Device"
    **Option         "UseDisplayDevice" "DFP-0"**
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

```

---

### Post by JohnSchu on 2010-02-19
I am brand spankin' new to Ubuntu and I bet I spent 4 hours alternating between hacking around on the installation and hunting for a solution. Finally I google "ubuntu 9.10 inspiron 8200" and it takes me right you your little gem here.

What I'm trying to say is **thank you**. Thank you very much. My wife also thanks you, as my sudden obsession with a decade old laptop has had her puzzled.

---

