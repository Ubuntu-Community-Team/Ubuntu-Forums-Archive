---
title: "Breezy Badger Upgrade Halts on libc6.postinst"
date: 2005-12-19
forum: Installation &amp; Upgrades
---

### Post by Unbathed on 2005-12-19
I am trying to upgrade from Hoary to Breezy using a freshly burn installation CD and Synaptic Package Manager.  After following the instructions, the upgrade process appears to be hanging on libc6.  When I ssh into the system and ps -a, it appears that the halted process is named libc6.postinst.  Any suggestions?

---

### Post by sethmahoney on 2005-12-19
Redownload the ISO and burn a new CD.

---

### Post by Jeandré on 2005-12-20
[QUOTE=Unbathed]I am trying to upgrade from Hoary to Breezy using a freshly burn installation CD and Synaptic Package Manager.  After following the instructions, the upgrade process appears to be hanging on libc6.  When I ssh into the system and ps -a, it appears that the halted process is named libc6.postinst.  Any suggestions?[/QUOTE]


While upgrading I found the install also stopping without any indication of what was wrong. The following note in [BreezyUpgradeNotes]("https://wiki.ubuntu.com/BreezyUpgradeNotes") fixed it for me: "If you're upgrading using Synaptic and your upgrade seems to have paused at the "Installing software" stage, click ">Terminal" to uncollapse the terminal subwindow and check it's not stopped waiting for user input".

---

