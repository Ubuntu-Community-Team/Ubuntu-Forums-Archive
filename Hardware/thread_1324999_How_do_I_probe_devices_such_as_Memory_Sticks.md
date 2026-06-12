---
title: "How do I probe devices such as Memory Sticks?"
date: 2009-11-13
forum: Hardware
---

### Post by Gogeden on 2009-11-13
Hi, how do I probe for devices such as Memory Sticks in Ubuntu? I'm trying to install Damn Small Linux on a Memory Stick but I don't know what to put for the Grub entry under the "Root" section like with Ubuntu is would be like this:

root       (0,1)


Or something. REALLY need help with this! Thank you! :lolflag:

---

### Post by aquavitae on 2009-11-13
What exactly are you trying to do? Configure grub on a memory stick? Whatever it is, something that might be useful is to enter the grub command line (you can to it at boot by pressing "c", I think, or IIRC typing "grub" in a terminal) and using autocomplete to find the devices.  To do this type, for example, "root hd" then press tab.  It will show a list of possible devices beginning with "hd".

---

### Post by Gogeden on 2009-11-13
I just want to have DSL on my memory stick and be able to boot off of that with Ubuntu's Grub.

---

### Post by aquavitae on 2009-11-16
As far as I know, grub shouldn't see any difference between internal hard drives and usb drives, so long as the bios reports them properly.  But to check, restart your computer, and at the grub screen press 'c' for command line.  Then type "root" and press tab. It should bring up a list of possible drives.  I don't remember exactly what order things need to be entered, but if you press tab whenever you're not sure it should bring up a list of options.

---

### Post by aquavitae on 2009-11-16
It looks like it might not bo so straight forward... have a look at this post: [http://ubuntuforums.org/showthread.php?t=992426]("http://ubuntuforums.org/showthread.php?t=992426")

---

