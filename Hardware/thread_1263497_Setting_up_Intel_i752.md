---
title: "Setting up Intel i752"
date: 2009-09-11
forum: Hardware
---

### Post by chewit on 2009-09-11
I have just got myself a new computer, to replace my aging 10 year old box which was struggling to run Xubuntu. My new box can now run full Ubuntu, very well. 

I have everything setup nicely, however I am concerned about the graphics card. Its a Intel i752. I have two questions, which driver does it require (intel, i740 or i128 ) and Is there any other tweaks which I have forgotten to add to my xorg conf file. My old PC was able to run compiz and get a high fps on glxgears. Though, my old PC had a dedicated graphics card (ATi 7000) and this new PC has a built in card. On the driver question, I understand the the i752 is the same card as the i810, if so, it requires the Intel drivers.

My Xorg tweaks:

	Option		"AccelMethod"			"uxa"
	Option		"EXAOptimizeMigration"		"true"
	Option		"MigrationHeuristic"		"greedy"
	Option		"Tiling"			"true"

---

### Post by chewit on 2009-09-11
Bump.

---

