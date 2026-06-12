---
title: "compiz and xorg.conf??"
date: 2008-09-22
forum: General Help
---

### Post by gazzzan on 2008-09-22
Hey guys I just installed compiz and its great except for the lag I get on the windows. I found a bug which fixes the lag with the intel chipsets, but I don't know how to edit the xorg.conf file. Here is the link that tells users what to edit.
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/205264](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/205264)

Here is what it says...
okay, well, a workaround exists for INTEL cards ONLY.

Adding this to my xorg.conf device section sovled it:
Option "AccelMethod" "exa"
Option "MigrationHeuristic" "greedy"
Option "ExaNoComposite" "false"

This is for intel cards only.

How do I add this file in order to stop the lag I get on windows I open or scroll through? Please give me step by step directions because Im a noob to linux :)

Thanks,
Mike

---

### Post by gazzzan on 2008-09-22
Please can someone just give me the simple steps to this. I know someone knows how to do it.

---

### Post by benerivo on 2008-09-22
To open the file for editing then open a terminal window (Accessories>Terminal from the main menu), and type ```
gksudo gedit /etc/X11/xorg.conf
```Then you'll need to add those three lines. I'm not 100% sure on where they should go, but I would put them at the end of
'Section "Device"

directly above the EndSection line.

---

