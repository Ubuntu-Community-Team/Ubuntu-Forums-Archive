---
title: "Greatly improved performance with Intel chipset"
date: 2009-08-11
forum: Hardware
---

### Post by TexLogic on 2009-08-11
Just to note, a small change to my xorg.conf file suggested in another thread has led to a big improvement in graphics performance in my Acer 5810T, which uses the Intel Graphics Media Accelerator 4500MHD chipset.  Specifically, the change was to add the the following three lines to the "Configured Video Device" section:

	Option        "AccelMethod" "exa"
	Option        "EXAOptimizeMigration"        "true"
	Option        "MigrationHeuristic"        "greedy"

The difference is particularly noticeable in Compiz desktop effects. Prior to this change, cube rotation in particular would bring the system to its knees -- the CPU would max out and the movement itself was dog slow and jerky, as if the graphics processor was not even involved.  Now it is fast and fluid and does not max out the CPU.  YMMV, of course, but hopefully others might find this useful.

---

### Post by coolvibe on 2009-10-02
I believe those settings are default with Karmic.

---

