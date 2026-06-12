---
title: "Different RAM settings for Dual Boot"
date: 2009-08-02
forum: Installation &amp; Upgrades
---

### Post by Isoas on 2009-08-02
Hello everyone, I have an ASUS G1Sn laptop with 4 gigs of RAM and an Nvidia 9500M gs graphics card. Because of the 4 gigs of ram, my graphics card doesn't seem to work with linux kernels. However, I am told that if I use only 2 gigs of ram then it should work.

I was wondering if there is any way to set up my boot so that I could use all four gigs with Vista and then only two with linux?

Thanks in advance!

---

### Post by running_rabbit07 on 2009-08-02
Your graphics card working has nothing to do with your RAM. Have you went into System>Administration>Synaptic Package Manager and installed nvidia drivers yet? See attached screenshot for what to look for. You want to install the one I have highlighted if you haven't already.

---

### Post by merlinus on 2009-08-02
You might also look in System/Administration/Hardware Drivers to install the correct one for your card.  Then you should be able to set it up via a gui.

```
gksu nvidia-settings
```

---

