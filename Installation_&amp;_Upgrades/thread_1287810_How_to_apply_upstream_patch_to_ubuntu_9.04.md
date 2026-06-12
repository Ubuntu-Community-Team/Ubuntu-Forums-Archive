---
title: "How to: apply upstream patch to ubuntu 9.04"
date: 2009-10-10
forum: Installation &amp; Upgrades
---

### Post by jauskelis on 2009-10-10
Greetings all, I'm enjoying my fifth day (and night) with Ubuntu.  I'm stuck, please share your council with me.

How to: apply an "upstream patch" to my system.

Problem:  Nvidia HDMI does not work.  After learning bout ALSA troubleshooting I found a bug report that appears applies to me.

the bug:   [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/416482](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/416482)
and the fix:   [http://bugzilla.kernel.org/show_bug.cgi?id=14097](http://bugzilla.kernel.org/show_bug.cgi?id=14097)

What do I do with this patch?  I need some step by step with this -THANK YOU.

*** linux-2.6.28/sound/pci/hda/patch_nvhdmi.c.orig	2009-08-19 23:48:28.000000000 +0300
--- linux-2.6.28/sound/pci/hda/patch_nvhdmi.c	2009-08-19 20:06:33.000000000 +0300
***************
*** 162,166 ****
--- 162,167 ----
  	{ .id = 0x10de0002, .name = "NVIDIA MCP78 HDMI", .patch = patch_nvhdmi },
  	{ .id = 0x10de0007, .name = "NVIDIA MCP7A HDMI", .patch = patch_nvhdmi },
  	{ .id = 0x10de0067, .name = "NVIDIA MCP67 HDMI", .patch = patch_nvhdmi },
+ 	{ .id = 0x10de0003, .name = "NVIDIA ID 3 HDMI", .patch = patch_nvhdmi },
  	{} /* terminator */
  };

---

