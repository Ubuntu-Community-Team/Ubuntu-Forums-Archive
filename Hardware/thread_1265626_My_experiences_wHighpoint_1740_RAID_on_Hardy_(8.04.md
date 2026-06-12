---
title: "My experiences w/Highpoint 1740 RAID on Hardy (8.04)"
date: 2009-09-13
forum: Hardware
---

### Post by NorthernSoul on 2009-09-13
I've had some experience with this controller and thought I'd post my experiences if anyone needs the help.
**All information pertains to Hardy (8.04)**

_Installing the OS on to controller_: Followed the directions on the alternate installer. Couldn't install, although it's probably a problem with MBR vs GPT partitioning, since my array is bigger than an MBR can handle. Haven't tried it with an array the could be handled by MBR.
_Installing the driver on an existing installation_: Worked with the open source driver. Did a make install and modprobe like in the readme and it worked. Tried the supplied pre-compiled driver and it didn't work.
_Installing the management software_: Installed the CLI interface, worked. Then installed the GUI interface, also worked. Tried on previous OS installs to install just the GUI or the web interface, didn't work.

Overall, decent RAID controller, I wish their supplied drivers would work but at least the open source driver will. Don't fool yourself though, this is fakeraid.

---

