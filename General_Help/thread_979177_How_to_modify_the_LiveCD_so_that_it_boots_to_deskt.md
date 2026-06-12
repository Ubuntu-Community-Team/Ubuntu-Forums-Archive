---
title: "How to modify the LiveCD so that it boots to desktop immediately?"
date: 2008-11-11
forum: General Help
---

### Post by sstecken on 2008-11-11
I'm using Reconstructor to build my own LiveCD.

Is there a way to modify the LiveCD so that it boots to desktop immediately?  I don't need the install options, memtest, CD check, etc.

I'm not sure where these settings are stored.

Edit: I'm using Hardy 8.04.1 with the most current upgrades.

---

### Post by red_team316 on 2008-11-12
The file you need to edit is:
/home/username/reconstructor/remaster/isolinux/isolinux.cfg

Most likely you will want to edit it to something similar to this. I removed the other options from the menu and set the TIMEOUT to zero.

```

DEFAULT /casper/vmlinuz
GFXBOOT bootlogo
APPEND  file=/cdrom/preseed/kubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
LABEL live
  menu label ^Try Kubuntu without any change to your computer
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/kubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
DISPLAY isolinux.txt
TIMEOUT 0
PROMPT 1
F1 f1.txt
F2 f2.txt
F3 f3.txt
F4 f4.txt
F5 f5.txt
F6 f6.txt
F7 f7.txt
F8 f8.txt
F9 f9.txt
F0 f10.txt

```

---

### Post by saltydog on 2008-11-17
But setting timeout to 0 the system will indefinitely wait until you press Enter...

---

### Post by saltydog on 2008-11-17
> **red_team316 said:**
> The file you need to edit is:
/home/username/reconstructor/remaster/isolinux/isolinux.cfg



How can I completely jump over this phase and let the CD starts automatically with the usplash screen on the live-CD option?

I have made several tests, but I am giving up...
Thanks for any info

---

### Post by red_team316 on 2008-11-17
My bad, setting the timeout to 1 should work better.

As far as bypassing the rest of it, you'll have to look into the isolinux documentation a bit. I know that the LiveCD's never used to ask what language you wanted either, so still thats an extra ENTER. Take a look at a feisty LiveCD, I know they didn't ask for language at boot.

---

### Post by red_team316 on 2008-11-17
Here is some good info on it:
[http://members.chello.at/bobby100/ILpart1.htm](http://members.chello.at/bobby100/ILpart1.htm)

Try setting:
TIMEOUT 1
PROMPT 0

---

### Post by saltydog on 2008-11-18
Thank you very much.

I have set timeout 1 and PROMPT 0, so now isolinux doesn't wait for my enter to go ahead, but I have always the "F1...F6" showing in the bottom line, even thou I have removed them for isolinux.cfg! Where do they come from?

---

