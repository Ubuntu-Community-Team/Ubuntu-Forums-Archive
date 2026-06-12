---
title: "Suspend and Hibernate don't restart computer"
date: 2007-02-08
forum: Hardware &amp; Laptops
---

### Post by dannyboy2k on 2007-02-08
Hi,

I've got a problem with my suspend and hibernate functions on Ubuntu edgy. Basically my laptop (acer with an amd64 turion processor, not sure of video card, less than year old) doesn't come back on after I've suspended/hibernated it.

I can hear the hard disk purring, but nothing on the screen and keyboard doesn't work, for instance ctrl-alt-backspace doesn't restart it.

I saw this post:

[http://www.ubuntuforums.org/showthread.php?t=334689&highlight=Suspend+hibernate](http://www.ubuntuforums.org/showthread.php?t=334689&highlight=Suspend+hibernate)

So installed nvidia-glk and modified the xorg.conf file like it said. But then when I restart my computer it says my vxideo drive is not configured correctly so I have copy my backup xorg.conf so that I can run again :cry: 

If anybody can help that would be great.

---

### Post by jimbren on 2007-02-08
I sometimes have the same problem on my laptop (Dell), but it happens because the machine things I'm using an external display when I open the lid back up or try to come out of suspend\hibernation.  All I do is toggle my external display back to the laptop's monitor.  The key combination is Function+F8 on my machine.

Have you tried that?

jimbo

---

### Post by dannyboy2k on 2007-02-08
Tried your idea.

If I suspend and then restart with function +F4 which has a little Z^z on it then it works. And hibernate kind of half restarts now. But that's good enough for me! If I hibernate I can restart with the power button.

Thank very much. Playing with the xorg.conf file is a little scary for a newbie like me.

But I did do this to the  /etc/default/acpi-support file:

$  sudo gedit /etc/default/acpi-support

# Comment the next line to disable ACPI suspend to RAM
#ACPI_SLEEP=true

and made sure that

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

This conflicts with the advice in the above post, but seems to work for me!

I'll post again if I have trouble restarting after long periods of time.

Can anyone explain what the above means?

---

