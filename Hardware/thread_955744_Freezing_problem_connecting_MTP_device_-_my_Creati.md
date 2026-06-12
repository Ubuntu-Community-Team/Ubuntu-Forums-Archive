---
title: "Freezing problem connecting MTP device - my Creative Zen mp3 player"
date: 2008-10-22
forum: Hardware
---

### Post by h84ll1 on 2008-10-22
Hi there,

I'm having an issue when connecting the device which makes it freeze, and i want to set up being able to sync and organize the music on it, but i can't do it until i have this issue fixed. :cry:

I first posted here so please reply here;
[http://ubuntuforums.org/showthread.php?t=954889](http://ubuntuforums.org/showthread.php?t=954889)

I figured the issue was also relevant to this section of the forum :)

Please help...[-o<

---

### Post by manuhank on 2009-04-08
i has the same problem and i has just solved it.
i have to:
open synaptic, uninstall gphoto2
install qlix, mtpfs, mtp-tools, libmtp8, phyton-pymtp
now i can use it like a flash drive, all works perfect
i'm so happy for that, that i registered here just for share it whit all of you :) ^^
excuse my poorly english

---

### Post by teamsuperoxide on 2009-04-11
> **manuhank said:**
> i has the same problem and i has just solved it.
i have to:
open synaptic, uninstall gphoto2
install qlix, mtpfs, mtp-tools, libmtp8, phyton-pymtp
now i can use it like a flash drive, all works perfect
i'm so happy for that, that i registered here just for share it whit all of you :) ^^
excuse my poorly english

Hi, I'm having a similar problem with my Zen 8GB however I'm a total newbie to ubuntu..... So how do I find those packets qlix, mtpfs etc. I've searched synaptic..... are they found in special repositories? If so whats the APT line.

Cheers

---

### Post by Kingy_0 on 2009-04-12
> **teamsuperoxide said:**
> Hi, I'm having a similar problem with my Zen 8GB however I'm a total newbie to ubuntu..... So how do I find those packets qlix, mtpfs etc. I've searched synaptic..... are they found in special repositories? If so whats the APT line.

Cheers


Unfortunately I'm new to Ubuntu as well so I may not be as much help as a Pro, but I have just installed gnomad2 and that has allowed me to access my Zen V 2GB Mp3 player (Read online it works well with other Creative products). It's available through Synaptic, the packages you are looking for those being qlix, mtpfs, mtp-tools, libmtp8, python-pymtp should be in Synaptic also.

If they're not you could open Synaptic from ***System > Administration > Synaptic Package Manager*** and then selecting ***Settings > Repositories*** and check to see if you have the options below enabled:

```
[tick box here] Canonical supported Open Source software (main)

[tick box here] Community maintained Open Source software (universe)

[tick box here] Proprietary drivers for devices (restricted)

[tick box here] Software restricted by copyright or legal issues (multiverse)
```

It should look slightly similar to what I have in the above box obviously there is tick boxes instead of what I've written, enable all of the above options then search for the packages again you should find them.

Hope I've helped somewhat... And good luck with getting your player to work.

Oh, and on a whim just be sure you have **libusb** installed as well although that should come installed by default.

**...** (Something I've added a little later after the first post)

Nearly forgot to mention, you can only access the Mp3 player and your files through Gnomad2. Your not able to access it like a normal usb flash drive.

---

