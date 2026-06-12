---
title: "nvidia driver blues"
date: 2009-11-01
forum: Hardware
---

### Post by danielsender on 2009-11-01
Hi,

I just upgraded to 9.10 on my Dell Mobile Precision M50 that has a Nvidia Quadro4 GoGL graphic chip. Everything went OK, so going after "special effects" I downloaded from the Nvidia website the following:

Linux Display Driver - x86            [B]Version: 96.43.13
Operating System: Linux x86
Release Date: July 01, 2009[/B] 
  **Release Highlights**
[FONT=Arial][/FONT]
[FONT=Arial]The compilation went OK, to module was installed and voila! No more display, I can go to the console by pressing ctrl-alt-f4 but I didn't know what to do next. I tried removing the nvidia module but no avail. I will appreciate someone to tell me how to fix the problem. Many thanks.[/FONT]


Daniel

*[FONT=Arial][/FONT]*

---

### Post by rldowling03 on 2009-11-01
I had a similar problem also when I installed the NVIDIA restricted drivers. Try going to /etc/X11 and firstly backing up the xorg.conf file, then deleting it and restarting. That helped me.

Make sure you backup first just incase, and dont forget to sudo when copying/deleting

---

### Post by danielsender on 2009-11-01
I also tried that by using the latest xorg.conf that was working but still nothing. When I had 9.04 I also tried this driver but in that case the installation failed and at least I got some kind of recovery menu in low resolution to fix it, now every thing is black.

Daniel

---

### Post by andrewkoff on 2009-11-01
In section "Device" of xorg.conf replace

```
Driver     "nvidia"
```

with

```
Driver     "nv".
```

Reboot

---

### Post by danielsender on 2009-11-01
Thanks! It works now however I can't still activate the "extra" in preferences->appearance->visual effects. It comes back with "special effects could not be enabled". I went to administration->hardware drivers->activate, but after rebooting and changing "nvidia" to "nv" in xorg.conf the same tab shows the activate sign. Is there another step that I should do to get this going? Thanks,

Daniel

---

