---
title: "MSI Wind and Intel Graphics for Ubuntu 9.04"
date: 2009-07-06
forum: Hardware
---

### Post by Shibblet on 2009-07-06
This thread has helped me the most.

[http://ubuntuforums.org/showthread.php?t=1130582]("http://ubuntuforums.org/showthread.php?t=1130582")

Although, I wanted to stay with the "Safe" option, so instead of UXA in the xorg.conf, I change it to EXA.  I don't want to upgrade the kernel, and cause other programs to not work.

My Xorg Device lines look like this...

```
Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"			**"exa"**
	Option		"EXAOptimizeMigration"		"true"
	Option		"MigrationHeuristic"		"greedy"
	Option		"Tiling"			"true"
EndSection
```

If you proceed to Optimal, keep it at UXA.  I went to optimal, but had to go back because a few programs started acting up after going to the 2.6.30 kernel.

---

