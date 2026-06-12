---
title: "Ubuntu can't start with Ati Radeon 9250."
date: 2011-06-19
forum: Hardware
---

### Post by drvymonkey on 2011-06-19
So, I just installed the new version of ubuntu (11.04), I was using Windows for a while..and the first thing I saw **after inserting the DVD and restarting the PC was that Ubuntu freezes at a black screen while loading and wont continue**. So I changed to my onboard graphic card and it was working perfectly.

**Once installed, I shutdown the PC, put back the AGP Video card (Radeon 9250) and tried to run ubuntu, but it freezes on the Grub**. Practically it wont even display the grub start options or anything, just the purple color and nothing more.

So can anyone please tell me, why is this happening ? 

My PC:

Motherboard: Gigabyte GA-8VM800PMD-775
Processor: Intel Pentium 4 (3.00)
Onboard Video Card: VIA (AGP)
AGP Video Card: ATI Radeon 9250 (250mb)


**Note that in previous versions (long time ago) it was working perfectly.**


Thanks and sorry for my english =)

---

### Post by iggi916 on 2011-06-19
It may not be compatible with the Radeon card. Try this thread:

[http://ubuntuforums.org/showthread.php?t=1744188](http://ubuntuforums.org/showthread.php?t=1744188)

You can probably get your Ubuntu to boot if you blacklist the radeon module.

---

### Post by mastablasta on 2011-06-20
use an older version to ubuntu and upgrade the driver with PPA if needed.

---

### Post by jocko on 2011-06-20
> **iggi916 said:**
> It may not be compatible with the Radeon card. Try this thread:

[http://ubuntuforums.org/showthread.php?t=1744188](http://ubuntuforums.org/showthread.php?t=1744188)

You can probably get your Ubuntu to boot if you blacklist the radeon module.
That link will not do anything to solve drvymonkey's problem. It's only for modern laptops that are capable of switching between two grahic cards.

@drvymonkey: If it freezes with a purple screen it means it has already gone through grub and freezes during actually booting ubuntu.
To get the grub menu, press the shift key *before* grub loads (while you still see the bios screen) and keep it pressed until you see the menu.
One thing you can do is to inactivate kernel modesetting for the radeon driver. To test this, highlight the first boot option, press 'e' to edit the boot parameters. Move the cursor to the end of the line that starts with "Linux":
```
linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=0d76854e-ae85-42be-8840-07ee9fb1b56c ro   quiet splash
```
Type "radeon.modeset=0" after "splash", so it now looks like this:
```
linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=0d76854e-ae85-42be-8840-07ee9fb1b56c ro   quiet splash radeon.modeset=0
```

To boot, press Ctrl+X (I think that's it, but in case I'm wrong the correct key combination is written below the grub editor). Note that this change is only temporary, so if this works you will need to do a few more things to make it permanent.
If it does not work, you may need to inactivate the onboard video. Try to find out if it's possible to inactivate the VIA gpu in your motherboard's bios. Or maybe it's possible to blacklist the driver for the VIA gpu...

---

### Post by drvymonkey on 2011-06-20
Thanks for the replies,

Well, @jocko, that worked! Thanks, can you help me making the change permanent ?



Thanks again.

---

### Post by jocko on 2011-06-20
Run this in a terminal:
```
gksudo gedit /etc/default/grub
```
Find the line that looks like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
Make it look like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.modeset=0"
```
Save and close the file, then run this in a terminal:
```
sudo update-grub
```
Now it should work when you reboot.

---

