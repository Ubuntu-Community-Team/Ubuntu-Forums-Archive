---
title: "Replaced motherboard, reformat needed?"
date: 2008-09-22
forum: General Help
---

### Post by AVT- on 2008-09-22
Good morning,

Firstly, I'm somewhat of a Linux newb, so bear with me. I've replaced a motherboard in a box running Mythbuntu. After some tinkering around, the box seems to be somewhat working. 

One problem I've run into so far is eth0 does not exist anymore, but an eth3 has appeared. eth1/eth2 are the same cards, so they seem to be unaffected. I assume there's 10,000 other such problems that I'm not seeing, but I may be wrong.

Is there some way to change all of this, or is reformat necessary?

---

### Post by mb_webguy on 2008-09-22
Most of the time an OS won't even boot after a hardware change as drastic as swapping out the motherboard, so you're lucky that Mythbuntu runs at all.

The best thing to do would be to reinstall Mythbuntu.  (Of course, you should make sure you back up any important files first.)  Also, make sure you're running the latest BIOS for your system.

---

### Post by AVT- on 2008-09-22
> **mb_webguy said:**
> Most of the time an OS won't even boot after a hardware change as drastic as swapping out the motherboard, so you're lucky that Mythbuntu runs at all.

The best thing to do would be to reinstall Mythbuntu.  (Of course, you should make sure you back up any important files first.)  Also, make sure you're running the latest BIOS for your system.

Yeah, at first it waited almost 15mins, then booted into low graphics mode, with onboard NIC and a bunch of stuff not working. 

I then booted to CD, that worked fine, then booted onto harddrive, and it magically started working. I don't want to have to reformat and re-set everything up, though. Hence why I'd like to know if I can find out if it's detecting any redundant hardware, or something.

---

### Post by mb_webguy on 2008-09-22
> **AVT- said:**
> Yeah, at first it waited almost 15mins, then booted into low graphics mode, with onboard NIC and a bunch of stuff not working. 

I then booted to CD, that worked fine, then booted onto harddrive, and it magically started working. I don't want to have to reformat and re-set everything up, though. Hence why I'd like to know if I can find out if it's detecting any redundant hardware, or something.

If you backup your home directory, you should keep all of your preferences, and therefore shouldn't have to reconfigure everything.  If you have any software installed that's not part of the default Mythbuntu installation, you'll still have to install them after reinstalling Mythbuntu, but again you'll keep your preferences as long as you backup your home directory.  Just make sure that when you do, you get all of the hidden files and folders.

---

### Post by AVT- on 2008-09-22
> **mb_webguy said:**
> If you backup your home directory, you should keep all of your preferences, and therefore shouldn't have to reconfigure everything.  If you have any software installed that's not part of the default Mythbuntu installation, you'll still have to install them after reinstalling Mythbuntu, but again you'll keep your preferences as long as you backup your home directory.  Just make sure that when you do, you get all of the hidden files and folders.

Well, that's the problem. Unfortunately as it is now wifi in Linux is a pain, especially AP mode, and even more so with security. 

Ugh, I guess I'll reformat anyway. I need to make a hostapd-madwifi .deb anyway..

---

### Post by mb_webguy on 2008-09-22
I'm not sure what wi-fi has to do with it...

If you can boot from the LiveCD, and you have a USB drive or a blank disc handy, just boot from the LiveCD, navigate to your current Ubuntu partition and copy the files from your home folder to the USB drive or disc.

---

### Post by Krupski on 2008-09-23
> **AVT- said:**
> Good morning,

Firstly, I'm somewhat of a Linux newb, so bear with me. I've replaced a motherboard in a box running Mythbuntu. After some tinkering around, the box seems to be somewhat working. 

One problem I've run into so far is eth0 does not exist anymore, but an eth3 has appeared. eth1/eth2 are the same cards, so they seem to be unaffected. I assume there's 10,000 other such problems that I'm not seeing, but I may be wrong.

Is there some way to change all of this, or is reformat necessary?

Go into your "/etc/udev/rules.d" directory.

Edit the "70-persistent-net.rules" file.

Remove all entries that look something like this:

```

# PCI device 0x8086:0x294c (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1c:00:00:00:00", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

```

...and leave only the comment block on top.

Then reboot. Your new NIC should come up just fine as "eth0".

Now, knowing what you did... you can (carefully!) edit the other "persistent-rules" files and remove references to your old motherboard. The new data will be added at next boot.

Problem solved.

---

