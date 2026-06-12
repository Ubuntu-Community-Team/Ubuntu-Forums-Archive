---
title: "VIA/S3G UNICHROME Pro driver not define?!"
date: 2009-02-07
forum: Hardware
---

### Post by Coldness on 2009-02-07
I have this built-in graphics card VIA/S3G UNICHROME Pro. It seems that it's not installed. I tried to install compiz, but to no avail. I read some help here and there, but I couldn't do anything with it.

It seems the output of this command "sudo lshw -C display" is required:
```
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro]
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 bus_master cap_list
       configuration: latency=32 mingnt=2

```

Also in a thread here on the forum, these packages were to be installed, xserver-xorg-video-unichrome', 'xserver-xorg-video-openchrome', 'libchromexvmc1' and 'libchromexvmcpro1. But when I try to install them with apt-get install, a no package found error comes.

I'm helpless, but help me!

---

### Post by Coldness on 2009-02-07
Anyone?! Please, I like all the GUI effects! And I'd like to have it all!

---

