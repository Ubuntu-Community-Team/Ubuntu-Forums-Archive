---
title: "Ubuntu removing necessary kernel options when updating Grub"
date: 2007-04-01
forum: Hardware &amp; Laptops
---

### Post by RossMM on 2007-04-01
I'm a new Linux user and have opted for Ubuntu, but when installing it yesterday I found a problem with my motherboard and I was wondering if anyone could help me with it. The problem I had is that the network card (along with other motherboard components) wasn't detected, so looking through this forum and bug lists I found that there is a known problem with my MoBo (MSI MS-6390) in Linux. The fix for this is to add 'nolapic' or 'noapic' to the kernel line in the menu.lst Grub file for the kernel I want to boot into. Now 'nolapic' didn't work for me at all (Ubuntu would start, but I wouldn't reach the splash screen where things like Nautilus are loaded), but 'noapic' seems to have fixed it.

Now this would be great, if it weren't for the fact that every time I update Grub (or maybe the kernel) I will need to change this file manually. Ubuntu seems unable to understand that any change to the menu.lst is intentional and replaces the file completely. Therefore I'm wondering if:

a) The kernel can be fixed so it works fine with my MoBo.
b) There is a way to tell Ubuntu to keep this addition to the line.

Failing that I could at least create a simple script that I can run after getting a new Kernel to automate the process, but unfortunately that's beyond my Linux know-how just yet.

Thanks in advance for any help you can provide.

---

### Post by teaker1s on 2007-04-02
edit grub then you must save and use this command
```
sudo update-grub
```


secondly you can
```
gksudo synaptic
```
**completely remove** the old kernels you don't want and synaptic will update grub for you

---

### Post by RossMM on 2007-04-02
Sorry, but I don't seem to have explained myself very well. If I understand your advice that would update Grub for me by setting it back to the Ubuntu default. I do not want this, in fact I want to stop Ubuntu from doing this at all as it is removing an option I need to ensure Linux is working with my motherboard.

---

### Post by GoBieN on 2007-04-02
Have you seen this section in menu.lst ;)
> ## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet noapic splash

If you fill noapic here in this line, grub-update will always append noapic to any new kernels or updates ...

it does for me anyways

---

### Post by RossMM on 2007-04-02
Fantastic, that's exactly the sort of option I was looking for. Thanks for your help.

---

