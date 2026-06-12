---
title: "Enter key dysfuncion on Install Splash Screen"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by parktrip on 2009-03-07
Hi, I'm new to ubuntu and having trouble installing.  The enter key does nothing when I hit "Install Ubuntu."  Any suggestions?  Thanks in advance.

---

### Post by bholub on 2009-04-28
I'm seeing this same thing with the 9.04 install. I am however under VMWare Workstation (hosted by 64-bit Vista). I know the enter key works because it allows me to select English, and I can also navigate help and change the other options using the enter key. The only menu item that actually functions when I hit enter is the boot from disk.. (which ends up doing nothing since it's a blank disk)

What was your solution, and has anyone else experienced this?

Thanks,
BH

---

### Post by Mark Phelps on 2009-04-28
I had a similar problem using a USB keyboard. Some of the keys would not work (Enter and arrow keys). Went into the BIOS and enabled Legacy USB.  Now, all the keys work.

---

### Post by bholub on 2009-04-30
the enter key works, just not on several of the menu options. it allows me to select language, boot from disk, and navigate through/select the function key options.

i've seen this on vmware workstation hosted on vista both 32 and 64 bit...

---

### Post by retroelectron on 2009-10-01
Was a solution ever found for this issue? I'm attempting to install Ubuntu 9.04. I have installed Ubuntu 8.04 on the exact hardware I'm attempting to install to now with no issues. 

I verified the .iso after download, as well as verifying the disk after burning. I'm using a USB keyboard, and I have tried it connected to a USB port and to the ps/2 keyboard port with an adapter. I have also tried setting BIOS to both enable and disable USB keyboard and mouse, and every variation thereof. I unfortunately do not have another keyboard available to use during the install.

I'm able to interact with the menu options involving the F# keys, as well as getting access to the non-graphical installer using escape and enter, but I'm not quite so Linux savvy that I can install from the command line. I selected the correct keymap for my keyboard, US English. 

Nothing I've done so far has enabled me to interact with any selectable menu option in the graphical installer other than Boot from first hard disk, which boots straight into Windows 7 without a hitch. I even went so far as to install from the same Ubuntu CD into VMware just to verify that the CD wasn't the issue, and it worked fine.

If anyone can make a suggestion as to what I can do to address the issue, or at least why the issue is occurring so I can research a solution myself, please let me know. Thanks.

---

### Post by yaronf on 2009-11-13
Same here, VMware 6.5.3, Ubuntu 9.10. Running on a ThinkPad with its native keyboard.

And when I go to the VMware/Phoenix BIOS, I don't see any applicable options.

Later update: downloading the image again fixed the problem. It must have been corrupt somehow.

---

