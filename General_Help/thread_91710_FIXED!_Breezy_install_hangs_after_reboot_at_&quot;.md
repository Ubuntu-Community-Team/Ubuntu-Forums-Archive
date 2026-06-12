---
title: "FIXED! Breezy install hangs after reboot at &quot;Installing Packages&quot;"
date: 2005-11-17
forum: General Help
---

### Post by samkivi on 2005-11-17
ok so this is a little niggle in the install process that could possibly make newbies give up, and I found a way around it.

I installed ubuntu 5.10 on second partition on my old laptop (190mb ram)
using the install command"

linux archive-copier/copy=false

which apparently doesn't copy over the extra packages leaving you with extra space if you have room.

when ubuntu installer asked me to remove the install cd and reboot, it rebooted and then hung at the "Configuring Base System: Installing packages" screen.

I think what's happening is, it needs the CD in the drive but doesn't ask for it so it just sits there waiting.
What I did to solve it was very simple: just go into your bios menu and set the harddrive to boot first and cdrom second and leave the cd in the drive.

(putting cd back in the drive after boot did not work)

now the installer will look on the cd and complete the installation.

hope that's helped someone.

---

