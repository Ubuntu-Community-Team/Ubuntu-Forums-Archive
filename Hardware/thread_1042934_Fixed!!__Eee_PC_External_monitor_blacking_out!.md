---
title: "Fixed!!  Eee PC External monitor blacking out!"
date: 2009-01-18
forum: Hardware
---

### Post by ruff on 2009-01-18
I have had a problem with my Asus 1000H Eee PC when watching movies with the device connected to my Plasma TV. The external screen would randomly 'Black Out'. The movie itself would still be running and the sound was still heard, just a BLACK screen. A signal was still being supplied to the external screen as the screen never went into standby and I imagine X was still running, just could not see it.

The problem was fixed by adding a line in xorg.conf to turn off Framebuffer. Include the following Option in the Device Section of “Configured Video Device”:

Section "Device"
Identifier      "Configured Video Device"
Option          “FramebufferCompression” “off”
EndSection


I hope this saves someone the pain I went through trying to fix the problem.

Cheers,

---

### Post by tavern on 2009-09-03
i've been having this issue, including flickering, just made the edit.

thanks for posting this, i'd have been stumped for a while.

i'll let you know if it works, will only need to wait a bout 5 minutes.

---

### Post by tavern on 2009-09-03
okay, well i made the edit as described and it killed it. so i went into low graphics mode and #'d out the line and restarted video.

it's probably important to stipulate that the line should go in the conf file in the section for the intel video card.
```

Section "Device"
        Identifier      "Configured Video Device"
        Driver           "intel"
        Option          "FramebufferCompression" "off"
EndSection

```

as i also had a section that is essentially empty, also labeled 

```
Identifier      "Configured Video Device"
```

but otherwise it seems to have worked, kudos to you ruff of the gong.

---

