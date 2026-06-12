---
title: "Lucid installation mistake cripples computer"
date: 2010-05-01
forum: Hardware
---

### Post by justinwood on 2010-05-01
I've already been a Ubuntu user for a couple of months and was preparing to install Lucid Lynx when midway through installation the laptop was accidentally powered off disrupting the final stage. Now when the laptop is booted all I get is code telling me how it doesn't have the ability to start. I need to find someway to do one of two things. 

1. Somehow complete the installation from where I'm at OR

2 Somehow reinstall my original Ubuntu OS. I know I'll lose all of my data but at this point I'm pretty crippled by this.

I know this description is incredibly sparse but I don't know enough about the software to know what would be helpful for you to know, so if you can help please let me know what details you need. Any help would be greatly appreciated.

---

### Post by ultiva on 2010-05-01
As far as I understand You were doing system upgrade, not clean install. Download Ubuntu iso image and burn it (on another machine of course). Then boot your laptop from CD and choose "try ubuntu" to start live session. Mount your hard drive, grab USB storage and copy all valuable data to USB. Then wipe out your hard drive and do a clean install - just choose "Install" from live desktop and carry on. When on partitioning stage - choose "Use entire hard disk". That is what I would do. I assume You have Ubuntu alone on your laptop - no other OS.

---

### Post by justinwood on 2010-05-01
I've tried using the disc I used when I first installed Ubuntu, but instead I just get 

Home directory /ect/timidity not ours.
[ 53.7728377] end_request: I/O error, dev sr0, sector 14113664
[ 53.7728377] Buffer I/O error on device sr0, logical block 176708

Am I missing something? Perhaps I missed a step.

---

### Post by justinwood on 2010-05-01
Oh, and yes, I was just running Ubuntu as my only OS.

---

### Post by eltonw on 2010-05-01
> **justinwood said:**
> Oh, and yes, I was just running Ubuntu as my only OS.

Perhaps this might help: when booting, hit ESC and see if this gets you to a graphic screen showing options for safe mode, try running fsck (the equivalent of 'defrag' in Windows), e.g.:

sudo fsck /dev/sda  OR fsck /dev/sda1

You will be asked for your admin password since you need to be root (super user) to do this ... hence the 'sudo' prefix to the command.

HTH...

---

### Post by justinwood on 2010-05-01
Thanks you everyone! I think I may have the problem fixed due to your sage advice. Help like this reminds me why I switched from Windows in the first place. Blessings of Kobol upon you all!

---

