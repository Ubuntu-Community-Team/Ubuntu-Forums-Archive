---
title: "compiz and xorg.conf??"
date: 2008-09-22
forum: General Help
---

### Post by gazzzan on 2008-09-22
Hey guys I just installed compiz and its great except for the lag I get on the windows. I found a bug which fixes the lag with the intel chipsets, but I don't know how to edit the xorg.conf file. Here is the link that tells users what to edit.
[https://bugs.launchpad.net/ubuntu/+s...iz/+bug/205264](https://bugs.launchpad.net/ubuntu/+s...iz/+bug/205264)

Here is what it says...
okay, well, a workaround exists for INTEL cards ONLY.

Adding this to my xorg.conf device section sovled it:
Option "AccelMethod" "exa"
Option "MigrationHeuristic" "greedy"
Option "ExaNoComposite" "false"

This is for intel cards only.

How do I add this file in order to stop the lag I get on windows I open or scroll through? Please give me step by step directions because Im a noob to linux

Thanks,
Mike

---

### Post by gazzzan on 2008-09-22
Guys please any advice would help I'm new to this thing and I wouldn't know a donkeys *** if it was looking at me lol

---

### Post by ThrobbingBrain66 on 2008-09-22
Open a terminal and make a backup of the file first.
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bak

```

The type the folowing to open the file:
```

gksu gedit /etc/X11/xorg.conf

```

Then copy those 3 lines to the Device section so it looks something like this:
```

Section "Device"
	Identifier	"Configured Video Device"
       Option "AccelMethod" "exa"
       Option "MigrationHeuristic" "greedy"
       Option "ExaNoComposite" "false"
EndSection

```

After that, logging out and logging back in, or a restart will apply the changes.

If for some reason that doesn't work and your get dropped to a command line, type the following to restore your backup:
```

cp /etc/X11/xorg.conf_bak /etc/X11/xorg.conf

```

---

